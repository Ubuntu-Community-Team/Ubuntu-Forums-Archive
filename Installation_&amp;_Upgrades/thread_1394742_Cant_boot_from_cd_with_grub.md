---
title: "Cant boot from cd with grub"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by zac7654 on 2010-01-31
Hey all, i currently have ubuntu 9.10 and windows vista installed on my laptop.
I utterly despise vista and wanted to try Windows 7 so i downloaded it, burned
it to a disc and viola! Nothing happened

I've put boot from cd/dvd on top of my boot list in the bios (i have about
half a second to click the bios entry button lol) to no avail, when i turn
on the computer the drive just makes a bit of noise and then grub loads up :(

so!

how do i stop grub loading and get it to boot from disc??

---

### Post by byStanderone on 2010-01-31
...booting from the cd drive is primarily selected through the cmos setup, re-check your setup.

---

### Post by amsterdamharu on 2010-01-31
Maybe the CD isn't bootable or burned wrong. You can test it in ubuntu with virtualbox (install with synaptec package manager).

In virtualbox you can "virtually" boot from cd or cd image, if both of them won't boot then there is something wrong with the image file.

You can run windows in ubuntu usig virtualization but it will be slow. Virtualbox is nice to try small linux distro's and to see if a cd will boot.

---

### Post by zac7654 on 2010-01-31
yes it was burned wrong /forehead slap

Thnx anyway guys

---

