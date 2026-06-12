---
title: "Dual-boot with 2 harddrives"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by Flame0001 on 2005-11-25
Here's my problem:

I've had Ubuntu installed on my first hard drive for a while now, but with the games I enjoy to play, I had to install Windows XP on a second hard drive.

If someone could give me a step-by-step for how to load into XP through Grub, it would be greatly appreciated.

I've researched this on the Grub wiki, and other posts, but to no avail... 

Thanks for the help.

---

### Post by azteech on 2005-11-25
[quote=Flame0001]Here's my problem:

I've had Ubuntu installed on my first hard drive for a while now, but with the games I enjoy to play, I had to install Windows XP on a second hard drive.

If someone could give me a step-by-step for how to load into XP through Grub, it would be greatly appreciated.

I've researched this on the Grub wiki, and other posts, but to no avail... 

Thanks for the help.[/quote] 
[I]If MS windows was already installed, before you setup Ubuntu, Ubuntu should automatically detect and set up the entry for you in grub. However, if it fails to do so, or if you installed Windows XP after you installed Ubuntu (as in your case), you can manually add the appropriate entry in grub menu.lst to access your Win XP OS by doing the following:

1. edit grub menu.lst using the following command line entry from your terminal screen

[COLOR=Red]sudo nano -w /boot/grub/menu.lst[/COLOR]

scroll to the bottom of the menu.lst file and add the following

[COLOR=Red]# This entry manually added for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1[/COLOR]

The above entry reflects that Win Xp is installed on the 1st hard drive (hda), on the 1st partition (hda1). For your set up, you will need to make any necessary adjustments to the line

[COLOR=Red]rootnoverify (hd0,0)[/COLOR]

to reflect the correct hard drive you have win xp set up on (e.g. it probably will read [COLOR=Red]rootnoverify (hd1,0)[/COLOR] )

2. save the file
3. reboot the computer
4. upon rebooting, press 'Esc' to access the menu listing. You should now see Microsoft Windows XP in the menu listing
5. high light the option you want to boot to and press enter to boot to it
[/I]

---

### Post by Flame0001 on 2005-11-27
Hmm... it doesn't seem to be working.

It just stops after showing this:
"Booting Microsoft Windows XP

rootnoverify (hd1,0)
savedefault
makeactive
chainloader +1"

The system didn't become COMPLETELY unresponsive... capslock and numlock still worked ;]

But anyways, it didn't seem to work... any ideas?

---

### Post by Flame0001 on 2005-11-28
Switching out the hard drives is a pain... any idea where I could've messed up, or an alternate solution?

---

### Post by x__dark on 2005-11-28
try mapping to the windows drive. i had to do this with mine to get windows to boot correctly from my second drive.


rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
boot

---

### Post by Flame0001 on 2005-11-28
Thanks guys. Posting this from WinXP right now.

Ironic, because when my first problem was solved (Network card), I said I was posting from Ubuntu :D

But, hopefully I'll be able to nuke this Windows and get Wine working well.

Again, thanks for the help.

---

### Post by x__dark on 2005-11-28
No problem. If you have anymore problems with GRUB, it helps to look through the GRUB manual.

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

