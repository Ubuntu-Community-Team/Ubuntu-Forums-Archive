---
title: "Thinkpad Dual boot with Windows 8 and 12.10 with UEFI"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by x509 on 2012-12-12
Hi,
I have exactly the same problem as MichelT but with a Lenovo ThinkPad S230u with Secure Boot enabled. Grub starts Ubuntu 12.10 without problems, but Windows 8 doesn't and can be booted via F12 and the UEFI's Boot Order Menu only.  As a temporary workaround this is ok but a proper fix by Ubuntu would be welcome.

Regards

Andreas

---

### Post by oldfred on 2012-12-12
Moved to your own thread.

Grub2 has a bug in its os-prober. I creates the old BIOS style chain load entry when with UEFI it has to be different. If you create a launchpad sign-on you can add to the bug. They fix the one's with the most reports or most critical issues.

       Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
'Windows ...) (on /dev/sdXY)'

Boot-Repair will add a correct chain entry back to the Windows efi entry. Then you can set Ubuntu as default from UEFI menu but choose either to boot.

You can run from your Ubuntu install, from the Ubuntu ISO DVD or flash or download a full repair version.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by moteprime on 2013-01-02
I had the exact same problem on a Thinkpad e130. 12.10 + Win8 dualboot.
Fixed it with boot-repair. +disable "Secure boot" in bios, "Quick startup" are enabled.

Thanks!!

---

