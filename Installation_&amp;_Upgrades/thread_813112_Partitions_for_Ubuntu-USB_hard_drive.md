---
title: "Partitions for Ubuntu-USB hard drive"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by cyclonedr on 2008-05-30
Hi all,
  I recently purchased a 160GB SATA WD hard drive and initially placed two partitions on it, a 78GB for XP Storage, as NTFS, and then a 56GB FAT32 partition so I could share files between XP and another 98SE computer.  The drive is in a USB enclosure, and the computer recognizes it as a USB Mass storage device.  I know I can boot from the device.  What I want to do is install Ubuntu on the remaining space.  I go to manually create the three partitions, \, swap and \home, but when I go to create the \home partition it says error cannot create more than 4 primary partitions.  My question is can I create an extended partition for any of the Linux partitions.  What would you recommend as the layout.  Would it work better to let the installer use the free space?  I've got the 7.10 distro. I do wish to keep the two storage partitions, but I don't have a problem with shrinking them down.  Thanks for any suggestions.

---

### Post by Pumalite on 2008-05-30
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Create an extended partition (keeping in mind the 4 primaries limit) and within that place 2 logicals; one for '/' and one for /swap.

---

### Post by cyclonedr on 2008-05-30
Ok, I was actually using GParted to intially format, and that is when I got the error, so just to recap my partitions would look like this:
78GB NTFS-XP
56GB FAT32-98SE
approx 20GB Free partitioned as 5GB logical /
                                1GB /swap
16Gb /Home as a primary

Does this look good?  I dual booted Fedora Core 5 two years ago, and am now trying to return to Linux, step by painful step

---

### Post by Pumalite on 2008-05-30
Post a screenshot of Gparted.

---

### Post by cyclonedr on 2008-05-30
Ok, I used the screenshot button in Gparted, but I couldn't figure out how to get that into a post in windows, so I just took a digital picture of it, so here is the link: [Gparted screen]("http://img105.imageshack.us/img105/8302/1041359nx0.jpg")

Now when I install Ubuntu, will it automatically figure out I've created the partitions for it, or is there an option I have to say, like put the root files here.  Thanks again for your help

---

### Post by cyclonedr on 2008-05-30
I forgot, how do I set flags for the partitions, or does it matter?

---

### Post by Pumalite on 2008-05-30
I can't see very well, but it seems you created an extended partition and put your logicals inside. From that I assume it should be OK. Don't worry about the boot flag.

---

### Post by cyclonedr on 2008-05-30
Ok great, I'm not sure if you noticed but I created what is supposed to be the /home partition outside of the extended partition group, is this ok, or should I place it with the other two / and swap.  Thanks again

---

### Post by Pumalite on 2008-05-30
You can place it anywhere you want as long as you don't exceed the rule of 4 primaries per drive.

---

