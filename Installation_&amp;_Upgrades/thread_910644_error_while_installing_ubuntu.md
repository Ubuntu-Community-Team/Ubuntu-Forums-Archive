---
title: "error while installing ubuntu"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by hannah beatdown on 2008-09-04
I messed up my computer pretty bad somehow. I used to have XP, and somehow now I have Windows 98. Well I've decided to give linux ubuntu a try, and i downloaded the ISO, and burned the image to a CD, when I ran the CD, and clicked on Install the disk this message came up on a black, coding screen:

"BusyBox v1.1.3 (Debian 1:1.1.3-5 Ubunutu12) Built in shell (ash) enter help for a list of built in commands"

when i entered Help, I got a list of maybe 20 commands. I tried typing of some of the commands and this message came up:

"(223.666128)atac:SRST failed (ermo=-16) (initramfs)"

i don't understand why i came to this screen, or what it wants me to do, and what failed.:confused:

can someone please help me?:

---

### Post by Pumalite on 2008-09-04
Post your specs.

---

### Post by hannah beatdown on 2008-09-04
Sorry, I'm not that smart with codes and stuff, what are specs? :/

---

### Post by Pumalite on 2008-09-04
Memory, Graphics? PCU?
If you can boot a Live CD; post:
lshw

---

### Post by hannah beatdown on 2008-09-04
ohh ok.

Well, um. 64MB SDRAM memory
the brand of the computer is HP Pavillion Genuinel Intel Pentium III processer 40.0 GB Ultra DMA hard drive

---

### Post by hannah beatdown on 2008-09-04
i can boot a live CD, that's how I downloaded the ISO image on a CD?

---

### Post by BlueTesla on 2008-09-04
When you get to the menu where you can select "Run From CD", "Install", etc, press F6 and type the following:

all_generic_ide floppy=off irqpoll

I had a similar error and this is what did it for me.

---

### Post by Rodr!go on 2008-09-04
Might sound stupid, but what worked for me is just to type "exit". After that, the installer just worked fine!

Im not that savvy, so just try it...Im also having issues with the install myself: [http://ubuntuforums.org/showthread.php?t=910724](http://ubuntuforums.org/showthread.php?t=910724)

Good Luck!!

---

### Post by Gavagai80 on 2008-09-05
> **hannah beatdown said:**
> 64MB SDRAM memory

64 MB isn't enough to run a general purpose modern OS like Ubuntu 8.04 (Ubuntu requires 256 MB RAM), so you'll need to get a distribution that's designed for old computers.

I hear [Puppy Linux](http://www.puppylinux.org/) has some [Windows '98 integration](http://www.freeveda.org/linux/puppy/PupWin98.htm) to make things easy.

---

### Post by Pumalite on 2008-09-05
Stick to a small distro: DSL or Puppy.

---

### Post by Crafty Kisses on 2008-09-05
I really like Slitaz Linux, really slick distro I think.

---

### Post by snowpine on 2008-09-05
Nothing in the Ubuntu family will work with 64mb of ram. Puppy, DSL, and SliTaz are probably your best options. Or a newer computer. :)

---

