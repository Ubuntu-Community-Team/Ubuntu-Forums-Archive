---
title: "Can't install 12.04 on Windows 8"
date: 2013-02-22
forum: Installation &amp; Upgrades
---

### Post by marcks on 2013-02-22
Hi

I would like to install Ubuntu 12.04 instead of Windows 8 but it isn't going well.

I run wubi.exe from a CD
It says to reboot with the CD in the tray
I reboot and it goes straight back into Windows

I reset the BIOS to boot from CD
No change

I tried using the option for not being able to reboot
when I get the choice to boot from the CD it says it is invalid

If I choose the boot to Ubuntu option I get a long message about Windows and at the end it says the following file is missing

\ubuntu\winboot\wubildr.mbr

what should I do?


Karen

---

### Post by oldos2er on 2013-02-22
You might find some help [here]("http://askubuntu.com/questions/225048/is-wubi-for-windows-8")
Otherwise please post your system specs and whether your system uses UEFI.

---

### Post by marcks on 2013-02-22
I have a Sony VAIO E Series Laptop
64 bit
i3 Processor
4gb RAM

It looks as if it uses UEFI on the USB and CD ports

I followed the link you gave and Ubuntu is not one of the Operating Systems in configsys

---

### Post by oldfred on 2013-02-22
wubi just does not work with gpt partitioning.

You choice is a full install.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

### Post by marcks on 2013-03-03
Thanks for the help. I couldn install from the usb, had to do it from a dvd. When I followed the instructions you gave the links for and used a dvd it worked fine.

thanks again
Karen

---

### Post by marcks on 2013-03-03
I can mark as solved because it isn one of the options under Thread Tools

---

### Post by oldos2er on 2013-03-03
See [this thread](http://ubuntuforums.org/showthread.php?t=2121377) for help in marking the thread solved.

---

