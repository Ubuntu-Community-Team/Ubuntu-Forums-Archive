---
title: "Configuring Grub with 2 hard drives."
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by dave1507 on 2008-11-15
I've just bought and installed a new 250GB PATA hard drive alongside my old 120GB drive which had XP on it. I did a fresh install of XP on the 250GB drive and formatted the 120GB and put Ubuntu on it. At first I had the new drive as the slave but after I installed ubuntu XP wouldn't boot because it couldn't find NTLDR. So I made the new drive the master and reinstalled XP. Basically my drives look like this:

250GB
---------
XP (20GB NTFS)
GAMES/APPS (180GB NTFS)
BACKUP (<50GB NTFS)

120GB
---------
Windows Swap (4GB FAT32)
Ubuntu Swap (1GB swap)
Ubuntu / (20GB ext3)
Ubuntu /home (20GB ext3)
MUSIC/VIDEOS (~75GB ext3)

At the moment I can only boot into Windows as Grub doesn't appear. If I change my BIOS so the 120GB boots first Grub appears but can't load either operating system. Can anyone tell me where and how grub needs to be installed so I can access both?

I've looked around but can't find anything that looks appropriate for my situation.

Thanks

---

### Post by cdtech on 2008-11-15
You can use your "Live CD" to reinstall the GRUB bootloader. Just open a terminal and type the following:
```
sudo grub
find /boot/grub/stage1
(Use the output from this command in the next command)
root (hd0,1)
setup (hd0)
quit
```

Here is some information on the procedures:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by dave1507 on 2008-11-15
Thanks for the quick reply. I just tried that and it works to get me into linux (there now), but when I select the XP option it says:

```

Starting up...

BOOTMGR is missing

Press ctrl+alt+del to restart

```

This is my entry for XP in menu.lst:

```

title		Windows XP Professional
root 		(hd0,1)
chainloader 	+1

```

Is that wrong?

---

### Post by Pumalite on 2008-11-15
Try this:

title		Windows XP Professional
map             (hd0,0)
map             (hd1,0)
root 		(hd0,1)
chainloader 	+1

---

### Post by cdtech on 2008-11-15
XP should be:
```
title		Windows XP Professional
root 		(hd0,**0**)
chainloader 	+1
```

---

### Post by Pumalite on 2008-11-15
Here is more info on how to boot from 2 hard drives:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by dave1507 on 2008-11-15
> 
title		Windows XP Professional
root 		(hd0,0)
chainloader 	+1


Thanks, that made it work. Silly mistake to make on my part :)

---

### Post by cdtech on 2008-11-15
Not a silly mistake, just a simple one. congrats..:guitar:

---

