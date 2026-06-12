---
title: "Unable to install"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by Zachmarius on 2009-11-20
Hello,

I am just starting to get into Linux again (It's been many many years) and I'm having trouble installing Ubuntu to my machine. Here's what I have...

Compaq Presario SR1000V
P4 @ 2.6Ghz
MSI - MS 6577
Evga Nvidia GeForce 6200 PCI 256MB
1GB Ram
WDC WD800BB - 80GB
WDC WD1000BB - 100GB (place of installation)
Bios: Phoenix - AwardBIOS v6.00PG

**Also BTW I'm currently running WinXP SP3 on the 80GB**. (Not that it should matter.


And these are the error messages I'm reciving when I try to load Ubuntu.

----------------------------------------------------------------------------

Error for Installation from CD
-------------------------------------------------------------------------------
/init: line 1: can't open /dev/sr1 on /cdrom failed: No medium found
/init: line 1: can't open /dev/sr1 on /cdrom failed: No medium found
mount: mounting /dev/sda1 on /cdrom failed: Invalid argument
mount: mounting /dev/sdc1 on /cdrom failed: Invalid argument
mount: mounting /dev/sr0 on /cdrom failed: Invalid argumen
/init: line 1: can't open /dev/sr1 on /cdrom failed: No medium found
/init: line 1: can't open /dev/sr1 on /cdrom failed: No medium found

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system

(initramfs)
----------------------------------------------------------------------------

Error from Installation on Windows and trying to load

-------------------------------------------------------------------------
Completing the Ubuntu installation. 
For more installation boot options, press 'ESC' now...
0
       [Linux-bzImage, setup=0x3400, size=0x3b26e0]
       [Initrd. addr=0x2f4b6000, size=0x57d098]


BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for list of built-in commands.

(initramfs) mount: mounting /dev/sda1 on /isodevice failed: Input/output error
Cannot mount /dev/sda1 on /isodevice

(initramfs)

---

### Post by mikewhatever on 2009-11-20
It looks like the installer can't see the cdrom for some reason. A simple workaround would be to try installing from a usb stick. I'd also recommend checking the downloaded iso file for errors.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Zachmarius on 2009-11-21
I have tried the winMD5 and the MD5SUM is the same. I am thinking using a USB  stick would be the best. However I cannot find a IMG file for the desktop. It seems like the only ones are CD's. And seeing how that the MD5 is correct yet my computer doesn't like it...

---

### Post by Zachmarius on 2009-11-21
Ok. I've correctly  loaded it onto a cd image as well as loading it onto a usb drive. I've tried to do both installers and still come up with the same error message as in my first post.

Honestly I'm about to give up.

---

### Post by presence1960 on 2009-11-21
> **Zachmarius said:**
> Ok. I've correctly  loaded it onto a cd image as well as loading it onto a usb drive. I've tried to do both installers and still come up with the same error message as in my first post.

Honestly I'm about to give up.

How did you make the bootable USB?

---

### Post by Zachmarius on 2009-11-21
I downloaded the i386 from the Ubuntu main page for the computer I am putting it on from the computer I'm putting it on. I ran WinMD5 to double check that the the MD5SUM was the same on the UbuntuHash page. I then had Unetbootin write the ISO to the USB drive. I then booted up my computer with the USB Drive as the primary. I still had the errors.

I am trying to use Ubuntu 9.10 but I am seeing a lot of documents solving problems for 9.04. Should I try to find 9.04 for a more stable system?

---

### Post by mikewhatever on 2009-11-21
Check out this bug report, [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/143958](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/143958).

> works and I can access the file system. After typing "exit" to return to the menu the CD is found and the next stage in the installer runs correctly and files are copied from the CD.

> I've encountered this same problem on an Acer Travelmate C104TCi, which also uses an external IEEE1394 DVD-ROM/CD-RW drive which appears as /dev/scd0.

From busybox I can do:

mount /dev/scd0 /cdrom
exit

and continue with the installation.

---

### Post by kslen on 2010-07-03
This error just resurfaced while installing Ubuntu 10.04 LTS on a Lenovo S12 netbook throug a USB stick.  Told initramfs to exit two times and it continued to load. :)

---

### Post by irv on 2010-07-03
From the specs on the computer I would think that the newest version (10.04) would work great. My first question would be, why are you trying to install a older version?
Maybe you can start here and just follow the pages to see if there is something you might have miss during installing.
[https://help.ubuntu.com/10.04/installation-guide/i386/pr01.html]("https://help.ubuntu.com/10.04/installation-guide/i386/pr01.html")

---

### Post by irv on 2010-07-03
Sorry, maybe I should have given you this link:
[https://help.ubuntu.com/10.04/installation-guide/i386/]("https://help.ubuntu.com/10.04/installation-guide/i386/")
> This document contains installation instructions for the Ubuntu 10.04 system (codename “‘Lucid Lynx’”), for the Intel x86 (“i386”) architecture. It also contains pointers to more information and information on how to make the most of your new Ubuntu system. 

---

### Post by mark_anon on 2010-10-19
Similar problem on Ubuntu 10.10 Netbook Remix trying to install on a new Asus 1018p.  Tried two different USB sticks, and used two different programs to create a bootable USB... unetbootin and universalusbinstaller.  4 total attempts, and same thing every time...  "Unable to find a medium containing a live file system".

I'd REALLY like to not use Windows 7 Starter, and there's no way I'm paying microsoft to get a usable computer.  (can't even change the background... FU M$!!!)

Also, disabled the quickboot option in bios and the usual boot options were correctly selected.

Huh.  

Any help appreciated.

---

### Post by irv on 2010-10-19
> **mark_anon said:**
> Similar problem on Ubuntu 10.10 Netbook Remix trying to install on a new Asus 1018p.  Tried two different USB sticks, and used two different programs to create a bootable USB... unetbootin and universalusbinstaller.  4 total attempts, and same thing every time...  "Unable to find a medium containing a live file system".

I'd REALLY like to not use Windows 7 Starter, and there's no way I'm paying microsoft to get a usable computer.  (can't even change the background... FU M$!!!)

Also, disabled the quickboot option in bios and the usual boot options were correctly selected.

Huh.  

Any help appreciated.
I don't have a Netbook, and the link I am sending you is for 10.04, but it should work for 10.10 also.
[https://help.ubuntu.com/10.04/installation-guide/i386/boot-usb-files.html]("https://help.ubuntu.com/10.04/installation-guide/i386/boot-usb-files.html")

---

### Post by mark_anon on 2010-10-20
Thanks for the link.  Tried using Ubuntu's built in startup disk creator program first, and same result as the other programs.

Tried the link you sent, and after some trial and error got it to load everything but then received this error:

[I]mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
Non init found. Try passing init= bootarg.
[/I]
Sigh.

---

### Post by mark_anon on 2010-10-20
Ah HAH!!!

Evidently, in addition to disabling the quick-boot option in the bios, you MUST use the left USB port on the Asus 1018p.

I was trying to install using the right usb ports, which are USB 3.0, however are apparently not bootable.

Thanks to the fellas at linlap.com

[http://www.linlap.com/wiki/asus+eee+pc+1018p](http://www.linlap.com/wiki/asus+eee+pc+1018p)

---

### Post by durilka on 2010-10-30
> **mark_anon said:**
> Ah HAH!!!

Evidently, in addition to disabling the quick-boot option in the bios, you MUST use the left USB port on the Asus 1018p.

I was trying to install using the right usb ports, which are USB 3.0, however are apparently not bootable.

Thanks to the fellas at linlap.com

[http://www.linlap.com/wiki/asus+eee+pc+1018p](http://www.linlap.com/wiki/asus+eee+pc+1018p)

I double that.
Tried installing on HP8540w and had the error with the right-side usb and eventually had it work with the left ones (don't really know if right is 3.0 and left 2.0). So the solution is to use different usb port.

---

### Post by mnix on 2010-11-05
I was just looking at this thread since I had a similar problem trying to install 10.10 from CD.  I finally figured it out.  I tried to think about everything I had changed since I had previously installed 10.04.  I remembered changed the SATA port that the DVD drive plugged into, based on advice for installing OSX (which I had been trying to do).  I moved the connector back and sure enough, no more "..unable to find live file system" problem.

---

### Post by Linuxselva on 2010-11-24
Hi Everyone,

I am facing the same error message like this user. Does this mean the CD is corrupted.


Error for Installation from CD
-------------------------------------------------------------------------------
/init: line 1: can't open /dev/sr1 on /cdrom failed: No medium found
/init: line 1: can't open /dev/sr1 on /cdrom failed: No medium found
mount: mounting /dev/sda1 on /cdrom failed: Invalid argument
mount: mounting /dev/sdc1 on /cdrom failed: Invalid argument
mount: mounting /dev/sr0 on /cdrom failed: Invalid argumen
/init: line 1: can't open /dev/sr1 on /cdrom failed: No medium found
/init: line 1: can't open /dev/sr1 on /cdrom failed: No medium found
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) Unable to find a medium containing a live file system
(initramfs)
----------------------------------------------------------------------------
Error from Installation on Windows and trying to load
-------------------------------------------------------------------------
Completing the Ubuntu installation.
For more installation boot options, press 'ESC' now...
0
[Linux-bzImage, setup=0x3400, size=0x3b26e0]
[Initrd. addr=0x2f4b6000, size=0x57d098]
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for list of built-in commands.
(initramfs) mount: mounting /dev/sda1 on /isodevice failed: Input/output error
Cannot mount /dev/sda1 on /isodevice
(initramfs).

---

### Post by mshadows on 2010-12-25
Incredible... Been battling with this ALL day! I can also confirm that it's the left USB port rather than the right. 

Thanks so much for the fix!

---

### Post by fbicknel on 2011-01-24
For the Lenovo ThinkPad W510, locate and use the USB port in the back - the ones on the side don't work for this purpose, it seems.

(That was scary.)

---

### Post by Basisnk on 2011-02-02
Dell XPS 15: 
Use the USB port to the right (USB/eSATA combiport). 
The USB 3 slots to the left and at the back are not working for this purpose (initreamfs error message: unable to find a medium containing a live file system)

---

### Post by metalman2007 on 2011-02-05
I've experienced the same issue and believe it or not it has nothing to do with the CD Rom, Medium in which it was burned, or USB device. The issue is the Nvidia 6200 Graphics card. Don't believe me? Try this experiment; remove the nvidia graphics card from your computer and then plug the monitor cable into the onboard video. You're going to see how you no longer get:

/init: line 1: can't open /dev/sr1 on /cdrom failed: No medium found
/init: line 1: can't open /dev/sr1 on /cdrom failed: No medium found
mount: mounting /dev/sda1 on /cdrom failed: Invalid argument
mount: mounting /dev/sdc1 on /cdrom failed: Invalid argument
mount: mounting /dev/sr0 on /cdrom failed: Invalid argumen
/init: line 1: can't open /dev/sr1 on /cdrom failed: No medium found
/init: line 1: can't open /dev/sr1 on /cdrom failed: No medium found

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system

(initramfs)

At this point the installation will continue without any issues. But you want to use your Nvidia graphics card right? How else would you use TV out? Well let me tell you, I have tried everything. Went to the bios and made the PCIE video primary and still nada. A lot of folks here have been very generous with offering tips and suggestions but I found myself replying with "Been there, done that, nothing!". You're going to find this with most of the other linux open source distros as well. I have built other computers in which i've loaded Ubuntu or kubuntu on and it's never been an issue. Very frustrating.

---

### Post by SantanaNL on 2011-02-22
I too had this error:
(initramfs) Unable to find a medium containing a live file system

But a friend of mine suggested another solution than all of the above. Create the USB stick with unetbootin from a Linux (Ubuntu) box and NOT a windows system. Apparently something is different between the two because now my system just boots flawlessly!

---

### Post by jaxxed on 2011-03-19
Definitely follow the advice listed above.

Try using a different USB port, as some of them won't boot properly.

My PC is an Asus AIO

---

### Post by Soplica on 2011-04-16
Hey fellas, I had the same problem and I have a solution. The problem is the BIOS settings. I entered to BIOS and in Advanced Bios Features menu I have changed the Installer OS Select option to -> Others. Save and exit the BIOS. And that was it, installation went silky smooth. I hope I could help. Greetings.

---

### Post by jtholb on 2011-06-24
I realize this is an old thread, but I just ran into the same problem with a Shuttle SH67H3 and thought I'd add my bit

I was booting off a USB flash drive and the problem was also that it was inserted into a USB 3.0 port.  When I switched it to a USB 2.0 everything went off without a problem.  Thanks you guys.

---

### Post by hutxubix on 2011-07-08
I was having this issue/problem "Unable to find a medium containing a live file system" for all versions of ubuntu from a Live CD on a PC (I was really trying 11.04).

After much trying, the solution was very easy in the BIOS (as some other people have found):

In Settings -> Integrated Peripherials -> Sata Configuration -> Sata Mode -> (It was in IDE in my case, for other people it was in RAID by default) you have to change it to AHCI and now you can install it!!!

Thank you everybody.

---

### Post by dvlong on 2011-07-11
I have been re-installing 11.04 because there were display issues I was unable to resolve - they seemed to occur overnight without anyone's help while the computer was off.

When I decided to reinstall new from the cd I had this error:
"(initramfs) Unable to find a medium containing a live file system." 

The drive began acting this way and I finally had to install from a usb drive. Now installed, I'm unable to mount the drive. It shows up in bios, and will boot but if it's an Ubuntu live cd, I get the above error. 

Once loaded from my harddrive, the CD doesn't appear. I've searched all relevant forums that I can find but haven't been able to come up with anything.

---

### Post by Ken Wood on 2011-07-20
Changing from IDE to AHCI in the BIOS resolved the issue for me. Thanks for your help. What a great community. :D

---

### Post by Juand_au on 2011-08-29
> **jaxxed said:**
> Definitely follow the advice listed above.

Try using a different USB port, as some of them won't boot properly.

My PC is an Asus AIO


This made it work for me as well, Thanks!!!! Asus computer

---

### Post by Stolgrove on 2011-09-02
I am installing on an Acer Aspire 1, I just threw in 1 GB ram and replaced my broken WD drive with one from an external. So I like to think its starting from scratch. Using the USB installer for Ubuntu (newest version). 
It runs the the install phase to the ubuntu loading window(similar to windows splashscreen), then goes through a stage where code is racing past on the screen. 
System pauses @ begin: preconfigure networking... .. /scripts/casper-bottom/23networking: line 31: can't create /root/etc/network/interfaces: nonexistant directory

After a minute, it jumps through more lines than I can stand to type on this phone

Mount: mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

BusyBoxv1.17.1 (ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter..help.....
(Initramfs) -

I have tried the switching usb ports, with small change and same end results, this will be the only OS running on the computer, and its a netbook, so usb is my only decent input.
Ran a memory test, 1 successful pass. 

Help Obi-wan Kenobi, your my only hope....

---

### Post by marijke on 2011-10-04
I got the same problem. Trying to install from a USB. Same message when having the USB in the side. When I put it in the back, the computer just ran the normal stuff, which then didn't work properly (could not shut down the computer until I took the USB out. 

I got an Acer Aspire 9300

ETA, using one of the other 3 ports did the trick.
I find this the weirdest problem ever.

ETA2: Stupid me had not plugged in the laptop properly so it turned itself off halfway installing. now I got the same problem again. unable to find a medium. In the same usb port. I don't get it.

---

### Post by marijke on 2011-10-05
yay, got it to work. stars must have aligned after all.

But the microphone doesn't work yet, which is a bummer.

---

### Post by CoDeHacKer on 2013-02-15
Hey, thanks, switching from left side to right 3.0 to 2.0usb ports worked for me.

:KS

---

