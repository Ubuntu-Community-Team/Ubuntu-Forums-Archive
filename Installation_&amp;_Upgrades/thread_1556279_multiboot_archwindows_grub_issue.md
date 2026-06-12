---
title: "multiboot arch/windows grub issue"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by Tweisted on 2010-08-19
Hello everyone, im having some issues regarding grub and multi booting arch linux with windows xp, on 2 seperate hard drives. Ill try to provide as much information as I can.

I have 2x 1tb hard drives. The first one has windows xp untouched, and the second has arch linux.

What I was trying to do was dual boot arch and windows together, and have the drive with arch installed let me select which OS to load, that being arch or windows. I installed windows on the first drive with no errors at all, I then proceeded to install arch linux on the second drive, and when i rebooted, i was greeted with grub with arch linux/windows to choose from, but neither would boot. Arch gave me grub error 17 and windows gave me grub error 13. Both hard drives were plugged in while doing both installs. One drive has windows xp, and works perfectly, the other has arch linux, with a grub menu with the ability to select either arch or windows, but unable to load either one.

Here is a link to the pastebin

[http://pastebin.com/iEjH53YY](http://pastebin.com/iEjH53YY)

there is the grub menu I took from arch linux, with both OS's setup on there. I hope that helps. Im not sure if i change a few things in grub menu if that would help or not? Not quite sure. Any help would be much appreciated. If I made something unclear or you need more information please let me know. 

Thank you:D

---

### Post by snowpine on 2010-08-19
Personally I would try changing the Arch entries from "root (hd1,0)" to "root (hd0,0)", and vice-versa for the Windows entry.

---

### Post by Tweisted on 2010-08-19
(hd1,0)" to "root (hd0,0)

So your saying change (hd1,0) on root to (hd0,0)

and for windows to (hd1,0)?

And thank you for the help and reply much appreciated.

---

### Post by snowpine on 2010-08-19
Correct; hd0 means "the first hard drive" and hd1 means "the second hard drive".

The installer thought the Arch drive was the second hard drive, however when you boot from that drive, it assumes it is the first drive.

At least I think that's what's going on, it is worth a try. :)

---

### Post by Tweisted on 2010-08-19
Okay thank you, I will try that, and report back with the results. thanks alot :D

---

### Post by Tweisted on 2010-08-19
(Update)

Okay, so changing the root and windows grub lists worked sorta

I got arch booting up perfectly and is running fine. But windows still is not loading.

When I tell windows to load it shows me this
'Booting Windows'
rootnoverify (hd1,0)
makeactive
chainloader +1

I was thinking maybe changing hd1,0, to hd1,1 maybe? 

Thank you for all your help.:D

---

### Post by snowpine on 2010-08-19
No problem! Since I am not an Arch user, I will refer you to this page for more info on dual booting with Windows: 

[http://wiki.archlinux.org/index.php/GRUB](http://wiki.archlinux.org/index.php/GRUB)

---

### Post by Tweisted on 2010-08-19
awesome! thanks, ill report back if any updates.

---

### Post by Tweisted on 2010-08-19
I followed the guide on Arch, and all I needed to do was add the mapping into grubs menulist since my copy of windows xp was on my second drive and on the first partition. 

Thank you for your help. This can now be marked as Solved.

---

