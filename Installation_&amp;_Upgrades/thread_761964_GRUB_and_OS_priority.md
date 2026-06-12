---
title: "GRUB and OS priority"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by ghostytwofish on 2008-04-21
I have a WinXP machine with two HDs. Ubuntu was recommended to me by a friend, as I'm looking to teach myself Linux. So, I now have an XP machine with Ubuntu on a second HD.

Since I am only just learning Ubuntu, I don't have any real understanding of anything as yet. I'd like to have Grub default to booting to my XP partition instead of the Ubuntu one. Could someone give me some simple steps to follow to accomplish this? 

Thanks so much --

---

### Post by tyblu on 2008-04-21
I used a walkthrough to dual boot Windows XP and Gutsy Gibbons. Googling "how to dual boot windows ubuntu" gives many promising hits:

[hot to dual boot windows and ubuntu]("http://www.google.com/search?hl=en&q=how+to+dual+bot+windows+ubuntu&btnG=Google+Search")

---

### Post by tyblu on 2008-04-21
the basic idea, though, is to partition your harddrive, install an OS on different partitions, then configure your bootloader (GRUB).

---

### Post by lizzard on 2008-04-21
open your menu.lst with an editor.
```
sudo nano /boot/grub/menu.lst
``` and change "default 0" to the according  number of your Windows entry. (You need to count from 0) So if Windows was the 4th entry,  it would be "default 3".

---

### Post by forestpixie on 2008-04-21
The file which you need to modifiy is menu.lst - it's in the boot/grub folder. Before you start you can backup the original just in case. This command does that - cp, you need to do so as root using sudo.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.2104
```

Now that it's backed up you can edit it - this will look more complicated than it actually is until you've done similar a few times. You can edit in terminal or in gedit which is a text editor. 

```
gksudo gedit /boot/grub/menu.lst
```

You now have the file open for editing - near the beginning of the file is a section which looks similar to this, this relates to the default chosen in the mneu list

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
```

Further down the file where it changes, count the instances of 'title' starting from 0
```

## ### ## End Default Options ##
```

Change the default to suit your menu.lst - you must also count the 'title' which is before the actual win boot line. If you're not sure post it here - use this command to show the file in terminal.

```
cat /boot/grub/menu.lst
```

But you'll probably learn more by getting it wrong and changing it to get it right - you could also change the timeout to a bit longer to make sure you have chance to deal with it.

The parts you're changing look like this on my system -

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]default		0[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Red"]timeout		3[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR="Red"]#hiddenmenu[/COLOR]

...

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2559168a-c07a-4117-95be-701030c233e4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2559168a-c07a-4117-95be-701030c233e4 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=2559168a-c07a-4117-95be-701030c233e4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=2559168a-c07a-4117-95be-701030c233e4 ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

If I changed my default to 4 I would have the memtest as the default. If you're hidden menu is uncommented put a # at the front of the line.

---

### Post by zvacet on 2008-04-21
[Here]("http://louboldt.com/ilinuxgrub.htm#xp1st")

---

### Post by ghostytwofish on 2008-04-21
lizzard and forestpixie, TY for the straight up text. I'll implement the fix sometime tonight. :)

---

### Post by ghostytwofish on 2008-04-22
That did the trick, GRUB works fine now, thank you.

Now to get my wireless card to work. :(

---

