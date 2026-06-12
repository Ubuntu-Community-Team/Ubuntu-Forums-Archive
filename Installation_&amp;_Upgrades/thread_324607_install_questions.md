---
title: "install questions"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by drury on 2006-12-24
I am wanting to install ubuntu on an old hard drive(WD 20G).  I have a Dell XPS with Windows XP installed on original HD(WD 250G).  The Windows drive is an SATA drive the old drive is an IDE drive that I have installed as a slave behind my philips DVD writer.  After some reading I am having some questions if what I want to accomplish will work.  I would like  to be able to dual boot.  I don't want to touch my windows drive and install ubuntu only on my old ide drive.

My questions are this:

Is this possible? has anyone done it?
Can I use the boot device menu by hitting F12 to do this (this would be preferable because I just want to get use Linux for now before I make the total switch)or GRUB?
Am i missing anything?


I am a noob to linux(but am very instered) but I do have some general computer knowledge so some help would be greatly appreciiated.

Thanks for your help!

---

### Post by kidders on 2006-12-24
Hi there,

I imagine you are describing most peoples' Ubuntu installs :-) The only change I would make is ...

> **drury said:**
> I don't want to touch my windows drive and install ubuntu only on my old ide drive.

... Generally, if you have two hard disks, the best thing to do in performance terms is to make full use of them both, all the time. For instance, XP's pagefile could be on one, along with Ubuntu's system files, and Ubuntu's swap partition could be on the other, with XP's system files.

I would recommend using a bootloader to manage multiple operating systems. Grub and Lilo are the most common in the PC world.

---

### Post by drury on 2006-12-24
Thanks for the reply.

I want to somewhat hide it from my wife (she's scared of change - actual quote -"You're going to crash it!"). So, I can install it only on the ide drive and boot from the dell boot device menu, if I wanted to install it that way, correct?  Basically I would have a system, that unless I hit F12, would always boot into windows.  If I wanted to use ubuntu I hit F12 then select the drive to boot from.  would that work? and unless you hit F12 you would never know that there was linux running...  

maybe just wishful thinking...but can it work?

---

### Post by gonesolo on 2006-12-24
Should work, might be bit of a pain to setup though. :-k 

Piece of advice on your hardware setup though, I'm not sure on the IDE channels of the XPS but I would advise, if you can, to put your hard disk and your CDrom on two seperate IDE channels. Otherwise your hard disk will be limited by the speed of your cdrom.

IMHO if you want to completely seperatly install ubuntu/linx on the second drive do the following.

Power down your system. 

Disconnect your SATA/Windows drive

Boot up and install linux to your IDE drive

Shut down again and reconnect your SATA drive

Boot and check your bios and make sure your boot order etc are setup correctly to boot from the re-inserted SATA hard disk

then you should be good to go, a quick press of the F12 (I think on the XPS) key should give you the option to boot from either hard disk and keep your linux and windows installations seperate.

---

### Post by drury on 2006-12-24
A couple of more questions (just a little nervous):

As far as I know there is only one ide channel, correct me if I am wrong? see image below...

[IMG]http://support.dell.com/support/edocs/systems/dimxpsg4/sm/millerd7.jpg[/IMG]

Also, if I install by taking out the SATA drive, does ubuntu install a bootloader if there is only one operating system(fresh install of ubuntu) on one drive (my IDE Drive)?  It's doesn't, correct, because there is only one option, as it sees it for a boot.

---

### Post by drury on 2006-12-25
Is that correct?

---

### Post by bulldog on 2006-12-25
Yes it will install GRUB to the MBR of the IDE disk.
You need GRUB to boot into ubuntu.

Just disconnect the Sata when you install ubuntu,just for security,because in my opinion,the IDE drive will be seen as the first hard disk by ubuntu.
But that's not relevant now.

---

### Post by drury on 2006-12-26
Thanks for everyones help! I am making this post from my working Ubuntu OS.  I just keep saying to myself "This is so cool!"

---

### Post by jtmedin on 2006-12-26
Been following this thread but have a question or 2. I have 2 hard drives but only one is used. Have winxp installed on that one. Have no problem with installing unix on the spare drive by disconnecting. However do not undersstand how f12 gets into the picture. How do i get grub & install it ... ? TIA

---

### Post by bulldog on 2006-12-26
> **jtmedin said:**
> Been following this thread but have a question or 2. I have 2 hard drives but only one is used. Have winxp installed on that one. Have no problem with installing unix on the spare drive by disconnecting. However do not undersstand how f12 gets into the picture. How do i get grub & install it ... ? TIA

There are a lot of computers where you can choose which device you want to boot ,by hitting a key in the first seconds of it's booting.
I myself have to use F11 to choose a boot menu and DEL to enter the BIOS.
Others have to use another one or a combination of two keystrokes,all depending on your BIOS version.

If your computer has this possibility,you should see some info about it on the boot screen,mostly at the bottom.

There are multiple ways to make your windows safe and not affected by GRUB.
If you have two hard disks it's pretty simple.
Just disconnect the first boot device or make it the slave drive and the ubuntu disk the master by switching it from place on the cable,so ubuntu disk is the master and windows the slave disk,and let them both connected on the cables. 
Install ubuntu on the,now master disk,and grub will be installed on this disk.
You have the possibility to boot ubuntu and windows  from the grub menu,and in case of disaster,you can boot windows by it's own boot loader by switching the disks back again,or change the boot order in the BIOS.

To know which disk is the master in ubuntu type this in your terminal,```
cat /boot/grub/device.map
```
The first disk is the master by ubuntu.

---

### Post by jtmedin on 2006-12-26
Ok made the ubuntu hd the master & winxp the slave. Checked setup for the priorites. Ubuntu is the highest priority. However, when i boot winxp starts up. Where did i go wrong? TIA

---

### Post by drury on 2006-12-26
I just wanted to let you all know how my system works now. If I hit my power button to turn on my computer and do nothing else, It boots into XP, exactly like it did before (nothing changed).  If I want to boot into Ubuntu, I hit F12 during the BIOS boot and it brings me to a boot menu that has several options. Namely: go to BIOS setup, boot SATA drive(XP), Boot USB, Boot CD, and at the bottom it has now added a boot to IDE device (it wasn't there before).  When I boot to IDE, Grub starts and loads Ubuntu.  

So now if my wife wants to get on the computer all she has to do is turn it on, she never has to fool with a boot menu or anything.  

Worked out perfectly (for me).... now if I could just get a few other things squared away, like codecs, flash, among others, I did get my widescreen resolution correctly with some help from this forum.

Thanks again for everyones help!

---

### Post by jtmedin on 2006-12-27
Have installed ubuntu on the master hd. Reconected both hd's. When i boot winxp starts up. There is no msg between the bios screen & when winxp starts. So what did i do wrong? TIA

---

### Post by bulldog on 2006-12-27
Can you give the output of ```
sudo fdisk -l (l as in like)
```

If windows starts up,probably grub is on the other disk.
You have to make the ubuntu disk master boot device and the windows disk the slave.
Map your windows in menu.lst and you're done.

---

### Post by jtmedin on 2006-12-27
Now i dont know how to boot ubuntu. System starts up winxp from the slave drive. What did i do wrong? TIA

---

### Post by jtmedin on 2006-12-29
> **bulldog said:**
> Can you give the output of ```
sudo fdisk -l (l as in like)
```

If windows starts up,probably grub is on the other disk.
You have to make the ubuntu disk master boot device and the windows disk the slave.
Map your windows in menu.lst and you're done.

sudo fdisk -l   produced

hda1 * linux
hda2    extended
hda5    swap

When i boot with only the ubuntu disk powered on i get a quick screen flash about grub. Too quick to read it. When i installed ubuntu the only disk powered up was the ubuntu hd so grub must be on that drive. What may have happened when i had both hd's on is unknown to me but winxp comes up as normal. BTW i did check the priority in setup & the ubuntu hd has the higher priority.

---

### Post by bulldog on 2006-12-29
I can tell you what happened.
You disconnected the windows disk so GRUB is installed on the ubuntu disk,that's okay.
**But** you didn't make the ubuntu disk master boot device,still the windows disk is.
If you connect both drives the windows disk is still master boot device and windows will boot.

You have to switch both hard disk from place on the flat cable,or if you can reverse the boot priority in the BIOS.
The ubuntu disk needs to be the master to see GRUB.
If you have done so,you can't boot windows without a minor editing of the menu.lst[mapping the disks]

If you reversed the boot order of the disks,boot into ubuntu and give us the output of
```
sudo fdisk -l (l as in like)
```
I can see which partition your windows is on and give you the changes you have to make to menu.lst.

---

### Post by jtmedin on 2006-12-31
ted@ted-tower:~$ fdisk -l
ted@ted-tower:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6997    56203371   83  Linux
/dev/hda2            6998        7297     2409750    5  Extended
/dev/hda5            6998        7297     2409718+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9689    77826861    7  HPFS/NTFS
ted@ted-tower:~$

---

### Post by bulldog on 2006-12-31
I can make the windows entry for you but to be absolutely sure I want to know the output of two commands,to see if things are setup the right way.
```
cat /boot/grub/device.map
```
```
gksudo gedit /boot/grub/menu.lst
```
Post the whole menu.lst between code tags so I can copy and alter it so you can copy it back.

---

