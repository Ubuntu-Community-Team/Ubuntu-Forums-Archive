---
title: "Install Ub15.10 with separate /home ?"
date: 2016-02-21
forum: Installation &amp; Upgrades
---

### Post by ra7411 on 2016-02-21
I want to install Ub 15.10 on a 2 TB HD with /home in its own partition.

During install, I choose "something else" and get into choosing partitions. I want the o/s in its own partition and /home in its own, and a swap partition. Can somebody walk me through this or refer me to a clear guide?

The stuff I google up looks different from the Ub 15.10 partion menu. The o/s goes in / right? And then you create a new partition located at /home, right?  There's no clear menu guide on how to do this.

Thanks

---

### Post by Dennis N on 2016-02-21
I always create the partitions with gparted before starting the installer, but you can do it after starting the install also.

_This assumes the needed partitions already have been created*_. 
In the partition display, select the partition you want to use for /
Click the "Change" button just under the partition display and a pop up window will appear so you can fill in the details about the partition - which includes where to mount it, and what kind of file system it will contain.
Repeat this for the partition you want for your home partition, and then for your swap partition.
Check the format box in the display for these new partitions.

*If you need to create new partition from the installer, use the "+" button after selecting some unallocated space instead of "change".

---

### Post by oldfred on 2016-02-21
I like Dennis N create partitions in advance.
Although once I created multiple partitions, one a large data partition which you cannot directly use during installer. But I did not pay attention to which was which and installed Ubuntu to large data partition. Since I had not data in data partition, yet, I was just able to reinstall. But learned good backups are important as users make mistakes, even those that should know better.

Some examples with screen shots. Is System UEFI/gpt or BIOS/MBR? Basic install is the same. And you normally choose default of sda as location of grub2's boot loader.

       How To Install Ubuntu Linux Alongside Windows 10 (UEFI)
[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

