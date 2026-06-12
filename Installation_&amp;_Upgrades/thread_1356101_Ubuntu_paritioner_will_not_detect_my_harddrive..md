---
title: "Ubuntu paritioner will not detect my harddrive."
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by cbwcjw on 2009-12-15
Righto, originally I thought my install problem was because of my lack of blank CDs, as I was installing from a flash drive, but then it turns out it wasn't that.

First, I just boot from cd or flash drive onto the dell computer I have designated as a desktop server thing. I then click install, and go through the installation like I always have. Then I see this:

[http://img682.imageshack.us/img682/2456/screenshotel.png](http://img682.imageshack.us/img682/2456/screenshotel.png)

The partitioner handsomely does NOT detect the WD 150gb SATA harddrive.

If anyone could help, that would be awesome. Id love not to use opensuse to set up a server, but if I am left with no speedy choice it looks like I will be.

---

### Post by darkod on 2009-12-15
Are you running raid?
This usually happens if the drive was used in raid earlier and settings traces remain. If you are NOT running raid, while bootd with LiveCD in terminal execute:
sudo apt-get remove dmraid

That usually helps.

---

### Post by cbwcjw on 2009-12-15
That fixed it, thank you!

---

### Post by =not4prophet= on 2009-12-15
nevermind

---

