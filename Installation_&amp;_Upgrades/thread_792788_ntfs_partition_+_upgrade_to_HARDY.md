---
title: "ntfs partition? + upgrade to HARDY"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by il-chino on 2008-05-13
hello every one
as most of the members here
I'm new ubuntu user
I have two prblems


1 - I installed ubuntu using the whole hard disc (and every thing works fine BTW)
......I packed up my files in my friend's hard disc
......my question is
    ......is it possible to make a new partition with ntfs format? so I can get my files back

2 - I installed ubuntu 7.010     and I have HARDY on CD
     ......how can I upgrade My system to HARDY?


I hope my questions are clear.

---

### Post by Pumalite on 2008-05-13
Did you loose your files while formatting the drive?

---

### Post by il-chino on 2008-05-13
I backed up my files before the formating

no I didn't loose my files
but I need to get them back from my friend

---

### Post by Pumalite on 2008-05-13
Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Resize your partition (right click). You can format the new space ntfs. It takes a while depending on the size of your drive and the number of your files.

---

### Post by il-chino on 2008-05-13
ok
I will try this one later (going out in a while)

what about upgrading

is there any guide site or a full description thread here in this forum

thanks btw
you were a big help for me

---

### Post by Pumalite on 2008-05-13
This might help:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by az on 2008-05-13
Why do you need an NTFS partition?  You can copy your files back onto your Ubuntu computer withouth needing an NTFS partition for them.  I am assuming that you do not have windows on that computer.  Obviously, if you are running windows on another disk, you may want to keep a separate NTFS partition.  

There is an EXT2 driver for windows.  You would be able to read/write to your linux partition from Windows.  [http://www.fs-driver.org/](http://www.fs-driver.org/)

As for upgrading, you will need to upgrade from the net.  You cannot upgrade using the Desktop cd.  You might be able to upgrade using the alternate cd, but you will still need access to the internet to download any package that are not on the cd, for example any packages you installed.

---

### Post by il-chino on 2008-05-15
az
hello my friend
I lost my HARDY cd
so I need to upgrade from net
but
how can I do that

BTW
I searched for upgrade and I gave me this program
Synaptic Package Manager

I clicked on it and got this message:

"Starting without administrative privileges

You will not be able to apply any any changes. But you can still export the marked changes or create a download script for them."

?????????????????

---

