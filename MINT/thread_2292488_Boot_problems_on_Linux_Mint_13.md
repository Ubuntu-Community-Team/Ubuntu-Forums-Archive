---
title: "Boot problems on Linux Mint 13"
date: 2015-08-28
forum: MINT
---

### Post by md11cf on 2015-08-28
I've been running a dual-boot system with Linux Mint 13 alongside Windows 7 for the last three years, and it all ran smoothly until around two weeks ago when I started experiencing a few problems when booting up. My computer is an aging Sony Vaio VGN-NW15G that I've been using since 2009; it shipped with Vista, though I upgraded to 7 shortly afterwards and then installed the Linux Mint dual-boot in 2012.

The problem I've been having manifests itself in any of the following ways:


[LIST=1]
[*]The computer loads the Vaio splash screen, then the GRUB 1.99 boot loader. I select Linux Mint 13 (the OS I normally use). The computer screen goes black, as it normally does while Mint is loading, but it doesn't load anything. 
[*]The Vaio splash screen and then GRUB both load, but as soon as I press either the "enter" key or the arrow keys, GRUB freezes. 
[*]The Vaio splash screen loads, but then I get a black screen with no error message, and GRUB doesn't load. 
[*]The Vaio splash screen doesn't even load, and instead all I get is a pale blue screen with no error message as soon as I hit the power button. 
[/LIST]

For about two weeks, I ignored the issue as I was only encountering problem 1, and it would resolve myself once I performed a force shutdown and booted up on a second attempt. However, yesterday it took me about 11 attempts before I was able to boot up after a combination of all four problems mentioned above.

Eventually I discovered [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") and ran the utility so that it would reinstall GRUB. I tested it by restarting twice, and both times the computer booted without any issues. On the third attempt, however, I once again encountered problem 1 and could only boot the machine at the second attempt. The report from boot-repair is available at: [http://paste2.org/JOcvPI0e](http://paste2.org/JOcvPI0e)

Has anyone got any insight? Any help would be appreciated. Thanks.

---

### Post by PaulW2U on 2015-08-28
*Thread moved to **MINT**.*

---

### Post by yancek on 2015-08-28
Looking at the boot repair output, I don't see any problems.  You have Grub code in the master boot record with the core.img file where it should be.  The grub.cfg (boot menu) is correct pointing to the correct drives for both Mint and windows with correct UUIDs.  Might be hardware but I don't see any problems with Grub.

---

### Post by md11cf on 2015-08-28
Thanks. I noticed this at the bottom, though:

> The boot files of [The OS now in use - Linux Mint 13 Maya] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))



Might this have anything to do with it, do you reckon?

---

### Post by yancek on 2015-08-28
If you have been using Mint from that same partition and haven't modified anything for three years I would not think that would be the problem.

---

