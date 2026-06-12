---
title: "Installation onto an SSD / Netbook"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by piloti on 2012-09-06
So, I have an old netbook I want to invigorate with an SSD Drive. Because it is a Netbook the SSD will be the only drive.
I have run Ubuntu via a bootable USB stick so I know Ubuntu will work. I run Ubuntu as my main laptop O/S.

When I try to "install" Ubuntu lets me choose the SSD disc, a 128Gb Kingston, but when it comes to the "install" bit [after the partition screen] it tells me there is a hardware error.

So, my question is : ho w do I install Ubuntu on an SSD [in simple easy to follow steps that an idiot can understand….]
I have found lots of pages for optimising, but none that tell me how to actually install.

Thanks
P.

---

### Post by sudodus on 2012-09-06
Since you get a hardware error, I suggest that you check the SSD while running the live [KLX]Ubuntu system.

I don't know if there is S.M.A.R.T. information on your drive. If its there, check it in your bios or with the Disk Utility Tool! This shows if there are read/write errors.

Check the partition table with Gparted. Show also the Drive Information (tick it in the dropdown menu)! You can attach a screendump of the Gparted window to a reply.

Check/repair the file system with
```
sudo e2fsck -f
``` (if you plan to use the existing file system, ext2, ext3 or ext4).

I don't know if there are some special settings for your SSD. If you specify the details about it (brand, model etc), maybe someone can help you with that.

---

### Post by oldfred on 2012-09-06
I prefer to partition in advance with gparted. Are you installing just Ubuntu or Windows also?

If just Ubuntu gpt may be better for SSD?

What BIOS setting do you have? SSD need AHCI not IDE to work with SSDs.

lThe Arch site has a lot of good technical info.
Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)

I just partitioned my SSD like any other hard drive. I did use gpt and had to have a bios_grub partition for grub to install correctly.

---

