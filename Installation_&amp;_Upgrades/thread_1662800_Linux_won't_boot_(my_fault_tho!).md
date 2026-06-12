---
title: "Linux won't boot (my fault tho!)"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by Ebonhawke on 2011-01-08
I was having an issue with my video and audio streams being 'speedy'.  After reading a few dozen threads, I tried a fix that others said worked, however I made a botch of it, and now can't boot unless I use a USB drive.

[http://ubuntuforums.org/showthread.php?t=1662313](http://ubuntuforums.org/showthread.php?t=1662313)

Any way I can fix this without reformatting the entire drive?  Goes through the boot sequence normally, but it seems I may have removed the desktop application when I removed pulseaudio.

(Linux only machine)

---

### Post by wilee-nilee on 2011-01-08
> **Ebonhawke said:**
> I was having an issue with my video and audio streams being 'speedy'.  After reading a few dozen threads, I tried a fix that others said worked, however I made a botch of it, **and now can't boot unless I use a USB drive.**

[http://ubuntuforums.org/showthread.php?t=1662313](http://ubuntuforums.org/showthread.php?t=1662313)

Any way I can fix this without reformatting the entire drive?  Goes through the boot sequence normally, but it seems I may have removed the desktop application when I removed pulseaudio.

(Linux only machine)

Highlighted section, do you mean you can only boot a thumb, not the installed OS?

Can you hold down the shift on power up the computer *_(without the thumb)_* and get the grub menu? If so hit recovery, have the computer plugged in, try the 3rd line dpkg repair first and see if it does. Then choose normal boot log in then run sudo apt-get install ubuntu-desktop

I'm assuming your using ubuntu put in the correct desktop if it isn't in the sudo line. after that  type startx to see if you get in.

If you are using the thumb to boot into the installed Ubuntu then do this. So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by Ebonhawke on 2011-01-08
[I]Clueless newbie alert!

[/I]I was able to get into the GRUB menu and run the latest kernel in recovery mode, selected the dpkg repair, and then selected normal boot.  This dropped me to a shell, and when I typed 'startx' it prompted me for a password.  I tried the password I used for using update/synaptic manager but it didn't work?

---

### Post by Ebonhawke on 2011-01-08
> **Ebonhawke said:**
> [I]Clueless newbie alert!

[/I]I was able to get into the GRUB menu and run the latest kernel in recovery mode, selected the dpkg repair, and then selected normal boot.  This dropped me to a shell, and when I typed 'startx' it prompted me for a password.  I tried the password I used for using update/synaptic manager but it didn't work?

OK - let me try to follow the actual instructions, since I missed the desktop download :P

---

### Post by Ebonhawke on 2011-01-08
OK, ran the install for ubuntu desktop and can now successfully boot into my computer!

Now - to figure out why my video and audio are in fast forward mode!

---

