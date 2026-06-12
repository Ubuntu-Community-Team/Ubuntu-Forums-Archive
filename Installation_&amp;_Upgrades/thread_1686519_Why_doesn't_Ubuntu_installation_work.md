---
title: "Why doesn't Ubuntu installation work?"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by Mertsi1340 on 2011-02-12
Today I tried to install Ubuntu 10.10 on my XP machine.

I am able to go to the installation menu after choosing the language but after that if I choose one of the installation options the PC tilts. By tilting I mean a blinking cursor on the top left hand corner over a black screen and one of the hard disks makes a noise which is like a rotating disk hitting another metal on each rotation (about once a second). I tried Ubuntu 10.04 LTS version but the same result.

The only item that works on the installation menu is the "test memory" option.

I wanted to try the dual boot option.

Maybe some background information makes helping me a bit easier:

Long time ago, I had a 6 GB hard disk and after buying a 80GB disk I tried to install XP again but this time on the 80GB disk. After installing XP and some other programmes I noticed that the disk where XP was reinstalled was assigned the letter F and my 6GB drive was assigned the letter C. Since every thing seemed to work I did not correct this problem. Today I did a little test and noticed that my windows wont start if I remove drive C (6GB drive). 

Today in relation with Ubuntu installation I added another 80GB disk to my machine, this time by removing one of the two DVD-ram drives and replacing it with the 80GB disk. This is on the secondary IDE cable and my hard disk is set as SLAVE and the DVD-ram as MASTER. I was planning on installing Ubuntu on this new 80GB disk.

I managed to format this new disk in XP and it has the drive letter E assigned to it.

My operating system is XP (SP3).
AMD Athlon 2100+, 1.7 GHz
1 GB of RAM

I hope these information was enough to find a solution for this problem.

Cheers

---

### Post by oldfred on 2011-02-13
Welcome to the forums.

Is this computer new enough to let you choose boot device in BIOS or can you only boot thru primary master on the IDE chain?

If it is real old you may have to have boot partition at beginning of drive, but since you have separate drive just install Ubuntu's root partition in the beginning of the drive 10 or 15GB and then make the rest /home.

You may also have video problem or other parameters to get it to work.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by Mertsi1340 on 2011-02-13
Thanks for welcoming me and the response to my post.

Yes it is new enough to let me choose boot device in the BIOS and in fact I changed the boot sequence so that the first device is the DVD-drive and then Drive E.

My problem is that I can't get the installation process started. If I remove Drives C and F and install Ubuntu while only the new 80GB disk (drive E) and the DVD are connected to the secondary IDE cable, how can I get the dual boot to work? Or would that creates conflicts with XP?

Any advice is more than welcome.

Cheers!

---

### Post by Hedgehog1 on 2011-02-13
> **Mertsi1340 said:**
> ...By tilting I mean a blinking cursor on the top left hand corner over a black screen and one of the hard disks makes a noise which is like a rotating disk hitting another metal on each rotation (about once a second). I tried Ubuntu 10.04 LTS version but the same result.
...
Long time ago, I had a 6 GB hard disk and after buying a 80GB disk I tried to install XP again but this time on the 80GB disk. After installing XP and some other programmes I noticed that the disk where XP was reinstalled was assigned the letter F and my 6GB drive was assigned the letter C. Since every thing seemed to work I did not correct this problem. Today I did a little test and noticed that my windows wont start if I remove drive C (6GB drive)...


Mertsi1340,

I am of the belief that until your resolve the Non-Ubuntu issue of having the MBR (Master Boot Record) on you old 6gb 'C:' drive, and your 2nd XP Install on your second 'F:' drive, you will be unable to dual boot any operating system in a reasonable way.

Ubuntu not getting any further than it did in the installation is a hint of what is going on.

Ideally, you should:

(1) Remove all but the NEW 80 gig IDE hard drives from you PC

(2) Put the 'NEW' 80 gig IDE as the master on the first controller (not the one it is on now with the DVD drive).

(3) Install XP on the new IDE 80 gig drive.  It will become your new 'C' drive.

(4) Once XP install installed on the 'NEW' 80 gig drive, put your old 80 gig drive in the 'slave' position on the main controller (where I think it is right now).

(5) Copy your **data** (not windows, just the data) from 'OLD' the 'F:' drive to the new 'C:' drive.

(6) **Do not** reinstall the 6 gig drive.  You need that same power from your power supply to drive the 'new' 80 gig drive.

Now you will be ready to do a dual boot with Ubuntu

Install Ubuntu as you see fit; either by having it take over the old 'F:' drive, or making a partition on the 'new' 'C:' drive and using the old 'F:' drive as a shared storage area for both XP and Ubuntu.

:popcorn:

---

### Post by oldfred on 2011-02-13
A good reference on installing to a 'second' drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by Hedgehog1 on 2011-02-13
> **oldfred said:**
> A good reference on installing to a 'second' drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Excellent link oldfred!  Thanks  - good reading, that.

:KS

---

### Post by Mertsi1340 on 2011-02-14
Thanks.

I was trying to avoid installing XP again (too many programmes to install all over again).

But I suppose if I want Ubuntu badly then there are apparently no other alternatives. 

Cheers

---

### Post by oldfred on 2011-02-14
One more reason to like Ubuntu. I now do clean installs of each new version and may do a clean install of beta, RC & final. With each I just run a list and it reinstalls all my programs.

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

The only issue is I have installed so many that it takes 20 to 30 minutes to install all of them. And usually not one reboot. XP takes 5 minutes to reboot and each app requires at least one reboot.

---

