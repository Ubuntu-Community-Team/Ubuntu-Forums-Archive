---
title: "Installation problem"
date: 2016-01-18
forum: Installation &amp; Upgrades
---

### Post by jrdeahl on 2016-01-18
I, newbie!

New Dell refurbished notebook. It has windows 7 Pro on it.

I partitioned hard drive for another 89gb next to the win 7. Set it active and formatted NTFS.

When I started the DVD Ubuntu 14 disk and tried the install, no matter what partition I choose it says "No root file system".

Help

John

---

### Post by grahammechanical on 2016-01-18
> it says "No root file system".

Is this on restart after the installation of Ubuntu has been completed? I do not think that Ubuntu will install on to an NTFS partition. Are you using the something Else option and instructing the installer to format the partition?

Ubuntu needs a minimum of 2 partitions. One for Ubuntu formatted as Ext4. The other as swap. It is best to use Gparted from the Ubuntu live session to create these 2 partitions from unallocated space and then install Ubuntu to them.

My advice would be to delete that partition from Windows using a Windows utility to create unallocated space and then load Windows a couple of times to make sure it is working and then defrag Windows a couple of times, restarting each time. Also use Windows utilities to do this.

Regards.

---

### Post by jrdeahl on 2016-01-18
It is a new install and used the other type. 

I did the new partition and set active, after it had done the same thing with an unpartitioned space.

---

### Post by yancek on 2016-01-18
> I partitioned hard drive for another 89gb next to the win 7. Set it active and formatted NTFS.

First mistake.  You might install a Linux system on a proprietary ntfs filesystem but if you do, it won't work. 
You do not need to set any Linux partition as active, that is only needed for windows.  If you set the Linux partition as active and leave it, you won't be able to boot windows.

I'd agree with the suggestion above to just leave unallocated space as you will need to format as a Linux filesystem and windows is not capable of doing that.

> When I started the DVD Ubuntu 14 disk and tried the install, no matter what partition I choose it says "No root file system".


You need to select that in the Edit options.  Take a look at the link below, scroll about half way down the page for instructions on dual boot installs.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by jrdeahl on 2016-01-18
I went away from the notebook for a while. 

Read your post and the link wasn't even close to what I had seen before.

I just booted the ISO DVD and then had a choice between "over write entire disk" or "something else". I clicked on the "something else", 
since I did not want to destroy the win 7, and the next thing was a screen that wanted me to chose where to install. Everything I tried 
gave me that error.

None of the links in the link, or any others were an option.

---

### Post by oldfred on 2016-01-18
Post this from terminal in live installer.

       sudo parted /dev/sda unit s print

---

