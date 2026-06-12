---
title: "[SOLVED] Start with Ubuntu automatically"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by songhk on 2008-01-09
Whenever  I turn on my computer, I see like 

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery)
Ubuntu 7.10, kernel 2.6.20-16-generic
Ubuntu 7.10, kernel 2.6.20-16-generic (recovery)
Ubuntu 7.10 memtest86+
other operating systems
Microsoft Windows 2000 Professional

I deleted Window last week. 

I want to start with Ubuntu(new version) automatically without choosing OS process.(above process). What do I do?  Please help me.

---

### Post by codesplice on 2008-01-09
Go check out your /boot/grub/menu.lst file.  That's where the GRUB boot options hang out.

You'll need sudo privileges to edit it, so
```
$ sudo nano /boot/grub/menu.lst
```

Here are the relevants parts of mine:

```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10



title           Linux Mint, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Mint, kernel memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

Note the "default     0" part.  That's telling GRUB that the first (counting from 0) OS listed should be the default.  The next part (timeout) tells it how many seconds to wait before booting that OS.

Make sure your default is set for your first Ubuntu entry (most likely number 0), and set the timeout to something reasonably quick (not too quick, though, in case you DO need to boot into recovery mode some day).  Two seconds should be sufficient.

While you're at it, you can delete the Windows entry from the menu as well :)

Press CTRL+X to save and exit after editing, and you should be good to go.

---

### Post by pebo on 2008-01-09
Back up your menu.lst:```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```Edit the menu.lst:```
sudo nano /boot/grub/menu.lst
```and delete the windows entry
Change your timeout line to a small amount, e.g. 2
Find the #hiddenmenu line and uncomment it
To access the menu during boot hit Esc during the 2 sec timeout period
You may need to run```
sudo update-grub
```- not sure if that's necessary
Good luck

---

### Post by songhk on 2008-01-10
Thanks for (codesplice) your kind explanation.
I got it very quickly.

And also Thanks Pebo for your reply.


------------------------------------------------------------------------------------------------------------------
> **codesplice said:**
> Go check out your /boot/grub/menu.lst file.  That's where the GRUB boot options hang out.

You'll need sudo privileges to edit it, so
```
$ sudo nano /boot/grub/menu.lst
```

Here are the relevants parts of mine:

```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10



title           Linux Mint, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Mint, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.22-14-generic
boot

title           Linux Mint, kernel memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

Note the "default     0" part.  That's telling GRUB that the first (counting from 0) OS listed should be the default.  The next part (timeout) tells it how many seconds to wait before booting that OS.

Make sure your default is set for your first Ubuntu entry (most likely number 0), and set the timeout to something reasonably quick (not too quick, though, in case you DO need to boot into recovery mode some day).  Two seconds should be sufficient.

While you're at it, you can delete the Windows entry from the menu as well :)

Press CTRL+X to save and exit after editing, and you should be good to go.

-----------------------------------------------------------------------------------------------------------

---

### Post by codesplice on 2008-01-10
Awesome, glad you got it to work :)

---

