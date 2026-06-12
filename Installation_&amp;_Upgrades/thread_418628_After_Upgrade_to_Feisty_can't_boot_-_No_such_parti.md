---
title: "After Upgrade to Feisty can't boot - No such partition"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by chinita96 on 2007-04-22
I have been searching this section if someone had a similar problem. There are so many posts, I couldn't find anyone who had this problem. Or atleast I don't know what I'm supposed to be looking for. After I upgraded through the update manager, I rebooted and now nothing will boot. All it gives me is "No such partition" and I don't know how to fix this. 

I'm in the live cd and I tried to mount the linux drive but it won't let me. When I do fdisk -l it shows my drives and says this:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15719   126262836    7  HPFS/NTFS
/dev/sda2           15720       19301    28772415   83  Linux
/dev/sda3           19302       19457     1253070    5  Extended
/dev/sda5           19302       19457     1253038+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    c  W95 FAT32 (LBA)

```

I know that /dev/sdb1 is my external harddrive which is usb. It shows all my partitions are there, but I don't know how to fix my grub so I can boot. I don't even know if it is the grub. I'm still a newbie so I'm confused. Please help. Thanks!

---

### Post by Crashmaxx on 2007-04-22
I had a similar problem. It turns out, feisty renames all drives to sd*, even if they were hd* before. So if when it gives you this error, it also gives you a prompt saying root@[yourcomputer]# then just type in "nano /etc/fstab" change anywhere it says hd to sd and press crtl+X to exit and yes to save. Then just reboot and all should be good. Hope that helps, worked for me.

---

### Post by chinita96 on 2007-04-22
Well I'm not sure that is the problem. But if it is, how do I get to the prompt? All I see is the grub list and when I try to edit it just shows root (hd1,2) which I thought the 1 was the problem and I tried editing root (hd1,2) to root (hd0,2) and I got an error 17: cannot mount selected partition. In the live cd I do fdisk -l and it shows what I posted above. So I know I have my partitions.

So, how would I get into a command line from grub if it just shows me the list of OSes? Is there a shortcut key for it or something? Also would it matter if I do have SATA drives? 

Thanks for the info though, once I get to command prompt I will try that out and see if it works.

---

### Post by Crashmaxx on 2007-04-22
You should want to change it to (hd0,1) not (hd1,2) or (hd0,2) grub starts counting at 0, so right now you are trying to boot extended, which isn't really anything.

If editing within grub fixes the problem, then don't forget to edit your menu.lst after to make the changes permanent.

---

### Post by chinita96 on 2007-04-22
Ok I tried that - I changed root to hd(0,1) on the boot screen - and it seemed like it was trying to start to boot, but it just threw a bunch of code on a black screen and stopped at usb:registered .. something like that. Can't remember exactly what it said. Lots of code came out on the black screen. From what I could read it seemed like it was loading everything but it did not go into the graphical screen, gnome. Just stayed in the black screen with white text.

Is this good or bad? Hmm.... not sure what to do now. Thanks for that reply though, that sorta seemed to work. Atleast it seemed to start to load when I changed root to hd(0,1).

---

### Post by Nimefurahi on 2007-04-22
Hmmm....

Is there any chance that this was an upgrade installation and not a freshly new install on your second partition?  The reason I ask... if this was an upgrade, your Grub menu may have an earlier entry that utilized a kernel that will work with your hardware. If, by miracle, you have a listing in Grub for a 2.6.17-10 or an earlier kernel without the libata module enabled, you can select it and be up and running shortly. (I say, "shortly." We may have to undo what you may have done in your panic. It's OK. We've all been there.) 

What alternatives does your Grub menu report beside the Microsoft OS in the first partition?

---

### Post by chinita96 on 2007-04-22
You are right. This was an upgrade and not a fresh install. It doesn;t show Microsoft XP at all in the grub menu. I assume this is from the upgrade because last time I updated grub it redid my menu.lst and didn't have Microsoft XP listed as default. I had to uncomment it last time. This time grub just has the ubuntu oses listed and various ones. I think it starts with 2.6.17-15 and also has -11. I don't remember if it has -10. My initial install of linux was Edgy. So maybe it will have 2.6.17-10, but I'll have to check again. 

Even if it does, I tried selecting all of them and loading them, neither one does.

---

### Post by Nimefurahi on 2007-04-22
So there are other kernel entries in Grub and you've already attempted to use them as well. Hmmm... does that include those suffixed with (Recovery mode)?

Let me research a workaround that we can include in the Grub menu.

---

### Post by Nimefurahi on 2007-04-22
I've got an idea...

Boot your live CD. I need to see your /boot/grub/menu.lst and your /etc/fstab files, first of the live CD and then those you find in the sda2 folder presented on your desktop whilst in the live CD environment. That's a total of four files. We'll take it from there.

---

### Post by chinita96 on 2007-04-23
Ok, I was able to get the menu.lst file and I noticed it renamed it all wrong like I stated earlier. It has (hd1,2) instead of being (hd0,1). Here is the menu.lst file contents:

```
gfxmenu /boot/grub/message.ububrown
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/sda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title 		Microsoft Windows XP Professional
root 		(hd0,0)
savedefault
makeactive
chainloader 	+1

title		Debian GNU/Linux, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda3 ro 
initrd		/boot/initrd.img-2.6.20-15-generic
boot

title		Debian GNU/Linux, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic
boot

title		Debian GNU/Linux, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro 
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Debian GNU/Linux, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Debian GNU/Linux, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro 
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Debian GNU/Linux, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Debian GNU/Linux, kernel memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
#title Microsoft Windows XP Professional
#root (hd0,0)
#savedefault
#makeactive
#chainloader +1
```

I updated it so it reads (hd0,1) - originally it all said (hd1,2). I also noticed it is trying to load root as sda3, but it looks like it's sda2. So in the grub menu on boot I tried 'e' for edit and changed it to sda2, but it just cycles through code. It looks like it's trying to load but just stops somewhere. It spits out all this code. I just get a black screen with white text.

Here are the contents of my fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=cd5791de-5797-4188-80d2-4b2aeedbaf9a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=715a62d8-e8e4-4c44-b191-c2f488d730dc none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/windows  ntfs  nls=utf8,umask=0222  0    0
```

Could it be that at the end where it says /dev/sda1 /media/windows it's missing where to mount linux? This looks like it could be the problem but I don't know what text should be here. Can someone please help? Also, I tried booting into Windows and that worked fine. But I usually used linux, I only use windows for apps I need to run since I'm a graphic designer (I need flash). I would like my ubuntu back. Thanks for any replies.

---

### Post by Nimefurahi on 2007-04-23
How about you leaving your fstab just as it is and modifying menu.lst thusly:

```
## ## End Default Options ##

title 		Microsoft Windows XP Professional
root 		(hd0,0)
savedefault
makeactive
chainloader 	+1

title		Debian GNU/Linux, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cd5791de-5797-4188-80d2-4b2aeedbaf9a ro 
initrd		/boot/initrd.img-2.6.20-15-generic
boot


```

Pay particular attention to the only line modified, the kernel line of your menu's second entry.

---

### Post by chinita96 on 2007-04-24
Actually I thought of that and tried it just before I went to sleep last night. It did the same as before. You know what I think it might be, but I'm not quite sure .. when it boots to 2.6.10.15-generic it hangs at loading. I wonder if it's the initializing file ... isn't that an init. file of some sort? Also, I tried going into the other versions, and it seemed to get me to the login screen for 2.6.10.10-generic. I was able to login and everything ... but after login I just get a white screen and that's it! I wonder if it's the initialize file or my graphics card. I have an nvidia graphics card.

I can't even get to a login screen for 2.6.10.15-generic or 2.6.10.11-generic. It's weird.

---

### Post by Nimefurahi on 2007-04-24
White screen of Death! Golly but I don't know what to do or say now, except that if you still can bring up the system with your 2.6.10.10-generic kernel right to the point of the gdm login screen, quickly key a Ctrl Alt F2 (all three keys together) to be directed to a console screen. There you could log in and snoop around to find out what's going on with the following:

```
dmesg >readme
vi readme

```

Don your Sherlock Holmes cap and scrutinize the readme file. To exit vi, key **:** followed by a **q**. (For clarity that is a colon [:] followed by a [q] )

---

### Post by chinita96 on 2007-04-24
Thanks ... yeah I thought "oh sh...." when I saw that screen. Actually I am going to try something else. I have a feeling it might be beryl. I forgot I had installed beryl and avant window navigator. I'll have to go into the autostart and delete those entries so they don't try to load right away. That might be the problem I'm thinking. I'll try that and let you know how it goes. Tonight I actually have to get some work done but tomorrow I will get right on that.

Thanks for trying to help though. I really do appreciate it. It's just frustrating not being able to get it working again. If it comes to it, I'll have to do a fresh install. I think I have most of my files backed up, but I'll run the live cd again and get in there to grab anything else I might need before I wipe it.

---

### Post by chinita96 on 2007-04-26
Well, I still haven't found a solution yet. I just get a white screen when I login to the 2.6.10.10-generic. I removed the autostart for beryl and avant window navigator. I will try to read the message files and see what it says. I'm stuck I might have to do a fresh install and hope feisty works. If not, I'm switching back to Edgy.

---

### Post by Nimefurahi on 2007-04-27
My only problem with the Feisty upgrade was the new kernel and its libata module. When the initrd finished its part of the booting process and jumped over to find my file system, it couldn't even find my root. My grub and fstab were confused by the new naming conventions of IDE drives. At first read of your lament I thought perhaps that you were having a similar problem. As for my problem, I've reconciled the naming convention with a simple workaround at the grub level. (hmm... sounds like a level beneath the soil.... sorry)

You, dear friend, have a much more serious problem with Xorg/beryl/avant that's way over my head. (again I'm beneath the soil with grub)

I'll keep watch of this thread to learn of your eventual success.

---

### Post by mach777 on 2007-04-27
> **chinita96 said:**
> Well, I still haven't found a solution yet. I just get a white screen when I login to the 2.6.10.10-generic. I removed the autostart for beryl and avant window navigator. I will try to read the message files and see what it says. I'm stuck I might have to do a fresh install and hope feisty works. If not, I'm switching back to Edgy.

If boot hangs while trying to detect sata drives, in the menu.lst, as a boot option add: irqpoll

---

### Post by chinita96 on 2007-04-27
Well, I tried the irqpoll and it didn't work either. Thanks for trying but I am completely stumped at this point. I actually decided to reinstall from scratch the edgy eft distro earlier today and did an upgrade again to feisty. This time it launched the splash screen, but it gets stuck at loading. It barely loads at all, just has a little bit of orange bar showing and that's it. It hangs at that stage. Now I am checking the fstab and other files to see what it could be, but I don't even know what this could be.

I hate being defeated by a computer. I will keep trying to get Feisty to work, but if I can't get it working then I will give up and revert back to Edgy Eft. I had no problems with Edgy.

Oh and how would I output the dmesg so I can post? It gets confusing what I've done at this point cause I've tried so many things. I need to look at the logs.

---

### Post by chinita96 on 2007-04-27
Well, I just got into Feisty! Yay! This was after updating my menu.lst one more time with the UUID instead of /dev/sda* then I was able to get into Feisty but the very last kernel option. I was able to login and get into 2.6.17-10-generic. This is of course after my reinstall and upgrade to Feisty. The previous upgrade gave me the white screen in 2.6.17-10-generic. 

So maybe I have a kernel problem? Not sure but atleast I can get into one of them. I'm not sure why I couldn't boot into 2.6.20-15-generic or 2.6.17-11-generic. It just hung at the splash screen and only loaded a tiny bit of orange bar like I said before. Weird. Atleast I can get some work done now. I have been trying to update my website. Now I can finally get something done now that I'm back in Ubuntu.

Thanks again for all your help. If you have any solutions for why I can't boot into the other kernels then please let me know and I'll give it a shot. But for now I'll log into 2.6.17-10-generic kernel.

---

### Post by mach777 on 2007-04-30
> **chinita96 said:**
> Well, I just got into Feisty! Yay! This was after updating my menu.lst one more time with the UUID instead of /dev/sda* then I was able to get into Feisty but the very last kernel option. I was able to login and get into 2.6.17-10-generic. This is of course after my reinstall and upgrade to Feisty. The previous upgrade gave me the white screen in 2.6.17-10-generic. 

So maybe I have a kernel problem? Not sure but atleast I can get into one of them. I'm not sure why I couldn't boot into 2.6.20-15-generic or 2.6.17-11-generic. It just hung at the splash screen and only loaded a tiny bit of orange bar like I said before. Weird. Atleast I can get some work done now. I have been trying to update my website. Now I can finally get something done now that I'm back in Ubuntu.

Thanks again for all your help. If you have any solutions for why I can't boot into the other kernels then please let me know and I'll give it a shot. But for now I'll log into 2.6.17-10-generic kernel.

Did you try adding irqpoll to the line of kernel options at boot alternatively in menu.lst ?

---

### Post by Nimefurahi on 2007-04-30
Bravo Chinita96! !

You're finally into Fiesty.

The newer kernel releases with libata and its affiliated modules enabled have caused me some minor grief. My only workaround was to incorporate the UUID throughout the fstab and menu.lst. At least all seems to work well until you try to invoke hdparm against any /dev/hdx OR /dev/sdx. No, sdparm doesn't work either.

This weekend I "rolled my own" compilation of the 2.6.21.1 release without the libata and SCSI stuff, but somewhere in the config I left out framebuffer or something and I see no splashscreen or vga at all until gdm initializes. Whew boy! No "white screen of death" but rather the "black screen of Limbo". Hmmm... maybe I should try booting without the prescribed initrd.  (just a thought, mind you)

But I'm not complaining. I have no need of video games, crossword puzzles, playing cards, beer drinking or other amusements. Tinkering with Open Source OS gives me more than enough challenge and amusement.

Future success to you, in all of your endeavors!

---

### Post by chinita96 on 2007-05-02
Thanks Nimefurahi. Sounds like you got yourself into a bit of trouble there. I know I've had the "black screen of limbo" before and it doesn't do anything. I'm glad to be back into linux and I still haven't figured out why it won't let me into the other kernels, but atleast I got into one of them and it hasn't caused me any problems since.

mach777 - I did try irqpoll option on boot and it still did the same thing. No change. 

I did notice that my nvidia graphics card might have something to do with the boot problem I am having. I tried to update the nvidia driver and on reboot, x server wouldn't start. It gave me an error with the driver. So I had to remove that driver and reinstall the old version 8776 driver to get back into the only working kernel I have.

I followed these directions I found with other people having graphics card problems. [http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/]("http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/")

Other than that, I haven't had any other problems.

---

