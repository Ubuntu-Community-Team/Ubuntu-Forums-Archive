---
title: "Help with selecting mount points on a fresh install"
date: 2016-03-10
forum: Installation &amp; Upgrades
---

### Post by gremious on 2016-03-10
Hello,
I'm switching to Ubuntu 14, this pc will be used as a home computer where I play just a couple of games, browse and store all my files, basically. Avrage PC.
I need help with selecting mount points for my partitions because I have an SSD and an HDD and I'm not sure how to a locate the space.
So far I have:
SSD 
Root partition of 20 gb
Swap of the same size, 20, I have 16gb of ram
The rest of the 80gb of space I want to a locate for just some files and programs like wine, that would benefit from SSD spesificly and I don't know what mount point to select for it as home is taken -
HDD 
1tb of /home, just pure file storage.

So my question is, what mount point do I use for the rest 80gb of my SSD space I have left, as I don't understand the use/labeling.

Thank you very much.

---

### Post by Dennis N on 2016-03-10
First, you don't need 20gB of swap. With that much memory, you probably will never use any. I never set more than 4gB for swap. 

Your installed programs from the Ubuntu repositories will install inside your root partition. There is no option to specify where they install.

I use the SSD for my root partition to benefit from fast startup of the OS and programs. I do not use a separate home partition. As I multi-boot, my other operating systems are installed to the SSD as well. 

I use a separate data partition on my HDD for personal data files - including media files which can use lots of your space. As to the mount point for that, I mount the HDD partition at /mnt/data using fstab. Change 'data' whatever name you prefer for that mount point folder. You could also put this data partition on the SSD, of course. Same mount point.

---

### Post by grahammechanical on 2016-03-10
You have 80 GB of SSD space that you do not know what to do with. That is what happens when we buy a large sized SSD. :) You have the space so use it for Ubuntu (/root). You may find that after installing wine & those few games that you are glad that you did so. 20 GB seems adequate for Ubuntu but it can quickly fill up once we start installing stuff.

How many of us have 1 TB drives that never get filled up? All that unused wasted space! It is a good position to be in.

Regard

---

### Post by TheFu on 2016-03-10
[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/) explains what different areas are for.

**Summary:**
/ - base OS - 10-20G
/boot - boot files and kernel - 1G (defaults are just a little too small for me)
/etc - system settings - tiny - usually part of /
/usr - all programs installed by package manager - usually part of /
/home - normal place for user HOME directories.
/opt - 3rd party applications NOT installed via package manager. Think enterprise web-apps.  - usually part of /
/var - variable data and VMs. Size as needed. Sometimes websites, virtualization and DBMS files get placed here by default.  - usually part of /

If the storage is located in the correct location (appears as the directory), then it will be used for that.  Mounts can be placed at the top level or at any depth below. Just update the fstab.

20G of swap is WAY-TO-MUCH!   With that amount of RAM, I cannot foresee any way there would be any swapping at all.  4G is what I'd start with and maybe go to 6G if there is any issues.

I like to use /D and /Data/ for extra storage, then use symbolic links into it from where ever the storage is needed.  For example, /var/lib/libvirt/ often needs more space and I'm just too lazy to mount fresh storage there.  A link from there to /D/VMs lets me have plenty of room for virtual machines without the extra hassles. Plus the new storage allocation doesn't have to be split up on a per-need basis.

Of course, if you are comfortable using LVM, there are flexible ways to handle storage allocations as-needed, for each logical volume, using spare storage that was held back until needed. But that isn't really something for someone with limited Linux experience to mess with.

So, if you make a grid of the mount points and storage amounts, we can provide suggestions.  Don't forget areas for versioned backup storage - hopefully on a different physical disk than the primary storage. If you boot with EFI, there's another partition needed. I don't use EFI.
Also, prefer GPT disks over MSDOS - this removes the 4 primary partition limitation that MSDOS has. GPT allows 100+ primary partitions.  Or you could use LVM which would need only 2 partitions - /boot and everything else would be inside the LVM.  Then setup VGs and LVs as needed.

You didn't mention encryption.  Whole drive encryption is easier with LVM, if that is a consideration.

Hope this helps. Plus, there are lots of other examples of storage layouts in these forums.  Last year and the year before had a few of those questions.

---

