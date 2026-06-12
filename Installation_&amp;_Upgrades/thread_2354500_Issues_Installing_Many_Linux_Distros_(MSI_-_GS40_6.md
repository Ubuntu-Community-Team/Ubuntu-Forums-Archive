---
title: "Issues Installing Many Linux Distros (MSI - GS40 6QE Phantom)"
date: 2017-03-03
forum: Installation &amp; Upgrades
---

### Post by utnubu4 on 2017-03-03
Hey folks,

I had a new laptop a few months ago and I attempted to install Ubuntu but failed so I gave up. Today I decided that I would make another attempt but using many different distros until one installed, I gave Ubuntu another try of a reinstall; failed. I gave Apricity a try; failed. I gave Bodhi a try; failed. I gave Magia a try; failed, and I gave Mint a try; failed. During the installation stage it seems that the issue is with the new OS installing a new partition on my SSD and attempting to completely overwrite it. To be honest I am completely clueless as to why these issues keep occurring? My laptop is an MSI and after purchasing it I did research to discover that MSI are not particularly great with Linux installs, but people have installed them and state that it can be done.

Laptop information:

Model - GS40 6QE Phantom
Processor: Core I7
GPU: Geforce GTX970M
Ram: 8gb
Disks: 125gb SSD & 1tb HDD
Current OS: Linux distros, installed but cannot boot. (Lost my windows OS trying Linux installs).

It would be truly great to get some help if possible because I would really like a Linux OS on this laptop and I want to completely write over the SSD. I am currently writing this booted up from the live version of Apricity.

Thank you very much for taking the time to read this!

---

### Post by yancek on 2017-03-03
How old/new is this hardware?  Which version of windows?  If 8 or 10, it is most likely using UEFI.  If that is the case, you need to boot Ubuntu (or whichever distribution you try to install) UEFI and install UEFI.  Some info on dual booting windowsUbuntu UEFI at the link below.  If you are using an older version of windows, post that info.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Ubuntu and most likely the other OS's you tried to install give you several Installation Type options.  Which did you use?  If you can open a terminal booting from Apricity, try running the command:  fdisk -l (Lower Case Letter L in command).  You may need to preface it with su - or sudo, post the output here.

---

### Post by utnubu4 on 2017-03-03
New hardware and the version of windows was 10 but no longer exists on my SSD.

I have attempted to boot them up in UEFI but nothing at all works... the distros will only boot up in Legacy mode. I did manage to get Apricity installed and I am current running it, but I can only install it if I install next to the previous install that failed, so I basically now have a corrupted install on my SSD and this working install next to it. I am irritated because I do not want my SSD to be partitioned when I require that disk space for usage.

I really need help and I do not have a clue.

---

### Post by Bucky Ball on 2017-03-03
Just a note: This is a Ubuntu forum. Consequently, if you can boot to a live session of Ubuntu it will give you a better chance of getting help as we'll have a better idea of how to do what you need to.

A start would be to boot into the BIOS and start checking out what setting are set for UEFI. Note down what you can find and post back. If you've wiped your Windows, accidentally or otherwise, may be causing issues. Check the boot repair link at the bottom of my post, don't do a recommended repair but use it to run the 'bootinfo script' and post the link it give you back here. That will show us what is currently on that disk.

* Just read your last post. So what do you want to do from here? If you want a blank SSD, boot to a live Ubuntu session, launch Gparted, delete all partitions. Done. Click the install button on the desktop, choose 'Something Else' at the partitioning section and you can manually partition the disk how you like.

---

### Post by utnubu4 on 2017-03-05
I cannot boot into Ubuntu live.. it just crashes out at the grub menu. I am currently running Apricity which is installed but I would much prefer to be running Ubuntu. If anyone could help me get Ubuntu working on my laptop that would be great!     OK I will take a look at the bios settings now, I will be sure too note down the settings and post them back here.    Yes I want to completely overwrite my SSD with Ubuntu only but this laptop needs some tweaking before most Linux distros will run. I currently have Gparted installed in Apricity but I cannot delete the other partition where the failed installation is installed.   Edit: The only UEFI settings that I have are to do with booting and UEFI update. I have fastboot disabled, secure boot disabled and I just tested and the USB will not load any of the dostros. The current Apricity OS that I have installed will not even boot in these settings.

---

### Post by yancek on 2017-03-05
If you have Apricity installed and GParted on it, you should be able to delete the 'other' partition with the failed install.  Open GParted and click on the partition you want to delete to highlight it.  Then right click that highlighted entry and select 'unmount'.  You can't modify mounted partitions.  Posting an image of the GParted windows here would be helpful.

---

### Post by utnubu4 on 2017-03-05
I do not care about the partition at this moment because I would just like to install Ubuntu instead of Apricity. Can anyone please help with the Ubuntu installation on my laptop please?  The only UEFI settings that I have in the BIOS are for the boot options. I had secure boot disabled, quick boot disabled and nothing will boot up in UEFI.

---

### Post by Bucky Ball on 2017-03-05
In Apricity, [download Ubuntu 16.04.2 from here]("https://www.ubuntu.com/download/desktop"), download UNetbootin [from here]("https://unetbootin.github.io/"). 

Plug in the USB, open Gparted, right click any partitions on it, unmount them. Go to 'Device> Create new partition table'. Once complete, right click on the empty space there and create one FAT32 partition on the entire USB.

Once complete, open UNetbootin and create a bootable USB from the Ubuntu ISO you downloaded. When that's done, reboot and get back to the BIOS.

You have nothing else on this SSD and you are not running Windows? Switch off everything to do with UEFI, save and continue. This should take you to a restart. On that restart, try hitting F12 and see if that gives you a boot device menu. If so, choose the USB. If not, reboot back to the BIOS and set the BIOS to boot from the USB device. 

Let us know what happens.

(PS: Apricity is based on Arch Linux which has nothing whatever to do with Ubuntu or Debian, so no idea whether any of the above is possible on your machine. No idea whether Unetbootin will run on Arch.)

---

### Post by utnubu4 on 2017-03-05
Hi Bucky,  I have Ubuntu already on my USB and I can boot into the grub menu but when I choose install Ubuntu or live version it crashes out when loading up. The USB is fine and boots up and installs fine on my old laptop. The main issue is with my MSI laptop... after doing some research I have discovered that MSI have issues with Linux installs but it can be done.

---

### Post by Bucky Ball on 2017-03-05
What do you mean 'it crashes out'? What exactly happens? Have you tried booting with the nomodeset option?

---

### Post by oldfred on 2017-03-05
While not your model, other MSI systems have required boot parameters.
And generally issues are by brand, so you probably need one or more boot parameters.
If you have nVidia chip/card then you at least need nomodeset, and probably libata.force=noncq and/or acpi=off.

 Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[URL="http://ubuntuforums.org/showthread.php?t=2298912"]http://ubuntuforums.org/showthread.php?t=2298912

[/URL]
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

[URL="http://ubuntuforums.org/showthread.php?t=2298912"]
[/URL]

---

### Post by utnubu4 on 2017-03-05
When I choose to boot into live or install from the grub it crashes on the Ubuntu loading screen.  What is booting with the nomodset option please?

---

### Post by utnubu4 on 2017-03-05
Yes I do have a nVidia graphics chip. Thank you for the information I will take a look at the links now! How do I get nomodset please?

---

### Post by Bucky Ball on 2017-03-05
> **oldfred said:**
> 

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

[URL="http://ubuntuforums.org/showthread.php?t=2298912"]
[/URL]

Like oldfred said ...

---

### Post by utnubu4 on 2017-03-05
Hey guys,

I got into the Ubuntu setting at grub, pressed f6 and enabled [COLOR=#000000]nomodeset, this then allowed me to boot up Ubuntu.. I tried to install and over the whole SSD and it failed again at the grub part of the installation stating "fatal error". This also happened with the other distros that I tried. I decided to do what worked for the Apricity install; installed Ubuntu along side the installation the just failed. This method actually allowed the full Ubuntu installation to complete fully. I reset the laptop, removed the USB and Ubuntu still wouldn't load.

So I am a little closer than before but now I have Ubuntu installed with a smooth install it still will not boot up? [/COLOR]

---

### Post by oldfred on 2017-03-05
If getting f6 way to add grub, that is BIOS boot and your install will be in BIOS boot mode.
Is not system UEFI and you want UEFI boot mode?
Your UEFI boot menu should have two boot options, one 'UEFI:flash' and the other 'flash' (BIOS) where flash is name, label or brand of flash drive.

If you are using manual partitioning and you had UEFI Windows, then it was gpt partitioned.
With gpt partitioning you need the ESP - efi system partition for UEFI or the bios_grub partition for BIOS boot.
I still add both partitions to all new gpt partitioned drives although only one or the other is used. 

 Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI) 

      
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by utnubu4 on 2017-03-05
Here are the results from the boot-info oldfred: [http://paste.ubuntu.com/24118958/](http://paste.ubuntu.com/24118958/)

---

### Post by oldfred on 2017-03-05
It looks like you have installed in BIOS boot mode to drive sda. But system is UEFI.
Boot-Repair says you may have Secure Boot on, best to check to make sure it is off. Cannot boot in BIOS mode with Secure Boot on.

Report only mentions NVMe drive.
Other brands have had issues with the new NVMe drives, often vendor issue that gets fixed with update to UEFI/BIOS from vendor. Not sure about MSI.
Do you have newest UEFI from MSI for your system?

Looks like you perhaps had sda1 as a bios_grub partition, but it was formatted, so would not work?
But now sda3 is shown as  a bios_grub and has core.img.

Can you boot in BIOS mode?
Are you adding the other boot parameters that other MSI users said were required?
If only one install, you will not get grub menu which you need to manually add boot parameters.
If BIOS, you must hold shift from UEFI/BIOS start of boot until menu appears. Usually need fast boot in UEFI off, or you do not get time to press any key.
If UEFI, you press Escape key (often more than once) from UEFI boot to get menu to appear.

---

