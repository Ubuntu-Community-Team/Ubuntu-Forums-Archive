---
title: "Grub 2 Editing help?"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by xpert_conqueror on 2010-01-07
Hello all I'm knew to this site and would like to thank anyone in advance of an responses. Basically I have updated my grub to 2.0 and now I have multiple entries for the same items. I would like to delete these to clean up my menu. I uninstalled the extra kernal. I have 2 entries for both windows xp and the netbook remix. I used to be able to use a gui with my old ubuntu install and even edit the menu.lst file to remove items however grub 2 seems overly complicated! can anyone help me?

---

### Post by -kg- on 2010-01-07
[LIST]
[/LIST]

Try the following in terminal:

```
sudo update-grub
```

If you have deleted the old kernel from the Ubuntu /boot directory, this should get rid of the extra menu items.

XP I'm not so sure about.  If you still end up with two entries for that, post back and there will be other avenues to explore.

---

### Post by oldfred on 2010-01-07
There is no menu.lst. It is now grub.cfg and is generated on every update/change so is not to be directly edited. You can edit a grub file and several other files for custom entries.

More info here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
GRUB 2: A Guide for Users 
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

If you have specific examples of your issues post those and someone should be able to help you.

---

### Post by xpert_conqueror on 2010-01-08
> **oldfred said:**
> There is no menu.lst. It is now grub.cfg and is generated on every update/change so is not to be directly edited. You can edit a grub file and several other files for custom entries.

More info here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Herman's pages on Grub2
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
GRUB 2: A Guide for Users 
[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

If you have specific examples of your issues post those and someone should be able to help you.



I ended up cp the grub.cfg file and editing it manually and then overwriting my original file. not the best practice but never mind. Worked now thanks for your help.

---

