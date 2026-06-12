---
title: "Help!  Install Vista+XP+Ubuntu?"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by Camanalis on 2008-05-24
Hello, I need some help.

I wish to install Windows Vista, Windows XP, and Ubuntu all on the same hard drive and have them all boot from GRUB.

I have an Acer Recovery CD with Windows Vista, a Windows XP Installation disk, and an Ubuntu Live CD.  I can wipe my entire HD and start from scratch if needed.

I am fairly new with Linux, so I will need thourogh instructions.  I thank anyone who will help me, it will be greatly apreciated.

---

### Post by tamoneya on 2008-05-24
well ubuntu unlike the two windows OSes is smart enough to detect other operating systems and to put them into grub for you.  What I would recommend is that you install vista and then xp in any order.  You should tell them to take just part of the harddrive(xp 20GB, vista 40GB) These numbers are very approximate.  It depends on your drive space and how much you will use each OS.  Then install ubuntu and tell it to use all the remaining space.  It will auto configure grub and you should be all set.

---

### Post by Camanalis on 2008-05-24
Ubuntu only saw Vista Last time I attempted this. I need to know how to modify GRUB to show all OS's.

---

### Post by Pumalite on 2008-05-24
You have to edit /boot/grub/menu.lst:
gksudo gedit /boot/grub/menu.lst
The rest depends on your installation.

---

### Post by housam on 2008-05-24
You have to edit the menu.lst file and in win-xp section point the to partition that has grub.
```
gksudo gedit /boot/grub/menu.lst
```

change the following section
```
title		Windows XP
root		[COLOR="Red"](hd0,2)[/COLOR]
savedefault	
makeactive	
chainloader	+1
```



to
```
title		Windows XP
root		[COLOR="Red"](hd0,0)[/COLOR]
savedefault	
makeactive	
chainloader	+1
```


because Windows does not install it's boot loader to the partition it is installed on, but normally to the first partition of the first hard disk.

If it does not work , read [[COLOR="Red"]_this thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=805051")

---

### Post by meierfra. on 2008-05-24
> install vista and then xp in any order

No. XP should be installed before Vista. XP does not recognize Vista and will overwrite the Visa bootloader.

---

