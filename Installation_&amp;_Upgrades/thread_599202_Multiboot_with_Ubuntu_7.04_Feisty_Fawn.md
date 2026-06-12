---
title: "Multiboot with Ubuntu 7.04 Feisty Fawn"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by omeg1976 on 2007-11-01
Greetings everyone, I decided to try my best and follow a multiboot tutorial however I am stuck

Here is my following partition table:
hda1 = XP pro
hda2 = Windows 98 (fat32) not yet installed
hda3 = Grub bootloader (fat16)
hda4 = Extended partition
hda5 = Swap
hda6 = Ubuntu

Now here is the interesting part, I was able to install grub and currently I can boot into xp without an issue, When the computer boots and loads grub, it shows my menu.lst like expected
However when I go to select the ubuntu partition, I get error 13 Invalid or unsupported executable format
I ran a cfdisk and everything agrees with my previously mentioned partition table.
Does anyone have any idea why this is failing?
-John

title			Windows XP (hda1)
root			(hd0,0)
unhide			(hd0,0)
makeactive
chainloader +1

title 			Windows 98 Second Edition  (hda2)
root 			(hd0,1)
hide 			(hd0,0)
unhide 			(hd0,1)
makeactive
chainloader +1

#title 			Grub Bootloader (hda3)
#title 			Extended Partition (hda4)
#title 			Swap Partition (hda5)

title 			Ubuntu (hda6)
root			(hd0,5)
chainloader +1




Oh, it would also be mentioning when I installed the partitions it was like this
1) installed xp
2) inserted live cd and setup grub partition swap and ubuntu partitions
3) changed the grub settings so that it would consider partition 3 the place to look for its menu.lst ( basically setup the mbr to be sourced from grub partition ( partition 3)
4) installed ubuntu on partition 6 and left partition 5 as its swap partition
5) turned on machine and got ubuntu's substituted menu.lst which did boot ubuntu by the way
6) booted live cd, changed settings back so mbr was sourced from grub partition
7) only xp boots

---

### Post by pay on 2007-11-01
The ubuntu entry is wrong. You need to point it to a linux kernel. For example her is mine> title=Gentoo Linux 2.6.22-gentoo-r8
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-gentoo-r8 root=/dev/hdc3

---

### Post by omeg1976 on 2007-11-01
ha!! youre right and youre damned quick! i didnt expect to see a reply this quick

I think i had the issue licked, i explored the linux partition and took its menu.lst and experimented

title 			Ubuntu (hda6)
root			(hd0,5)
chainloader +1

Now yes i see why this is wrong, Im just wondering why i dont need the chainloader statement, what exactly does that do?

----------------------------------------------------------------------------------------------------------------------------------------------------

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c73b673a-268b-48a9-8c23-d62d789b2bfe ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

This entry doesnt work either because of the quiet and the savedefault lines, any idea what they do? The reason that I came to that conclusion is because the next entry has a working result


----------------------------------------------------------------------------------------------------------------------------------------------------
title		Ubuntu, Feisty Fawn 7.04
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=c73b673a-268b-48a9-8c23-d62d789b2bfe ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic

[http://robertmarleysoffthechain.ytmnd.com/](http://robertmarleysoffthechain.ytmnd.com/)

---

### Post by pay on 2007-11-01
I don't exactly know what the chainloader is used for. I just know that it is only really needed for Windows drives. The quiet option hides the information when it is being booted up (I'm pretty sure). You don't have an x800 series card by any chance?

---

### Post by omeg1976 on 2007-11-01
No sir, This thing is running in my 733mhz beast I cant get my head in the case to even tell you what video card I have, (hope thats what youre asking about) I think its an nvidia or something
anyway why do you ask

ooh - and



title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

gives me error 15 file not found
----------------------------------------------------------------

title			Windows XP Professional
root			(hd0,0)
unhide		(hd0,0)
makeactive
chainloader +1

works without an issue, im guessing its because i unhide the partition? but if thats so... what hides it?

---

### Post by pay on 2007-11-01
I was asking because a few other people had issues with x800 video cards and the quiet option. Sorry but I've never used the unhide option so I can't really help you. Sorry.

---

### Post by omeg1976 on 2007-11-01
no worries thanks again, perhaps one day ill post a walk through of how i did this

---

### Post by omeg1976 on 2007-11-01
:popcorn:

---

### Post by Chappy7777 on 2007-11-01
Boot into your XP partition. Once it's happily loaded, open Control Panel and dbl click on System.
Open the Hardware Tab and you'll see Device Manager. Your hardware will all be listed there. Or is should be. I think you'll have to be in your admin account to do this. Not sure.

Hope this helps.

---

