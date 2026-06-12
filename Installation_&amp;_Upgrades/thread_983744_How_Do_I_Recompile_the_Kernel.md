---
title: "How Do I Recompile the Kernel"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by HDTimeshifter on 2008-11-16
I installed Virtualbox, but when I try to start it, it complains that I need to disable the KVM kernel extension and recompile the kernel.  I removed the KVM kernel in Synaptic Package Manager, but I don't know how to recompile the kernel.

Here is the error message:
> 
VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot.
VBox status code: -4011 (VERR_VMX_IN_VMX_ROOT_MODE).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Console
Interface: 
IConsole {e3c6d4a1-a935-47ca-b16d-f9e9c496e53e}

---

### Post by Partyboi2 on 2008-11-16
You may not have to recompile your kernel according to [[COLOR=Blue]this[/COLOR]]("http://www.thesigb.com/weblog/2008/oct/28/virtualbox-and-kvm-conflict/") you may only need to 
```
sudo /etc/init.d/kvm stop
```

---

### Post by HDTimeshifter on 2008-11-18
Thanks, that worked.  However, when I logged off Ubuntu, rebooted and re-logged in, it looks like KVM reloaded I have to unload the KVM module again to start Virtualbox.  In Synaptic Package Manager, it looks like all the KVM stuff is not installed.  Do you know what to do to keep KVM from loading on startup?

---

### Post by Partyboi2 on 2008-11-19
When you removed it from Synaptic did you [[COLOR=Blue]purge [/COLOR]]("https://help.ubuntu.com/community/KVM#Removing%20KVM")it? 
Here is another thread talking about it.
[http://backports.ubuntuforums.com/showthread.php?t=824795](http://backports.ubuntuforums.com/showthread.php?t=824795)

---

### Post by Nandro3 on 2009-10-24
I have the same error but I have no /etc/init.d/kvm .  So if there is no KVM file or Dir whats making that happen?

---

### Post by thgruiz on 2010-05-21
guys.... 

apt-get remove qemu-kvm

on
Linux user-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

---

### Post by 1script on 2010-11-16
In my case (*virtualBox 3.2.10 r66523* on *Ubuntu 10.04 LTS*) just "sudo apt-get remove qemu-kvm" did not work  

But this did: 
```
sudo aptitude remove qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils
```
Apparently bridge-utils was still hanging in there and VirtualBox would not work until I remove it...

---

### Post by stanz on 2011-01-24
> **1script said:**
> In my case (*virtualBox 3.2.10 r66523* on *Ubuntu 10.04 LTS*) just "sudo apt-get remove qemu-kvm" did not work  

But this did: 
```
sudo aptitude remove qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils
```Apparently bridge-utils was still hanging in there and VirtualBox would not work until I remove it...

Wow..this is going on for awhile!!
Glad to see {upper post} someone on laptop has it working..many posts say 'no way'.
I'm gonna try this also...the 'bridge-utils' is new.
Will post back results!

---

### Post by stanz on 2011-01-24
Success !!
I made sure first, that anything 'kvm & qemu' was not installed.
Found 'bridge-utils' & un-installed that also.

Ran in terminal:
~$ lsmod | grep -i kvm
kvm_amd                37070  0 
kvm                   286367  1 kvm_amd

~$ sudo modprobe -r kvm-amd (should return nothing!)
~$ lsmod | grep -i kvm (again, should return nothing.)

Then I opened: /etc/modprobe.d
And 'as Root' edited the 'blacklist.conf' file by adding: blacklist kvm_amd

Rebooted and fired up VBox-4 with no more errors!!

---

