---
title: "Ubuntu partition deleted.. urgent"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by ziikutv on 2010-12-19
Hello,

I was looking for an OS that is light and can be used to surf to watch movies etc. For that, I needed some softwares to be installed on that OS.. I installed Ubuntu, hoping it would would be compatible... it wasn't.

I logged in Windows 7.. and deleted the partition directly. I usually put my pc in sleep mode so I did not realize that I just screwed myself. 

Yesterday, I restarted my pc and I get the following message

> No partition
Grub rescue>

Note, its not exactly like that, the first line.. I dont remember exactly what it said but it did say no partition found.



Anyways, I know the solution. Insert the windows 7 disc, boot off of it.. goto the setup.. use the CMD.. you know the rest..

The problem is that I can't boot off of the DVD... its because my DVD Drive is messed up... I cannot read any DVD.. so I guess I'll have to get a new DVD Drive..

I am wondering though, if there is another solution.. I know the Grub info is stored on my harddrive.. can't I plugin in my harddrive in my laptop (using some wire that will make the harddrive act like a usb device.. or like an external harddrive).. and then delete the MBR or what ever its called..

If I do that, will my windows 7 be corrupted?

Please let me know. My Pc is really old.. I added too much stuff and don't really want to add a DVD drive.. if I don't need to.

Thanks

---

### Post by wilee-nilee on 2010-12-19
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

There is a per-session boot from menu key prompt as if you were going to the bios hit at powering on mine is f12 yours may be different, like esc.

---

### Post by amsterdamharu on 2010-12-19
You can boot from a win 7 CD and restore boot sector but I don't know how because I don't have Windows. You may have better luck on a Windows forum.

Or

If you only deleted the partition than it should be easy to recover it with testdisk.

Boot from a live cd -> open a terminal -> copy and paste the following commands:

```
sudo apt-get install testdisk
```

close all the windows and log out (Not reboot)

press control + alt + f1 and type the following commands:
```
sudo service stop gdm
sudo testdisk
```

When testdisk is done restoring your partition you can exit it and press control + alt + delete to reboot.

---

### Post by wilee-nilee on 2010-12-19
> **amsterdamharu said:**
> You can boot from a win 7 CD and restore boot sector but I don't know how because I don't have Windows. You may have better luck on a Windows forum.

Or

If you only deleted the partition than it should be easy to recover it with testdisk.

Boot from a live cd -> open a terminal -> copy and paste the following commands:

```
sudo apt-get install testdisk
```

close all the windows and log out (Not reboot)

press control + alt + f1 and type the following commands:
```
sudo service stop gdm
sudo testdisk
```

When testdisk is done restoring your partition you can exit it and press control + alt + delete to reboot.

I believe the partition was deleted on purpose, they just want W7 to boot now I think.

---

### Post by amsterdamharu on 2010-12-19
Restoring the partition makes the /boot directory available again and makes the computer grub bootable again but you're still stuck with the Ubuntu partitions. 

If you want to get rid of Ubuntu and it's partitions you need Windows 7 to restore the mbr (boot with windows 7 CD).

---

### Post by psusi on 2010-12-19
You can have the grub rescue prompt boot your windows install.  Type ls to see what partitions are detected.  Your windows install is probably in (hd0,1).  If so, enter the following:

```

set root=(hd0,1)
chainloader +1
boot

```

---

### Post by Quackers on 2010-12-20
Installing Lilo will do it (from the Live usb).
See post #3 here
[http://ubuntuforums.org/showthread.php?t=1643408&highlight=lilo](http://ubuntuforums.org/showthread.php?t=1643408&highlight=lilo)

---

### Post by ziikutv on 2010-12-20
Alright guys.
Thanks for the effort

I ended up buying a new DVD Rom drive, making a recovery disc and then fixing the issue.

Thanks.

---

### Post by bubblew on 2010-12-21
i need help, while i was fixing my vista and ubuntu partition (using GParted) ... i've accidentally deleted the whole thing, now the partition is unallocated and i don't know what to do

should i create a new partition to recover the files? or use testdisk?

thanks

---

### Post by amsterdamharu on 2010-12-21
I suggest try testdisk from a live CD but if you wrote data to a new partition some of the data is gone.

If your disk contained personal data then stop writhing to that disk and try to recover the old partition table with testdisk.

---

