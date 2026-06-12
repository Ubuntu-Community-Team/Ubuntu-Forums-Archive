---
title: "reordering Grub"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by mitchellholt on 2008-09-25
I installed Ubuntu 8.04 on my laptop after installing vista and i installed the grub boot manager. is there way I can make the first option, the one that goes automatically if you don't hit anything, Vista instead of ubuntu?? Ubuntu noob please help!

---

### Post by Idefix82 on 2008-09-25
Yes, it's simple. Open the terminal, and type in the following:
```

cd /boot/grub
sudo cp menu.lst menu.lst.bak
gksudo gedit menu.lst
```
This will open a text editor with the file which contains the configuration of your boot manager. Scroll to the bottom of the file and find an entry which looks like this:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Microsoft Windows XP Professional

```
or something similar. Cut this bit including everything underneath it and paste it above the entry which looks like 
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=cd29e314-6005-4acd-bf45-06b3fcee5c23 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
quiet
```

Finally, you can also remove the bit with "title  Other operating system"

However, all that is unnecessary if you merely want Windows to be the option which is selected by default. This can be achieved even simpler. You need to post the last bit of your menu.lst (after the line "## ## End default options ##") if you want me to tell you how you change the default selection.

---

### Post by mitchellholt on 2008-10-27
thank you. sorry it took me so long to respond. my vista took a dump so i've just been using ubuntu all the time

---

