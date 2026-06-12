---
title: "Ubuntu does't boot. How can I access Ubuntu files from Win7?"
date: 2016-08-20
forum: Installation &amp; Upgrades
---

### Post by tudoralexe on 2016-08-20
Hi all,

My adventure with Ubuntu ended abruptely, when one day it simply didnt want to boot anymore.
Luckly I also have Win7 installed so I can still use the machine.

When I boot Ubuntu, it goes into the loading screen, then screen turns and stay black. Any ideas??

Meanwhile, I really need to access some files from my previous Ubuntu desktop folder.
How can I do this from Win7?

Many thanks for your help!

---

### Post by mook765 on 2016-08-20
You need to install a driver in Windows to do that.
Possibility no 1:
[https://sourceforge.net/projects/ext2read/](https://sourceforge.net/projects/ext2read/)
ext2read will give you only read access.Open-source.
Possibility no 2:
[https://www.paragon-software.com/home/extfs-windows/](https://www.paragon-software.com/home/extfs-windows/)
Read+write-access, but speed-limit after 10 days.Freeware/Trial.
Kind regards...

---

### Post by steeldriver on 2016-08-20
It might be easier to use Windows to burn a CD/DVD/USB with a Linux live distribution and use THAT to recover your data

You can use an Ubuntu install disk/USB, but it doesn't have to be - there are several lightweight alternatives such as systemrescuecd

---

### Post by alexanderdg83 on 2016-08-22
On windows, you can also install [Linux Reader]("http://www.diskinternals.com/linux-reader/") if your ubuntu file system is Ext2/Ext3/Ext4, HFS or ReiserFS.

---

### Post by tudoralexe on 2016-08-25
Thanks @alexandrerdr83

That seems like a good sw, but this gives me this error message as I try to access the linux partition:

[http://imgur.com/MBlyRQN](http://imgur.com/MBlyRQN)

---

### Post by tudoralexe on 2016-08-25
for the others: what is ext2/3/4?

---

### Post by mook765 on 2016-08-25
You tried to open the swap-partition.
there is nothing useful for you in swap, and the swap doesn't have a file-system, so you got this error.
In the folder-pane (Left-side of your screenshot) you can still see some folders off your Linux, scroll up and look for the folder named "home" and open this one. There you will find all your documents.
Ext is the name of the used file system, like in Windows you have NTFS, in Linux we have ext with different versions, recent version is ext4.

---

