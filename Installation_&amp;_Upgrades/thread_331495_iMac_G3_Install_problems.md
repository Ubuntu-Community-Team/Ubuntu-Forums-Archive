---
title: "iMac G3 Install problems"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by D_Murdock on 2007-01-04
I have an older iMac G3. I recently tried booting the latest Edgy of Ubuntu, the first copy i made would give me I/O errors, I figured maybe I was having hard drive problems until i tried booting it on my new iBook G4 to find out it produced the same error and I know this laptop is fine. I decided to re-download and re-burn it to cd. This time it runs the Ubuntu image with the progress bar bouncing, but when it finishes it goes to a blinking cursor which lets me do nothing. I replaced the old hard drive with a newer 40GB and I'm still getting nowhere. Any suggestions? Thanks

Murdock

---

### Post by linear on 2007-01-04
[COLOR=SeaGreen][COLOR=Black]The LiveCD does not set up xorg.conf correctly for the iMac G3. The usual fix, after you get to the blank screen, is to drop to a shell prompt and edit xorg.conf.

If you don't know how to do this:

After booting is complete,
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. Modify "HorizSync" to 58-62 and "VertRefresh" to 75-117. Both are in the monitors section.
4. Disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo killall -HUP gdm (return) to restart Gnome

If you are booting the LiveCD you'll need to do this every time.[/COLOR]   
[/COLOR]

---

### Post by danjo1 on 2007-03-10
Hi there,

I was also having this problem, but linear's instructions fixed it (thanks :) ).  The other problem I'm having is that when I double-click the install icon, it opens the installer window and then freezes.  Does anyone have any ideas on how to help me with this?

I'm trying to run it on an iMac G3/266 with 128MB of RAM.  Is it just underpowered? If so, can someone suggest a distribution for me to try?

Thanks.

---

### Post by linear on 2007-03-11
Yes, 128 MB of RAM is underpowered. Probably best to ask for suggestions in the [Apple PPC Users]("http://www.ubuntuforums.org/forumdisplay.php?f=133") forum.

---

