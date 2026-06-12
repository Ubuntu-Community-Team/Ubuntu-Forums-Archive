---
title: "Trying to install Windows 10 on Virtualbox and having difficulties."
date: 2021-02-02
forum: Installation &amp; Upgrades
---

### Post by oldnew1786 on 2021-02-02
I have virtualbox installed. I have a virtual machine created.

When I go to attach the ISO file to the empty slot, I get this message: 
Failed to open the disk image file **/home/user/Downloads/Win10_20H2_v2_English_x64.iso**.

Could not get the storage format of the medium **'/home/user/Downloads/Win10_20H2_v2_English_x64.iso'** (VERR_NOT_SUPPORTED).

[TABLE="width: 100%"]
[TR]
[TD]Result Code: [/TD]
[TD]VBOX_E_IPRT_ERROR (0x80BB0005)[/TD]
[/TR]
[TR]
[TD]Component: [/TD]
[TD]MediumWrap[/TD]
[/TR]
[TR]
[TD]Interface: [/TD]
[TD]IMedium {ad47ad09-787b-44ab-b343-a082a3f2dfb1}[/TD]
[/TR]
[TR]
[TD]Callee: [/TD]
[TD]IVirtualBox {d0a0163f-e254-4e5b-a1f2-011cf991c38d}[/TD]
[/TR]
[TR]
[TD]Callee RC: [/TD]
[TD]VBOX_E_OBJECT_NOT_FOUND (0x80BB0001)[/TD]
[/TR]
[/TABLE]

I also have an official Windows USB flash drive, but IDK how to use it with virtualbox as I had problems trying to get it to work.

---

### Post by CelticWarrior on 2021-02-02
The ISO is probably corrupt: [https://forums.virtualbox.org/viewtopic.php?t=66675](https://forums.virtualbox.org/viewtopic.php?t=66675)

---

### Post by oldnew1786 on 2021-02-02
Tried it again and I was able to attach the ISO for some unknown reason but then I get this error:
"RTR3InitEx failed with rc=-1912 (rc=-1912)
The VirtualBox kernel modules do not match this version of VirtualBox. The installation of VirtualBox was apparently not successful. Executing
'/sbin/vboxconfig'
may correct this. Make sure that you are not mixing builds of VirtualBox from different sources.
where: supR3HardenedMainInitRuntime what: 4 VERR_VM_DRIVER_VERSION_MISMATCH (-1912) - The installed support driver doesn't match the version of the user."

Edit: Thanks for the help CelticWarrior. I got the ISO to work by exiting and entering virtualbox. Now I have the above problem.

---

### Post by CelticWarrior on 2021-02-02
You should get into the habit of googling the error messages:
[https://stackoverflow.com/questions/41146264/virtualbox-verr-vm-driver-version-mismatch-on-ubuntu](https://stackoverflow.com/questions/41146264/virtualbox-verr-vm-driver-version-mismatch-on-ubuntu)
[https://superuser.com/questions/971844/how-to-solve-the-installed-support-driver-doesnt-match-the-version-of-the-user](https://superuser.com/questions/971844/how-to-solve-the-installed-support-driver-doesnt-match-the-version-of-the-user)
[https://askubuntu.com/questions/789451/virtualbox-failed-to-install](https://askubuntu.com/questions/789451/virtualbox-failed-to-install)

So, how exactly have you installed Virtualbox?

---

### Post by oldnew1786 on 2021-02-02
> **CelticWarrior said:**
> You should get into the habit of googling the error messages:
[https://stackoverflow.com/questions/41146264/virtualbox-verr-vm-driver-version-mismatch-on-ubuntu](https://stackoverflow.com/questions/41146264/virtualbox-verr-vm-driver-version-mismatch-on-ubuntu)
[https://superuser.com/questions/971844/how-to-solve-the-installed-support-driver-doesnt-match-the-version-of-the-user](https://superuser.com/questions/971844/how-to-solve-the-installed-support-driver-doesnt-match-the-version-of-the-user)
[https://askubuntu.com/questions/789451/virtualbox-failed-to-install](https://askubuntu.com/questions/789451/virtualbox-failed-to-install)

So, how exactly have you installed Virtualbox?

IDK how I installed Virtualbox. I have gone through many times of installing it and uninstalling it. It seems to be working now, so I now have my windows 10 on Virtualbox.

Thanks for your help.

---

