---
title: "Trouble installing xubuntu with unetbootin"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by neuxioz on 2011-03-13
I am having trouble with installing xubuntu on my flash stick (4gb) using unetbootin. It managed to copy all the xubuntu files and install the bootloader on to my usb, but once i reboot from my usb stick, all I get is a blank screen....:confused:

---

### Post by neuxioz on 2011-03-13
[SIZE=2]OK, I managed to install xubuntu (using start up disk manager), but when i logged into xubuntu, i cannot see any of my other partitions (except for the file system xubuntu is on). Any suggestions?[/SIZE]

---

### Post by wilee-nilee on 2011-03-13
> **neuxioz said:**
> [SIZE=2]OK, I managed to install xubuntu (using start up disk manager), but when i logged into xubuntu, i cannot see any of my other partitions (except for the file system xubuntu is on). Any suggestions?[/SIZE]

Open a terminal in Xubuntu and run this comand and post the results.
sudo fdisk -lu

we are looking for something like this.
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    83888127    41943040    7  HPFS/NTFS
/dev/sda2        83894270   312580095   114342913    5  Extended
/dev/sda5       254951613   308369407    26708897+  83  Linux
/dev/sda6       308371456   312580095     2104320   82  Linux swap / Solaris
/dev/sda7        83894272   213891071    64998400   83  Linux

---

### Post by neuxioz on 2011-03-13
> **wilee-nilee said:**
> Open a terminal in Xubuntu and run this comand and post the results.
sudo fdisk -lu

we are looking for something like this.
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    83888127    41943040    7  HPFS/NTFS
/dev/sda2        83894270   312580095   114342913    5  Extended
/dev/sda5       254951613   308369407    26708897+  83  Linux
/dev/sda6       308371456   312580095     2104320   82  Linux swap / Solaris
/dev/sda7        83894272   213891071    64998400   83  Linux

It showed nothing......
see attachment

---

### Post by wilee-nilee on 2011-03-13
Hmm that is strange the command works without the sudo. My general route here is a screenshot of gparted or clicking on the bootscript in my signature, as far as what I need to work with. If you decide to post the script you can attach it like you did before, or post it in code tags, with a click on the # in the reply panel to make them; to wrap the text

---

### Post by neuxioz on 2011-03-13
> **neuxioz said:**
> It showed nothing......
see attachment

OK I think I get it now. It turns out that Xubuntu manages partitions a little bit differently from ubuntu (xubuntu treats them as remote filesystems). For ubuntu you simply go to places -> your partitions but Xubuntu you go to system -> gigolo to view all of your partitions.:D

---

### Post by wilee-nilee on 2011-03-13
> **neuxioz said:**
> OK I think I get it now. It turns out that Xubuntu manages partitions a little bit differently from ubuntu (xubuntu treats them as remote filesystems). For ubuntu you simply go to places -> your partitions but Xubuntu you go to system -> gigolo to view all of your partitions.:D

Cool, it has been awhile since I used Xubuntu, I just go for the terminal first, even though it's not necessarily where I always go, I like a nice shiny gui as much as the next person.:)

---

