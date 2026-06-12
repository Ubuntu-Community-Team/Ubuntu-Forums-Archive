---
title: "Crashing while making boot partition"
date: 2015-01-13
forum: Installation &amp; Upgrades
---

### Post by KonT on 2015-01-13
I'm try to install ubunto 14.1 next to the windows 7 I use 'something else' metode and create:


ex4 /boot(500 MB)
swap area (2048 MB)
ex4 / (19000MB)
but when I try to installing ubuntu , crashing in first step such as below :


**Creating ext4 file system for /boot in partition #9 of SCSI1 (0,0,0)(sda)**


/usr/lib/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 12277 was not found 


when attempting to remove it Glib.source_remove(self.rows_chanded_id)


**could anyone please help me in this situation ??**

---

### Post by fantab on 2015-01-13
What tool are you using create a /boot partition? I recommend [Gparted]("http://www.dedoimedo.com/computers/gparted.html"), which is available on Live ubuntu DVD/USB.

Also tell us more about your computer hardware.
Post the output of:
```
sudo parted -l
sudo fdisk -l
```

If there isn't a particular need to have a separate /boot partition, I suggest you don't make one. Just partition with '/' and get on with it.
A separate /boot will create problems if you are not mindful of it space limitations. You will have keep on eye on the 'remaining space' in /boot... if /boot is small then you'll have to keep removing the unwanted kernels regularly.

---

