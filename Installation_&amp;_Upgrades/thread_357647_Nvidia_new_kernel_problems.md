---
title: "Nvidia new kernel problems"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by FreakTech on 2007-02-09
I am having problems with the new kernel version.  I installed it fine but when I boot from it I get X server errors about my Nvidia Driver being the wrong version.  I can still boot into the old kernel version just fine.  Can anyone help me?

---

### Post by TwistesdTexan on 2007-02-09
I saw the problems with the update yesterday. I waited until today and updated. I will have the weekend to sort things out. I updated and it said that there was a syntex error in my xorg. I went to the grub (I accessed by pressing my Esc key repeatedly when the message was suppose to come up, Grub didn't pause) and sellected a previous Kernel. My boot went fine then. I rebooted and again grub didn't pause but I let the default Kernel load and everything went fine.
Question: Since I choose a different kernel once and acheived a good boot, did my next boot with out a selection use the older Kernel or the new problem child (i've notice a few gliches ie.. Title bars washed out no color even on buttons Max Min Close).
Edit/Delete Message

---

### Post by FreakTech on 2007-02-09
Yes i think your system is defaulting to the old kernel.  Try selecting the new kernel and seeing if you are still having the issues.

---

### Post by TwistesdTexan on 2007-02-09
Here is an update on my small accomplishments. I now have a wait period in grub menu. I edit my grub menu list with  'sudo gedit menu.lst'. I change it so the time out is after the hidden menu line. Here is a copy of the finished grub menu

# menu.lst - See: grub(8#), info grub, update-grub(@8#)
#            grub-install(8#), grub-floppy(8#),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

I've cut out a lopt of the file to save space. This does show the order though.

---

### Post by TwistesdTexan on 2007-02-09
I did another reboot and it selected the new kernel. Not any good with that one. I just posted the fix for the grub timer hope that helps. The # symbols in te ()'s are the ones added to keep it from Smilies. ie..( 8 ) has spaces to keep it from looking like (8).

---

