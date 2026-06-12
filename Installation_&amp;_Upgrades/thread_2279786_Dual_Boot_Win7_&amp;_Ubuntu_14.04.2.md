---
title: "Dual Boot Win7 &amp; Ubuntu 14.04.2"
date: 2015-05-26
forum: Installation &amp; Upgrades
---

### Post by ronnie8 on 2015-05-26
I downloaded Ubuntu 14.04.2 and have Win7 on my laptop im wanting to install Ubuntu to probably use as my main OS but still want Win7 Everytime i goto Shrink the volume in win7 then try installing it says no root folder or something not really sure then it directs me to install it in win7 but i dont see any options and has me restart my laptop and goes back to loading it from the disc and this keeps happening over and over again. not sure if its because i dont have my laptop plugged into a power source and no internet connection. Any help? Normally i can do this cause im pretty good with computers but this i cannot figure out for some reason :/ plz help

---

### Post by Ben_Shaver on 2015-05-26
So, in Windows 7 you're trying to shrink the partition that has Ubuntu on it? Or is this from the Ubuntu installation menu? Perhaps pictures of this? I'd need more details before I could give a thorough response.

---

### Post by Bucky Ball on 2015-05-26
How are you trying to shrink the Win7 partition, presuming that is what you are trying to do? Do NOT resize it using Gparted from the Ubuntu live media. That has a good chance of screwing your Win install.

Do you have an area of unallocated, free space on the drive to create the Ubuntu install? It needs free space (do not make partitions for the Ubuntu install using Windows) to install to.

---

### Post by ronnie8 on 2015-05-26
Im using Disk Management Shrunk C: made a 30Gb partition just now then deleted the Volume and now it says 30 gb unallocated space and I cant do pics right now unless theres a way to screenshot on win7?? And i dont have the ubuntu install disk with me ill have to wait until i get home to see what it says

---

### Post by Ben_Shaver on 2015-05-26
Why aren't you simply choosing the "install alongside *insert operating system here*" option? It's much easier, and doesn't require that much tampering with partitions...

---

### Post by ronnie8 on 2015-05-26
Cause i didnt see that option.. Ill post pics when i get off work

---

### Post by Ben_Shaver on 2015-05-26
Ah, right, right, sorry. So, you have 30gb of just empty space now... You're going to have to choose the "Something else" option, you're going to need to format the empty space as ext4 on the next screen, and flag/mark it with a forward slash (/). Hit continue and you should be good.

---

### Post by oldfred on 2015-05-26
Almost all Windows 7 systems use all 4 primary MBR partitions, so you do not get the along side option.

       Shrinking a Windows Vista/7/8 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)


 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

Be sure to create recovery DVD(s) first. And a Windows repair CD.
      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

---

