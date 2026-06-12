---
title: "How Do I Format a Previous Linux Drive?"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by RonRock on 2008-01-25
Hello Everyone, New here and of course asking complete strangers for help. Thank You in advance.
I have a computer that has some version of Linux installed. Used computer from a server enviroment. I have a copy of Ubuntu 5.10 that I want to install and get familiar with Linux. 
Trouble is that the drive is already a Linux drive. Aparently Ubuntu will not let me format and install over another OS. Can you tell me how to format this drive and install Ubuntu? 

Again Thank You,
Ron

---

### Post by taurus on 2008-01-25
If you haven't, I would recommend you try something a little newer than the 5.10 version.  That thing is over two years old.  

Assuming you have downloaded and burnt Gutsy, 7.10, boot from it and you can use gparted in System -> Administration to erase all the partition.  Then, format it to ext3.  Now, just click on the install icon on your desktop and tell the installer to use the whole disk.

By the way, what is the spec of your machine?

---

### Post by ajgreeny on 2008-01-25
Version 5.10 is now old and not supported anymore so will not be ideal as a tryout for ubuntu.  I suggest you get a copy of the latest and greatest version, 7.10, and that will be much better.

But to answer your question, get a copy of a gparted live CD or use the ubuntu 5.10 CD if that was a live version (I can't remember).  Run gparted , gnome partition manager and delete the current partitions from the disk to leave it empty.  Now you should be able to install ubuntu using the whole disk, even the 5.10 version if you really must, but I repeat, there is no way you can update it or get new packages to install any more, so it's not a great deal of use to try the distro properly.

---

### Post by RonRock on 2008-01-25
Thanks Guys, I will check into the newer version. This is the disk that I had here, my son used it for a while, now he has moved onto a new version. It's been damn cold here in Iowa and I decided to take the time to play inside. Thank You, I'm sure I'll be back! Ron

---

### Post by RonRock on 2008-01-25
A little more info here. I may have figured out a way. I changed my BIOS to boot from CD rather than HD. It now sees the Ubuntu CD and looks like I'm able to format and repartition. Cool!

---

