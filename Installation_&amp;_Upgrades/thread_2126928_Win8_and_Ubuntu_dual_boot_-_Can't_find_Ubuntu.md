---
title: "Win8 and Ubuntu dual boot - Can't find Ubuntu"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by feljin on 2013-03-18
I couldn't find a thread with a similar issue to mine so here's my issue, sorry if I missed something completely stupid.

I booted from USB and installed Ubuntu on a separate partition to dual boot with Windows 8. The installation went fine and eventually it told me to restart..so I did. But when the computer starts up it just takes me straight to Windows 8 :(
I've tried several times but it doesn't give any options. How do I Get to Ubuntu??

I've dual booted W8 before with XP, 7 etc. and it used to take me to a Blue Win8 screen and ask me which OS I'd like to boot..

What am I missing here??

---

### Post by oldfred on 2013-03-18
Was this Windows 8 pre-installed with secure boot?

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

Post link to BootInfo report.

      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by tejpatel98 on 2013-03-18
If I understand correctly, you used the Wubi installer? If so you had to have installed Windows 8 on your computer after you got it. If Windows 8 came pre-installed then I don't think that you can use Wubi.

---

### Post by feljin on 2013-03-23
This came with Windows 8 pre installed. Secure boot definitely seems to be the problem, I wasn't aware of it when I tried to install Ubuntu. I guess I'll try [this]("http://blog.hansenpartnership.com/linux-foundation-secure-boot-system-released/") when I have more time

---

### Post by oldfred on 2013-03-23
Ubuntu is using shim.
 UEFI generic shim - Secure Boot bootloader
[http://mjg59.dreamwidth.org/20303.html](http://mjg59.dreamwidth.org/20303.html)

[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/) 
> Yes, and that's actually pretty much the plan now. I'm working on  integrating the LF loader's UI and security code into Shim with the aim  of producing one loader that'll satisfy the full set of use cases, and  James is [happy with this]("http://blog.hansenpartnership.com/linux-foundation-secure-boot-system-released/#comment-4152").

[h=3][/h]

---

