---
title: "How to weak up my Ubuntu?"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by superthin on 2008-09-19
Hello everybody,

I am a Ubuntu newbie. I am also a basic Windows XP user.

A few days ago, I installed SUN VirtualBOX into my Windows XP SP2. I created a virtual PC with 1 IDE HDD (virtual too). In the virtual PC, I setup Ubuntu with LiveCD Ubuntu 8.04 LTS (setup default, Ubuntu manage disk / partition automatically itself) and Ubuntu worked. In virtual PC, Ubuntu run slowly. So, I want to "convert virtual PC to real PC" (do not touch Windows) for better performance.

Because I don't want to begin to install Ubuntu again into the real PC, I used Norton Ghost to have 2 images file (*.ghost) - 1 was Ubuntu Root, 1 was Swap partition).

[IMG]http://img522.imageshack.us/img522/9831/myubuntuyx3.gif[/IMG]

I "ghost" 2 images successfully into **19.53 GB** (all files Ubuntu), **2.01 GB** (Ubuntu Swap from virtual PC).

I could use Windows XP normally.

How to tell Windows XP (boot.ini and NTLDR) to know that "having a new member named Ubuntu, and permit "him" to join list boot"?

I don't want LILO / GRUB / any boot loader override current MBR / fist sector.

My friend told me "*You should have virtual PC with Ubuntu turning on. Make an file which contains all boot information (with modify for matching with structure HDD on real PC). Save that file to Floppy Disk. Then, save the file into an partition which Windows XP could access to. Use a small utility to **make boot.ini and NTLDR in partition G:** to know and can pass boot process to Ubuntu*". I think that's a good idea, but I cannot do it myself. I need your help.

My real PC has an floppy device.

Thank you very much.

Best regards,
SuperThin.

---

### Post by Sef on 2008-09-19
Read [How to Multi-Boot Operating Systems]("http://www.vsubhash.com/writeups/multiboot_os.asp").

---

