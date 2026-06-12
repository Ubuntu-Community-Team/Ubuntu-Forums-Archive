---
title: "ubuntu on external hdd and grub problems"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by billygt on 2008-09-25
Hi,

i'm kind of a linux newbie and i need help. at start, i installed ubuntu 8.04 on my external hdd (i divided it in two parts, and ubuntu took a part and did its stuff -- created an ext3 and a swap). Everything was ok, my pc would boot with grub and i could choose xp or ubuntu. 

something then happened when i booted my computer: i got grub error 21. now i understood that problem was because my external hdd took too much time starting and wasn't recognized early enough. I had to plug in my external hdd right before launching my computer, this was everything was ok.

the problem came when i tried to launch my pc without my external hdd plugged in (wanted to launch xp simply) : grub error 21!!! I was stunned. grub is installed on my external hdd (dev/sdb/boot/grub...)

next i tried installing ubuntu again on my internal hdd on another partition, but think i did a mistake during istallation, when i configured grub to installed on sda5 which is my linux ext3 partition (grub was set on default to hd0, which is sda (with no partition specified if i get this right). Well when i rebooted, my original grub loaded, without the option for me to load my internal hdd linux and the same old error 21 when i reboot without external hdd plugged in.

Well thats about it, here's my partitions setup:

Internal hdd:

sda1 : dell utility partition (or something like that -- it's small enough, about 50MB, to let sd2 be the boot drive)

sda2 : boot drive, where xp is installed

sda3 : dell pc restore partition

sda4 : Extended

sd5 : linux ext3 main partition

sd6 : linus swap

External hdd:

sdb1 : data
sdb2 : linux ext3 main partition (first installation)
sdb2 : linux swap


Thats about it, but further on i can go back in ubuntu to get to exact info if necessary. Note that there are more partitions on sdb that i use for backup, but that wasn't there initially (when first installed linux on external hdd)

Hope i'm clear enough, thanks

---

### Post by billygt on 2008-09-26
forget it

i reinstalled ubuntu on my main hdd and let grub choose its default place to install n everything is ok now

---

