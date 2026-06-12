---
title: "Ubuntu 10.10 GRUB fails to load after upgrade."
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by billfreeboy on 2010-12-07
I currently have a Dell Dimension 4100 from 2000 upgraded with an Nvidia Geforce 6200 video card and 160 gig hard drive, I just upgraded to Ubuntu 10.10 from 10.04 and once I restart, I hear a beep come out from my computer speaker, and then displays the following text:

```
GNU GRUB version 1.98+20100804-5ubuntu3

Minimal BASH-like line editing is supported. For the first word,
TAB lists possible command completions.
Anywhere else TAB lists possible device or file completions.

grub>
```

I'm not used to typing in command line, but if anybody has a way around it for me, I'll be pleased. It's Ubuntu or Windows goes back on... or bust.

---

### Post by oldfred on 2010-12-07
Do you know what partition you have installed to? You can manually boot. (hd0,1) = sda1 Change to your partition.

set prefix=(hd0,1)/boot/grub
insmod (hd0,1)/boot/grub/linux.mod # Probably not necessary, but if it returns an error there is no use in proceeding (unless it's already loaded).
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

You also can use ls to list partitions and 
#If on (hd1,1) or sdb1
sh:grub>ls (hd1,1)/
#Should show the links vmlinuz & initrd.img

---

### Post by billfreeboy on 2010-12-07
> **oldfred said:**
> Do you know what partition you have installed to? You can manually boot. (hd0,1) = sda1 Change to your partition.

set prefix=(hd0,1)/boot/grub
insmod (hd0,1)/boot/grub/linux.mod # Probably not necessary, but if it returns an error there is no use in proceeding (unless it's already loaded).
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
boot

You also can use ls to list partitions and 
#If on (hd1,1) or sdb1
sh:grub>ls (hd1,1)/
#Should show the links vmlinuz & initrd.img

I just used ls and my partion is (hd0). I set my prefix and got nothing. I then typed in "linux /vmlinuz root=/dev/sda1 ro"
and got "error:unknown filesystem". What now?

---

### Post by oldfred on 2010-12-07
(hd0) is just the drive, it did not show a partition?

To see where everything is at:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by billfreeboy on 2010-12-07
Actually what came up was (hd0),(hd0,msdos1), and (if i can remember because I'm home now, (fd1) when I tried ls.

---

### Post by oldfred on 2010-12-07
The newest version of grub2 adds the msdos. It think it is optional. the example I gave with hd0,1 then is the correct drive, partition for you to try to boot with.

---

### Post by billfreeboy on 2010-12-11
Craaaaaaaaap... Nothing that I type ends up working... I'll stay on 10.04 for this machine until they can fix the issue.

EDIT: Why can't I mark this thread as done for? lol.

---

### Post by oldfred on 2010-12-11
Without boot script I cannot give specific help.

You can review this and chroot into your system and reinstall grub2.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by billfreeboy on 2010-12-23
I had to do it the other way, I went back to Ubuntu 10.04 on that machine, and now it's completely fine.:p

---

### Post by bornagainpenguin on 2010-12-27
> **billfreeboy said:**
> I had to do it the other way, I went back to Ubuntu 10.04 on that machine, and now it's completely fine.:p

Could you link me to what you did to get 10.04 up and running?  I have the 4100 also but am unable to get past the boot screen in anything beyond Hardy!

--bornagainpenguin

---

