---
title: "Trouble Installing"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by testa101 on 2013-02-26
Hello everyone,

Okay, I've got some interesting issues, and I'd like to let people know that I'm a fairly novice user. I just got a Thinkpad X1 Carbon Touch Ultrabook and have been trying as hard as I can to install Ubuntu 12.10 on it, but just can't get it.

So I've used Unetbootin to install the iso along with Grub to a USB key and instead of the normal grub table with Try Ubuntu (without Installing), Install Ubuntu, etc, I just get a grub> prompt. 

So I try some stuff, eventually to figure out that what I think is the best way forward is to do the rest manually (as I come to find out that the config file hasn't loaded and [HTML]configfile (hd0,msdos1)/grub/grub.cfg[/HTML] does pull up the table, but all options result in errors.

So the commands I do are as follows:

[HTML]linux (hd0,msdos1)/casper/vmlinuz.efi.signed
initrd (hd0,msdos1)/casper/initrd.lz
boot[/HTML]

And from here I get into BusyBox... And I know **NO** BusyBox!! I've tried this both with Ubuntu 12.10 Desktop and Ubuntu 12.10 Server, both 64 bit. I torrented the ISOs from the Ubuntu website, and have used both to install on machines before. I've purged and reinstalled unetbootin to no avail.

Any ideas? Anyone know *where* the problem is?

Thank you

---

### Post by oldfred on 2013-02-27
Are you booting live flash in UEFI mode or BIOS mode. You should from UEFI menu get both options, but most systems should boot in UEFI mode.

If an UltraBook, you also have issues with that.
What video does your system have?

       Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)

            Asus S46CA Ultrabook Problems with Windows Recovery and grub after dual-boot install with Ubuntu 12.04
[http://ubuntuforums.org/showthread.php?t=2098477](http://ubuntuforums.org/showthread.php?t=2098477)

You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 

Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

 Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

