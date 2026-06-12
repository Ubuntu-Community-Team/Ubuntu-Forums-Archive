---
title: "No more room in /boot"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by yizrahomme on 2013-02-25
Hi,
New to Linux, I run the update-manager, and get the message that there's no more room in /boot.  This is interesting, as I do recall having to update the kernel 'back in the day', but haven't done so this time.  Anyway .. 

```
root@amypond:/boot# ls -lrt *3.*
-rw------- 1 root root  2901710 oct.   9 20:54 System.map-3.5.0-17-generic
-rw-r--r-- 1 root root   147884 oct.   9 20:54 config-3.5.0-17-generic
-rw-r--r-- 1 root root   844882 oct.   9 20:54 abi-3.5.0-17-generic
-rw-r--r-- 1 root root  5129040 oct.  17 18:12 vmlinuz-3.5.0-17-generic
-rw------- 1 root root  5132592 nov.  13 18:10 vmlinuz-3.5.0-19-generic
-rw------- 1 root root  2902610 nov.  13 18:10 System.map-3.5.0-19-generic
-rw-r--r-- 1 root root   147847 nov.  13 18:10 config-3.5.0-19-generic
-rw-r--r-- 1 root root   845342 nov.  13 18:10 abi-3.5.0-19-generic
-rw------- 1 root root  5133840 déc.  11 19:14 vmlinuz-3.5.0-21-generic
-rw------- 1 root root  2903614 déc.  11 19:14 System.map-3.5.0-21-generic
-rw-r--r-- 1 root root   147871 déc.  11 19:14 config-3.5.0-21-generic
-rw-r--r-- 1 root root   848069 déc.  11 19:14 abi-3.5.0-21-generic
-rw-r--r-- 1 root root 23631506 déc.  12 14:40 initrd.img-3.5.0-17-generic
-rw-r--r-- 1 root root 23635076 déc.  12 14:46 initrd.img-3.5.0-19-generic
-rw-r--r-- 1 root root 23639528 déc.  19 10:13 initrd.img-3.5.0-21-generic
-rw------- 1 root root  5134960 janv.  8 22:09 vmlinuz-3.5.0-22-generic
-rw------- 1 root root  2904407 janv.  8 22:09 System.map-3.5.0-22-generic
-rw-r--r-- 1 root root   147871 janv.  8 22:09 config-3.5.0-22-generic
-rw-r--r-- 1 root root   848290 janv.  8 22:09 abi-3.5.0-22-generic
-rw-r--r-- 1 root root 23647435 janv. 22 11:17 initrd.img-3.5.0-22-generic
-rw------- 1 root root  5134032 janv. 24 13:38 vmlinuz-3.5.0-23-generic
-rw------- 1 root root  2904246 janv. 24 13:38 System.map-3.5.0-23-generic
-rw-r--r-- 1 root root   147871 janv. 24 13:38 config-3.5.0-23-generic
-rw-r--r-- 1 root root   848290 janv. 24 13:38 abi-3.5.0-23-generic
-rw-r--r-- 1 root root 23647872 janv. 25 22:14 initrd.img-3.5.0-23-generic
-rw------- 1 root root  5138608 févr.  7 02:13 vmlinuz-3.5.0-24-generic
-rw------- 1 root root  2905147 févr.  7 02:13 System.map-3.5.0-24-generic
-rw-r--r-- 1 root root   147944 févr.  7 02:13 config-3.5.0-24-generic
-rw-r--r-- 1 root root   849836 févr.  7 02:13 abi-3.5.0-24-generic
-rw-r--r-- 1 root root 23660962 févr. 18 10:29 initrd.img-3.5.0-24-generic
```


OK, so I'm guessing that I can sudo apt-get remove say, all but the last two?  But what?  Do I delete the kernels I don't need, and leave the images, or can I delete the vmlinuz files as well as the img?

Thank you in advance.

---

### Post by schragge on 2013-02-25
initrd images are worthless without the kernel they belong to.
 
Package names you're looking for, are like *linux-image-VERSION*. They contain all files related to specific kernel: vmlinuz-VERSION, initrd.img-VERSION etc.

I'd be scripting the removal like this.
```

#!/bin/sh
prev=`readlink /vmlinuz.old` && prev=linux-image-${prev#*-}+
exec sudo apt-get purge '^linux-image-[0-9]' linux-image-`uname -r`+ $prev

```

---

### Post by yizrahomme on 2013-02-25
> **schragge said:**
> initrd images are worthless without the kernel they belong to.
 
Package names you're looking for, are like *linux-image-VERSION*. They contain all files related to specific kernel: vmlinuz-VERSION, initrd.img-VERSION etc.

Forgive my being obtuse, but.. I don't understand.

```
sudo apt-get remove linux-image-3.5.0-17-generic 

```
..for example?

---

### Post by schragge on 2013-02-25
Yes, exactly. I've updated my post with an example of a shell script.

---

### Post by Elfy on 2013-02-25
If you're not sure you should have synaptic installed - it'll be in the System menu.

Go there, then in the quick filter box put 3.5.0-2

it'll list all the kernel files you've got installed.

Click on Installed Version - it'll sort them for you. 

Keep the newest couple of version - select the others and mark for complete removal.

---

### Post by yizrahomme on 2013-02-25
> **Elfy said:**
> If you're not sure you should have synaptic installed - it'll be in the System menu.

Go there, then in the quick filter box put 3.5.0-2

it'll list all the kernel files you've got installed.

Click on Installed Version - it'll sort them for you. 

Keep the newest couple of version - select the others and mark for complete removal.


Thank you all - it's fixed, and I can now update.

---

### Post by dino99 on 2013-02-25
the easy way:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

---

### Post by Elfy on 2013-02-25
> **dino99 said:**
> the easy way:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

How do those commands remove old kernels? 

I recently cleared a load of old kernels - there were some packages to autoremove - none of which had anything at all to do with the kernel. 

Old kernel packages - 

linux-headers-3.5.0-21
linux-headers-3.5.0-21-generic
linux-headers-3.5.0-22
linux-headers-3.5.0-22-generic
linux-headers-3.5.0-23
linux-headers-3.5.0-23-generic
linux-image-3.5.0-21-generic
linux-image-3.5.0-22-generic
linux-image-3.5.0-23-generic
linux-image-extra-3.5.0-21-generic
linux-image-extra-3.5.0-22-generic
linux-image-extra-3.5.0-23-generic

Packages autoremove wants remove - 

nvidia-settings
python-xkit
screen-resolution-extra

---

### Post by SeijiSensei on 2013-02-25
Is this worthy of a bug report?  Why doesn't the installer automatically delete the (N-2)th or earlier kernels when installing a new one?  I see people with this problem all the time and have encountered it myself.  In a default installation, /boot is on the same filesystem as / so that space usually isn't at a premium.  For people like me who use a separate partition for /boot on dual-boot systems, it's a pain in the neck that old kernels are allowed to accumulate over time.

---

### Post by arpanaut on 2013-02-25
> For people like me who use a separate partition for /boot on dual-boot  systems, it's a pain in the neck that old kernels are allowed to  accumulate over time.

I would assume that it is believed that if someone is advanced enough to use a separate /boot partition, then they would know that the maintenance of said partition would be their responsibility.  It is not the default, so it is not the developers who need to do the extra work to make it work as a few advanced users desire.  A bug  might be reported, but I would expect it to be marked as "Wish-List"

My 2 cents worth.

---

### Post by SeijiSensei on 2013-02-25
I just don't see the value of having half-a-dozen kernel images and their associated files kept around on the average Ubuntu workstation.  Surely if something stops working after a kernel update, reverting to the (N-1)th or at worst (N-2)th kernel should fix the problem.  The OP has six kernels installed.  Isn't that a bit excessive?

---

### Post by schragge on 2013-02-25
And the OP doesn't have separate /boot partition. Instead, he has a WUBI installation which is also space-constrained, but targeted specifically to new users.

---

