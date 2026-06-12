---
title: "Reinstalled Windows after installing Ubuntu, now only boots to Windows"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by HungerGalaxy on 2012-10-27
Hi all, 

After running Ubuntu exclusively for a month or so I remembered that to update my BIOS I need Windows. I made a 50gb ntfs partition and installed Windows onto it, but now my system only boots into windows. I tried booting from a Live CD and running Boot-Repair but at the end it said to make sure my BIOS was set to boot from /dev/sdb (the SSD, attached to my hard drive, on which Ubuntu is installed). However, because the SSD is integrated into my hard drive (I have a Samsung series 7) I can only boot to the terabyte hard disk and not the ssd from bios. Something interesting I noticed on running gparted from a live cd was that my /boot partition (at the beginning of my hard disk, had before the windows install) still seems to have linux-y things in it (init.d, memtest) and gparted detects the windows file system but still thinks the previous partition is its old size, not 50gb smaller like it should be. 

Any insight or possible fixes are much appreciated!

---

### Post by aabed91 on 2012-10-27
Try these steps:
- Insert the Live CD of the Ubuntu version that installed on your computer.
- Select 'Try Ubuntu' not 'Install Ubuntu'
- Now open the terminal and type these commands:
```
sudo -i
```
```
fdisk -l
```
now you can list all partitions on your hard.
find the partition that have system linux.
there is a system column in the list

then type these commands:
```
mount /dev/sda? /mnt
``` 
Where ? is the nuber of sda

finally type:
```
gtup-install --root-directory=/mnt /dev
```

and reboot the system

---

### Post by darkod on 2012-10-27
There is an error in the final command. It should be:
```
grub-install --root-directory=/mnt /dev/sda
```

That would install it to /dev/sda if you can boot only from there. Make sure you use the correct /dev/sdbX partition in the mount command, it should be your root partition. Since you have ubuntu on sdb it will be like /dev/sdbX.

I am not sure what you mean by a /boot partition on sda. Are you using it or not? If you have a separate /boot partition you also need to mount it before running the grub-install.

---

### Post by HungerGalaxy on 2012-10-27
Originally I had everything on my hard disk but I wanted to boot from my ssd. However I messed something up so I had to reinstall, and I put /boot at the beginning of my hard disk and the rest of it as home, and then put root onto my ssd. Should I still try the above commands? Thanks for the speedy replies!

---

### Post by darkod on 2012-10-27
If that /boot is in use, you need a modification in the procedure. Find the root partition (or you seem to know which one is it) on your sdb disk, lets call it /dev/sdbX.

Then try:
```
sudo mount /dev/sdbX /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda
```

Try that first and lets see.

Note: The previous poster mentioned running sudo -i and after that you don't need to put sudo in front of every command. In my suggestion above, there is sudo in front unless you run the sudo -i first. It's the same thing, you can do it one way or the other.

---

### Post by HungerGalaxy on 2012-10-27
Posting from Ubuntu again :) thanks! Just so I'm clear on what I did: I installed grub to my root directory, but because grub handles booting I also needed my /boot partition in there for the install to work properly, right?

---

### Post by darkod on 2012-10-27
Not exactly.

When installing grub from "outside", like from live mode running from the cd, you need to tell it first where is the root partition, and if separate /boot exists you need to tell it where it is too.

But since linux works with mount points, you first mount the root and /boot partitions somewhere, like the temporary mount point /mnt.

So, first you mount the root partition at /mnt, and the boot partition at /mnt/boot.
With the third command you use grub-install to install it at /dev/sda but also passing the --root-directory parameter to tell it where you mounted the root, in this case /mnt.

So, it's not that you installed grub2 to the root partition, you installed it to the MBR of the /dev/sda disk. The mount of the root partition is only used so that grub2 knows to "connect to it" in a way.

---

