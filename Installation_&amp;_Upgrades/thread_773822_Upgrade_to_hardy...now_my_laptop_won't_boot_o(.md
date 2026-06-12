---
title: "Upgrade to hardy...now my laptop won't boot :o("
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by kathrync on 2008-04-29
I upgraded to Hardy yesterday and now I can't get my laptop to boot at all :o( 

I was running Gutsy and that was working fine.  I upgraded via the upgrade manager.  Now one of several things happens when I try to boot...

1:  After the "hit F2 to enter BIOS" and "loading GRUB" screen, the screen will just go completely blank and the computer will hang there

2:  The computer will reach the login screen but will go blank after I have entered my password

3:  The computer will boot up and load GNOME but hang within seconds before I can do anything.  In this case it will sometimes go blank, sometimes the GNOME screen will remain visible but freeze and sometimes I will get a red and white pixellated screen that is also frozen.  This last option is very rare, the computer usually freezes before it gets as far as loading GNOME.

So any thoughts anyone?  I can go back to Gutsy using my boot CD but I would rather avoid that if I can as there are some photos on my HDD that I forgot to back up before I upgraded (yes I am a numpty!).  So if anyone has any other solutions, I would be happy to hear them!

Cheers

Kathryn

---

### Post by bsh on 2008-04-29
i have done this too, but i started with a fresh install of 7.04 and gone through the whole update via internet through 7.04 -> allupdates -> 7.10 -> allupdates -> 8.04 :D
and sometimes the pc stops booting, but unloads ubuntu and reboots fine, if i press ctrl-alt-del. strange.
anyway, you might have problems with your x server setup, try pressing ctrl+alt+f1 or ctrl+alt+f2 to get to a terminal, and reconfigure your x server to vesa, that may help to get to the gui first.
but you might try a complete fresh install. boot with the live cd, and backup your photos (vreate a new partition, or just burn them to CD's, or put them onto a pendrive, etc.), then do a fresh install.

---

### Post by kathrync on 2008-04-29
Thanks :)

I have tried to reconfigure the x server (using dpkg-reconfigure xserver-xorg) by booting into the recovery mode and accessing the command line from there .  It lets me configure the keyboard and mouse set-up but there is no mention of video to change to vesa.  Have I missed something?  I'm finding it hard to work out what I am doing as I am not used to not having the GUI available to me!

K

---

