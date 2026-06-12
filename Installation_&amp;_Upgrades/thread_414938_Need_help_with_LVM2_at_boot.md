---
title: "Need help with LVM2 at boot"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by mac.ryan on 2007-04-20
I am trying to switch my partitioning scheme to LVM. But - although I have managed to create the Volume Group and the Logical Volumes and successfully managed to mount them within a running system, I cannot obtain the same result automatically at boot-time (which I need as i would like to put my /home on the VG).

I am using LVM on a single sata HD and - in the empty space I had on it - I created a VG with two LV in it (formatted in ext3). In order to get one of them mounted at boot I modified the /etc/fstab as follows:

```
# Entry for LVM
UUID=2c5E42-eTvX-gQwi-Exrc-MkNN-ZDea-1EZfCz /media/jabbar_lv2 ext3 defaults 0 0

```(the UUID is the one of the logical volume, obtained with 'lvdisplay')

I think the problem might be in relation to the fact at boot time

```
vgchange -a y jabbar
```is not issued automatically (jabbar being the name of the entire VG).

How can I work around this?

SIDE POINTS:[LIST]
[*]Although the above is being done under Edgy, yesterday I tried to install Feisty with alteranate64 version and "priority=low"; I selected the passage "configure LVM" in the installer, but it failed without neither having a go... anybody having had this issue as well?
[*]Just a question: how many LVs can i have under a single VG?[/LIST]Many thanks in advance!

---

### Post by mac.ryan on 2007-04-20
Never mind... I discovered that Feisty does what it is assumed to (contrarily to Edgy), so now I am an happy man... ;)

I wonder if the problem has to do with some patch to add to the kernel (this was the case for kernels <=2.4 but for 2.6 it should have been ok...:confused:

---

