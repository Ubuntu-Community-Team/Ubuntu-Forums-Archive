---
title: "Trouble installing 9.10"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by John Z on 2010-03-07
When I try and install Ubuntu 9.10 it gets to the flashing Ubuntu logo, then the screen just goes black.

It then says: (initramfs) Unable to find a medium containing a live file system.

I've searched for similar problems, but the proposed solutions don't seem to work for me.

I also tried the disk on a another computer and it worked fine, and I've installed Ubuntu 7.10 on this computer before without a problem.

Thanks.

---

### Post by uRock on 2010-03-07
In the boot screen, have you run the "check disk"?

---

### Post by John Z on 2010-03-07
Yes. When I run it from this computer it just gives me the same blank screen and message. 

When I ran the disk check on my other computer it said it was fine.

---

### Post by uRock on 2010-03-07
What are your system specs?

---

### Post by John Z on 2010-03-07
AMD Athlon 64 Processor 3500+
1.0GB Ram
NVIDIA GeForce 8800 GT
Widows XP Professional SP3

Anything else?

---

### Post by uRock on 2010-03-07
It is odd to say the least. There shouldn't be any problem with your hardware. I am thinking that there has to be something wrong with the live image.

---

### Post by Kaligo on 2010-03-07
Could be faulty RAM. Have you tried running the Memtest utility?

---

### Post by John Z on 2010-03-07
I just finished running the memory test utility. It got no errors.

I also tried downloading a copy from a different source and burning it, but I get the same issue.

Could the CD's be the issue?

---

### Post by Kaligo on 2010-03-07
How long did you run memtest for? I normally let it run overnight to get a thourough scan.

---

### Post by uRock on 2010-03-07
> **John Z said:**
> I just finished running the memory test utility. It got no errors.

I also tried downloading a copy from a different source and burning it, but I get the same issue.

Could the CD's be the issue?

CD brand shouldn't be an issue. I use the cheapest ones I can find and they still work. Are you burning them at a reduced speed? The high speed can cause problems sometimes.

---

### Post by Kaligo on 2010-03-07
If the CD boots fine in another computer and the disk check verifies it then it is unlikely to be anything to do with the installation disk.  I defnitely suspect some hardware fault/incompatability.

---

### Post by korgkeys on 2010-03-08
I'm having the exact same problem with the 64 bit installation (live execution, disk check and install options).

ASUS M4A78TE motherboard, 8GB RAM, AMD Phenom II X4 @ 3.4 GHz and PNY GeForce GT220.

I've tried burning the CD a couple of times but got the same error.  I've downloaded a fresh copy of the ISO image and ran a diff between the two downloads - no differences,

This system has been running a 64 bit Slackware setup under XWindows and doing a lot of compiles with no problems for several weeks.  It doesn't appear to be a hardware problem.

---

### Post by John Z on 2010-03-08
I've seen some bug reports of similar issues for 9.10 but I haven't found any conclusive answers.

Is there anything else I can try? I would really like to get Ubuntu up and running on this machine.

---

### Post by korgkeys on 2010-03-08
Okay, correction to my configuration listed above.  I was running Slackware with the on-board ATI controller.  It doesn't have support for the GT220 in its drivers.

As a test I pulled the GT220 and tried installing the 64 bit Ubuntu 9.10 again.  Still no luck - same problem.

I also tried installing the 32 bit Ubuntu 9.10 - same problem.

Went back to a 32 bit Ubuntu 8.04 disk that I had used in the past.  Was able to run the live execution option with no trouble.

So...  There's something broken in the 9.10 distribution for this MB or processor.  I suspect that the more likely suspect is the processor.  Something specific to the newer AMD processors - probably some kind of processor specific optimizations or tests.

*sigh*

---

### Post by uRock on 2010-03-08
When you put in the LiveCD and the boot menu comes up press F4 and select safe graphics mode.

---

### Post by Pratik Ali on 2010-03-08
Hi,

 
Upon partitioning during install, I receive the following message:
   
Error informing the kernel about modifications to partition /dev/sda2 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda2 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.

 
It is repeated over and over again.

 
This is during the installation of Karmic, and I have tried it in various possible ways, i.e., first by manually assigning the partitions, then even by letting the setup do it for me. 

 
My specifications were:

 
swap  2833mbs
/           10288mbs
/home  10000mbs
fat32    20000mbs

 
have been running on live cds ever since.

 
Please help.

---

### Post by Kaligo on 2010-03-08
@JohnZ Did you try running memtest overnight?  You could also try the alternate installer.

---

### Post by John Z on 2010-03-08
I didn't run the memtest overnight. I sleep right next to the tower, so I'd like to leave that as a last resort.

I'll run it in safe graphics mode and see if that helps.

---

### Post by John Z on 2010-03-08
Okay I tried it in safe graphics mode. No luck.

I think I'll give 8.04 LTS a shot. Maybe it's just the specific version of Ubuntu causing the problems.

---

### Post by 2hot6ft2 on 2010-03-08
Since the disc works (checks ok) on another computer I'm thinking the cd/dvd drive. Have you tried blowing it out with compressed air or one of those lens cleaner discs.

I've even had problems with a disc and if I wiped it on my shirt then blew any dust off of it just before sticking it in the drive it would work.

I have had similar problems in the past and swapped the cd/dvd drive out with another one to get it to work. That was a desktop so it may not be an option for you.

Just some things to try.

---

### Post by John Z on 2010-03-09
I don't think the problem was my CD drive, or the live image. I downloaded and burnt Ubuntu 8.04 the same way as I did 9.10, but 8.04 worked perfectly.

---

### Post by uRock on 2010-03-09
> **John Z said:**
> I don't think the problem was my CD drive, or the live image. I downloaded and burnt Ubuntu 8.04 the same way as I did 9.10, but 8.04 worked perfectly.

So, Hardy is working where Karmic didn't? That bites. At least Hardy has a little over a year of support left. Hopefully Lucid will work for you when it comes out.

---

### Post by Die in Sente on 2010-03-09
I'm having the exact same problem.

Downloaded ubuntu-9.10-desktop-amd64.iso
Verfied the MD5 checksum (DC51C1D7E3E173DCAB4E0B9AD2BE2BBF)
Burnt to CD with Nero.  (Nero verfied the burn!)
When I boot the disk and try to install:

[LIST]
[*]Screen goes blank for about 2 minutes, then the Ubuntu logo appears
[*]Screen goes blank again and stays blank for up to 15 minutes!
[*]When I touch the keyboard, text appears on the screen, with the error message:     (initramfs) Unable to find a medium containing a live file system.
[/LIST]
I've been using this computer for over a year;  It has Windows 7 Ultra, Windows XP (64 bit) and Open Suse (64-bit)  installed on it, all working OK.

The disk is readable and the DVD drive is working fine if I boot one of the other OSes.

If I try the disk's self-test option, get the same blank screen and error message.

I previously installed the 32-bit version of ubuntu 9.10 on this same system without incident.  (And uninstalled it after I realized my mistake;  I need the 64-bit version)

Since the problem can't be download corruption or bad hardware or bad CD, I can only guess that the live image on the disk has some sort of "plug-and-play" bug, that it can't read the disk.

The motherboard has ATI RD790 and SB600 chipsets.

---

### Post by uRock on 2010-03-09
> **Die in Sente said:**
> If I try the disk's self-test option, get the same blank screen and error message.

Bad disk. Try a lower speed when you burn the next one. Maybe even try [Infra Recorder.]("http://infrarecorder.org/")

---

### Post by Die in Sente on 2010-03-09
P.S. iRock's suggestion to use the F4 - Safe Graphics Mode install had no effect for me.

---

### Post by Die in Sente on 2010-03-09
> **iRock said:**
> Bad disk. Try a lower speed when you burn the next one. Maybe even try [Infra Recorder.]("http://infrarecorder.org/")

iRock,

[SIZE=4]*_**NO**_*[/SIZE] it most definitely is [SIZE=4]_***not ***_[/SIZE]a bad disk.  As I said above, Nero verified the burn, and when I boot one of the Windows partitions in the same machine, it reads the disk fine.

Since my previous post, I've booted the CD in another computer, and run the integrity test and it reports no errors.

---

### Post by uRock on 2010-03-09
> **Die in Sente said:**
> iScream

Must be a hardware incompatibility. Don't get offended when others doubt the compatibility of programs like Nero. Using their software made me about 100 coasters in a 1 week period.

---

### Post by Die in Sente on 2010-03-09
> **John Z said:**
> AMD Athlon 64 Processor 3500+
1.0GB Ram
NVIDIA GeForce 8800 GT
Widows XP Professional SP3

Anything else?

John,

Can you post some information about your motherboard and chipsets?
Also, is the CD/DVD drive you're trying to boot from IDE or SATA?
It would be a very suspicious coincidence if we were having the same identical problems on similar motherboards.

I'm probably grasping at straws here, but I'm suspecting something related to the IDE interface in the SB 600 chip.

---

### Post by Die in Sente on 2010-03-09
> **iRock said:**
> Must be a hardware incompatibility. Don't get offended ....

No offense taken.  Just frustrated.

I've downloaded and burned the 9.04 image ( ubuntu-9.04-desktop-amd64.iso) and it seems to not have the same hardware incompatibility.   At least when I boot the 9.04 disk in the same system, the integrity check runs just fine.

---

### Post by uRock on 2010-03-09
It has something to do with Karmic's compatibility with your hardware. I loved Jaunty when I had it. Hopefully the issue both of you are having will be cleared up in Lucid.

---

### Post by gmjs on 2010-03-09
> **Kaligo said:**
> You could also try the alternate installer.

After burning a second CD and finding it still doesn't work, using the 'alternate' installation CD is definitely the next thing to try.

Due to the nature of the error, I'm pretty confident you'll have success that way (personally I tend to go straight for the alternate installation CD).

Grab a copy of *ubuntu-9.10-alternate-amd64.iso* from your favourite mirror!

**[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")**

Hope that helps.

---

### Post by Die in Sente on 2010-03-09
Just to put a nail in the coffin...

After installing 9.04, I re-inserted the 9.10 disk, ran "[COLOR=Blue]md5sum /dev/cdrom[/COLOR]" and got the correct checksum (DC51C1D7...etc).

---

### Post by uRock on 2010-03-09
> **Die in Sente said:**
> Just to put a nail in the coffin...

After installing 9.04, I re-inserted the 9.10 disk, ran "[COLOR=Blue]md5sum /dev/cdrom[/COLOR]" and got the correct checksum (DC51C1D7...etc).

Still not shopping for Nero....;)

---

### Post by Tzipi on 2010-04-07
1) So I've tried Ubuntu 9.10 Desktop i386 by burning the image on 2 cd's to make sure it wasan't IMGBurn fault or a cd bad.

Error : System cannot find a medium containing a live ....

2) I've tried Ubuntu 10.04 Beta 1, same error.

3) I've tried Ubuntu 9.10 Alternate i386 and after I chose keyboard layout it gives me somthing like " Cd-rom drive not found" .


IS THERE A CHANCE THAT I CAN INSTALL UBUNTU ON MY COMPUTER?


OH and btw all of these metods were tried using Verbatim Cd's .

---

