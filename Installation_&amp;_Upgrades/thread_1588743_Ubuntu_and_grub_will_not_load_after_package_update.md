---
title: "Ubuntu and grub will not load after package update"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by ionraice on 2010-10-05
I have a recent install of the Ubuntu Netbook Remix on my Asus EEE PC 1005h. Two days ago I used the package updater to update. I didn't check what is was updating. Directly after it restarted I could not boot properly. It loads the screen where it allows me to choose between Windows XP and Ubuntu. When I pick Ubuntu it used to give me a grub screen of all the different Ubuntu versions i could boot. Now it gives a very short script and goes back to the screen for picking between XP and Ubuntu. 
     I downloaded a calender program that has all my notes, assignments and testing schedule in it. If I could just access the backup file it can make I would be greatly revealed. 
     I think I can boot from USB but i did install from a false drive while in XP.

---

### Post by P4man on 2010-10-05
False drive?

Is this a wubi install, or did you install ubuntu on its own partition?

---

### Post by drs305 on 2010-10-05
You should be able to access the files in your Windows wubi installation with the following:

Boot to a LiveCD desktop.
Mount your Windows partition (assuming it is sda1, if it is not, change to the correct partition):
```

sudo mkdir /mnt/windows /mnt/wubi
sudo mount /dev/sd**a1** /mnt/windows
#  Mount the wubi file on a new mountpoint:
sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/wubi
gksudo nautilus /mnt/wubi

```

---

