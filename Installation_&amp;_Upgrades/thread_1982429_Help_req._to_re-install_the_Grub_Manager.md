---
title: "Help req. to re-install the Grub Manager"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by Saurabhdua on 2012-05-18
Hello Folks!

I have gone through the following link in order to bring back the Grub Manager::

[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

Result from sudo fdisk -l have shown the following Outcome for my case::

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa8a8a8a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2805    22531131    7  HPFS/NTFS
/dev/sda2            2806        4998    17613825    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5            2806        4901    16832512   83  Linux
/dev/sda6            4901        4998      780288   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

Now, I have an apprehension for running the next set of commands.

So, Should I punch in the leftovers by following /sda5 OR /sda2?

Please help steer me through the next set of commands & alleviate the fear of losing Windows XP again..! :-|

---

### Post by kc1di on 2012-05-18
you can make it easy on your self and install boot repair 
found here it will fix it for you. 

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by darkod on 2012-05-18
Or you can make it even easier and by the time you install boot-repair you will reinstall grub2. :)

```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

The linux partition is sda5, like it says in fdisk. sda2 is the extended partition.

---

### Post by Saurabhdua on 2012-05-20
Hello Darkod!

By using your set of commands, Iam not yet able to scour the Windows XP option that comes listed within the Grub Manager..!? Instead, the "Grub-Manager" has started showing up some BOGUS entries related to Ubuntu 9.04..!? Don know how to showcase the "Weird" behavior within the Grub Manager screen..!?

---

### Post by wilee-nilee on 2012-05-20
> **Saurabhdua said:**
> Hello Darkod!

By using your set of commands, Iam not yet able to scour the Windows XP option that comes listed within the Grub Manager..!? Instead, the "Grub-Manager" has started showing up some BOGUS entries related to Ubuntu 9.04..!? Don know how to showcase the "Weird" behavior within the Grub Manager screen..!?

Download this script, extract it to the desktop and run the command. Then copy and paste the whole results.txt to a reply. When you open the reply hit the # in the reply panel to generate code tags and paste between.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by Saurabhdua on 2012-05-20
I don know what you are talking about..!? Heck with Ubuntu! Only the characters within the movie Avatar or alike can type & use such commands :-\

Going for a complete FORMAT of my Hard Drive with Windows XP now being my only choice.

Good Bye...

---

### Post by wilee-nilee on 2012-05-20
> **Saurabhdua said:**
> I don know what you are talking about..!? Heck with Ubuntu! Only the characters within the movie Avatar or alike can type & use such commands :-\

Going for a complete FORMAT of my Hard Drive with Windows XP now being my only choice.

Good Bye...

Sorry this seemed not understandable, we would be glad to work with you. :)

You are welcome to PM me if you need help in this thread.

---

### Post by darkod on 2012-05-20
In case you are still interested, if you believe the grub2 boot menu is wrong, you can try an update it in terminal with:
sudo update-grub

You never even mentioned what version of ubuntu are you running.

---

