---
title: "Kernel update failed - Help removing and retrying manually"
date: 2022-08-27
forum: Installation &amp; Upgrades
---

### Post by securitydad on 2022-08-27
The Kernel update that was started this week failed.  It actually blocked all network connections.  After rebooting the system into an older kernel, I restored access to the network.

I would like to remove the new kernel, and manually update the OS (not using the Software Mangler).  I have two questions.

What command do I use to list the installed Kernels?

What command will delete the newer kernel??

Thank you.

---

### Post by tea for one on 2022-08-27
> **securitydad said:**
> 
What command do I use to list the installed Kernels?
```
ls /boot | grep vmlinuz-
```

I would not remove the latest kernel because some of the packages are involved in future kernel updates.
You must always have these installed [COLOR="#0000FF"]linux-generic linux-headers-generic linux-image-generic[/COLOR]

It may be better to use the earlier kernel temporarily and wait for a kernel upgrade to see if your network problem is resolved.

To remove kernels, I use 
```
sudo apt remove *5.15.0-27*
```
Of course, you have to change the kernel id to reflect the packages you wish to remove.

---

### Post by grahammechanical on 2022-08-27
> manually update the OS (not using the Software Mangler).

Ubuntu Software runs three apt commands and the refresh snap command. To manually update run these two commands.

```
sudo apt update
sudo apt upgrade
```

Those commands will update and upgrade all software packages including Linux kernels. Old kernels are not removed. To remove old kernels leaving just two run this command

```
sudo apt autoremove
```

Any obsolete software packages will also be removed.

Regards

---

### Post by securitydad on 2022-09-01
Thanks everyone, this is harder given that networking is completely hosed.  I have retrieved the needed data, and I am re-installing.

---

