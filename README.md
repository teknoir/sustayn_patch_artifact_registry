# sustayn_patch_artifact_registry
A repo for an ansible play to patch devices with pull secrets for artifact registry

Using Kubeflow pipeline set up from: https://github.com/teknoir/ansible-kubeflow

This play is scheduled by the supplied flow, that can be added to a Devstudio.

The flow runs 1/day.

The filter/limit in ansible i set to:
```
hardware_nvidia_jetson_nano_b00,!ar_access_enabled
```
Where we first select the devices that should be patched, in this case all devices with hardware=mvidia-jetson-nano-b00.
Secondly we only patch those who dont already have the label ar_access=enabled. This label is then added to any 
successful play run on a device. By doing this we ensure we only patch devices that have not been patched before. 
