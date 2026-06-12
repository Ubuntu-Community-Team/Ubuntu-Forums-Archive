---
title: "Installing Ubuntu 10.10?"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by apanton06 on 2011-01-25
Hi, 
I'm just attempting to install Ubuntu 10.10 now and need some help.
Basically I shrunk my hard drive so I have my Windows partition and around 200 GB of free space.
Now I am looking to install Ubuntu 10.10 to one partition, a swap and install the Grub to the Ububtu partition to chainload (using easy BCD).

I selected: Specify Partitions Manually (Advanced) during the install and so far I have this:
/dev/sda
/dev/sda1  ntfs   269417     
free space        230688

I know I have to add the partitions, but what do I exactly select in the pop up menu for the Ubuntu partition and swap partition?

---

### Post by mikewhatever on 2011-01-25
System partition:
type: logical
file system: ext4
mount pont: /

For swap, just select 'swap' in the file system drop down menu.

---

### Post by kansasnoob on 2011-01-25
You might find this useful:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

And this:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Be certain you understand device designations before beginning :)

---

### Post by thefasterblueone on 2011-01-25
I set mine up using this guide. Was my first time and all went like clock-work.

[http://tipsneeded.com/how-to-install-ubuntu-10-10-maverick-meerkat/]("http://tipsneeded.com/how-to-install-ubuntu-10-10-maverick-meerkat/")

goodluck :)

---

