---
title: "Simple Grub question"
date: 2005-06-18
forum: Installation &amp; Upgrades
---

### Post by sfboarders on 2005-06-18
I'm dual booting ubuntu with windows xp. How do I make windows xp the default os to boot too if I don't choose an option? Also why are there so many ubuntu options? Do I need all of them? If not how do I get rid of them? TIA. :)

---

### Post by irusun on 2005-06-18
Edit the grub menu.lst

sudo gedit /boot/grub/menu.lst

There are instructions within the file (set the default number to the corresponding placement of Windows in the list).

While the various options aren't necessary, they could be real handy if anything ever goes wrong.  It may not look pretty, but...

Hope that helps.

---

### Post by sfboarders on 2005-06-22
I just want to make sure I do this right before I edit anything. Below is what I have

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

According to this quote at the top of GRUB

> 
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0


Does that mean I make "savedefault" a "0" like this below and this will make XP the default OS to boot to if I don't choose an option? TIA :)

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
0
makeactive
chainloader	+1

```

---

### Post by Jenda on 2005-06-22
This might help [http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub)

---

### Post by Lunde on 2005-06-22
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
default 4

Here you go!

0 = from top
1 = first in list
2 = Second in list (recovery mode)
3 = Third (memtest86+)
4 = XP

Make sure you dont mess with the timeout so you can't choose from the list

---

### Post by sfboarders on 2005-06-23
Thanks guys for your help. I appreciate the clarification. *raises thumb* :)

---

