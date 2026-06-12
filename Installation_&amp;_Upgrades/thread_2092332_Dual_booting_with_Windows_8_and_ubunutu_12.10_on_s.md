---
title: "Dual booting with Windows 8 and ubunutu 12.10 on samsung series 5"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by kiranchavala on 2012-12-07
windows 8 came pre installed on my new samsung ultrabook series 5

i disabled the secure boot and installed ubuntu 12.04 on a partition  during instaerllation i created a separate partion Reserved for Bios as the installer demanded not sure why

After installing ubuntu 12.10

and repaired  the grub using boot repair

Out put 
[http://paste.ubuntu.com/1417126/](http://paste.ubuntu.com/1417126/)

After a reboot able to login to windows but not to ubuntu from the grub menu 

Please try to solve my problemn

---

### Post by oldfred on 2012-12-07
Welcome to the forums.

So you get grub menu & Windows works.

Then Boot-Repair seems to have fixed grub's part of booting and now you are into loading kernel and devices. Often video issue or other boot parameter required for some of the new hardware.

Also in UEFI/BIOS have you turned quick boot off?

What video chip do you have? 
Have you tried recovery mode from advanced grub menu?

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

[http://www.linlap.com/samsung_np530u3b](http://www.linlap.com/samsung_np530u3b)

This was a series 7 user, but may be similar?
       
 Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

---

### Post by kiranchavala on 2012-12-07
Hi 

My graphics card is intel HD 4000

The quick boot is turned off 

I had tried with Recovery mode and also adding nomodset in the boot

It was giving Kernel panic - not syncing: Fatal Machine Check

It reboots later on gets back grub menu 

A fresh installtion of linux works fine but dual booting seems to be a issue

will try with acpi=off option and let u know

This tried with this link also
[http://askubuntu.com/questions/221328/kernel-panic-fatal-machine-check](http://askubuntu.com/questions/221328/kernel-panic-fatal-machine-check)

---

### Post by oldfred on 2012-12-07
I have seen it said that the Intel graphics just work.

Some other boot options for Intel even though different vendor.

       Asus i3 with Intel graphics, 
"acpi_osi=Linux"
"video=1280x1024-24@75" or whatever native resolution is

---

### Post by kiranchavala on 2012-12-08
tried with 
"acpi_osi=Linux"
"video=1280x1024-24@75" 

No progress so far

---

### Post by oldfred on 2012-12-08
In recovery mode it does not have splash quiet so you should see the loading process. Does it show anything errorring out or having issues.

Same entries are in log files. From liveCD/Flash you can mount your install and look at log files. I look at dmesg but there are many log files in /var/log.

Change example sda6 to your Ubuntu partition

       sudo mount /dev/sda6 /mnt
gksudo gedit /mnt/var/log/dmesg


Look for outright errors, long boot time spacing, or repeated tries and then it just gives up type entries.

---

### Post by kiranchavala on 2012-12-11
The Dual Booting is worked  Fine of Ubuntu 12.04 

Thanks very much for the help

---

### Post by Thimoteus on 2012-12-11
> **kiranchavala said:**
> The Dual Booting is worked  Fine of Ubuntu 12.04 

Thanks very much for the help

Could you let us know what changes you made that made it work?

---

### Post by wild_oscar on 2012-12-23
It would be nice to other users to post the resolution to your problem, as it can benefit other users...

---

### Post by mobiu5 on 2012-12-23
> **wild_oscar said:**
> It would be nice to other users to post the resolution to your problem, as it can benefit other users...

I agree.  I am having a similar problem...

[http://ubuntuforums.org/showthread.php?t=2097575]("http://ubuntuforums.org/showthread.php?t=2097575")

---

### Post by fhyusran on 2012-12-26
Hi all,

I am planning to do the same to my one-week old Samsung Series 5 but with Ubuntu 12.10.  So, it would be nice to have a step by step how to as suggested earlier.  kiranchavala has done with Ubuntu 12.04, right?.

Waiting for the how-to from oldfred.

---

### Post by oldfred on 2012-12-26
oldfred does not have an howto. With 12.10 it just works for most users to install. But you may then have all the other driver type issues like video, Internet or others which vary a lot.

The links to this are current and Boot-Repair can fix BIOS installs in case you did not install in UEFI mode. And you have to use Boot-Repair to fix grub2's bug on linking to the correct efi entry to chain to Windows (or you can manually add a chain entry).
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

Grub2's standard chain entries have this type of description and these do not work.
'Windows ...) (on /dev/sdXY)'

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

       [http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)
    
Most of the links oldfred posts:
       Some general UEFI info from oldfred and links.
[http://ubuntuforums.org/showthread.php?t=2086883](http://ubuntuforums.org/showthread.php?t=2086883)

Otherwise best to start own thread with specific issue in title.

---

