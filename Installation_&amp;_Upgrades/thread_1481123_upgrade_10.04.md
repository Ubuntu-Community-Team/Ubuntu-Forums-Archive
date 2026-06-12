---
title: "upgrade 10.04"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by ragwing on 2010-05-12
On an upgrade from 9.1 to 10.04 I answered the question incorrectly about replacing the menu.lst. Now my windows XP partition does not work. I edited the menu.list and add the section for windows example, but then I only get a dell hardware test procedure. Can someone tell me what I should do to correct my problem.
Thanks
Rex

---

### Post by dino99 on 2010-05-12
a mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

grub2 is used with lucid, and menu.lst have to be removed, then:

sudo grub-mkconfig
sudo update-grub

hope you have not installed grub over the windoz bootloader :confused:

---

### Post by kansasnoob on 2010-05-12
> **ragwing said:**
> On an upgrade from 9.1 to 10.04 I answered the question incorrectly about replacing the menu.lst. Now my windows XP partition does not work. I edited the menu.list and add the section for windows example, but then I only get a dell hardware test procedure. Can someone tell me what I should do to correct my problem.
Thanks
Rex

It would probably be best if we could see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ragwing on 2010-05-12
> **kansasnoob said:**
> It would probably be best if we could see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Here is the results from the bootinfoscript

  [ATTACH]156627[/ATTACH]


Thanks
Rex

---

### Post by kansasnoob on 2010-05-12
Sorry to take so long, I'm just now looking at this. I'll be back ASAP.

---

### Post by kansasnoob on 2010-05-12
XP is on sda2:

> sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

In legacy grub sda2 = (hd0,1) but your entry says:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

Should edit to this:

```
# This entry added for a non-linux OS on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1
```

---

