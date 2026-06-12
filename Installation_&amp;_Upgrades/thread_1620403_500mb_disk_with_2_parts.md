---
title: "500mb disk with 2 parts"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by mosaic2s on 2010-11-13
The enclosed pix shows the gparted of my system.
Can I format the /dev/sda6 that has /usr/local directory? it has no data. 
will it create trouble in existing installation of 10.04 on /dev/sda1?
Can I use the /dev/sda6 to install any other OS?

---

### Post by sidzen on 2010-11-13
See this link re: [fstab]("http://www.tuxfiles.org/linuxhelp/fstab.html") for a basic understanding of the concept of what you ask, if you would, please.
Your setup looks like it would be better for [LVM]("http://www.linux.com/archive/feature/118645")
Also,[ Slackware Linux Essentials]("http://www.linux-books.us/slackware_0001.php") has sections that are a good basic reference on partitioning and other 
"essentials.'

Best wishes!

---

### Post by mosaic2s on 2010-11-13
Thanks. Did go thru the fstab section. LVM seems good but my data usage is not extensive. So i can do without it. Slackware file is 2006 - is it not vintage since ubuntu has changed some things around?

What I understand till now - 

/dev/sda6 - the physical drive is mounted at /usr/local. and is currently formatted as ext3.
so no major issue if i format the /dev/sda6.

formatted the /dev/sda6 from 250gb to 60gb ntfs and created sda7 as 180gb ext3. loaded other OS CD, it recognised only ntfs partition. so MBR will get overwritten. currently searching for how to restore grub to MBR.

Listing fstab here - 
> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=455e93b8-1fdb-466c-be8b-6ad7f3214279 /               ext3    errors=remount-ro 0       1
[COLOR=Red]# /usr/local was on /dev/sda6 during installation
UUID=9d123297-be53-402d-a99d-f292169324f1 /usr/local      ext3    defaults        0       2[/COLOR]
# swap was on /dev/sda5 during installation
UUID=c1e83792-ee07-4096-8ae3-3046c03a59ed none            swap    sw              0       0


---

### Post by sidzen on 2010-11-15
The Slackware reference was just that, a ref for the basics one seems to have to search for other places.

Speaking of searching -- Search: Keyword(s): restore, grub, MBR 
[URL="Search:%20Keyword%28s%29:%20restore,%20grub,%20MBR%20%20%20http://ubuntuforums.org/search.php?searchid=77405132"]
http://ubuntuforums.org/search.php?searchid=77405132[/URL]

This was SOLVED, eh?

Best wishes!

---

### Post by mosaic2s on 2010-11-24
I have used gparted to create total of 3 partitions.
Primary /dev/sda1 formatted as ext3. running ubuntu 10.04.
Extended /dev/sda6 and sda7.

When installing other OS, it will says that it can not recognise the ext3 primary partition and hence it will delete.
How to avoid that?

Can I transfer the ubuntu entire files to /dev/sda7 and then allow other OS to format /dev/sda1? Or will that delete the entire hard disk?

---

