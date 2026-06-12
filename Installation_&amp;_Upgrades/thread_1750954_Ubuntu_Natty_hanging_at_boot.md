---
title: "Ubuntu Natty hanging at boot"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by User124 on 2011-05-06
After upgrading from 10.10, The new instillation refuses to start up. Grub loads properly, and I can enter Windows 7 without any problems. I cannot start Ubuntu, though, as it hangs at the loading screen (5 white and orange dots under the Ubuntu logo). The OS also hangs when loading recovery mode.
Methinks this might be a compatibility problem, as it still occurs when I try and boot from a liveCD, and when I reformat and install using the Alternative CD installer.
The computer is an HP Envy-14 1188ee (6GB Ram, i7-720 processor, ATI graphics card).

Any ideas what might be going on?

---

### Post by An Sanct on 2011-05-06
The alternative CD is meant for "offline" upgrades for computers, that cannot access the internet or their connection is too slow (from the users point of view).

Download the "normal" CD or even better DVD (please use the torrent ;)) and give it a try.

---

### Post by User124 on 2011-05-06
I did that before going for the alternate installer.
And yes, I downloaded both via torrent :D

---

### Post by Dutch70 on 2011-05-06
Check the md5sum of the .iso you downloaded.
[[COLOR="Red"]https://help.ubuntu.com/community/HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

The next time you boot the cd, instead of selecting try or install ubuntu, select "check cd for defects".

If that doesn't help, try some other boot options. 
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by User124 on 2011-05-06
All 4 disks I ISOed seem to be working..

Changing to NOMODESET works for the live CD, but not when I try and use the HDD instillation, in either normal or recovery mode.
Strangely enough, when I try and edit the GRUB for either one, they both seem to have NOMODESET already in by default.

---

### Post by Dutch70 on 2011-05-06
If it works in live cd mode, it should work on the install. I really don't know anything about it, except that you have to do the same thing with the install and make it permanent.

---

### Post by MAFoElffen on 2011-05-06
> **User124 said:**
> After upgrading from 10.10, The new instillation refuses to start up. Grub loads properly, and I can enter Windows 7 without any problems. I cannot start Ubuntu, though, as it hangs at the loading screen (5 white and orange dots under the Ubuntu logo). The OS also hangs when loading recovery mode.
Methinks this might be a compatibility problem, as it still occurs when I try and boot from a liveCD, and when I reformat and install using the Alternative CD installer.
The computer is an HP Envy-14 1188ee (6GB Ram, i7-720 processor, ATI graphics card).

[COLOR=Blue]***Any ideas what might be going on?***[/COLOR]
(and you later said that nomodeset lets you boot into the LiveVD...)
You didn't say "which" ATI graphics you had... Some use fglrx and some not. All seem to need "nomodeset in the kernel boot line.  Some seem to use "radion mode=o" and some use "radion mode=1"... Some (cuurently) need to run a 2.6.37.x kernel or the newly proposed 2 2.6.38-9 (Where the current kernel is not letting xorg boot the graphics on some hardware, open LP bug on that)... It all depends.

So-- when it is locked up at the bootsplash, can you get to a tty text console? Try it with <cntrl><alt><F1>.  If not, follow the instructions here to temporarily edit the kernel boot line from a grub menu...
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)... Then you could try some of the things in that sticky... and see what works for you. Once you find what does work, the instructions for making those things permanent are in post 1 of that sticky.

---

### Post by User124 on 2011-05-07
The graphics card seems to be a 5650.
It won't respond to <ctrl><alt><f1>, so I tried editing the boot to load into text, as mentioned:
```
 linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=32939def-1f4a-4134-9b56-bed2319a9216 ro  nosplash text
```and then I arrive at a gray, flickering screen. <ctrl><alt><f1> still not working.

Note, every time the boot hangs, the fans go full strength a few seconds after the hang starts, and the computer heats up.

I don't want to go forward with any of the more exotic grub commands before checking to see if you have a solution, as frankly some of them look scary, like the ACPI one.

---

