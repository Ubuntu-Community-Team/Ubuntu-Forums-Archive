---
title: "Kubuntu 8.04.1 USB Install"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by wakojakop on 2008-09-13
I was just browsing things randomly yesterday, when it came to me...
How do you persistently install kubuntu to a flash drive?
The main problem is grub!
Can anyone help me?:confused:

---

### Post by frklin on 2008-09-13
> The main problem is grub!You can more clearly? What does this mean?

---

### Post by wakojakop on 2008-09-13
What i meant is that grub installs to my first HD instead of the flash drive.

---

### Post by Pumalite on 2008-09-13
In step 7 or so, go to 'Advanced Tab' and change (hd0) for /dev/???
Where ??? is your USB
You can find out with:
sudo fdisk -lu

---

### Post by wakojakop on 2008-09-13
Thanks,
I didn't wanna phisically remove my hd.
Do you know a linux distro like kubuntu (Apart from Puppy, DSL, xubuntu,edubuntu & ubuntu) That can run on 64mb of ram, 4gb hd & not a very big download (Under 400mb) and that can easily install to a partition with grub. and an installer in text mode. so i can vm it (I only haVE 256MB ram)

---

### Post by Pumalite on 2008-09-13
256 MB of RAM>Xubuntu Alternate CD:
[http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/)

---

### Post by wakojakop on 2008-09-13
Thanks, does it install in text mode

---

### Post by Pumalite on 2008-09-13
Yes, but is easy.

---

### Post by wakojakop on 2008-09-13
i will install in expert mode

---

### Post by Pumalite on 2008-09-13
Good luck!

---

