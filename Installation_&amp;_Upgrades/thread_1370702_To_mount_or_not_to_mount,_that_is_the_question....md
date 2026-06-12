---
title: "To mount or not to mount, that is the question..."
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by Zeone on 2010-01-02
Hey everybody,

I've just bought a HP mini compaq laptop. The laptop doesn't have any CD/DVD "reader". So i was forced to download the .iso file to install ubuntu in addition to Windows XP that was present when i bought it.
To do so i used UNetbootin, and i used my only hard disk as a live CD. But when i wanted to install ubuntu, they told me to create a partition. The problem is that i can't. I have only one partition sda1(nfst) which covers the whole stockage memory, and an empty space(8Mo). I can't acceed to any of the resizing or modifying options to edit the nfst partition. The only options are manage flags and umount. When i click on this one, they tell me : # umount /cdrom : cdrom is busy.

I don't know what to do.
Any help is welcomed!! ;)

---

### Post by bumanie on 2010-01-02
You download the .iso of gparted that can go on a usb stick and pre-partition your drive - it basically allows you to create partitions with the drive unmounted. Have a look [here]("http://gparted.sourceforge.net/liveusb.php").

---

### Post by Zeone on 2010-01-02
Thanks for replying!
I've downloaded the .iso of Gparted. But i don't know what to do with it oO
I've extracted it to the desktop using ubuntu, but how do i launch it?

---

### Post by Zeone on 2010-01-03
Yay! :D
Thank you very much, I've finally insalled Ubuntu yesterday. I launched the Gparted .iso through Unetbootin, and could partition my drive =D.

---

