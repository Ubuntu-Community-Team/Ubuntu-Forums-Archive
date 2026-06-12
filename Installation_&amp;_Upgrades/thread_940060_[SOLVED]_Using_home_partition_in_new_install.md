---
title: "[SOLVED] Using /home partition in new install"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by greyblitz on 2008-10-06
Since I'm a newbie and just experimenting with Kubuntu linux, I set apart a separate /home partition in case I mess something up. Lo and behold, I mess something up and format the Kubuntu install partition and reinstall it. 

I notice that in my new install, when I try to get to the Documents folder, it is not reading from the /home partition I created last time but is reading from the /home folder in the Kubuntu install. What do I have to do to tell it to read from the /home partition?

At install, do I have to somehow tell the partition manager that I already have a /home partition I want to use?

Thanks very much in advance.

---

### Post by norgur on 2008-10-06
Okay, let's do this the more transparent way. First, you have to find out, how the system has called the partition, you put your /home on. so type into your console:
```
konqueror /media/
``` there you will see various folders, carrying strange names like "sda1" "sdb1" or something. now just klick through the folders until you find the one with your old /home on it. 

Then you have to tell your system that it should mount (which means integrate into the system) this partition on /home.

This information is stored in "/etc/fstab" -a simple text dokument- open it with ```
sudo kedit /etc/fstab
``` don't expect to understand too much from what is written in this file... just search the name of the partition ("sda1" or something) you looked up above. The entrie looks something like that:
```
# /dev/sdb1
UUID=a1954ad6-6653-43cd-9f20-5a8bdaea03b1 /media/sdb1           ext3 relatime        0       2

```
now change this entrie like this:
```
# /dev/sdb1
UUID=a1954ad6-6653-43cd-9f20-5a8bdaea03b1 [COLOR="Red"]/home[/COLOR]           ext3    relatime        0       2

```
to get these changes to work, do a reboot. Now you will have got back your old home directory.

---

### Post by greyblitz on 2008-10-06
Thanks for your reply. I did check it out but it did not work, by that I mean after the reboot I ended up at the terminal saying something failed. I put in a "sudo reboot" command and it brought me back to my lovely GUI! Then I reversed the changes I made.

However, I noticed right after the UID=xxxxxxx, instead of saying "/media/sdb1", it just has "/". 

Also, is there a method to do this prior to installation?

---

### Post by norgur on 2008-10-07
perhaps the fallback to busybox had been fixable...
but of course there is a way to do this during setup. when you get asked about the method, ubuntu should use to partition your system, choose manual. Now you will come to a list with all your partitions. Look for the one which you want to install the kernel on, doubleklick on it and choose "/" as mountpoint. Now you look up the former "home" partition and choose "/home/" as mountpoint. Now you can go on with installing as usual.

---

### Post by Seb71 on 2008-10-07
> **norgur said:**
> Now you look up the former "home" partition and choose "/home/" as mountpoint.

And make sure you choose to NOT format that partition.

Also you should choose the same user name.

---

### Post by greyblitz on 2008-10-07
Exactly what I was looking for, I was hoping it were there! Thank you very much for your help!

---

### Post by greyblitz on 2008-10-08
Wow, I also found out something new! If I go into System Settings --> Advanced --> Disk & Filesystems --> set the correct partition as the /home partition then the same thing will work. I now have all my old settings and files back! Hopefully this can help some others.

---

