---
title: "All my partitions disappeared."
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by thelocust on 2007-06-04
I tried to dual boot Windows and Kubuntu on the same HDD (500 Gigger) and Windows has to be on the first partition. Then when I was trying to use the program that I installed windows for I found that Windows installed it's self on the E drive which made it useless to me so I deleted it and installed Windows on my 40 Gigger (my back up drive). Now Windows works but I can't get my Kubuntu to boot. Gparted (on my System Rescue CD) says that the whole drive in unallocated. So I think when I deleted Windows I deleted the MBR. So is it even possible to get my Kubuntu back or do I have to format the whole drive?

In the beginning:

hda1>fat32>backup

sda1>ntfs>windows **[COLOR=Red](partition I deleted)[/COLOR]**
sda2>ext3>boot
sda3>ext3>root
sda4>extended
>sda5>home
>sda6>swap

Now:

hda1>ntfs>windows

sda1>unallocated

---

### Post by Dougie187 on 2007-06-04
Can you just reinstall grub?

Edit:
here is a guide
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by thelocust on 2007-06-04
When I put:

grub-install (hd0,0)

I get:

zsh: unknown file attribute

---

### Post by Dougie187 on 2007-06-05
So do you not have grub installed at all then?

---

### Post by thelocust on 2007-06-05
Grub is installed on the boot partition but the boot partition is no longer there.

---

### Post by Dougie187 on 2007-06-05
and you did the grub-install (hd0,0) in the ubuntu live cd right?

---

### Post by thelocust on 2007-06-05
Yea and I get  **zsh: unknown file attribute** (using system rescue cd)

---

### Post by Dougie187 on 2007-06-05
and nothing happens if you type ```
sudo grub
```
Using the ubuntu live cd?

---

### Post by thelocust on 2007-06-05
I reformatted thanks for the help though.

---

