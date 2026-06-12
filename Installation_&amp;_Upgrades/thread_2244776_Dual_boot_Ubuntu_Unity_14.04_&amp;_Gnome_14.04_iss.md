---
title: "Dual boot Ubuntu Unity 14.04 &amp; Gnome 14.04 issue"
date: 2014-09-18
forum: Installation &amp; Upgrades
---

### Post by eipapp on 2014-09-18
OK, I'm confused. I've been running Ubuntu 14.04 on my system for the past few months and today decided to set-up a dual boot with Ubuntu 14.04 Gnome. 
However, when I re-start my machine it goes right into Ubuntu Unity and does not give me the option to even select Gnome. What Happened???
When I run G-Parted the Gnome partition is clearly there. Can someone help me to resolve this issue, please.
I'm running a HP-Pavilion 23 desktop.

Thanks,
Bruce

---

### Post by grahammechanical on 2014-09-18
In Ubuntu run

```
sudo update-grub
```

and in the printout see if Grub is detecting a Linux kernel on that Ubuntu Gnome partition. Do not expect Grub to list Ubuntu Gnome but Ubuntu on sdax. If you are dual booting and only have one hard disk and Ubuntu Gnome was installed second I would expect the system to be automatically loading Ubuntu Gnome. And I would expect the configuration file in Ubuntu to be unware of the existence of Ubuntu gnome until sudo update-grub is run in Ubuntu.

Regards.

---

### Post by Dennis N on 2014-09-18
It would be informative as well to know the installation mode of each - UEFI or BIOS. This can affect what happens on startup.

---

### Post by eipapp on 2014-09-18
This is output of "sudo update-grub" and GParted view: (Hope I did this right)```
[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=256537&stc=1&thumb=1&d=1411089909[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=256537&d=1411089909")
```[[IMG]http://ubuntuforums.org/attachment.php?attachmentid=256538&stc=1&thumb=1&d=1411089930[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=256538&d=1411089930")

---

### Post by Dennis N on 2014-09-19
Tentative conclusions based on your two images: 

Your Ubuntu on sda2 looks like it was installed in UEFI mode. The Ubuntu Gnome on sda5 could have been installed in BIOS mode (this is not clear from just the posted images). If so, the UEFI boot loader might not be able to load an OS installed in BIOS mode - I have seen mixed reports on this for different distros - and I imagine it might not even appear on the (grub) menu.  

In any case, you should be able to start Ubuntu Gnome from the UEFI firmware boot menu options.

---

### Post by grahammechanical on 2014-09-19
My guess is that in the Grub boot menu the label "Ubuntu" would load the image found at /boot/vmlinuz-3.13.0-35-generic and that should be Ubuntu + Unity. And the label Ubuntu 14.04.1 LTS (14.04) on /dev/sda5 would load Ubuntu Gnome.

Do not expect to see a Ubuntu Gnome label in Grub because Grub gets its labels from a file call os-release. Boot into both Ubuntu and Ubuntu Gnome and run

```
cat /etc/os-release
```

and you will see that it is the same file in both Ubuntu and Ubuntu Gnome. Now, if you are not seeing a Grub boot menu it could be that you have set the time out from 10 seconds to zero or perhaps that warning message about setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set as being no longer supported is the cause of the problem. Have you been editing the Grub configuration files?

Regards.

---

### Post by fantab on 2014-09-19
UEFI systems can boot in both EFI and 'Legacy' modes. To boot in EFI you need an ESP (efi system partition), and to boot in 'legacy' mode you need a 'bios_grub' partition.
If you have one system installed EFI then you must have the os too in EFI... it appears that you have one with EFI and one with 'legacy'... It works but its a PITA. 

[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") tools can effortlessy convert a 'legacy' boot to UEFI....
but first install run Boot-Repair (pereferably from a Live media), '*create a BootInfo Summary*' (don't run any repairs just yet), note down the url link it creates to the bootinfo file and post it here.

---

### Post by Dennis N on 2014-09-19
> Boot-Repair tools can effortlessy convert a 'legacy' boot to UEFI....

Very interesting discussion. I will be waiting to see how Boot Repair can manage to have both of these - Ubuntu and a Ubuntu derivative - both boot in UEFI mode and be on the same disk. I am seeking installation solutions for doing just that.

EDIT: Boot Repair can fix this: see [http://ubuntuforums.org/showthread.php?t=2244950](http://ubuntuforums.org/showthread.php?t=2244950) for a similar case. But, Boot Repair leaves you with a system with a /boot/efi/EFI/ubuntu folder for only the final install. Still, you can boot the first install from the grub of the 2nd install. Should you remove the second install, the first is left no longer bootable. If you initially did normal installs using default grub location of both Ubuntu and the derivative in UEFI mode (no boot repair needed), this would result in the same state of affairs.

---

### Post by eipapp on 2014-09-29
Sorry I couldn't get back to you sooner, Dennis.
I installed Boot Repair, ran it, and this is the output. 
Let me know what other information you need before I proceed.

Thanks for your patience. Bruce

[ATTACH=CONFIG]256823[/ATTACH]

---

### Post by eipapp on 2014-09-29
Dennis,

Should have included this with my last post.............My apologies.

[ATTACH=CONFIG]256824[/ATTACH]

---

### Post by Dennis N on 2014-09-30
@eipapp

Hi,

Looking over the boot info you posted at: [http://paste.ubuntu.com/8462632/](http://paste.ubuntu.com/8462632/), it appears you have just one OS on this system. 

sda1 contains the only OS:

```

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 
```
    
    
and it's not in UEFI mode or using GPT, and SecureBoot is disabled. (I notice that in post #2, you have a setup for UEFI, which no longer exists here. Did you reinstall?)
    
```
    =================== UEFI/Legacy mode:
This installed-session is not in EFI-mode.
SecureBoot disabled.


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	grubenv-ok	grub2,	grub-pc ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes

```

So, it seems straightforward that if you plan to dual boot, install the other OS in BIOS (Legacy) mode also, and then boot in the same mode. If both systems are installed in the same mode (both BIOS or both UEFI), GRUB should detect the other one and show it on the menu as you expect. Both should work.

---

### Post by eipapp on 2014-09-30
Dennis,

Oh snap !!  Yes I did do a reinstall but with everything that has been going on in our lives, of late, I completely forgot. So Very Sorry.
If I understand you correctly then I should be able to install Gnome or another Linux distro on my machine without any issues as regards UFEI.
Are there any special things I should look out for or do when installing the second Linux OS or just let it do it's normal thing and it will come out all right?
Thanks again for all your help, it's much appreciated.

Bruce

---

### Post by eipapp on 2014-10-05
Hi Dennis,

Just a quick update. I was able to install a second Linux OS on my machine and can now dual boot into either OS with no problems.
Thanks again for all your help.


Best,
Bruce

---

