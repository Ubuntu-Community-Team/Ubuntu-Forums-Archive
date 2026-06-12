---
title: "Installing Ubuntu on D: drive?"
date: 2014-04-13
forum: Installation &amp; Upgrades
---

### Post by govinda3 on 2014-04-13
I have Windows on my pc on C: drive. I want to install ubuntu on D: drive what steps should i follow?After reading few articles i got to know regarding difficulties of Windows8 and Ubuntu dual boot on Laptops with preinstalled Windows8 ,But i dont have Windows 8 streaker on my laptop.
please help me.
Thank You in Advance.

---

### Post by Mark Phelps on 2014-04-13
> I want to install ubuntu on D: drive 

Basically -- you don't!  Drive letters are an MS Windows convention that Linux does not use.

You have to install Ubuntu to a Linux filesystem, so first, you would need to remove "D:".

Then, when you boot with the Ubuntu install media, open GParted -- this is a partitioning tool.  Use that to create an Extended partition in the space that was formerly used by "D:".  Then, use the Something Else option in the installer to create an Ext4 partition inside that (mount it at "/") and create a swap partition the size of your system memory.

---

### Post by Mark Phelps on 2014-04-13
> I want to install ubuntu on D: drive 

Basically -- you don't!  Drive letters are an MS Windows convention that Linux does not use. You have to install Ubuntu in a Linux filesystem, not Windows.

But, if you're running Win8, there's a possibility that you have UEFI as well, which complicates the install.

Sorry, not an expert in that, so you will need to wait until such an expert comes along.

---

### Post by Double.J on 2014-04-13
Hi there!

Welcome to the forums!

Can I ask which laptop you have? and also if it came with windows 8, or if you upgraded?

So just to outline initially, the steps are:
1)Backup your existing windows install.
2)Triple check that there is absolutely nothing left on D: 
3)Check that C: will be big enough for you after D: is gone (once D: is formatted for ubuntu, Windows cannot see it, although ubuntu can see windows)
4)Download the ubuntu ISO (making sure that it is the 64bit [recommended] image and burn to DVD or
4.1)Use [Pendrive linux]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") to create a bootable usb, ensuring that there is nothing on the USB stick you need.
5)Final check that everything you need from windows is safely backed up on an external drive NOT CONNECTED to the laptop at all.
6)Read Oldfred's UEFI guide [here]("http://ubuntuforums.org/showthread.php?t=2147295")
7) When ready, boot from the USB and click on 'Try ubuntu' to get a feel for how it's running and whether you like it, what hardware is working, if any doesn't and so forth.

I know I didn't cover the actual install, but that part is quite straight forward and we can easily help along with that. The preparation is actually more important and takes longer in many ways!

Keep us updated,

Jj

---

### Post by sudodus on 2014-04-13
Welcome to the Ubuntu Forums :-)

1. As *Mark Phelps* suggests, please let us know if you boot the computer in UEFI or old style BIOS (sometimes called CSM) mode. This makes a difference in how to manage the partition table of the drive.

2. Also let us know about the drives, partitions and file systems including boot sectors. I suggest that you get and use the tool ***Boot Repair***, and use it to run the boot-info script 'Create a BootInfo Summary'

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Later on, after installing Ubuntu, you may or may not need to run the Recommended Repair part of the tool (or the Advanced Options).

3. The more we know about the computer, the better. If you describe the hardware, we can suggest what version and flavour of Ubuntu might be the best choice: Brand name and model, CPU, RAM (size), graphics chip/card, wifi chip/card.

---

### Post by govinda3 on 2014-04-13
COmpaq 610 i upgraded it to Windows8.

---

### Post by sudodus on 2014-04-13
I found this link describing Compaq 610,

[http://h20566.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?spf_p.tpst=kbDocDisplay&spf_p.prp_kbDocDisplay=wsrp-navigationalState%3DdocId%253Demr_na-c01767234-16%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken](http://h20566.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?spf_p.tpst=kbDocDisplay&spf_p.prp_kbDocDisplay=wsrp-navigationalState%3DdocId%253Demr_na-c01767234-16%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken)

but there are several CPUs, so please tell us

- which CPU is in your computer
- how much RAM is in your computer,

and please try to reply to the other questions too (including running the BootInfo summary and giving us the result). Otherwise we can only guess, and the advice might be misleading.

---

### Post by Double.J on 2014-04-13
Probing theough the hp firmware support, this does not appear to be a UEFI machine. 

Jj

---

### Post by sudodus on 2014-04-13
> **Double.J said:**
> Probing theough the hp firmware support, this does not appear to be a UEFI machine. 

Jj

Yes I agree, so we have eliminated one big questionmark. Running is BIOS will make things much easier :-)

---

### Post by Double.J on 2014-04-13
> **sudodus said:**
> Running is BIOS will make things much easier :-)

Just to update you  Govinda3 what we have been trying to find out is whether your machine runs the classic BIOS or thr new UEFI. By confirming that it is most likely a standard bios set up, then you should not have much trouble with windows 8. I have installed windows 8 on a core2duo compaq from around this time with no issues with ubuntu.

This means that you can ignore step 6 in my first post :D i still advise following the others pre install. As mark phelps says it may well be advisable to erase drive D: from inside windows before running the installer.

if, as sudodus said you give us the hardware specs such as RAM, cpu, hard drive info (how many hard drives, partitions, size of disk) we can help advise you with the install!

Jj

---

### Post by govinda3 on 2014-04-13
RAM=2GB
CPU=Intel core2duo 2GHz
hard drive=hitachi 300GB
i have four partitions 
C::Windows) 67GB with17 GB free space 
D::Empty 55GB
E: 79GB with 10GB
F:100GB with 2 Gb free

I dont know about My BIOS but it doesn't support Secure boot

---

### Post by Double.J on 2014-04-13
Hi there! 

Thise specs look absolutely fine for ubuntu. 

I do notice that your disk is pretty full. For optimum performance it may be good to put some stuff on an external disk in the future. However right now we can help a bit.

so the total space ubuntu will need is a lot smaller than windows - most people use around 20 GB as a recommendation (because ubuntu formatted stuff is going to be unreadable in windows) this means you can give 30GB back to windows. 

It is a really good thing that you have created free space to put ubuntu on. If you wish, you can tell the installer to use the free space on the disk. This will create what is called an extended partition, inside which will be one partition called swap (this is an area of the hard drive used as extra ram space. It is a lot like page filing in windows. By default it will be the same size as RAM, so 2gb. The other partition will fill up the rest of the free space. For most users this is the optimum setting.

you will have the option to 'go advanced' this will allow you to change the size of swap (bare in mind if it is less than RAM the machine cannot hibernate, and i would not advise swap less than 1GB) as well as add extra logical partitions. Most users do not need this, but some prefer to have a separate partition for /home. (/home is like c:/users in windows) to store all their user info separately. As you are using three other partitions for data you may well not need this. you will also have the option to select the file system. Ext4 is recommended. Finally if you go advanced, the installer will ask you where to poot the bootloader. By default it should be at /dev/sdx where x is the letter of the hard drive in the partitioner. It should not end with a number.

For example in my machine /dev/sda is my hard disk, /dev/sda1 is the first partition on that disk. /dev/sdb is my external hard drive, /dev/sdb1 is the first partition on that hard drive. When you install the bootloader to the start of your hdd, it get writen to the MBR (first 512bytes of a hdd) and your computer will know to boot it. If you install it to a partition, your computer will not see ubuntu at boot and install windows like normal.

hope it helps?

Jj

---

### Post by sudodus on 2014-04-13
We think it is old style BIOS.

With those specs I would recommend either of ***Xubuntu*** or standard ***Ubuntu***. If you can download iso files reasonably easy, I suggest that you try both. With 2 GB RAM and BIOS, you can download the 32-bit desktop iso files of either version 12.04.4 LTS, polished and debugged and with long time support, or version 13.10, new but support only until July.

To make the choice simpler I'd suggest that you start with ***ubuntu-12.04.4-desktop-i386.iso***

You can follow the steps suggested by *Double.J* (and if you get problems booting, try Unetbootin instead of Pendrivelinux). See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

