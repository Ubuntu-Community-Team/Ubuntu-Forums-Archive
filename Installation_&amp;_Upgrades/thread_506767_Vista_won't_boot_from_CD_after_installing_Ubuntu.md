---
title: "Vista won't boot from CD after installing Ubuntu"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by Tank8131 on 2007-07-22
I just recently uninstalled Vista and during this re-installation process received the blue screen.  So, I thought I'd give Ubuntu a try.  I'm sure Ubuntu works for some people and I'm sure they love it....it's just not for me.

My problem is that whenever I try to boot from my Vista CD it just continues to boot ubuntu.  I'm not sure if I need to install some sort of driver for this or software.  I'm just ready to go back to Vista especially after I paid for it.

Also, I might consider putting Ubuntu on a separate partition if I could just get it to do a higher resolution than 1024x764.

---

### Post by Pumalite on 2007-07-22
You can do both. First use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) Make 1 primary partition of your drive, formatted ntfs. Install Vista. Then partition with Vista's partitioner and make one primary or extended partition for Ubuntu. Install Ubuntu.

---

### Post by Old Pink on 2007-07-22
> **Vista won't boot from CD after installing Ubuntu**Result. ;)

Welcome to Ubuntu.

You could snap it to make sure?

---

### Post by louieb on 2007-07-22
> **Tank8131 said:**
> My problem is that whenever I try to boot from my Vista CD it just continues to boot ubuntu. 
The three common reasons this happens. 
[LIST]
[*]The CD drive itself has gone bad.
[*]The CD drive is not first in the boot order (go into the BIOS setup program to check and change if needed)
[*]The CD your trying to boot has gone bad or is not a boot able CD.[/LIST]
Will it boot to the Ubuntu CD? If it does that rules out the first 2. 

Is your vista CD from MS or is it a recovery CD you made?

---

### Post by Gremlinzzz on 2007-07-22
most likely CD drive is not first in the boot order 
go into bois and check boot order make cd drive first to boot.
:guitar:

---

### Post by Pumalite on 2007-07-22
This happens to me for not believing people would forget to do that. Oh well.

---

