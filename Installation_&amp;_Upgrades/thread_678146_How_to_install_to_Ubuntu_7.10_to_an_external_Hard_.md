---
title: "How to install to Ubuntu 7.10 to an external Hard Drive"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by gpmartinson on 2008-01-25
I have installed Ubuntu twice and Mint Linux once on an external hard drive and I think I have come up with a very reproducable process for installing 7.10 on my computer without ruining the internal hard drive.  

Here's what you'll need: 
1. External USB Hard drive (I use a maxtor 250 gigabyte drive and it works flawlessly.  
2. Ubuntu 7.10 install CD
3. Vista install CD (only in case things go wrong--don't worry you won't lose your Vista.  In a worst case situtation, you might need to restore the MBR.  

About my set-up: 
I have a Dell Inspiron E1505 computer with Vista taking up the internal hard drive.  I use Vista in my job and really can't go full-time linux, so this works well.  I can keep my drive available with Linux for me, and that can stay at home.  

Ready? 
Here's the process.  
1. First step is to get to the BIOS.  On my Inspiron that's f2 at startup.  You'll want to navigate to the section in your bios that sets your boot order.  Make sure that USB is set to boot before the Hard drive.  You may want to set CDs to boot first.  In my case, I didn't, but that's up to you.  The easiest arrangement is to set the following boot order: 
1. USB
2. CD-ROM
3. Internal Hard Drive
4. Netboot
You'll want to save your settings and exit.  

2. Boot.  Stick the Ubuntu disk in and boot.  Nothing special is needed to boot like this.  Start up with the first option in the startup enu "live cd or install"   It will take some time, but you'll soon see the Ubuntu desktop with the installer available.  

3.  Install.  Use the standard install app right on the desktop.  You'll want to pay special attention to the Disk Selection and last screens.  
In the Disk selection screen, choose manual.  Here' make sure that you are selecting your USB drive to install too.  There will be some text describing the drive.  Make certain that you are installing to your external drive.

When you get to the last screen select the advanced button and you get an option on which drive to install grub into.  Make sure you choose HD1.  This is your USB drive.  

4.  Don't shut down.  Instead open a terminal window and you'll have to make some adjustments yet or things won't boot.  

5. In the command prompt type "sudo mkdir /mnt/ubuntu" This command makes a directory for putting your ubuntu installataion in.You need to mount your drive to the computer and make some adjustments.  

6. next type "mount /dev/sdb1 /mnt/ubuntu" This mounts the ubuntu installation.  That is, provided that you made ubuntu your first partition on your external disk.  

7. Type "mount -tproc proc /mnt/ubuntu/proc" This is process magic in order to make the compile work. 

8. type "chroot /mnt/ubuntu" This changes the OS so the ubuntu installation is your current OS, in a sense. Your root level is now the USB drive and you are kind of using your new Ubuntu disk. 

9. type "su" to make yourself superuser.  You are going to work on system files that require this access.  

10. edit /etc/initramfs-tools/modules. I use nano for this; "nano /etc/initramfs-tools/modules"
and add the following lines to the end:
sd_mod
ehci-hcd
usb-storage
scsi_mod
sd_mod
close the file and save.
This adds the support needed (but not initially available) to mount and run a USB hard drive in the initial ram disk, where the OS is.  Linus sees this drive as a SCSI drive, and Ubunu doesn't initially come with the drivers for external USB disks built into its pre-installed kernel.  So, you're adding those additionally needed modules.  

11. I edit /etc/initramfs-tools/initramfs.conf ("nano /etc/initramfs-tools/initramfs.conf")to include a line at the top that reads:
"WAIT=12" in the front of the file.  
close and save this file. This just allows the computer time to mount and see the USB drive where your Ubuntu is from your initial ramdisk.
then I made the initial ramfs:

12. "mkinitramfs -o /boot/initrd-img."<hit tab and enter> /lib/modules/"<hit tab and enter>"
This makes the initial ram disk with your newly added goodness. You are replacing the existing initial ram disk with the new one.  You are linking it to the kernel modules as well, that's why the two "hit tab and enters" are there.  

13. Not done yet! Edit /boot/grub/menu.lst ("nano /boot/grub/menu.lst")
and I made sure to change the lines in the end of the file so that all references to linux (hd1,0) point to (hd0,0) and all references to (hd0,0) point to (hd1,0).  This is needed because the Ubuntu install always gets the install on an external backwards.  

14. Now you can exit the install and click on the shutdown button.  

Hopefully this will boot yourself into a fresh install.

WHAT TO DO IF THINGS Go WRONG? 

1. Don't Panic.  You can fix any of the problems by finding your way back onto the partition, correcting whatever errors you had and then rebooting.  Let's deal with each of the problems as they come up.  

[COLOR="Red"]Grub got installed on the Windows hard drive? [/COLOR]
How will you know?  Unplug the external drive and make sure that you can boot.  If you see grub instead of the windows screen, you hosed your MBR.  

Is this the problem?  OK.  Well, let's deal with Vista first.  

   1. Insert your Windows Vista Install DVD and boot from it.
   2. After selecting your language options choose the &#8220;Repair your computer&#8221; option in the bottom left corner.
   3. Select your Windows Vista Installation and continue (note: my screenshot does not show an installed OS because there is none).
   4. Open a new Command Prompt window
   5. When command prompt is open, type the following commands (note: my screenshot shows an error as vista is not installed)
         1. Bootrec /fixboot
         2. Bootrec /fixmbr

The MBR/Boot Loader&#8217;s are now repaired, restart your computer and it should boot in to Vista where you can then delete the Linux partitions from the hard drive if you wish.

Now, if you have XP [http://www.webtree.ca/windowsxp/repair_xp.htm](http://www.webtree.ca/windowsxp/repair_xp.htm) has a good description of what to do.

Now, you'll have to reinstall grub and rebuild your menu.lst.

---

### Post by K.Mandla on 2008-01-25
Moved to Installation and Upgrades.

---

### Post by goodgame on 2008-01-26
> **gpmartinson said:**
> I have installed Ubuntu twice and Mint Linux once on an external hard drive and I think I have come up with a very reproducable process for installing 7.10 on my computer without ruining the internal hard drive.  

Here's what you'll need: 
1. External USB Hard drive (I use a maxtor 250 gigabyte drive and it works flawlessly.  
2. Ubuntu 7.10 install CD
3. Vista install CD (only in case things go wrong--don't worry you won't lose your Vista.  In a worst case situtation, you might need to restore the MBR.  

About my set-up: 
I have a Dell Inspiron E1505 computer with Vista taking up the internal hard drive.  I use Vista in my job and really can't go full-time linux, so this works well.  I can keep my drive available with Linux for me, and that can stay at home.  

Ready? 
Here's the process.  
1. First step is to get to the BIOS.  On my Inspiron that's f2 at startup.  You'll want to navigate to the section in your bios that sets your boot order.  Make sure that USB is set to boot before the Hard drive.  You may want to set CDs to boot first.  In my case, I didn't, but that's up to you.  The easiest arrangement is to set the following boot order: 
1. USB
2. CD-ROM
3. Internal Hard Drive
4. Netboot
You'll want to save your settings and exit.  

2. Boot.  Stick the Ubuntu disk in and boot.  Nothing special is needed to boot like this.  Start up with the first option in the startup enu "live cd or install"   It will take some time, but you'll soon see the Ubuntu desktop with the installer available.  

3.  Install.  Use the standard install app right on the desktop.  You'll want to pay special attention to the Disk Selection and last screens.  
In the Disk selection screen, choose manual.  Here' make sure that you are selecting your USB drive to install too.  There will be some text describing the drive.  Make certain that you are installing to your external drive.

When you get to the last screen select the advanced button and you get an option on which drive to install grub into.  Make sure you choose HD1.  This is your USB drive.  

4.  Don't shut down.  Instead open a terminal window and you'll have to make some adjustments yet or things won't boot.  

5. In the command prompt type "sudo mkdir /mnt/ubuntu" This command makes a directory for putting your ubuntu installataion in.You need to mount your drive to the computer and make some adjustments.  

6. next type "mount /dev/sdb1 /mnt/ubuntu" This mounts the ubuntu installation.  That is, provided that you made ubuntu your first partition on your external disk.  

7. Type "mount -tproc proc /mnt/ubuntu/proc" This is process magic in order to make the compile work. 

8. type "chroot /mnt/ubuntu" This changes the OS so the ubuntu installation is your current OS, in a sense. Your root level is now the USB drive and you are kind of using your new Ubuntu disk. 

9. type "su" to make yourself superuser.  You are going to work on system files that require this access.  

10. edit /etc/initramfs-tools/modules. I use nano for this; "nano /etc/initramfs-tools/modules"
and add the following lines to the end:
sd_mod
ehci-hcd
usb-storage
scsi_mod
sd_mod
close the file and save.
This adds the support needed (but not initially available) to mount and run a USB hard drive in the initial ram disk, where the OS is.  Linus sees this drive as a SCSI drive, and Ubunu doesn't initially come with the drivers for external USB disks built into its pre-installed kernel.  So, you're adding those additionally needed modules.  

11. I edit /etc/initramfs-tools/initramfs.conf ("nano /etc/initramfs-tools/initramfs.conf")to include a line at the top that reads:
"WAIT=12" in the front of the file.  
close and save this file. This just allows the computer time to mount and see the USB drive where your Ubuntu is from your initial ramdisk.
then I made the initial ramfs:

12. "mkinitramfs -o /boot/initrd-img."<hit tab and enter> /lib/modules/"<hit tab and enter>"
This makes the initial ram disk with your newly added goodness. You are replacing the existing initial ram disk with the new one.  You are linking it to the kernel modules as well, that's why the two "hit tab and enters" are there.  

13. Not done yet! Edit /boot/grub/menu.lst ("nano /boot/grub/menu.lst")
and I made sure to change the lines in the end of the file so that all references to linux (hd1,0) point to (hd0,0) and all references to (hd0,0) point to (hd1,0).  This is needed because the Ubuntu install always gets the install on an external backwards.  

14. Now you can exit the install and click on the shutdown button.  

Hopefully this will boot yourself into a fresh install.

WHAT TO DO IF THINGS Go WRONG? 

1. Don't Panic.  You can fix any of the problems by finding your way back onto the partition, correcting whatever errors you had and then rebooting.  Let's deal with each of the problems as they come up.  

[COLOR="Red"]Grub got installed on the Windows hard drive? [/COLOR]
How will you know?  Unplug the external drive and make sure that you can boot.  If you see grub instead of the windows screen, you hosed your MBR.  

Is this the problem?  OK.  Well, let's deal with Vista first.  

   1. Insert your Windows Vista Install DVD and boot from it.
   2. After selecting your language options choose the “Repair your computer” option in the bottom left corner.
   3. Select your Windows Vista Installation and continue (note: my screenshot does not show an installed OS because there is none).
   4. Open a new Command Prompt window
   5. When command prompt is open, type the following commands (note: my screenshot shows an error as vista is not installed)
         1. Bootrec /fixboot
         2. Bootrec /fixmbr

The MBR/Boot Loader’s are now repaired, restart your computer and it should boot in to Vista where you can then delete the Linux partitions from the hard drive if you wish.

Now, if you have XP [http://www.webtree.ca/windowsxp/repair_xp.htm](http://www.webtree.ca/windowsxp/repair_xp.htm) has a good description of what to do.

Now, you'll have to reinstall grub and rebuild your menu.lst.



I did an install of 7.10 server.  I used a 7.04 live cd to make all of the changes you mentioned.  I reviewed the menu.1st and didn't see where I had to make any changes.  It appeared to be setup properly already.  

title    Ubuntu 7.10, kernel 2.6.22-14-server
root     (hd1,0)
kernel   /boot/vmlinuz....
initrd    /boot/initrd.img-2.6.22-14-server

....
....
...
..

title   Windows XP Pro x64
root   (hd0,0)
.....

If I select Ubuntu 7.10 from Grub I get:
"error 17: cannot mount selected partition
press any key to continue"

Ideas?

---

### Post by gpmartinson on 2008-01-26
Never gotten an error 17...but it might be worth checking your bios.  Check [http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945") for a potential solution.

---

### Post by goodgame on 2008-01-26
I turns out it had nothing to do with my BIOS.  I switched the mappings in device.map
from:
(hd0)  /dev/sda                -- internal drive
(hd1)  /dev/sdb                -- external drive

to:
(hd1)  /dev/sda                -- internal drive
(hd0)  /dev/sdb                -- external drive


I also then switched all references in menu.1st
from                   to
(hd1,0)    --->   (hd0,0)
(hd0,0)    --->   (hd1,0)


It makes no sense, but worked on first boot.

---

### Post by gpmartinson on 2008-01-26
Excellent.  Glad  to hear it.

---

### Post by tromik on 2008-01-26
Unfortunately, I read this after I installed 7.10 to my external drive.

I could fix the Windows MBR, and reinstall Ubuntu following your steps. But is there a way to fix it now that I already have everything installed?

Also, I'm still a newb at this stuff, really, so will steps work for everyone? I'll double check, but I think Ubuntu is installed to the second partition on the external.

---

### Post by gpmartinson on 2008-01-26
I'm not 100% sure about what you are asking.  You have Ubuntu on an external and windows on your internal drive.  The problem then is that you need to have grub on the internal drive.  If that's the case, here's my suggestion: 
1. boot from a Ubuntu disk.  and in the command line 
2. mkdir /mnt/ubuntu
3. mount /devsda? /mnt/ubuntu 
4. mount -tproc proc /mnt/ubuntu/proc
5. chroot /mnt/ubuntu
6. su 
7. type "grub" 
8. then in the grub shell execute: "setup hd0" 
9. Make a boot/grub/menu.lst file that includes at least 

default 0
title Ubuntu, 
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic (or whatever)
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

and 
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader +1

save and 
exit 
exit
shutdown -r now
cross fingers.  
Good luck.

---

### Post by tromik on 2008-01-27
I actually went back and started from scratch, but thamks for responding.

And it was working great! Turn on the external HDD, the BIOS finds it and GRUB loads. Turn off the external, or unplug it, the BIOS just starts up mt internal drive, and Windows starts as normal. 

It worked perfectly!

For about five minutes.

The first thing I did when I booted to the external was update Ubuntu and install the nvidia drivers it found. Then it said a restart was needed. I restarted, GRUB loaded, but I get error 17 when I try to load Ubuntu. I assume the update changed something.

I'm going to load the Live CD and see if any changes were made to menu.lst, but I don't know how to change device.map like the other user did.

EDIT: Yup, something changed the GRUB menu list and did a pretty wonky job of it - it changed Ubuntu back to HD1,0 and left Windows as HD1,0. Changed any references to Ubuntu back to HD0,0 and it's working fine again. Any idea why that would have changed? It'd suck to have to do that every time I installed an update or app.

---

### Post by gpmartinson on 2008-01-27
Try to rebuild the initrd.  "mkinitramfs -o /boot/initrd-img."<hit tab and enter> /lib/modules/"<hit tab and enter>" That worked for me.  I'm guessing the initrd got rebuilt.  But I might be wrong.

---

### Post by confused57 on 2008-01-27
> **tromik said:**
> I actually went back and started from scratch, but thamks for responding.

And it was working great! Turn on the external HDD, the BIOS finds it and GRUB loads. Turn off the external, or unplug it, the BIOS just starts up mt internal drive, and Windows starts as normal. 

It worked perfectly!

For about five minutes.

The first thing I did when I booted to the external was update Ubuntu and install the nvidia drivers it found. Then it said a restart was needed. I restarted, GRUB loaded, but I get error 17 when I try to load Ubuntu. I assume the update changed something.

I'm going to load the Live CD and see if any changes were made to menu.lst, but I don't know how to change device.map like the other user did.

EDIT: Yup, something changed the GRUB menu list and did a pretty wonky job of it - it changed Ubuntu back to HD1,0 and left Windows as HD1,0. Changed any references to Ubuntu back to HD0,0 and it's working fine again. Any idea why that would have changed? It'd suck to have to do that every time I installed an update or app.
You need to change the line with #groot to (hd0,0):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

BTW, here's another set of instructions, using the alternate cd:
[http://ubuntuforums.org/showpost.php?p=2982257&postcount=2](http://ubuntuforums.org/showpost.php?p=2982257&postcount=2)

---

### Post by tromik on 2008-01-29
Yup, made the change, worked fine. Dunno what changed it back, though. The updater or something?

---

### Post by gpmartinson on 2008-01-30
Glad that worked.  I wish that the installer would actually look at the existing initrd  settings and the existing grub.lst.  Maybe that should be a bog report?

---

### Post by tromik on 2008-01-30
'm actually going to install 7.10 to an other HDD that'll be in the enclosure. I'll let you know if the same thing occurs.

This is a great guide BTW.

---

### Post by gpmartinson on 2008-01-30
Thanks, and I think we actually have a bug or feature request to report.

---

### Post by marykavanagh on 2008-01-30
this is a really great tutorial but one question, i am trying to do this with a 500 g hard drive that I have partitioned 15 g to install on, when I boot from usb and select install, is it going to ask me which partition???

---

### Post by tromik on 2008-01-30
> **marykavanagh said:**
> this is a really great tutorial but one question, i am trying to do this with a 500 g hard drive that I have partitioned 15 g to install on, when I boot from usb and select install, is it going to ask me which partition???
Yes, it will. If you don't know from the past which partition is which, you'll be able to figure it out from the different sizes. 

When you start to install, you can choose a guided install or manual. If you use the guided install it'll use the enture disk basically. Use the maunual install, find your partition on the list, make sure you have a small partition for the swap (if you don't delete the 15gb partition, make a new partition, and just subtract a couple of megs from it).

If the partition you're installing to isn't the "first" parition, you'll have to adjust the guide according. Instead of sdb1, it might be sdb2 or 6 or something else. Just make a note of it.

---

### Post by marykavanagh on 2008-01-30
thanks! but i have one more question about the tutorial, in steps 10 11, 13 it says to edit /etc/initramfs-tools/modules and /etc/initramfs-tools/initramsfs.conf  etc, what exactly does that mean? am i to type those into the terminal and then the edits one by one?

also, is step 12 to be typed in the terminal?

sorry if im asking ridiculous questions-im pretty new at this, and am under a time crunch unfortunately

---

### Post by confused57 on 2008-01-30
Maybe this guide will help you also, if it works for Gutsy:
[http://ubuntuforums.org/showpost.php?p=2982257&postcount=2](http://ubuntuforums.org/showpost.php?p=2982257&postcount=2)
when installing grub, on the last step, click on the Advanced button, then select /dev/sdb(or however the partitioner recognized your external hard drive).
 step 8 should be:
```
sudo nano /boot/grub/menu.lst
```
you should be able to just copy & paste most of the commands

You may want to make a copy of both tutorials...hope this doesn't make things too confusing.

---

### Post by tromik on 2008-02-01
> **confused57 said:**
> Maybe this guide will help you also, if it works for Gutsy:
[http://ubuntuforums.org/showpost.php?p=2982257&postcount=2](http://ubuntuforums.org/showpost.php?p=2982257&postcount=2)
when installing grub, on the last step, click on the Advanced button, then select /dev/sdb(or however the partitioner recognized your external hard drive).
 step 8 should be:
```
sudo nano /boot/grub/menu.lst
```
you should be able to just copy & paste most of the commands

You may want to make a copy of both tutorials...hope this doesn't make things too confusing.
7.10 is different - when you're choosing where to install GRUB (last step, "Advanced" button), the default is "HD0" and you have to manually change it (that is, type over it and change it) to "HD1." This is included in the guide in the first post in this thread.

---

### Post by tromik on 2008-02-01
> **gpmartinson said:**
> Thanks, and I think we actually have a bug or feature request to report.
Okay, same install procedures, same partition on a different external (both at two partitions) and same results: When I use the auto updater it changes the grub menu.lst selects for Ubuntu back to "HD1,0."

I just loaded the CD, and edited it back. Don't know if this happens with all updates or just the initial update.

---

### Post by jgood on 2008-02-04
I followed the installation as best as possible (I am a newb).  Compared to another installation it worked pretty well as far as only giving the boot option when the hard drive was plugged in otherwise booting into vista.  I did have a problem with the steps on mounting it gave me a return of not being root or whatever.  When I try and boot into linux with the external I get the error 17 message and I assume its because I did not put the extra commands in.  Could you help me in how I enter the commands as a root so I can try and reinstall it or if there is an easier way where I wouldn't have to uninstall that partition.

---

### Post by abd5hafeeq on 2008-02-05
Excuse me. I have a question(noob here).
Is it possible to use the external hard disk on other computers without making changes to the computers? I mean, the external hard disk acts like a "portable operating system". Having a "portable ubuntu" would be cool so I can show it to my friends.

---

### Post by Scavok on 2008-02-05
> **abd5hafeeq said:**
> Excuse me. I have a question(noob here).
Is it possible to use the external hard disk on other computers without making changes to the computers? I mean, the external hard disk acts like a "portable operating system". Having a "portable ubuntu" would be cool so I can show it to my friends.
You're not the only one asking this question--it's in this thread, too:

[http://ubuntuforums.org/showthread.php?t=688088](http://ubuntuforums.org/showthread.php?t=688088)

---

### Post by smartboyathome on 2008-02-05
LiveUSB would probably be the best for this situation. I made a guide for making one [here]("http://ubuntuforums.org/showthread.php?t=647587"). Be warned, though, that if you use a Gutsy CD, I find it will not boot up very quickly. Instead, it takes approx. 5 minutes for me.

---

### Post by Thecoolguru on 2008-02-05
i selected my external drive in step 4 of the installation, and i don't know what i should select for the mount point. im confuzzled!

---

### Post by pieisgood4589 on 2008-02-05
> **Thecoolguru said:**
> i selected my external drive in step 4 of the installation, and i don't know what i should select for the mount point. im confuzzled!

Edit your fstab file to tell it to mount your filesystem automatically.

Code:

sudo gedit /etc/fstab

put 'defaults' under the <options> column for your desired mountpoint

good luck

I know too much.... LOL
Bibi Jacob see u 'morrow

---

### Post by ad0 on 2008-02-14
Hello,

i followed all the rules from this tutorial (installing 7.10) and my Hardware is:

HP Laptop Compaq nx9420
Internal disk 80GB

External USB Disk: WD Passport ( [WD Passport]("http://www.amazon.de/exec/obidos/ASIN/B000JRSMM2/100006612-21/?m=A3JWKAKR8XB7XF") ) ...

I created 4 Partitions on the USB disk ... that is:

/dev/sdb1 ( 80 GB ... NTFS Partition to use in Windows)
/dev/sdb2 ( 2,5 GB ... swap)
/dev/sdb3 ( 20 GB ... /home .... ext3)
/dev/sdb4 ( 50 GB ... / ........... ext3)

Now everything is fine ... except when the GRUB is trying to load, it says ... 

Grub error 18: 

And it stops ... i tried to change settings in BIOS (for the USB Disk) but there are no options in BIOS to set the USB drive as LBA ... help?

---

### Post by smartboyathome on 2008-02-14
Did you change every instance of hd(1) to hd(0) and vice versa? It sounds like it can't find GRUB on the disk.

---

### Post by swedishlightning on 2008-02-18
Hello,

I am a new user, and unfortunately I read this thread a little too late. I have already installed Ubuntu onto a Maxtor external drive and I did not change the advanced settings so that GRUB does not overwrite my MBR. At this point, both XP Pro and Ubuntu boot and run fine as long as I have the external plugged in, but as the OP put it, I seem to have "hosed" my MBR. 

My main problem is that I forgot to bring my XP DVDs with me to school this semester, and I will not have access to them for at least a week or so. Is there any way that I can mend my MBR without the XP discs?

Many thanks for any advice,

Thatcher

---

### Post by confused57 on 2008-02-18
> **swedishlightning said:**
> Hello,

I am a new user, and unfortunately I read this thread a little too late. I have already installed Ubuntu onto a Maxtor external drive and I did not change the advanced settings so that GRUB does not overwrite my MBR. At this point, both XP Pro and Ubuntu boot and run fine as long as I have the external plugged in, but as the OP put it, I seem to have "hosed" my MBR. 

My main problem is that I forgot to bring my XP DVDs with me to school this semester, and I will not have access to them for at least a week or so. Is there any way that I can mend my MBR without the XP discs?

Many thanks for any advice,

Thatcher

You can try Super Grub Disk or MbrFix:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#Super_Grub_Disk](http://www.users.bigpond.net.au/hermanzone/p18.htm#Super_Grub_Disk)

---

### Post by swedishlightning on 2008-02-18
Thanks Guys!

I was able to get mbr all sorted out with super grub and then reinstall ubuntu using the original poster's instructions.

I appreciate your time,

Thatcher

---

### Post by Breandean on 2008-03-21
Hello, I pressed F8 and got options, but cannot find a way to change boot order to my EHD.

I did find a microsoft intruction using the my computer option, but it is not exact, detailing how to modify OS options only.

How do I make sure I am installing grub into my HD1?

After typing in instructions, I press enter?

My OS is XP Home Edition, on a Dell Dimension 2200. 

Is there a recommendable You Tube instruction?

Here is what I have in my Note Pad Start Up Settings:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect

---

### Post by scottc992004 on 2008-03-21
i set my maxtor usb as 1st boot then my cd as 2nd.

when i start the computer i get an error:

mbr error 1
press any key to boot from floppy...

press any key and i get 

mbr error 2
press any key to boot from floppy...

What is causing this to happen?

---

### Post by Breandean on 2008-03-22
You can look up the microsoft website and their are instructions concerning MBRs, Boot.ini ... Maybe boot floppy into safe mode?


[http://support.microsoft.com/default.aspx?scid=kb;en-us;289022](http://support.microsoft.com/default.aspx?scid=kb;en-us;289022)

---

### Post by Breandean on 2008-03-24
I just got this explanation from kgwagner14,
[http://discuss.extremetech.com/forums/ShowThread.aspx?PostID=1004408710#1004408710](http://discuss.extremetech.com/forums/ShowThread.aspx?PostID=1004408710#1004408710)    :

Boot order is not set by the OS, it's set using variables stored by BIOS in the CMOS memory. Not all BIOS versions/revisions support as many possibilities as there are. OEM machines in particular can be frustratingly sparse in this area.


You need to get into the BIOS setup routine to change the boot order, which is most commonly done by pressing the DEL key at a strategic point during startup. I usually just power up the machine and hold the DEL key down until the it starts bitching. At that point, I can't be of much help, as setup routines vary quite a bit. But, generally speaking, you want to get into the "Advanced Options" portion of the thing. If you don't see an option for doing it there, perhaps your BIOS supplier has it under a different heading. Just look around until you find a line item for "Boot Order". Select the option you want, usually using the PageUp/PageDn keys. Set the first device first, then the second, then third if offered, keeping in mind that changing one device's order sometimes changes the others, as you can't have the same device repeated in the ordering list. Once you're sure the order is set the way you want it, usually F10 will save your choice and exit the routine.


The boot loader is a different beast entirely. It doesn't come into play until after the BIOS decides what it's going to boot from, based on the boot order, and assuming it finds a bootable device. At that point, it looks for a boot loader. In Linux, the loader is usually LiLo (Linux Loader) or GRUB (GRand Unified Bootloader), and in Windows, it's boot.ini (boot initialization).  

The boot loader tells BIOS where to find the MBR (Master Boot Record) for the OS(s) it's giving you a choice of loading, as well as some options to pass along to them.

---

### Post by Breandean on 2008-03-24
I got somewhere, right at the start I pressed F2. Using Cyberwalk.com instructions, but went through it a bit differently, there was a primary drive which was "off" and I put it to auto, so the computer tried to boot from primary drive 1 instead of 0, and it goes into XP properly, after pressing a button.  Maybe because it says it cannot find primary drive 1, and the EHD is on, that it is secondary drive 1 I need.

Must study, and later download Ubuntu, wednesday...

I recommend you look in google, "change BIOS" and your computer brand name.

---

### Post by georgew77 on 2008-03-24
Im confused at step 12, do I hit tab and enter together or no?  What sort of response am I expecting, could someone post up the response?

Thanks

G.

---

### Post by georgew77 on 2008-03-24
And when I do a tab after /lib/modules/ it simply autofills in the rest of a folder name, namely

2.6.22-14-generic

?

edit: when I try and boot from the usb, I get an 'Error loading operating system'

double edit: when I unplug the usbhdd to boot into vista, I get GRUB loading stage1.5 followed by error 21.

triple edit: when I boot from the laptop hdd with the usb plugged in I get the grub menu, Ubuntu comes up with Error 17, vista with Error 13

G.

---

### Post by georgew77 on 2008-03-24
Ok I have got a bit further now, if I boot from the laptop hard drive the grub menu works and I can boot either vista or ubuntu.

To achieve this I swapped the hd(0,1) and hd(0,0) back to the way they were originally.

If I unplug the usb I get grub on the vista drive but with error 21.

How do I get this working back the right way round?

G.

---

### Post by oligray on 2008-03-24
grub is on the internal drive of my computer and i get an error when my external drive isnt plugged in and it wont boot windows..

am i correct in thinking that i need to move the grub file(s) from my internal (windows) to my external (ubuntu) 

how and because im a noob simple steps please..

thanks

---

### Post by georgew77 on 2008-03-24
oligray sounds like you did exactly what I did.

I have sorted mine out now.  First repair your windows MBR with super grub

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

And then follow the instructions properly (well at least that was my issue) I missed out this bit of step 3

> When you get to the last screen select the advanced button and you get an option on which drive to install grub into. Make sure you choose HD1. This is your USB drive.

If you go back to square 1 you should be able to sort it out.

G.

---

### Post by mrsack on 2008-03-24
edit: made my own thread about my issue

[http://ubuntuforums.org/showthread.php?t=734690](http://ubuntuforums.org/showthread.php?t=734690)

---

### Post by mrsack on 2008-03-24
edit: made own thread

---

### Post by Breandean on 2008-03-26
When installing 7.10 on the EHD, why does one need go manual, and add the instruction from the OP? Why not just go automatic?

What would go wrong?

And Ubuntu partitions automatically?

In instruction 10, how do you not only leave a space but a line?

Forgive me, I am a newbie.

---

### Post by smartboyathome on 2008-03-26
If you went automatic, it would install it wrong on the computer (ie, you wouldn't be able to boot the computer unless the hard drive was plugged in). Ubuntu can partition your drive automatically by selecting use entire disk and choosing your external drive. Push shift and then - to leave an underscore.

---

### Post by Breandean on 2008-03-27
You know, if it won't start unless the Hard Drive is plugged in and switched on, but if it will start up from the internal hard drive, that's okay with me.

By line I meant a whole space, 

like
this.

Ubuntu will configure the old hard drive? Erase old stuff?

---

### Post by oligray on 2008-03-31
does this method work on hardy heron because if it does i can finally have a working distro on my computer.. :)

maybe... lol

Gutsy's live cd wont boot in my laptop and the alternative cd doesnt view on my screen properly instead it shows first half on left side and second half on right side whilst missing out a chunnk aswell so this makes it very awkward and i gave up because i didnt want to ruin anyhitng :)

---

### Post by smartboyathome on 2008-03-31
It should. Nothing has significantly changed in Uqiquity (Ubuntu's installer) between Gutsy and Hardy (well, except for the timezone selector).

---

### Post by blastus on 2008-04-01
Will this work on a computer that has NO hard drives connected to it except a USB key?

---

### Post by Pumalite on 2008-04-01
Sure

---

### Post by blastus on 2008-04-01
Step 12
"mkinitramfs -o /boot/initrd-img."<hit tab and enter> /lib/modules/"<hit tab and enter>"

The tab key doesn't do a thing on my machine. Is this supposed to include the contents of "uname -r"??? I tried...

```
mkinitramfs -o /boot/initrd-img/2.6.22-14-generic /lib/modules/2.6.22-14-generic
```

...but I don't know what it is supposed to do??? Is the mkinitramfs command supposed to prompt for more input so you have to press enter to go to a new line? 

All I get when I boot is the BIOS message "Boot Failure. Reboot and Select proper Boot device or Insert Boot Media in selected Boot device" 

> **Pumalite said:**
> Sure

I don't think this is possible. Every single tutorial/guide/article I have searched for so far have explained how to install Ubuntu FROM a USB key, not TO a USB key. This tutorial is the exception but I do not understand step 12.

---

### Post by smartboyathome on 2008-04-01
Just do this like a normal install if there are no hard drives but a usb key. It will install as it should.

---

### Post by oligray on 2008-04-08
i made my own guide for my self using your guide as a base thanks..

i now have put it as a new thread for anyone that wants a slightly more simple version.. and i did give you credit

thanks 

[http://ww.ubuntuforums.org/showthread.php?t=747263](http://ww.ubuntuforums.org/showthread.php?t=747263)

---

### Post by oligray on 2008-04-08
> **blastus said:**
> Will this work on a computer that has NO hard drives connected to it except a USB key?

tht seemed like an obvious thing to say yeh you still need to dot tht at first.. but thinking about it yes it would still work but you would just have to do a straight forward install because being the only hardrive it owuld be (HD0) so nothing grub wise would have to change.....



actually you would because lots of it is about booting from usb lol

sorry just writting my chain of thought

---

### Post by oligray on 2008-04-08
> **blastus said:**
>  This tutorial is the exception but I do not understand step 12.

you just hold TAB then hit enter

---

### Post by nikRbokR on 2008-04-08
For Step 12, instead of doing:```
"mkinitramfs -o /boot/initrd-img."<hit tab and enter> /lib/modules/"<hit tab and enter>"
```

do

```
mkinitramfs -o /boot/initrd.img-'uname -r' /lib/modules/ 'uname -r'
```

This should work.

For Steps 6 - 11:
If it complains, just put 'sudo' in front of all of the lines.  This will work.

For Step 3, instead of typing HD1, you could also do dev/sdb (sdb is the name of the drive that appears for me... just check what it says on the summary right before you hit the Advanced tab)

I've used this guide many times in the past few weeks.  I keep messing up after installing, but this guide is the best!  Thank you very much... I hope the tips above help others who ran into a few problems.

---

### Post by oligray on 2008-04-08
yeh nikRboKr is right

i never knew bout the mkinitramfs bit but the rest.. i knew would work i even made sure people write sudo in my guide, [http://ww.ubuntuforums.org/showthread.php?t=747263](http://ww.ubuntuforums.org/showthread.php?t=747263)

this guide has also been a savioiur to me over the last few days.. lol :)

---

