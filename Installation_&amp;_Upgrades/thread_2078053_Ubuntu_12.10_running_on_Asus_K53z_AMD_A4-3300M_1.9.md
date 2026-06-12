---
title: "Ubuntu 12.10 running on Asus K53z AMD A4-3300M 1.9GHz"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by kenpachiZaraki on 2012-10-30
First BUG to note.

- I have only just bought my inexpensive laptop (Asus k53z). I managed to install Ubuntu 12.10 along side of Windows 7 Prem. Originally had a problem with the grub not loading properly though after a bit of research all I had to do was install grub properly (there was no menulist). That problem fixed, boot my lappy and choose to run Ubuntu from the grub menu, though about 50% of the time I get a blank purple screen instead of the user login screen?!?!?!

Does anyone know of a solution already posted about this problem?

---

### Post by kenpachiZaraki on 2012-11-09
- Second note

The battery seems to not last as long as it does in windows. I get 2 hours ubuntu battery time instead of 8 hours windows battery time. 

Anyone know why this might be the case and any known solutions out there?!?!?

---

### Post by kenpachiZaraki on 2012-11-09
- note three

If the computer falls into suspension mode, there is no way to wake system up; Pressing power button, space bar, touchpad, function keys; mashing the keyboard. Only way is forcing the system to shutdown (holding power button in for a few seconds) and  then power on again will gain control again.

---

### Post by 2F4U on 2012-11-09
Please post your hardware specs. What graphics card and driver do you use?

---

### Post by kenpachiZaraki on 2012-11-10
my graphics card is: Radeon HD 6480G

im looking at the Xorg.0.log and am seeing:

[    17.003] (II) RADEON: Driver for ATI Radeon chipsets:
    "huge list..."

[    17.006] (II) VESA: driver for VESA chipsets: vesa

not sure of a more accurate way of checking for what driver is being used. I am also new to reading log files; wish there was a better guide/tutorial to read (read the one on ubuntu forums but it was quite brief and only gave a few commands and such, looking for a tutorial that would teach more on how to read them and what errors to look for etc...).

---

### Post by kenpachiZaraki on 2012-11-12
Did this help?

---

### Post by kkoz83 on 2013-04-21
Hi, I just started with Ubuntu 12.10 (64 bit) so sorry for late addition.  I also have an Asus K53Z with same graphics and I can't even try Ubuntu without freezing   I used "nosplash noquiet nomodeset" and got in it enough to successfully install.  Now Iget it stuck on the purple screen too.  Any suggestions?

---

