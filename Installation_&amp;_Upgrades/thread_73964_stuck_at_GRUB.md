---
title: "stuck at GRUB"
date: 2005-10-10
forum: Installation &amp; Upgrades
---

### Post by motomixon on 2005-10-10
Hello All,
I just finished installing 5.10 RC to my Toshiba A75-s209. The installation completed without errors, but now when booting from the HD, all I get is the text GRUB and the machine stops.

I have a 60 GB HD, with Win XP on the first partition. Then comes 15 GB for Ubuntu, 1 GB swap file and 1 GB VFAT partition. During installation I chose partition hda0,0 (something like that nomenclature...). 

The live CD 5.10 preview seems to work ok, so I could start the machine with that, and edit the ...whatever-i-need-to-do

Can someone tell me how to save this installation? I'm a NOOB. I could start an editor and do "stuff", but don't know where to start.:confused:

---

### Post by mlomker on 2005-10-10
> During installation I chose partition hda0,0 (something like that nomenclature...).

You could try booting the CD and reconfiguring grub.  Here is a [how-to]("http://geodsoft.com/howto/dualboot/grub.htm#install") for that.  I haven't worked with the liveCD very much, but I've done this before with a Knoppix disc.

The grub menu list is /boot/grub/menu.lst.

---

### Post by Jussi Kukkonen on 2005-10-10
Just to make sure: it's 
```
GRUB
```
and not 
```
GRUB>
```
right? AFAIK that means that the problem is not *menu.lst*, but somehow broken master boot record -- grub is not fully loaded. Even with a borked *menu.lst* you should get the grub prompt (*GRUB>*).

> During installation I chose partition hda0,0
I don't know what you were choosing, but (hd0,0) in GRUB lingo means the first partition of the first hard disk... Which would be your Windows partition. (hd0,1) is the second partition on the same disk.

---

### Post by motomixon on 2005-10-11
Thanks Folks,
Using the Live CD I have discovered that there isn't a "/boot/grub/menu.lst", so perhaps Jussi's point is likely correct. I guess I'll do a reinstall.

By the way, maybe part of my problem is working with Breezy B, perhaps for learning purposes I should start with Hoary H??!!

---

### Post by motomixon on 2005-10-11
Oops,
My error.

I did find the menu.lst and it seems complete. I guess my task now is to reinstall GRUB to the MBR.

:???: 

Lotsa luck on that.

---

