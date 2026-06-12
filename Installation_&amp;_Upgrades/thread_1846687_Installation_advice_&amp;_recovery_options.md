---
title: "Installation advice &amp; recovery options"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by hell_rider on 2011-09-19
Hello all,

Need some help with a new installation and accessing data on an old installation.


Query 1:
--------
I've got a new Thinkpad SL410. Intel Core2Duo T6670 CPU.  Intel 4 Series Express chipset GMA for display. Its got 4GB RAM and 320GB SATA HDD.  Like my earlier laptop, I need this to be a dual boot. 

I've already installed XP Pro SP3 on the main partition. I wanted to install Ubuntu 10.04 LTS 64-bit on the other 40 GB partition.

Any known issues of running 64-bit 10.04 LTS on a laptop ?? I really want to experience 64-bit with 4 GB of RAM.

For XP to install and run, SATA has been set to "Compatbility Mode" in BIOS as XP does not work with AHCI mode.


Query 2:
--------
My older laptop crashed with a MoBo failure.  The HDD itself however is OK.  I removed it, put it into a USB casing and attached it to another Windows machine.  I am able to access all my Windows partitions on the old hard disk.

Is the same thing possible with the Ubuntu partition as well ? If I make my new installation 64-bit (the 8.04 installation was 32-bit), can I access the data on my Ubuntu partition on the old HDD ?  There are some files on the Desktop and my personal folders that I need to access and copy over to my new installation.

I (unfortunately) did not make a separate /home partition on the old installation.
The filesystem was ext3.

So the main query is if I can access the data on my old 32-bit 8.04 Ubuntu partition and whether its possible to do so from a new 64-bit Ubuntu 10.04 LTS installation.

I only have a LiveCD of 7.04 Fiesty Fawn.  This was the initial installation which I later upgraded to 8.04.

Looking forward to your assistance in my queries. 

Thanks in advance.

---

### Post by Hakunka-Matata on 2011-09-19
> **hell_rider said:**
> Hello all,

Need some help with a new installation and accessing data on an old installation.


Query 1:
--------
I've got a new Thinkpad SL410. Intel Core2Duo T6670 CPU.  Intel 4 Series Express chipset GMA for display. Its got 4GB RAM and 320GB SATA HDD.  Like my earlier laptop, I need this to be a dual boot. 

I've already installed XP Pro SP3 on the main partition. I wanted to install Ubuntu 10.04 LTS 64-bit on the other 40 GB partition.

[COLOR=Red]Any known issues of running 64-bit 10.04 LTS on a laptop ??[/COLOR] I really want to experience 64-bit with 4 GB of RAM.

For XP to install and run, SATA has been set to "Compatbility Mode" in BIOS as XP does not work with AHCI mode.


Query 2:
--------
My older laptop crashed with a MoBo failure.  The HDD itself however is OK.  I removed it, put it into a USB casing and attached it to another Windows machine.  I am able to access all my Windows partitions on the old hard disk.

Is the same thing possible with the Ubuntu partition as well ? If I make my new installation 64-bit (the 8.04 installation was 32-bit), can I access the data on my Ubuntu partition on the old HDD ?  There are some files on the Desktop and my personal folders that I need to access and copy over to my new installation.

I (unfortunately) did not make a separate /home partition on the old installation.
The filesystem was ext3.

[COLOR=Red]So the main query is if I can access the data on my old 32-bit 8.04 Ubuntu partition and whether its possible to do so from a new 64-bit Ubuntu 10.04 LTS installation.[/COLOR]

I only have a LiveCD of 7.04 Fiesty Fawn.  This was the initial installation which I later upgraded to 8.04.

Looking forward to your assistance in my queries. 

Thanks in advance.
Hi, Welcome:

1. no
2. yes

---

### Post by hell_rider on 2011-09-19
Hakuna Matata,

Many Thanks for your clear and concise replies.  Based on your response I understand :

1. I can install 10.04 LTS 64-bit happily on my laptop.  It will not give any issues with SATA set to "Compatability mode" in BIOS.

2. I can access my Ubuntu 32-bit 8.04 data on my old laptop hard disk (by putting it into a USB casing) from the new Ubuntu 64-bit installation.


I have further doubts on Point 2.
=================================
1. Will this be as simple as just plugging in and accessing a removable drive ? Or are there certain additional steps I need to perform ?

2. Would there be security / ownership issues as I had not created a /Home partition in my old 8.04 installation.  I was under the assumption that you could not access the /root partition of a Linux installation that easily.  Was my assumption wrong ?

Thanks once again.  Your help is much appreciated.

---

### Post by Hakunka-Matata on 2011-09-19
> **hell_rider said:**
> Hakuna Matata,

1. I can install 10.04 LTS 64-bit happily on my laptop.  It will not give any issues with SATA set to "Compatability mode" in BIOS.

I can't take ownership of the BIOS settings and SSD drive issue.  i.e. I don't know.

as far as accessing a portable USB drive, it should be no problem at all, it should mount when you plug it in, and you should be able to access your data.  Is it encrypted?

---

### Post by hell_rider on 2011-09-19
Hakuna-Matata

Its not encrypted.  I certainly did not choose any encryption options during the last install.  I went with the standard ext3.

Okay.  So it looks like I just need to go ahead with the new installation of 10.04 LTS and attach the old hard disk (USB) to get at the data.

One final question, though I am not sure if its appropriate here.  This is more for my knowledge.  Will this also work if I choose to go ahead with a new installation of Linux Mint instead of Ubuntu 10.04?  What I mean to ask is, whether this access of an older Ubuntu installation on a USB HDD works because it is being accessed from another new Ubuntu installation (10.04 LTS) or is it just as easy no matter which Linux distro I am using to access the old Ubuntu installation ?

Thanks once again for your quick responses.

---

### Post by Hakunka-Matata on 2011-09-19
AFAIK, linux is the keyword, I think it's so neat that one can look at anything at all on a windows hard-drive.  If the larger windows community knew that, I wonder?

---

### Post by hell_rider on 2011-09-21
Hakuna-matata,

All done.  I attached the old HDD to a a USB casing as mentioned.  It worked just fine.  I could access all my files and copy them into my new system.

Many thanks for your responses and help.

---

