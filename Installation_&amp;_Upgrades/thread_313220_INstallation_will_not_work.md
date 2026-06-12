---
title: "INstallation will not work"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by dan_seguin90 on 2006-12-05
Hello,
I have currently bought a ethernet card for my old hp desktop (192 mb ram, 500HZ processor, cd drive.) I used to have Fedorra 4 on ths computer and before that i had Windows 98. Like an idiot i tried to uninstall fedora and put windows back on the computer. I did this because the cd with the ethernet was only for windows and i was stupid enough to not just search on teh internet for a driver (which i later found). So once that i reformatted the HD and nothing was working at all i figured why not try a new OS, so i decided to download teh ISO image for ubuntu and burn them to a disk. After this i made a 98 boot disk and reformatted once again to make sure the HD was completely empty. 

So i now put the unbuntu image in the cd drive (bios configured to boot from cd) then i turn on the computer. 
I get to the main screen and i say start and install. shortly after this a bunch of command lines wiz by and it stops.

the final line reads:
<0>kernel panic - not syncing: Attempted to kill the idle task!

so i retry and the same problem occurs over and over. even after another HD format.

Can anyone help me with this since i would liek to get this computer back up and runing.

---

### Post by hollaburoo on 2006-12-05
trying burning another cd at a slower speed and if that doesn't work you'll need to use the alternative cd to install in text-only mode

---

### Post by wpshooter on 2006-12-05
I believe with that low amount of memory, you are going to be forced to install from the ALTERNATE (text based version) CD.

If it were me, I would get the **KILLDISK** program from from this site and **WIPE** the drive completely clean before attempting to install Ubuntu.

[http://www.killdisk.com/](http://www.killdisk.com/)

Make sure you check the integrity of your burned Ubuntu install CD ISO image by running the verfication test found on the initial Ubuntu boot screen menu.

Good luck.

---

### Post by dan_seguin90 on 2006-12-05
For all those who are havin this problem do one thing.

Test the memory at the ubuntu welcome screen.

when i did this i found i had no memory working. i took it out and replaced it then tested again and it was all working. there are no problems now and it is currently installing.

---

### Post by doobit on 2006-12-06
> **dan_seguin90 said:**
> For all those who are havin this problem do one thing.

Test the memory at the ubuntu welcome screen.

when i did this i found i had no memory working. i took it out and replaced it then tested again and it was all working. there are no problems now and it is currently installing.

I think this may be the issue with the brand new computer I'm trying to install on. I've had no trouble installing on other machines using the same CD, but I get Seg Faults and Kernel panics everytime with this machine.

---

### Post by doobit on 2006-12-07
That was it. Ran the memtest and got all kinds of errors.

---

