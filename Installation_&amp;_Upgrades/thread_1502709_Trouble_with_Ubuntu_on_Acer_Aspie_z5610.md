---
title: "Trouble with Ubuntu on Acer Aspie z5610"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by ClayJ on 2010-06-05
Hello,
 
I am having trouble installing any version of ubuntu on my acer aspire z5610. Is it possible or is there a fundamental flaw/unsupported component of my system that makes it impossible for ubuntu to be installed? The furthest I have got is with Ubuntu Mint 8 32 bit Universal Edition. It loads up the LM logo, but no further. All other distros seem to hang after selecting Live CD boot of the boot screen. 
 
My computer is currently running Windows 7, Core 2 Duo E7500 with ATI Radeon Mobility HD4670. BIOS version (off the box) is P01-B0.
 
Has anyone had problems with this computer or know what the problem is?
 
Thanks

---

### Post by madverb on 2010-06-05
It might not hurt to test your RAM.
Run Memtest86+ from one of the live CDs.

---

### Post by ClayJ on 2010-06-20
Downloaded latest Ubuntu 10.04 LTS and it loaded/installed with no problems. Not sure why I was getting so many problems with the earlier versions/distros.

EDIT: Spoke too soon. Ubuntu Live CD boots up and works well, but when installed it has a kernel panic like this:
Kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

---

### Post by ClayJ on 2010-06-21
Got ubuntu loading by changing a BIOS setting - I changed AHCI to IDE, and in GRUB changed the UUID reference to a /dev/sda*. The only problem is that Windows & needs AHCI enabled to boot. Is there any way to get ubuntu to load with the AHCI setting? It is getting so annoying having to manually switch between AHCI and IDE in BIOS.

---

### Post by Mucku_Mucku on 2010-07-11
Hello,

I had to change the value of "memory hole mapping" in the BIOS. After that it was working for me.

---

### Post by franklos on 2010-10-05
so what did you change in the memory hole?

---

### Post by Mucku_Mucku on 2010-10-14
You have to disable it. It is enabled by default in the BIOS.
Afterwards it worked normally.

---

### Post by BFG on 2011-05-07
> **Mucku_Mucku said:**
> Hello,

I had to change the value of "memory hole mapping" in the BIOS. After that it was working for me.

That was very useful for me - thanks.  Found this via google.

The next problem for me now is getting video to work on the Z5610

---

### Post by fballem on 2011-05-07
[http://ubuntuforums.org/showthread.php?t=1548313](http://ubuntuforums.org/showthread.php?t=1548313)

I ran into several problems with a z5600. There may be something in the above post that might prove helpful to you.

The Z5600 is working well (Ubuntu 10.10, 10.04 previously).

---

### Post by fballem on 2011-05-07
[http://ubuntuforums.org/showthread.php?t=1552281](http://ubuntuforums.org/showthread.php?t=1552281)

This might help with the Video.

---

