---
title: "Uninstall Ubuntu Dual Boot on from Second Hard Drive"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by keeganxvx on 2013-05-15
I just got a desktop PC from my friend that runs a dual boot of Windows Vista and Ubuntu.
He has two hard drives in the computer, C: for windows and D: for Ubuntu.
This is what the disk management looks like:
[IMG]http://i42.tinypic.com/6oo9br.jpg[/IMG]

So, can I still use the EasyBCD Vista bootloader reinstall method and then just delete that D: partition?
The files for D: are still accessible and usable on the Windows boot.

---

### Post by fantab on 2013-05-15
I think Ubuntu is installed with WUBI. You can remove it using 'add/remove software' from Vista, just as you remove any windows program.

---

### Post by keeganxvx on 2013-05-16
It's not, I already checked.

---

### Post by fantab on 2013-05-16
Can you boot into Ubuntu? If yes, then post the output of:

```
sudo fdisk -l
```

from ubuntu and also post a screeshot from GPARTED of your partitions.

---

### Post by keeganxvx on 2013-05-17
[IMG]http://i40.tinypic.com/206er0k.png[/IMG][IMG]http://i40.tinypic.com/2l51q9.png[/IMG]I could also take a screenshot of EasyBCD from Windows.

---

### Post by sudodus on 2013-05-17
Please post the output of the command

```
 cat /etc/mtab
```

It is faster are uses less resources to cut and paste from the terminal window to this editing window instead of attaching screendumps.

In order to make it easy to read, please high-light the text and click on the # icon above this window to mark it with code tags.

---

### Post by keeganxvx on 2013-05-17
[IMG]http://i43.tinypic.com/34yd35i.jpg[/IMG]

from the bootloader path of ubuntu it sounds like it's installed with WUBI, but I don't see it at all when I go to the uninstall program list

---

### Post by sudodus on 2013-05-17
**cat /etc/mtab** would show it.

---

### Post by fantab on 2013-05-17
There is no Ubuntu on those disks. Both Disks are formatted with NTFS and Ubuntu/LInux does not install on NTFS partitions or drives. It is either WUBI or you don' t have Ubuntu.

---

### Post by keeganxvx on 2013-05-17
Actually, I found the /ubuntu folder in the D: drive.

There's an 'uninstall wubi' executable file. Running this will totally uninstall it?

---

### Post by sudodus on 2013-05-17
> **fantab said:**
> I think Ubuntu is installed with WUBI. You can remove it using 'add/remove software' from Vista, just as you remove any windows program.

^ This is the way to remove a wubi installation. ^

---

### Post by fantab on 2013-05-17
Yes it should....

---

### Post by keeganxvx on 2013-05-17
If I try to run the uninstall-wubi file, I get this:
[IMG]http://i39.tinypic.com/ajuo9l.jpg[/IMG]
Which is apparently an error code for when you try to run something with the wrong drive letter, so you have to go into disk management and change it.

But I was looking at the Wubi Guide at [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
and under the manual uninstall guide, I can either use EasyBCD or go into command prompt and run bcdedit and then type *bcdedit /delete {GUID} *to remove it.
So it's essentially doing what EasyBCD does, I guess.

Does this fully uninstall it? I don't want to mess the bootloader or computer up.

---

### Post by keeganxvx on 2013-05-17
[IMG]http://i41.tinypic.com/d8hs6.jpg[/IMG]

---

### Post by keeganxvx on 2013-05-17
So, to my understading, what WUBI does it create a option in the boot menu to boot to Ubuntu.
Using EasyBCD or the bcdedit command removes this option from the menu, only leaving Windows, therefore it boots automatically to Windows.

Ubuntu is only existing as a file within the D: drive which I can just delete,
thus removing Ubuntu entire from the system.

---

### Post by sudodus on 2013-05-18
I think you as much as I do about the wubi installation now :-)

So if you remove

1. the option from the Windows boot menu, and

2. the big file which contains a file system, which holds the Ubuntu installation,

there is not much left (probably nothing that will cause any trouble or occupy any significant disk space).

-o-

Do you want a regular installation of some other flavour of Ubuntu or some other linux distro? For example, if your computer is getting old, the standard flavour of Ubuntu might be slow, but it may work very well with a lighter desktop environment.

Or do you want to continue with only Windows?

---

