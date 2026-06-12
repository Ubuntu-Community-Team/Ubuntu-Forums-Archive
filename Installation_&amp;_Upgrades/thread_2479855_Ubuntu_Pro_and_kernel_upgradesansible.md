---
title: "Ubuntu Pro and kernel upgrades/ansible"
date: 2022-10-10
forum: Installation &amp; Upgrades
---

### Post by allbits on 2022-10-10
Hi,

I am trying out ubuntu pro with live patch. My system just did an upgrade from 5.15.0-48-generic to 5.15.0-50-generic. The 5.15.0-50-generic packages were installed but the running kernel version with uname -r was reported as 5.15.0-48-generic. A reboot was not indicated as being required. This is causing issues with my ansible scripts that would otherwise reboot the system if a reboot was required. I am a bit unclear if this is expected behavior or not. I know livepatch should provide security updates, but i would assume a new kernel version would result in a reboot still being flagged as required. Once doing a manual reboot my kernel version is reported as 5.15.0-50-generic. From my perspective a reboot should still have been reported as required..

---

### Post by MAFoElffen on 2022-10-10
In the LivePatch Documents, the first paragraph:
> 
[Ubuntu Livepatch]("https://ubuntu.com/security/livepatch")  patches high and critical linux kernel vulnerabilities removing the  immediate need to reboot to upgrade the kernel, instead allowing the  downtime to be scheduled.

I have thought about this a while now... I too would think that if a kernel updated versions without having to reboot (which is the whole premise and selling point to LivePatch) that if it did change the kernel version, that with that process, that it should also update the environment to know that it is running on an updated kernel version.

If the goal is to not have to reboot to the newer kernel, so that the server stays up and is available for services, then I feel that not updating the enthronement for that change is "a missing step" in that process.

I think that it should not flag ansible for a reboot, because that would defeat the goal of not having to reboot... But that is should update the running environment of the kernel version change.

I feel that missing step is a BUG that should be addressed in the LivePatch process. But how that is worded, they have an out on
> 
"*...instead allowing the  downtime to be scheduled."*


---

