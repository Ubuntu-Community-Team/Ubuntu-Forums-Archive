---
title: "Partition Help"
date: 2005-11-27
forum: Installation &amp; Upgrades
---

### Post by kgilkerson on 2005-11-27
Hi, this is my first post. I am running Win2000 on an old AMD processor. I'm pretty new to linux. I am going to install Ubuntu and I want it to duel boot with Win2000. I searched the forums and I got my game plan down except for one thing. I know I have to partition my HDD to let Ubuntu install, I just never figured out from the forums how to actually do the partitioning . Should I use software from the Internet (shareware?), the Win2000 CD, or will the Ubuntu installer do it for me. My win2000 is on NTFS so I want a FAT32 exchange partiton in addition to the FAT32 partition for Ubuntu. All responses would be greatly appreciated. Thanks alot!

---

### Post by bwog on 2005-11-27
The ubuntu installer can resize the Windows partition for you, Check how much space you have left there and defragment it. When the installer has made the windows partition smaller, you have some space left to install ubuntu. When you dont understand what you should do, come back here and ask a new question. Good luck.

Make an ext3 partition instead of FAT. Dont use windows software for the partitioning.

---

### Post by kgilkerson on 2005-11-27
So if I under stand you correctly, Ubuntu will resize the windows partition and make a partition for itself. One more question, Will the Ubuntu installer make the "exchange" partition that I want also? Because that would be sweet.

Thanks for your time,
Ken Gilkerson

---

### Post by yesplease on 2005-11-27
The installer wiil make free space (by making windows partition smaller). Now you can select this free space and make an ext3 partition on it of the size you want, So you can leave some space free for a third partition. 

If this 3rd partition is fat32 I would make it after installing ubuntu (because I saw that fat gave a problem during install once).

However, you may not need an exchange partition, you can read windows from ubuntu and the files on the ext3 partition from windows (with the program explore2fs)

---

### Post by kgilkerson on 2005-11-27
The people on this forum might just be the nicest poeple I've ever meet. Thanks alot! 
Wish me luck.

---

### Post by majkmil on 2005-11-27
Does thi work the same for Power pc (mac)? Do I need to use the live cd? I really don't want do mess with my OSX partition. I tried once but was confused. When I got to the partiotion phase it recognised my mac OS partition. Do I EDIT this one to resize? Is there anything I should know before I try this? Sorry about all the questions.

---

### Post by yesplease on 2005-11-27
@majkmil: it is probably roughly the same, but dont take my word for it, search the ppc/mac forum [http://ubuntuforums.org/forumdisplay.php?f=95](http://ubuntuforums.org/forumdisplay.php?f=95) and ask a question there if you cant find it.

It is also better to start your own thread if you have a question, good luck.

---

