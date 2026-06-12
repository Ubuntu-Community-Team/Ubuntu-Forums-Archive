---
title: "Grub install on usb hdd.... too hard"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by fragment_gr on 2008-08-12
hello guys, i have a problem. i installed ubuntu 8.04 on a usb hdd drive (3 parts-> 1)ext2 for ubuntu 2)swap for ubuntu 3)windows ntfs partition).

the grub mbr boot code wrote on my other main hdd 320gb disk which windows vista installed. i removed the grub code back to vista. now my hdd have ubuntu installed and i cannot boot. how can i write the code not to my main hdd but on the usb hdd which ubuntu installed?

i tried with grub codes from the live cd (grub-install) but nth. is there a easy utility on windows to do that easily? because from live cd is very difficult... thx

---

### Post by Pumalite on 2008-08-12
Step 7>Advanced TAB>Change (hd0) for /dev/???
???=your USB
You can find it with:
sudo fdisk -lu

---

### Post by caljohnsmith on 2008-08-12
> **fragment_gr said:**
> how can i write the code not to my main hdd but on the usb hdd which ubuntu installed?

Actually it should be really easy from a Live CD. But first, I assume you don't have any other Linux distro's installed other than Ubuntu, correct? If that is true, just boot a Live CD, open a terminal, and do the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][this should find your Ubuntu partition in the form of (hdX,Y)][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit

```
That will install Grub to the MBR of the HDD that Ubuntu is on, and it will use the Ubuntu partition for all its config files.

---

