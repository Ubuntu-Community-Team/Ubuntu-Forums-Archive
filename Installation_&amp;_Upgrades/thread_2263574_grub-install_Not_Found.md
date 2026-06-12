---
title: "grub-install Not Found"
date: 2015-02-01
forum: Installation &amp; Upgrades
---

### Post by PopsTheSailor on 2015-02-01
I have 3 OS on my laptop. I have 1 windows 8, 1 Ubuntu 14.04 (sda9) and 1 Ubuntu 14.10 (sda7). Grub2 is installed and defaults to sda7. I want to have grub default to sda9. In the past, I thought all I had to do was boot to the install where I wanted to have grub default (sda9 in this case). Then run sudo gurb-install dev/sda9. The problem is that when I try to run the grub-install command I get an error stating: sudo: grub-install: command not found.

What's the command to move Grub2 to a different partition / install?

---

### Post by yancek on 2015-02-01
It's not that simple any more if you have windows 8 and you are using UEFI/GPT to boot.  If you have a pre-installed windows 8, it most likely uses UEFI.

On the other hand, if all you want to do is to have the default boot option be sda9 rather than sda7, you can change that.  Since it defaults to sda7 then the Grub bootloader on that partition is responsible for booting.  Boot Ubuntu 14.10, go to the /boot/grub/grub.cfg file and count down the menu entries to the entry for 14.04 then go to the /etc/default/grub file and change the line below which is at the top of the file:

> GRUB_DEFAULT=0 

Change the zero to whatever the entry was for Ubuntu 14.04.  Counts from zero so if the 14.04 entry was the 4th one, put a three there.  Save the file and run:  sudo update-grub

---

### Post by oldfred on 2015-02-02
Is install UEFI or BIOS?

If not sure of details post this:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by PopsTheSailor on 2015-02-03
Windows is installed under UEFI but the 2 Ubuntu partitions are now. I really have this all mucked up now!

---

### Post by yancek on 2015-02-03
I would suggest you take a look at the two links posted by oldfred above to get some info on UEFI and the bootinfo summary.

The efi files for both Ubuntu installs generally have the same name which causes problems.  One will have to be renamed and I'm not sure how to do that.  oldfred would be able to explains so wait for him or someone else to come along.  There is a general explanation of the problem at the link below dealing with Ubuntu/Mint as Mint was using the same name for its efi file.  Unfortunately, there is no solution with the explanation.

[http://www.zdnet.com/article/uefi-boot-with-kororafedora-and-mintubuntu-hands-on/](http://www.zdnet.com/article/uefi-boot-with-kororafedora-and-mintubuntu-hands-on/)

---

### Post by oldfred on 2015-02-03
If UEFI you may be able to change the name.
 UEFI install broken when GRUB_DISTRIBUTOR!=Ubuntu (e.g. Kubuntu/UbuntuStudio) Mostly fixed in Saucy & Trusty
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1242417](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1242417)
grub2 installs bootloader in \EFI\${GRUB_DISTRIBUTOR} directory, where
GRUB_DISTRIBUTOR is defined in /etc/default/grub. 

But if installed in BIOS mode, you only can dual boot from UEFI menu or perhaps one time boot key. UEFI and BIOS are not compatible. Once you start booting in one mode you cannot switch. Or then only installs in same boot mode can be used in grub menu.

Boot-Repair can convert a BIOS install to UEFI (or vice-versa). It uninstalls grub-pc(BIOS) and installs grub-efi-amd64 (UEFI). 
Boot-Repair has shown details of grub install in some versions:
 grub-install: info: Registering with EFI: distributor = `ubuntu', path = `EFIubuntushimx64.efi', ESP at hostdisk//dev/sda,gpt2.



Best to only install in one mode and always be sure to boot in that mode either always UEFI or always BIOS/CSM/Legacy. And if Windows 8 pre-installed in UEFI mode then always use UEFI mode.

---

### Post by PopsTheSailor on 2015-02-03
Thanks. I'm going to close this thread. I have a Dell Inspiron and I can't figure out how to let me boot from the DVD when in UEFI mode. I use windows just for a fishing game and nothing else. I'm set up to give me the my Ubuntu partitions and can work my way though the Boot process if I want to get over to Windows. Good enough. This is all too complicated to troubled with. 

I really do appreciate your help and comments!
Thanks

---

