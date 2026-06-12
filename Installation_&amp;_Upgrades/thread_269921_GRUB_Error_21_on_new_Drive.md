---
title: "GRUB Error 21 on new Drive"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by natural_orange on 2006-10-02
I just installed ubunto on an older driver that I pulled of an old computer I had.

I put it in my newer computer as a slave and installed ubunto on to it from the cd.

When i restart the computer it comes up with screen saying:
```

GRUB Loading Stage1.5.

GRUB Loading, please wait....
Error 21

_

```

I know this has probably been posted on like a thousand times, but Im new to Linux/Ubuntu and have no knowledge of anything related to it.

Can anyone explain how to fix this in like really really simple terms? pretty please....

---

### Post by natural_orange on 2006-10-02
I booted from a WinXP install CD and through the recovery console did a "fixmbr" so now i can boot to windows....

---

### Post by griblik on 2006-10-03
Hey there,

I just came to the forums looking for info on the same problem, and I promised myself I'd come back to help if I found the solution.

Error 21 means that Grub can't read the hard drive that you've got Ubuntu installed on. 

In my case, it was because I didn't have it enabled in my bios - weird thing, it's been there for years and I've been running Gentoo off it without any problems so I didn't notice (had my boot partition on the first drive though).

When you boot, go into your bios - usually involves hitting delete or F8, or if you've got a Dell (dude), it could be F2 - it'll say "Press [something] to enter [BIOS or Setup]" in the boot text. Look for the second hard drive and check that it's not marked as "off". Mine was, and changing it to auto fixed the problem.

If you want to try it again (and I recommend it - Ubuntu installed like a dream for me), and you've already installed it once on the second hard drive, you can just reinstall grub by following the instructions here:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351). You don't have to go through the whole Ubuntu install again.

You can always reinstall the windows boot loader as you did before if it doesn't work :)

Hope that helps.

G

---

### Post by natural_orange on 2006-10-04
Thank You....got it to work

anyway to change the default kernel? I want windows to be default not Ubuntu

---

### Post by griblik on 2006-10-04
Simple enough :)

This looks really complicated, but all you're doing is opening a text file with vi, changing a number, and saving it. Job done. I've put a lot of detail in here because I don't know how much you've used linux before. Better to have too much info than too little, I reckon. Hope this helps - if you have any problems, just hit the reply button and I'll pick it up in the morning.

Boot into Ubuntu and open a terminal window. At the prompt, type
> sudo vi /boot/grub/menu.lst

Take time for a deep breath and a thought here; the file you've opened is the one controlling the boot menu. If you get this wrong, you might have to reinstall grub again, so if you're not sure you've got it right, type "ZZ" (capitals - shift+z twice). That quits you out of vi without saving the changes so you can go check what you're doing without fear of breaking things. I do this a lot :)

Navigate around the file with the arrow keys and Page Up/Page Down.

Near the top of the file, there's a line saying

> default 0

That defines what the default option in the menu is. This is the line you want to change. You want it to be Windows.
Towards the bottom of the file after where it says
## ## End Default Options ##
there should be a set of lines beginning
> title Ubuntu, kernel 2.6.15

There will probably be a few sets of these, all beginning "title [Text you see in the boot menu], root something, kernel something else...".

The "default 0" line is what sets the default boot option (which you want to be windows). They're numbered from 0, ie the first title line is 0, the second is 1 etc.

Just change the "0" after "default" at the start of the file to the number of the entry it lists Windows as (ie if Windows is the 4th entry, change "default 0" to "default 3").

To change it, move the cursor up to the "0" with the arrow keys, and press the insert key. Delete and backspace work as you'd expect after that, and you can put the number in. Hit escape to stop editing.

When you've changed it, , type ":wq!"

That should save and quit. Next time you boot, it should have Windows as the default entry.



Example - Here's my grub config - if I were booting windows by default, I'd change "default 0" to "default 3" at the start, as it's the 4th time the "title" elements appears.

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

[Lots of things starting with "#" - these are just comments, they don't actually do anything, so I've deleted them from this post]

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-686
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-27-686 root=/dev/hdb3 ro single
initrd		/boot/initrd.img-2.6.15-27-686
boot


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1


G

---

