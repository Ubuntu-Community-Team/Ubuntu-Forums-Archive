---
title: "Ubunto 7.04 installs but pc won't boot after"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by davlaw2000 on 2007-08-19
Hi can someone please help? I am doing a 'clean' install of Ubuntu 7.04 on my PC. I won't post spec details yet as I think it's not relevant. 
I downloaded 7.04 and created a bootable CD. It boots fine, and installs Ubuntu smooth as anything. Once it says it has finished and needs to re-start the PC, it ejects the CD and the PC re-starts, but gives me an immediate error message saying that it can't find a bootable disk. The exact error message is "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER". 
I have tried the installation twice now, both times making sure the hard disk is partitioned and formatted along the way. Both times the same result. It's as if it has done everything EXCEPT make the disk bootable, which is really wierd. 
If I boot off the CD and look at the hard drive, I can see all the correct directories etc on it. 
I bet it's me doing something wrong but I can't think what it might be. Any suggestions?

---

### Post by Pumalite on 2007-08-19
Re-install Grub following these guidelines: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by davlaw2000 on 2007-08-19
Well I followed the instructions provided on the thread, and got all the right noises back from Grub but it made no difference. This is really wierd. At first I thought it was a fault with my hard drive but I have tried with 2 different drives and I get the same problem with both. 
This is so frustrating. I still have a live CD somewhere around with Edgy on it - I think I will re-install that and see what happens. Meantime please keep those suggestions coming!
Thank you.

---

### Post by Pumalite on 2007-08-19
Post: sudo fdisk -lu (using Live CD; from File System)
Post: cat /boot/grub/menu.list ( same )

---

### Post by davlaw2000 on 2007-08-19
OK will do.... might be a little while as I am part-way through putting Edgy back on (currently at 66%). 
I noticed a major difference with the Edgy install - it specifically mentions that Grub will be installed, whereas I didn't see that message when I installed 7.04. 
Why would it not put Grub onto a machine after formatting the hard drive? Wierd. 
:confused:

---

### Post by Pumalite on 2007-08-19
If you use Live CD for installation, in step 7 there is an 'Advanced' tab that allows you to choose where to install Grub. Default is (hd0,0)

---

### Post by davlaw2000 on 2007-08-19
Now this is very odd. Edgy has just done the same thing to me. Must be a hardware fault or an incorrect BIOS option. I will have a dig around and report back!! :(

---

### Post by davlaw2000 on 2007-08-19
Found it! The boot sequence was wrong in the BIOS. I have two hard drives, and it showed drive 1 in priority over drive 0. As soon as I switched them around it was fine and now Edgy boots OK. 
Now I'll start over with Feisty and hopefully it'll be OK this time. 
Thanks for your help!

---

### Post by t0nydean on 2007-09-26
I am having the same issue..I have gone through all the steps and I am just out of ideas....boot sequence in BIOS is good, install says it works ok, then I reboot and get "please install system disk" 

running off the live cd works fine, and the hardware was a working windows machine before i reformatted to Ubuntu, and I have run several utilities that have reported no problems with the HD or memory.

any ideas? 
Besides throwing the whole thing in the lake, I already thought about that...

---

### Post by Pumalite on 2007-09-26
XP or Vista?

---

### Post by t0nydean on 2007-09-27
it was XP

---

### Post by Pumalite on 2007-09-27
Post specs.

---

### Post by t0nydean on 2007-09-28
Presario S4120WM
AMD Athlon XP 2.13 GHz 
512 MB / 60G 

Its a pretty old machine, but was running fine on Windows Xp Home sp2

I have tested the hardware several times and it always comes up clean.


detailed specs here:
[http://www.dealtime.com/xPF-Hewlett-Packard-HP-S4120WM-AMD-Athlon-XP-2600-256MB-60GB-DVD-ROM-CR-RW-Combo-Windows-XP-Home-Edition-R-](http://www.dealtime.com/xPF-Hewlett-Packard-HP-S4120WM-AMD-Athlon-XP-2600-256MB-60GB-DVD-ROM-CR-RW-Combo-Windows-XP-Home-Edition-R-)

---

### Post by Pumalite on 2007-09-28
Your link tells me that you have an AGP slot, but it doesn't tell what kind of Video Card do you have.

---

### Post by t0nydean on 2007-09-28
I have an aftermarket ATI 128MB card installed....I forget exactly which one...I can boot the machine on the live cd and try to find out, but I'm not really sure how to see that info in Ubuntu...(still a recovering Windows user :) )

---

### Post by Pumalite on 2007-09-28
You are better off trying the Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign 'Start Download'

---

### Post by t0nydean on 2007-09-28
I'm downloading that alternate CD now...

What is the difference between that and the live CD?

---

### Post by Pumalite on 2007-09-28
You can avoid graphical and possible hardware problems. You also have more control over the installation process.

---

### Post by t0nydean on 2007-09-28
Cool....anything I need to know? keeping in mind I am a total Ubuntu n00b

---

### Post by Pumalite on 2007-09-28
Learn with the knocks and report back. We are always here.

---

### Post by t0nydean on 2007-09-28
I tried with the alternate CD and when it got the step called "select and install software" I got a red screen of death...it said the step failed but I could possibly continue, so I did, and the GRUB install to the master boot record failed as well...I ran the verify CD-ROM utility and it said the CD is fine. 

I wish it gave a little more detailed info, such as why it failed or what software caused the problem...

---

### Post by Pumalite on 2007-09-28
Did you do an md5sum on the iso?Did you burn at 4x?

---

### Post by t0nydean on 2007-09-28
I burned the ISO at 32x, and I do not know what a md5sum is. 

I re-ran the install and it completed ok this time, I didnt do anything different...I still have the problem of getting it to boot off the hard drive though...I again  got the error "boot disk failure, please insert..." after it re-booted itself when the install finished.

So you think re-burning the iso at 4x will make a difference?

---

### Post by Pumalite on 2007-09-28
Doing the md5sum too.
[http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html)
[http://www.etree.org/md5com.html](http://www.etree.org/md5com.html)
[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)
[http://en.wikipedia.org/wiki/MD5](http://en.wikipedia.org/wiki/MD5)
[http://www.pc-tools.net/win32/md5sums/](http://www.pc-tools.net/win32/md5sums/)
[http://www.delorie.com/gnu/docs/textutils/md5sum.1.html](http://www.delorie.com/gnu/docs/textutils/md5sum.1.html)

---

### Post by t0nydean on 2007-09-29
well, The md5sum checked out ok and I re-burned at 4x with the same results....boot disk failure after a "successful" install....

I'm beginning to think it just isnt going to happen

---

### Post by Pumalite on 2007-09-29
Let's see what you have in your computer. Get a Knoppix: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Boot from it and from the terminal post:
sudo fdisk -lu
(Also check your partition and see if you can find a 'boot' and a 'Grub' folder.)

---

