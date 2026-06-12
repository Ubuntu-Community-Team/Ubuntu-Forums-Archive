---
title: "Installer sits at blinking cursor"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by Resolent on 2008-08-26
I have burned three copies of ubuntu version ubuntu-8.04.1-desktop-i386.iso.

I run windows xp on my system. I have checked the integrity of the iso from my desktop and everything seems to check out.

If more information is needed let me know.

Thank you

---

### Post by overdrank on 2008-08-26
> **Resolent said:**
> I have burned three copies of ubuntu version ubuntu-8.04.1-desktop-i386.iso.

I run windows xp on my system. I have checked the integrity of the iso from my desktop and everything seems to check out.

If more information is needed let me know.

Thank you

Hi and welcome, could you give us some system specs? At what speed did you burn the cd? Do you receive any graphics from the live cd? You may want to do a checksum on the iso
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by manishtech on 2008-08-26
> **Resolent said:**
> I have burned three copies of ubuntu version ubuntu-8.04.1-desktop-i386.iso.

I run windows xp on my system. I have checked the integrity of the iso from my desktop and everything seems to check out.

If more information is needed let me know.

Thank you
You say the CD's are desktop editions not Alternate. Can I know where does it sit at the blinking cursor, during LiveCD boot time? 

Additionally please furnish your system specs. if you can somehow get a snapshot, it would be of immense help.

---

### Post by Discoteka on 2008-08-26
I am having the same problem.

I received my installation CD via "Beginning Ubuntu Linux" for a class I'm taking.  I installed Ubuntu on one of my tester PC's before attempting on my main, and rather expensive PC.  My main PC is home built, MSI motherboard, AMD 64x2, 4 GB RAM, ATI HD graphics card.

I set my BIOS to boot from CD/DVD-ROM, and the first page came up fine.  When I select Install or Start Ubuntu, it installs the kernel, but then sits at a blank black page with a gray cursor blinking.

I have edited the boot and got rid of the "quiet splash --" line using the F6 option.  Doing this got me a little further, but after a list of codes scrolled down the screen, it was just a blinking cursor again.

It does the same on Safe Graphics Mode.  At the moment, I am running the MemTest86 v1.65.

I know it's not the CD/DVD because it installed fine on my tester PC.

Any advice would be great.

---

### Post by Resolent on 2008-08-26
[IMG]http://farm4.static.flickr.com/3281/2800951262_146e87a533.jpg?v=0[/IMG]

I actually have 4gigs of ram, but windows can't address that.

I'm also using an Nvidia GeForce 9600 GT.

I used a program called Burn4Free. I believe I burned at maximum speed. The hashes on my iso check out with the ones provided.

When I burned a dvd using InfraRecord it would not bring up the boot screen. I tried this twice on 1x speed. Both disks do not trigger the machine to boot from the dvd.

The disk that "works" will boot to the ubuntu menu. Ive tried installing normally and with safe graphics mode. Both load the kernel 100% then proceed to a black screen with the blinking cursor in the upper left hand corner. After the Kernel loads I do not see anymore Ubuntu graphics whatsoever.

EDIT: I might have fixed my own problem. I'll update after I check it out.

---

### Post by Discoteka on 2008-08-26
I seem to have fixed my own problem.  Googling around, I found that there can be problems if you have a USB storage device attached to your system.

I removed my mini flash USB reader, rebooted from CD, it went to the blank screen with the cursor for about 2 seconds, the continued to load.  No boot modifications necessary.

Right now it is loading, and I will be working on the install.  

Hope this helps everyone else having this problem.

---

### Post by Resolent on 2008-08-26
I managed to get Ubuntu installed. Now it's time to figure out how to get my wireless connection running.

I'm using AR5007EG Wireless network adapter by AzureWave

---

### Post by manishtech on 2008-08-27
> **Resolent said:**
> I managed to get Ubuntu installed. Now it's time to figure out how to get my wireless connection running.

I'm using AR5007EG Wireless network adapter by AzureWave

Did you also remove the USB drives before continuing?

---

