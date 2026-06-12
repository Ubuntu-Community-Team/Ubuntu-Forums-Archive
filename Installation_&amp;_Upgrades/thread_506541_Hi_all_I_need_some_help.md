---
title: "Hi all I need some help"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by tricccple on 2007-07-21
hi there, I know this question might allready have many ppl asked or answer, but due to my everyday schedule, right now I really don't have the time to search for my answer, please give me a hand, thank you

I downloaded 7.04 from official site, burned it onto a cd, restart and boot to the ubuntu manu, I set the resolution to 1024x768 and then the loading sreen pops up, but it never does anything then, 

what can I do with that? right now I'm download 6.06 also, hope to make a difference, 

I'm dying to try linux, wanna to learn more about it, ubuntu looks like fun, please help me out .

thanks

---

### Post by Pumalite on 2007-07-21
We need your specs please. Motherboard? Video?Chipset?1 or 2 hard drives?Dual booting? With what? XP? Vista? It all counts.

---

### Post by tricccple on 2007-07-21
AMD Athlon64 x2 3800+ AM2 65w
ASUS M2A MVP
512mb x 2 (1g) GEIL DDR2 800
Sapphire X1650 pro 256mb
250G IDE 
80G IDE 
80G SATA
Benq DVDRAM or Sony DVDROM

---

### Post by Pumalite on 2007-07-21
Dual booting from same hard drive? Using second drive for Ubuntu? Vista? XP?

---

### Post by tricccple on 2007-07-21
I have Vista x64 on C but I disconnected these drives, only leave the sata 80g and dvdram

so there's no other os , the drive was formatted

---

### Post by Pumalite on 2007-07-21
Then you can install anything. Go back to basics: check iso, do md5sum, burn at 4x, check CD for corruption before install. If you have to download again: torrent better than HTTP or FTP.

---

### Post by tricccple on 2007-07-21
4x is necessary huh, well I got no mroe cdrs, will burn the image on dvd

thanks for ur help

---

### Post by tricccple on 2007-07-21
so what was the reason that the disc just simply stopped reading

does it have everything to do with not burning with 4 x? 

also, let say if i do trying to boot with the OS on first drive, would that might be the reason also 
say.. Win XP pro or Vista 32bit

---

### Post by Pumalite on 2007-07-21
Did you do md5sum on iso and compare it to the one displayed in the site you downloaded from or Ubuntu.org?

---

### Post by tricccple on 2007-07-21
ok, no i didn't do any of that
but I got a new question now, 

going to post a new topic with that

---

### Post by sblanzio on 2007-08-28
Hi
I've the same problem: no way to start the ubuntu installation cd. I even tried the alternate version but with no luck.

I think the problem is the m2a-mvp mainboard which i bought thinking it was ok for ubuntu...

I found another thread where somebody has the same problem too here
[http://ubuntuforums.org/showthread.php?t=507467&highlight=m2a+mvp](http://ubuntuforums.org/showthread.php?t=507467&highlight=m2a+mvp)

they say the amd64 version installs correctly, but i dont want that one!

I'll make some more test and please post if you found a way to solve this probleml.


thanks
sblanzio

---

### Post by klueless on 2007-08-30
Try flashing to the latest bios. I have the M2A-VM and it won't boot 7.04 (all versions). After flashing the bios to 1101 (for the M2A-VM), the install discs booted up without any problems. Installation went smoothly.

Hope this helps.

---

### Post by sblanzio on 2007-08-31
I already tried to flash the latest bios from asus but this didnt solved anything.

I solved the booting problem adding "acpi=off" to the grub booting options. So I installed ubuntu.

The problem now is that, because of acpi=off, I cannot shutdown my computer via shutdown commands both in console and gnome.

When I try it closes everything and just say "Will now halt" but nothing happens and I have to push the power switch.

They say this is a mainboard problem but this is just the latest bios and this it is very annoying.

If anybody would found a solution please post here.
tnx

---

