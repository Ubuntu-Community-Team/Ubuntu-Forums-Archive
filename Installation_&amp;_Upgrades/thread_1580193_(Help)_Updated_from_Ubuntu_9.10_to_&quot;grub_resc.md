---
title: "(Help) Updated from Ubuntu 9.10 to &quot;grub rescue&gt;,&quot; kinda disappointed with the GUI"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by JaggedG on 2010-09-23
So I'm having a problem that is way out of my league. I consider myself fairly computer savvy but I am not familiar with Linux at all because I've been running it for less than a day. So here is a brief history of my problem:

-Ran Windows XP Media Center for most of the life of this HP Pavilion notebook with 2 hard drives, C: and D:, no partitions except the default HP recovery partition

-Yesterday, installed Ubuntu 9.10 through Wubi on D: from an ISO (because the CD drive doesn't work). I assigned it 30gb on D:, which I assume created a 30gb FAT32 partition on this secondary drive.

-Dual-booted successfully from Grub between XP and Ubuntu, so I thought, "Mission accomplished" and started making friends with GNOME. Got a pretty good score in Tetris.

-Was asked if I would like to update to the latest Ubuntu (10.04 I think?) which struck me as a good idea. Everything went smoothly until it asked me to reboot.

-Reboot brought me to a command-line that says "grub rescue>" and above it says "error: no such device: e76e00f3-........" (there's more, I can write it out if that helps)

-Rebooted several more times (cause that usually fixes things) but just got back to "error: no such device: ..." and "grub rescue>"


And that's where I am now.

I gotta stress now, I have almost no experience with how Linux (UNIX?) works differently than Windows or how to use the command line... I know that the hard drives are (hd0), (hd1) instead of C: and D: and that everything important seems to start with "sudo" and that's about it. I was going to ease myself into the whole thing gradually, picking up little bits as I go along... But now I'm just stuck in command line limbo and none of my usual troubleshooting strategies apply here, not even yelling rude things about the computer's manufacturer. 

It's like learning to swim by being thrown into the deep end for me... I need some water-wings before I drown :( Everything I read so far has either been irrelevant to my problem or over my head... I kind of need somebody to go back to square one with me. I'm willing to put in the work, I just need some guidance.

---

### Post by Rubi1200 on 2010-09-23
Hi and welcome to the forums :)

Ok, I am not going to answer all your points as some of them you will learn going forward.

But, I will address the most important ones:

Wubi creates a virtual disk _within_ your Windows installation.

The upgrade almost certainly messed things up.

Don't worry, there is a solution.

Wubi is not really intended for anything except to try Ubuntu; it would be much better to create a partition for Ubuntu and dual-boot with Windows.

Very important question: do you have the Windows installation or recovery CD?

Because what you need to do is reinstall the Windows bootloader.

This explains what has happened to you:
> **[COLOR=Red][SIZE=3]Important Note to Wubi (Windows Ubuntu) Users: Grub Update results in "No Such Disk":[/SIZE][/COLOR] **
A late July 2010 Grub 2 update is causing a "**[COLOR=DarkRed]no such disk[/COLOR]**"  error for some users of WUBI, resulting in an unbootable system. If the  system doesn't display the original Windows menu, the most likely cause  of the failure is that Grub 2 was installed in the MBR and/or on the  Windows partition. To correct this, restore the Windows bootloader using  this link:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

Whether the failure is due to improper user selections or Grub 2's  failure to recognize a Wubi install, it has been reported in the  following bug and users can review it for status updates and recovery  options when they become available:
[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

This link explains how to restore the bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

This explains how to dual-boot:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

If you have any questions, feel free to ask.

---

### Post by JaggedG on 2010-09-23
Thanks for the quick response!

I totally see how the Wubi build and the normal upgrade were never meant to be together, I feel like I should have figured that out on my own. Damn. I hope I didn't damage my file system or anything?

I am not sure off the top of my head where my recovery CD is, but I think a more impeding problem is that the CD drive does not actually work. That's why I installed with Wubi, actually... It seemed like an elegant solution to my problem.

So is there another way to reload the Windows boot loader?

---

### Post by Rubi1200 on 2010-09-23
Does your BIOS allow booting from USB?

If yes, there is another alternative, but it makes no sense to mention it now if you are not able to do so.

---

### Post by JaggedG on 2010-09-23
Yes, it seems so. In my BIOS boot order options, it has:

USB Floppy
ATAPI CD/DVD ROM Drive
Notebook HD
USB Diskette on Key
USB Hard Drive
! Network Adapter

(Not sure what the ! in front of "Network Adapter" is about, I think it means booting from it is disabled... But it's there)

---

### Post by Rubi1200 on 2010-09-23
Ok, what we are going to have to do is download the latest stable version of Ubuntu and put it on a USB stick. The easiest program to use, in my opinion, is called UNetbootin.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Then, boot the laptop setting BIOS to boot from > USB Diskette on Key if the first option > USB Floppy does not work.

You choose to try Ubuntu in live mode (not install) and once at the Desktop open a terminal (Applications > Accessories) and enter the following commands:

NB: don't worry if there are error messages

```
sudo apt-get install lilo

``````
sudo lilo -M /dev/sda mbr
```> May show error messages about the rest of lilo missing, ignore, we just want MBR

(courtesy of forum member oldfred)

This fix will restore a basic Windows bootloader; it is not pretty but effective nonetheless.

---

### Post by JaggedG on 2010-10-01
Great! That did it, thanks for your advice :) The other two boot options didn't wok (USB diskette and USB floppy) but when I tried it as a USB hard drive, voila. The installation was smooth, and I actually find Lilo quite elegant. I'm back into Windows with no problem. So now my question is... How do I make a proper installation of Ubuntu, instead of the virtual one that Wubi set up? My original idea was to keep the disk that currently has Windows running Windows, and put Linux on the other hard drive to dual-boot.

Also... I'm kind of curious about what exactly I did by following your instructions... Like I don't really know what the commands did. Is there like an "Introduction to the Terminal" book that I should read or something?

---

### Post by Rubi1200 on 2010-10-01
> **JaggedG said:**
> Great! That did it, thanks for your advice :) The other two boot options didn't wok (USB diskette and USB floppy) but when I tried it as a USB hard drive, voila. The installation was smooth, and I actually find Lilo quite elegant. I'm back into Windows with no problem. So now my question is... How do I make a proper installation of Ubuntu, instead of the virtual one that Wubi set up? My original idea was to keep the disk that currently has Windows running Windows, and put Linux on the other hard drive to dual-boot.

Also... I'm kind of curious about what exactly I did by following your instructions... Like I don't really know what the commands did. Is there like an "Introduction to the Terminal" book that I should read or something?
I am really pleased things worked out for you :)

To answer your questions:

 > How do I make a proper installation of Ubuntu, instead of the virtual one that Wubi set up?There are a couple of options; either create a separate partition and install Ubuntu there or migrate the Wubi install to the drive (this is useful if you had already saved work, pictures etc. and do not want to start over again).

This guide by forum member bcbc walks you through the process:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

 > I'm kind of curious about what exactly I did by following your  instructions... Like I don't really know what the commands did. Is there  like an "Introduction to the Terminal" book that I should read or  something?An explanation:
```
sudo apt-get install lilo
```sudo invokes administrative rights; apt-get is the mechanism to install or remove software; lilo is a bootloader program.

```
sudo lilo -M /dev/sda mbr
```Again, sudo invokes admin rights; lilo -M tells the program what it needs to do (write a Master Boot Loader to a drive); /dev/sda/mbr is the path where lilo needs to go; in other words, the Master Boot Record of the first drive.

As to learning about the terminal:
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

This is a good place to start.

If you have more questions, feel free to ask.

---

### Post by JaggedG on 2010-10-03
Okay. Well my ideal end result would be to keep the hard drive that's running Win XP doing that, and to have the other hard drive formatted to run Linux and then dual boot between the two. My reason is just because it seems simpler to keep one hard drive totally NTFS and the other totally FAT32. I don't need to keep the Wubi installation, I feel like it's better karma just to start fresh :KS

I used the "Install Ubuntu" application that is on the desktop when I boot from the USB key (a live session?), but it didn't seem to offer that option, it looked like it wanted to create a partition on the drive that XP is installed on. Although I've backed up my C: in anticipation of the collateral damage of the learning process, I didn't want to do anything until I'm armed with a little bit more knowledge here...

---

### Post by JaggedG on 2010-10-18
Bump please? :(

---

