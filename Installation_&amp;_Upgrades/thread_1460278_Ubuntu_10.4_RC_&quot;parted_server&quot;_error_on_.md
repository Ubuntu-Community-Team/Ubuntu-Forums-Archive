---
title: "Ubuntu 10.4 RC &quot;parted_server&quot; error on install"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by magicdave26 on 2010-04-22
Help ! 

I can not install Ubuntu 10.4 RC, if I boot from the disk, it get past the Keyboard choice screen and hangs, if I try the install from Live CD Ubuntu Desktop of 10.4 RC it gets past the keyboard choice screen and gives me the error below

sorry, the program "parted_server" closed unexpectedly


And then will not go any further

Please help, this problem has been going on since Beta 2

Thanks, Dave


---

EDIT:
I tried reporting the error and I got this message, maybe it will help with the problem ?

--
[B]The problem can not be reported:

The program crashed on an assertion failure, but the message could not be retrieved. Apport does not support reporting these crashes.[/B]

---

### Post by magicdave26 on 2010-04-27
> **magicdave26 said:**
> Help ! 

I can not install Ubuntu 10.4 RC, if I boot from the disk, it get past the Keyboard choice screen and hangs, if I try the install from Live CD Ubuntu Desktop of 10.4 RC it gets past the keyboard choice screen and gives me the error below

sorry, the program "parted_server" closed unexpectedly


And then will not go any further

Please help, this problem has been going on since Beta 2

Thanks, Dave


---

EDIT:
I tried reporting the error and I got this message, maybe it will help with the problem ?

--
[B]The problem can not be reported:

The program crashed on an assertion failure, but the message could not be retrieved. Apport does not support reporting these crashes.[/B]


Ok thanks for the help Ubuntu guys, I ended up getting help from a mainly Windows orientated forum. 

(Neowin, the Windows forum to fix all your Ubuntu problems)
(Ubuntuforums, the place to relax and clear your mind)

Solved the problem.

I had an SD Card in the card reader, removing it cured the issue

---

### Post by esemax on 2010-05-01
tnks a lot guys..

 a small usb was plugged in, unbelievable. it was the reason. I have spent 4 hours till i see your response.

---

### Post by erjoalgo on 2010-05-02
I had the same problem, unbelievable the responses you got on that forum as opposed to this one.
In my case, it seems that the problem is a small USB that I have attached in the front.
The problem is, im running ubuntu from that USB!!
As I dont have cd drive in that computer, that is my only option. I hope this gets fixed.

By the way, I agree with the bug reporting problem. They ask you waaaaaaay too many questions, discouraging anyone from posting a bug.

---

### Post by magicdave26 on 2010-05-19
Yea and Ubuntu have not even confirmed this as an error, they have left it unconfirmed, uncomplete

---

### Post by deshowell on 2010-05-25
I have just come newly to Ubuntu. I have been running netbook remix from a USB on my Acer Aspire One - it runs extremely well. When I try to install it I get the "parted_server" error on install and the installation hangs. From other posts it seems the instalation doesn't like SD cards and presumably "parted_server" is trying to partition the card. However my machine is the solid state memory version with 8Gb of memory and no HD. (I needed robustness for travelling) It would seem that it is therefore possibly impossible to install ubuntu on a machine without a HD. Is this correct? 
Des

---

### Post by MadHatter1992 on 2010-07-02
I am having the same problem. I have removed any SD cards and even removed my USB mouse. The only thing I cannot remove is the USB Flash Drive which has Unbuntu on it.

I can't install from a CD because my Asus Eee PC does not have a CD drive.

Can anyone help?

---

### Post by deshowell on 2010-07-09
Hi there.
I solved this on my solid state Acer - I installed the earlier version 9.something. It installs easily, and runs perfectly. Now that I am comfortable with it I am about to try an upgrade from itself avoiding the installation USB - in theory this should work.

---

### Post by dougvk on 2010-09-24
> **deshowell said:**
> Hi there.
I solved this on my solid state Acer - I installed the earlier version 9.something. It installs easily, and runs perfectly. Now that I am comfortable with it I am about to try an upgrade from itself avoiding the installation USB - in theory this should work.

Yes. Just went through this. With 10.04/10.10 I got the parted_server error, but not when I started from 9.04 -> 9.10 -> 10.04.

To all who are having troubles, just gotta do it the slow way.

---

### Post by lilphil on 2010-10-14
I'm just finding the same problem today. I think I have forced it to install now though in a somewhat complex fashion (installing now). I won't go into great detail, as if you don't know what these steps mean then you probably don't want to be doing it this way.

I used a memory stick with grub2 and the netbook iso on it initially (but any bootable disk will do if you can get access to the iso)

1) Format your netbook harddrive in the way you would like it to end up.
2) Mount it, and install grub2 onto the drive (grub2 --no-floppy --root-directory /mnt/foo)
3) copy iso onto harddrive and setup grub2 to boot the iso (google for grub2 iso boot)
4) reboot into live cd from hard drive - this avoids the need for a usb stick but means you can't format from the installer
5) this is the important bit, do a lazy umount of the /isodevice directory (umount -l /isodevice) - otherwise the installer wont continue as the drive is already mounted
6) run through installer but choosing things like manual partitioning and make sure you don't tell it to format anything.

Hope that helps someone!

Edit: This crashed due to out of memory shortly after posting this, so I'm still trying, but I think it would have worked.

---

### Post by Gen. Fussypants on 2010-10-21
I also had this issue with 10.10 on 2 different USB flash drives.  I was using the Windows Universal USB Installer tool to flash the USB drives.  While playing around I decided to enable the 1GB persistent storage option and I suddenly started working without issue.

---

### Post by BigDXLT on 2010-10-29
I've discovered that simply pulling the USB out of the drive will also let me bypass this particular crash.  Not sure if cures it, haven't completed a full install yet (another story altogether.)  Have not tried the persistent storage option yet either (don't know what that does.)

Anyway, maybe these will be the clues someone needs to fix this problem, so reporting my findings here anyway.

---

### Post by PhilEvans on 2011-01-25
Hey folks,

A colleague of mine also had this issue and asked me to have a play. A good way to test exactly what's going on is to open a terminal and run "sudo gparted" and look to see where you get an error. At least on my friend's machine the error reported was a failed assert, that of head_size<=63. This is just a screwy partition table (in her case, on the USB stick from which she was installing Ubuntu).  The stick was made using Windows, already installed on the netbook.

If that's the case, here's what I did to solve it.

1) Find another ubuntu machine (my laptop)
2) Sitck the USB stick in and run dmesg to check the device label given to it (in this case /dev/sdb).
3) Run sudo dd if=/dev/zero of=/dev/sdb bs=1024 count=1024 (note, this kills all the data on /dev/sdb)
4) Download the Ubuntu installer.
5) Run the startup disk creator.
6) Test it: sudo gparted /dev/sdb

The last command ran OK, so job done. Stick the stick back in the netbook and all works. 

Of course, this only solves the problem if the issue was a screwy partition table on the install stick, but running sudo gparted manually will help confirm that.

---

### Post by Ursus7 on 2011-07-27
Hi folks,
I'm a new user and had the same pesky problem at the keyboard stage
many times over (10.04). In desperation, I tries installing from an SD card and PRESTO! Worked like a charm 1st time! I followed the advice and did a 1 GB persistence thing, which may have made a difference, but not sure cuz I did it the 1st try. I tried doing that on a flash chip but still didn't work. Anyway, hope this info helps someone!
Cheers,
Barry

---

### Post by bubu105 on 2011-11-14
> 3) Run sudo dd if=/dev/zero of=/dev/sdb bs=1024 count=1024 (note, this kills all the data on /dev/sdb)

Acctually this is all you need to do (at least it was for me) after you start Ubuntu from your flash drive. No need for searching another PC with Ubuntu.

---

### Post by joepz on 2012-10-05
Now this advice helped me greatly and saved going the long route.
Thanks a lot!!!!:popcorn:

---

### Post by wildmanne39 on 2012-10-06
Thanks for sharing. Thread Closed.

---

