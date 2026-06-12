---
title: "Problem with installation of Ubuntu 7.10"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by Bheegerji on 2007-10-29
I'm new to linux and found that Ubuntu distributions are easy to be installed.So, I downloaded a ubuntu 7.10 iso and burnt it. I checked the cd for defects and there were no problems with the burnt cd. I'm using Win XP Pro. I'm planning a [COLOR="Red"]dual boot[/COLOR] installation. I've a 80GB hard disk partitioned into 4 drives( c: 19GB, d: 19GB, e: 19GB and  f: 15GB). Win XP has been installed into c: drive and I like to install Ubuntu in f: drive. So, I emptied all the contents of f: drive and made available all the 15GB for Ubuntu.

I read many posts and started my installation. I inserted the cd and rebooted my system and started my installation. Here are the problems 

1) I use a 15" monitor and the "forward" and "back" buttons at the bottom of the install window were not visible. I tried to resize the window and still found no success. The window wont resize. So I realigned the top and bottom task bars to left and right and checked the autohide option. This time I could see half of the button. [COLOR="Red"]Will this problem persist even after the installation?[/COLOR]

2) I proceeded with the installation and went ahead to "Manually edit partition table".  The window showed it had 17092MB and others had around 20000MB. There was a free space of around 8000MB. I selected f: drive as it was the only drive with least space. I entered a  value 13000MB in the box and selected fat32 formatting and clicked ok. A new box appeared showing that it was scanning the drive and later another window appeared that showed  "Writing the changes to disk.  You cannot undo the changes later." I clicked ok and waited for sometime. [COLOR="Red"]Then an error box appeared stating " Error: Root file not defined."[/COLOR] I din know what to do and rebooted the system and removed the cd.

3) Windows started and I checked my f: drive. It was formatted as fat32 and [COLOR="Red"]it showed only 11GB (initially 15GB) as available free space. How can I undo this? Will I be able to restore the f: drive to its initial condition?[/COLOR]

Please help me with the installation.

---

### Post by Pumalite on 2007-10-29
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

[http://gparted.sourceforge.net/larry/livecd/main/livecd.htm](http://gparted.sourceforge.net/larry/livecd/main/livecd.htm)

---

### Post by Bheegerji on 2007-10-29
Thanks Pumalite. Can u help me with the installation? Was the error caused due to fat32 formatting? And during the installation, I was not asked for a username and password.

Thanks anyways.

---

### Post by Pumalite on 2007-10-29
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
I would start again and install with the Alternate CD
A good installation ends up generally with an ext3. The installer does the formatting.

---

### Post by Bheegerji on 2007-10-29
This time I tried ext3 and specified a location for the root file. It's asking for a location for the swap partition. When I clicked on th e f: drive, I couldn't find the "New Partition option". Has the swap partition to be specified seperately in another partition ?

---

### Post by Pumalite on 2007-10-29
Follow my links and you'll be OK.

---

