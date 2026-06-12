---
title: "Boot hangs on AMD64 X2 system, using alternate Edgy Eft install CD (after install"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by mimiko on 2007-03-07
Hi, it appears I need help. I've been digging through past posts on these forums and other linux forums and can't seem to find a solution. 

Here's the situation:

0) I am using an HP Pavillion dv6000 with an AMD Turion64 X2 processor, 2gb memory, 120gb hard drive.
1) I downloaded and burned Ubuntu 6.10 Alternate AMD64 Install CD
2) I ran install and after finishing install, rebooted and it hung at about the second bar.
3) I rebooted this system into the recovery mode (or whatever it's called) so I could see what was actually happening, and it was hanging during the unpacking of kernal.
4) I ran the install disk test and it said everything was fine.
5) I reinstalled, this time added NOAPCI, etc in the boot command before beginning the install.
6) Installation completed, and I booted up in normal mode.  Boot image hung approximately in the middle of the bar.
7) I rebooted into the recovery/safe mode and now see where the boot process is hanging, but have no idea how to resolve this or what is going on, so advice would be really appreciated.

Here are the last few lines before the booting freezes/stops (I can't switch terminals or anything):

(hopefully the photo I snapped will show up)

[IMG]http://www.ashliana.net/photos/d/1092-1/ubuntu_hang+003.jpg[/IMG]

Any comments, links to other threads, or whatnot are greatly desired and appreciated. :)

---

### Post by chewearn on 2007-03-08
Maybe you might want to try the generic (32bit) desktop liveCD install?

---

### Post by watson540 on 2007-03-08
ever since i solved this for myself i have seen this error pop up everywhere!

when you turn on the computer it goes to the grub screen ok. highlight the first option when it comes up (normal mode) make sure its highlighted (it is by default) then hit E because you want to edit that line. it will take you to another screen, hit down and e again. you should be looking at a big line of text now, says quiet and splash at the end of it. at the end of all that type this 
vga=791
hit enter , then hit B to boot - good luck , you're welcome :)

PS: once you get back into your box you can make it permanent by adding the same line to the same place in the file /boot/grub/menu.1st
about 3/4's way down in the file (open with text editor) (as sudo/root) you will see the line you had to edit. just throw that vga=791 at the end of it. this is such a wierd fix i happened on purely by mistake but i was having lockups about 9 out of every ten times i tried to boot, ever since i added that line its been fine and this fix worked for others too. the funny part is , that all that line does is change your console resolution to 1024x768!! crazy huh? who woulda thought it?!

---

### Post by mimiko on 2007-03-08
> **watson540 said:**
> ever since i solved this for myself i have seen this error pop up everywhere!

when you turn on the computer it goes to the grub screen ok. highlight the first option when it comes up (normal mode) make sure its highlighted (it is by default) then hit E because you want to edit that line. it will take you to another screen, hit down and e again. you should be looking at a big line of text now, says quiet and splash at the end of it. at the end of all that type this 
vga=791
hit enter , then hit B to boot - good luck , you're welcome :)

PS: once you get back into your box you can make it permanent by adding the same line to the same place in the file /boot/grub/menu.1st
about 3/4's way down in the file (open with text editor) (as sudo/root) you will see the line you had to edit. just throw that vga=791 at the end of it. this is such a wierd fix i happened on purely by mistake but i was having lockups about 9 out of every ten times i tried to boot, ever since i added that line its been fine and this fix worked for others too. the funny part is , that all that line does is change your console resolution to 1024x768!! crazy huh? who woulda thought it?!

Thank you for this info -- I just tried doing this and it still seems to hang, perhaps because I reinstalled again, this time not disabling ACPI, SMB, etc.  Does it still require these options to be disabled? (And if so, can one re-enable them later after install?)

---

### Post by watson540 on 2007-03-08
no the only line you need is vga=791 you can try the other options along with it though, but i only needed that 1 option. you can enable/disable them at will whenever you want. but try just the vga option with nothing else and that should work for you :)

---

### Post by mimiko on 2007-03-08
> **watson540 said:**
> no the only line you need is vga=791 you can try the other options along with it though, but i only needed that 1 option. you can enable/disable them at will whenever you want. but try just the vga option with nothing else and that should work for you :)

Heh, okay, so, I tried this, and I get past the previous hang point, and instead am stuck at "Starting kernel event manager...." (I get this info from going into the recovery mode, still using the vga option you suggested.)  Any ideas now?

Here's a new picture of where I'm at:

[IMG]http://www.ashliana.net/photos/d/1098-1/unbuntu_hang_4thtry_jpg.jpg[/IMG]

Thanks again.

---

### Post by teaker1s on 2007-03-08
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

---

### Post by mimiko on 2007-03-08
> **teaker1s said:**
> [https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

Yeah... I found that wiki link before I even tried installing ubuntu -- I was really trying to be prepared to deal with whatever issues might arise, but that wiki page seems helpful only after you've successfully booted, really.

I did find this other thread about the kernel event manager hanging.... will try to test out some of the suggestions there shortly.

[http://ubuntuforums.org/showthread.php?t=291690&highlight=kernel+event+manager]("http://ubuntuforums.org/showthread.php?t=291690&highlight=kernel+event+manager")

---

### Post by teaker1s on 2007-03-08
better success  is normal with 64bit alternate iso

---

### Post by mimiko on 2007-03-08
> **teaker1s said:**
> better success  is normal with 64bit alternate iso

yep, that's what i'm using... alas.

---

### Post by teaker1s on 2007-03-08
the dv6000 has several different hardware configurations, have you tried using ANY OR ALL OF THESE
NOAPIC NOAPCI NOSMP

[COLOR="Black"]**edit**[/COLOR]
Looking again at the screens you posted, the BARO situation you have is Identical to the issues I had and edgy, I did a bios update and used feisty- for a while apart from shutdown all was well.
Then xorg 7.2 came in feisty and my laptop wouldn't work with any of the drivers 
(nv/ vesa or beta nvidia).

That forced me to use Debian etch,beta nvidia driver and these forums as ubuntu is debian based

---

### Post by watson540 on 2007-03-09
try booting with noapic as well as vga=791 and irqpoll
all at the same time on the same line.

---

### Post by jhineman on 2007-04-12
I recently upgraded from 6.06LTS to 6.10.  I'm having a booting problem that looks similar.  I've tried both of the suggestions here to no avail (i.e. adding vga=791 and irqpoll).  With no luck where should I look next?

System was working fine under 6.06LTS.  Seem to also get to approximately around

Begin: Running /scripts/init-bottom ...

before the thing hangs .

---

