---
title: "Ubuntu 8.04 Installation Problem"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by jedimasterk on 2008-04-24
When I go to boot with the 8.04 cd and I click either Try Ubuntu without Changes or Install Ubuntu. I will get a (initramfs)_ prompt. This never happened with any version of Ubuntu I had in the past. Whay's wrong. Tried burning CD from 2 different mirrors.

---

### Post by Pumalite on 2008-04-24
Did you do md5sum?. Did you burn at 4x or less?

---

### Post by jedimasterk on 2008-04-24
> **Pumalite said:**
> Did you do md5sum?. Did you burn at 4x or less?

I used Brasero and let it burn an iso with default settings. Max Speed. Never had problems with Brasero and burning iso's in past. I am doing a dualboot with XP Pro. And 7.10 installed no problem. I have a single SATA 500GB drive split two ways. XP and Ubuntu.

---

### Post by Pumalite on 2008-04-24
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Doing mde5sum is essential and a must first step to obtain a good disk. The speed is very impostant also.

---

### Post by bluecandylover on 2008-04-24
I have same errors.

Image here [http://img518.imageshack.us/img518/7830/dsc00297yu3.jpg](http://img518.imageshack.us/img518/7830/dsc00297yu3.jpg)

VMware = Failed
VirtualBox = Installed
Actual PC = Failed

I downloaded the file twice - burnted it TWICE (second time half the speed of first time).

Both same error and even tried that Wubi (3 times) (Second/Third time using the .ISO and a virtual CD, first time using Virtual CD had the Windows "This program encounted and error and needed to close")

Previous Versions worked 100% everytime installed.

---

### Post by jedimasterk on 2008-04-24
> **Pumalite said:**
> Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Doing mde5sum is essential and a must first step to obtain a good disk. The speed is very impostant also.

How is this giving me the (initramfs) error.

---

### Post by jedimasterk on 2008-04-24
> **Pumalite said:**
> Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Doing mde5sum is essential and a must first step to obtain a good disk. The speed is very impostant also.

And the md5 hash sums for 8.04 are not even posted yet.

---

### Post by jedimasterk on 2008-04-24
Could this be a bad iso circulating. Just made 2 cd coasters!. Never had this issue in the past releases. And as I said before Ubuntu 7.10 installed fine with my new SATA drive. This one gives me (initramfs)_ prompt error.

---

### Post by Pumalite on 2008-04-24
Let's hope is not a bad iso from the Servers.
7d0ac92c56361949d099dd9337c975e7 *ubuntu-8.04-alternate-amd64.iso
166991d61e7c79a452b604f0d25d07f9 *ubuntu-8.04-alternate-i386.iso
fc43f665ba51c4be0d95c011aefef45d *ubuntu-8.04-desktop-amd64.iso
8895167a794c5d8dedcc312fc62f1f1f *ubuntu-8.04-desktop-i386.iso
8a73cf85b04f37d5d91fb436525ea395 *ubuntu-8.04-server-amd64.iso
c3162b21757746c64a0a22cdd060b164 *ubuntu-8.04-server-i386.iso
cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe

---

### Post by jedimasterk on 2008-04-24
> **Pumalite said:**
> Let's hope is not a bad iso from the Servers.
7d0ac92c56361949d099dd9337c975e7 *ubuntu-8.04-alternate-amd64.iso
166991d61e7c79a452b604f0d25d07f9 *ubuntu-8.04-alternate-i386.iso
fc43f665ba51c4be0d95c011aefef45d *ubuntu-8.04-desktop-amd64.iso
8895167a794c5d8dedcc312fc62f1f1f *ubuntu-8.04-desktop-i386.iso
8a73cf85b04f37d5d91fb436525ea395 *ubuntu-8.04-server-amd64.iso
c3162b21757746c64a0a22cdd060b164 *ubuntu-8.04-server-i386.iso
cdd32124f23b455b0aa22cc3ff35ff35 *wubi.exe

Now how can I check this after burning the iso to a disk and deleting the iso.

---

### Post by ssam on 2008-04-24
> **jedimasterk said:**
> Now how can I check this after burning the iso to a disk and deleting the iso.

md5sum /dev/scd0

you might need to replace scd0 with hdc, cdrom, dvd or something else depending on your hardware

---

### Post by jedimasterk on 2008-04-24
Ok thanks for the tip. I got 8895167a794c5d8dedcc312fc62f1f1f which is the same one the previous poster gave me. But the probem still exists. Why am I getting a (initramfs)_ prompt and not a normal bootup like previous versions.

---

### Post by bluecandylover on 2008-04-24
> **jedimasterk said:**
> Ok thanks for the tip. I got 8895167a794c5d8dedcc312fc62f1f1f which is the same one the previous poster gave me. But the probem still exists. Why am I getting a (initramfs)_ prompt and not a normal bootup like previous versions.

It's annoying me as well - I keep downloading and burning with no vail! Also now the download servers are slowlu maxing giving me a slow slow download speed :(

---

### Post by bluecandylover on 2008-04-24
> 
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Ender 'help' for a list of built-in commands.

(initramfs) ~[   67.265133] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 actio
n 0x2 frozen
[    67.265198]  ata3.00: cmd a0/01:00:00:06:00/00:00:00:00:00/a0 tag 0 dma 96 in
[    67.265257]  ata3.00: status: { DRDY }
[    83.610055]  ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[    83.61115] ata3.00: cmd a0/01:00:00:06:00/00:00:00:00:00/a0 tag 0 dma 96 in
[    83.610174] ata3.00: status  { DRDY  }




My that took alot of typing .

---

### Post by jedimasterk on 2008-04-24
> **bluecandylover said:**
> My that took alot of typing .

I just get

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Ender 'help' for a list of built-in commands.

(initramfs)_

---

### Post by Lateralis on 2008-04-24
I've got the same issue and it is pissing me off no end.  I've had no issues installing 7.10 on other computers, although I did have a slight hardware issue (that no one was able to solve) surrounding the DVD/CD drive on this machine after I rebuilt it with the following specifications:

Intel E8400 processor
Inno3D Nvidia 8800GT graphics card
Asus P5KC motherboard (has a JMicron chip...) 
SATA 160gig Maxtor hard drive partitioned into two parts - one for Win XP Professional and one ready and waiting for Ubuntu
SATA 250gig hard drive for storage
IDA hard drive for work related bits and other junk (but is largely redundant)
IDE Samsung DVD/CD burner

I've tried using the 32 and 64-bit discs.  Tried safe graphics mode for both.  Tried changing the JMicron mode from IDE to ACHI and then RAID - no cigar in any setup with either disc in either graphics mode.  In all cases I get taken to the initramfs terminal and can go no further.  I'm loathed to use the alternate CD as I shouldn't have to.  Another thread on here ([http://ubuntuforums.org/showthread.php?t=763054](http://ubuntuforums.org/showthread.php?t=763054)) has suggested a few things, but it is getting a little late where I am and I've got work in the morning, so will have to try some of the suggestions tomorrow evening.  In the meantime, if anyone has any other ideas, I'd greatly appreciate them.

---

### Post by jedimasterk on 2008-04-24
This seems like a pretty big bug that wasn't fixed before the final release. Seeing how the past distro 7.10  and 7.04 installed fine. Guess I'll be skipping this release, can't afford to be wasting blank cd's.


BusyBox v1.1.3 

(Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Ender 'help' for a list of built-in commands.

(initramfs)_ ("blinking cursor")

---

### Post by jedimasterk on 2008-04-24
I wonder if upgrading with the Alternate CD would be a better option, since the Live CD is a no go for me?.

---

### Post by konstrictor on 2008-04-24
Same problem.  Downloaded the 8.04 Live CD today.  Interestingly, I have a release candidate .iso from about a month ago that works just fine.

In addition to my sig. I have a 120gb Seagate IDE drive and a Sony dvd burner, also IDE.

BTW, I'm a total Linux noob.  My main install is XP Pro, which i'm fairly fluent with.  I'm always messing around with it and crash it occasionally.  It's really nice to have a Live CD in my back pocket  to help me get running again.  My old distro (7.04) stopped working when I got my 8800GS.  I hope they get this bug worked out soon.

---

### Post by Pumalite on 2008-04-24
Both of you can upgrade with the Alternate CD:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
Or do a clean install with it.

---

### Post by cafe con leche on 2008-04-24
I had the exact same problem as you guys last night, here's what i did:

BTW: your ISO's are fine!

1. Use alternate CD 
2. at the installation menu hit f6 and add "pci=nomsi" (without the quotes) to the end of the sentence that shows up at the bottom of the screen when install ubuntu is highlighted. then hit enter and enjoy.

i assume most of you guys are using sata hardware, and i think there is an issue with hardy. 

have fun with ubuntu tonight!


if you guys need some more detailed help or are confused by what i just said you can AIM me at SN: h4q

---

### Post by jedimasterk on 2008-04-24
> **cafe con leche said:**
> I had the exact same problem as you guys last night, here's what i did:

BTW: your ISO's are fine!

1. Use alternate CD 
2. at the installation menu hit f6 and add "pci=nomsi" (without the quotes) to the end of the sentence that shows up at the bottom of the screen when install ubuntu is highlighted. then hit enter and enjoy.

i assume most of you guys are using sata hardware, and i think there is an issue with hardy. 

have fun with ubuntu tonight!


if you guys need some more detailed help or are confused by what i just said you can AIM me at SN: h4q

Will just doing an upgrade work

---

### Post by HDave on 2008-04-25
I have done an upgrade from Gutsy and get the same error.  The pci=nomsi workaround doesn't work for me or dozens of other folks I have found in other threads.  

[http://ubuntuforums.org/showthread.php?p=4793473#post4793473]("http://ubuntuforums.org/showthread.php?p=4793473#post4793473")

Any ideas?

---

### Post by HDave on 2008-04-25
FIXED!

The hard drive UUID in my GRUB menu.lst was wrong.  I had swapped out my hard drive when my machine was running Gutsy.  I had fixed the UUID in /etc/fstab (you have to or you can login).  However I never changed the UUID in /boot/grub/menu.lst and when I upgraded to Hardy I used the new "merge" capability to get my new menu.lst file.

Apparently Gutsy didn't care the UUID was wrong, but Hardy does.  I booted into windows, copied the UUID from fstab and pasted it into menu.lst I now I am swimming in 8.04 goodness.

---

### Post by sabbathpriest on 2008-04-25
Same problem, and changing the SATA controller to RAID or doing the pci=nomsi option does not change anything on my system.... what troubles me the most is all the hoopla about Hardy on the press... how many people will have THIS mess of an installer as a first Linux experience? 
My system:
Asus  A8V-XE Mobo
AMD 64 Athlon 3800 Processor
2 SATA + 1 PATA drives

---

### Post by brett11808 on 2008-04-25
Same problem here nothing has worked. I've been using the beta and upgrading along the way on my laptop and all is well but i cant get past this (intramfs) on my desktop! I'm want to set up a dual boot with XP but i guess I'll just have to wait till this bug is ironed out.

---

### Post by maturin on 2008-04-25
My brother's had the same problem with this initramfs.  He's tried numerous downloads & attempts, but hasn't gotten anywhere.  I was going to update to 8.04, but with his experience and numerous posts describing similar experiences, perhaps I'll wait.

Ubuntu's been (and is!) great, but it's not a good sign if a brand new release needs various workarounds for installation...

---

### Post by sabbathpriest on 2008-04-27
Just an update, in case someone can make sense of what's happening:
I Installed 7.10 (amd64) on a separate partition on my hda (hda1) in order to do a "Version Upgrade". On first reboot grub shows me two kernel versions of Ubuntu 8.04: 2.6.24-16 and 2.6.22-14. If I try to boot into the first kernel on the list (2.6.24-16) I still get to the BusyBox / initramfs prompt, but if I choose the second kernel (2.6.22-14) I can boot into 8.04 normally.

---

### Post by dfdumaresq on 2008-04-27
Not sure if this is the best place to post this, but I was also getting the  (initramfs) failure after upgrading from 7.10 to 8.04

Solved it by changing my BIOS setting for ATA/IDE Configuration from Enhanced to Compatible.

Some random details:
Motherboard: ASUS P5KPL-VM

Startup messages:
Loading, please wait
ata3:00 revalidation failed

...
ALERT! /dev/disk/by-uuid/.... does not exist

(initramfs)



Hope this helps!
-Dave

---

### Post by HDave on 2008-04-27
Folks -- can you verify that the UUID in the grub menu matches your fstab and is actually the right value for your hard drive?

---

### Post by Lateralis on 2008-04-28
Just to update people with my problems... 

They're all fixed.  I've now got Ubuntu 8.04 dual-booting with Windows XP.  For me, there were two main problems.  One I suspect is a hardware issue with the motherboard, the other is a result of my own laziness and incompetence. 

My motherboard is an Asus P5KC.  It uses a JMicron controller for the IDE port.  On the IDE I have my optical CD/DVD writer drive and a spare hard drive.  In a previous Gutsy (7.10) installation, the hard drive was recognised (and had Ubuntu installed on it) but the disk drive wasn't.  To install Ubuntu then, I used an external (USB) CD drive that I had floating around.  For this current installation, I experienced similar problems, in that the BIOS would load up the CD to begin with, but upon selecting option 1, I'd get the Ubuntu splash screen for about 20 seconds and then it would take me to the Busy Box command line screen.  Using the external CD drive, I could make it into Ubuntu.  The funny thing though was that the CD drive was actually being detected and I could use it to play CDs.  Kookie.  

As for my own incompetance, I had a few problems with boot loaders.  Picture it:

SATA1 - 250 GB drive for media and important document storage
SATA2 - 160 GB drive partition up for Windows XP and Ubuntu

GRUB automatically installs itself on the first hard disk - SATA1 - irrespective of which physical hard disk it is being installed on, but the boot order in my bios was SATA2, then SATA1.  The BIOS was checking my second disk for a boot loader, found the Windows XP boot loader and was loading straight into Windows XP.  (At the time of the XP installation, Windows had no knowledge of Ubuntu.)  Changing the boot order to SATA1 then SATA2 now gives me the GRUB screen and everything works exactly as it should.  


As I've never before had this kind of trouble installing any Linux operating system on any other computer, I'm inclined to believe that the JMicron controller is pure evil.

---

### Post by B3n3v3nt3 on 2008-04-28
> **HDave said:**
> Folks -- can you verify that the UUID in the grub menu matches your fstab and is actually the right value for your hard drive?

How do I do that? I have the same problem here but I'm kinda new into this.

---

### Post by Rocky37 on 2008-04-28
Yep,  My too.

Loaded Hardy on my laptop last Friday with no problem.  Cleaned up my desktop today - stuck my CD in the drive and bam - black screen with a blinking curser.

I did get a fast flash of the menu screen which was then covered by the language selection screen -- hitting enter the disk spins for about 5 seconds and goes to the blank screen.

I tried the loading in windows which worked to the restart which also went to the blank screen.  Tried all 4 of the different modes.  the verbose mode hung at
[101.742822] early unpacking initramfs...

Burned a new disk p-------------- same results.

I do love 8.04 though -- out with the damn windows xp!!

---

### Post by Stray_Wulfe on 2008-05-06
I'm having the same problem i think, except when My Busybox  appears it has no error messages or anything, Also i ordered my Cd i have two hard drives but their not partitioned. one is completely full so it doesn't matter.

---

### Post by Francewhoa on 2010-03-11
Same here. **The following worked for me** [http://ubuntuforums.org/showthread.php?p=8952609#post8952609](http://ubuntuforums.org/showthread.php?p=8952609#post8952609)

---

