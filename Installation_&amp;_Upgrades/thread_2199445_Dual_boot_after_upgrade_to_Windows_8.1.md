---
title: "Dual boot after upgrade to Windows 8.1"
date: 2014-01-13
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2014-01-13
Has there been a consensus on how to fix the dual boot after upgrading to Windows 8.1?  I see many, many solutions on the net and AskUbuntu etc... but each "solution" seems to have some who say it works and some that say it doesn't work.  And usually the process is not very clear or in more simple terms.  Some solutions are on the windows side and some on the linux side.  I have not been able to find a solution using bootrepair.   I have two computers with similar situations, but different Ubuntu versions.

What are the accepted solutions from Ubuntu?  What is their response to this?  Is there going to be a solution for this in the next release?  I feel for the beginner ubuntu user this would be a game changer and an obstacle insurmountable. 

Thanks,

Dennis

---

### Post by oldfred on 2014-01-14
The issue is every vendor's implementation of the UEFI 'standard' does not follow the standard or standard is not specific enough.

So different work arounds are needed for just about every system and sometimes versions by vendor are different particularly Intel vs AMD and video issues or Ultrabook with Intel SRT issues.

There is a specific bug report on 8.1 secure boot.
       Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

But some UEFI specifically only boot Windows. They hard code the Windows description into UEFI which is not part of standard.

And it seems Windows syncs its BCD with the UEFI NVRAM so it can always be first in boot order with UEFI as Windows always thinks it is the only system you want to boot.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

