---
title: "Ubuntu Server 12.04.3 LTS Install Failure"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by zpierce on 2013-08-28
Hello,
I am attempting to install Ubuntu Server 12.04.3 LTS on an old Dell machine that has been wiped.  During the "Loading Additional Components" portion of the install, it fails to read a file and cannot complete.  I ran the "Check Disc for Defects" option and get:
.pool/main/m/maas/python-maas-provisionserver_1.2+bzr1373+dfsg-Oubuntu1~12.04.1_all.deb
file failed the MD5 checksum verification. Your CD-ROM or this file may have been corrupted.

I am installing from a USB drive.  I downloaded the 12.04.3 LTS 64-bit from [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server) and created a bootable usb disk using Universal USB Installer 1.9.3.9.  When that failed, I tried creating it with Unetbootin.  When that failed, I tried a different USB drive.  When that failed, I redownloaded the whole thing and tried all of the above again.  I have consistently gotten the same error on every attempt.

At this point I can only think that Ubuntu has a corrupted file for download, unless someone can suggest something else.  Help would be a appreciated.

---

### Post by papibe on 2013-08-28
Hi zpierce.

My guess is either your download file got corrupted, or the USB stick have some issues.

You can test the integrity of the download yourself using MD5 on the ISO and comparing it to the sums found [here]("http://releases.ubuntu.com/12.04.3/MD5SUMS"). If it doesn't match you need to downloaded again. I recommend downloading using torrent since it reduces the chances of corruption significantly.

Once you are sure the ISO file is OK, burn it again.

To check if that process went OK, boot into the installation media and check its integrity choosing the proper option from the menu (something like [this]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck")).

Hope it helps. Let us know how it went.
Regards.

EDIT: To burn/install the ISO on the USB stick, I'd recommend using the method described on post#4 [here]("http://ubuntuforums.org/showthread.php?t=2153157&highlight=server+usb").

---

### Post by zpierce on 2013-08-28
Thanks for the reply,
I wasn't clear before, I used 2 different USB sticks and 2 separate downloads of the .iso.  I didn't try using MD5 to test the download, I will do that tomorrow.  This is a server I'm trying to set up at work, having told my coworker there's no need to buy a new Microsoft Server license, so hopefully I get it working soon.

---

### Post by zpierce on 2013-08-29
papibe,
Just to report back, the thread you linked to, which  ultimately linked to [http://crunchbang.org/forums/viewtopic.php?id=23267](http://crunchbang.org/forums/viewtopic.php?id=23267),  solved the problem.  Seems it is a bug with the installation  referencing a CD.  Thank you for your help.

---

### Post by danhansendenmark on 2014-02-23
Hi,

I did this post, because even though this thread is marked "SOLVED" the fix didn't work in my case.[I]


With thanks to Mr. David W. Pierce & Mr. Christopher Hinkle[/I]

I've been fighting this all night long.. Now it's early morning and I found the solution. 
There's many different suggestions to the problem out there, and I can  see why some are trying to fix it by mounting this and mounting that. It  really looks like a mounting error. But please note, that the error in  most cases appears _after_ reading from the USB-stick. The real issue is  the file names. If you want to install e.g. Ubuntu 12.04 Desktop  there's no problem. If you want to install Ubuntu Server 12.04 you got a  problem. 

Mr. AgentOfCode describes the problem pretty good in this thread: [http://ubuntuforums.org/showthread.php?t=2152193](http://ubuntuforums.org/showthread.php?t=2152193)

It doesn't help to choose another method, Unetbootin, Lili USB Creator, Pendrivelinux etc., same error!

Here' the solution! You can use this solution in both Windows and Linux, doesn't matter were you make the bootable USB-stick
Follow this Todo: [http://cirrus.ucsd.edu/~pierce/fix_ubuntu_usb/]("http://cirrus.ucsd.edu/%7Epierce/fix_ubuntu_usb/")

If the link for some reason goes dead, please don't hesitate to leave a  note, I've downloaded the scripts and wrote a short ToDo...

I'll leave this solution in the forums I have access to...

Kind Regards,
Dan Hansen
Denmark

---

### Post by gugani-pub on 2014-02-27
Thanks danhansendenmark for the info. The Perl Script in [http://cirrus.ucsd.edu/~pierce/fix_ubuntu_usb/](http://cirrus.ucsd.edu/~pierce/fix_ubuntu_usb/) worked for me.

---

