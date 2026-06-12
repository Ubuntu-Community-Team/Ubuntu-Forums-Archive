---
title: "Xubuntu 7.10 Alternate CD installation can't detect my harddisk?"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by Hannz on 2007-12-05
Hi all,
I'm a total newbie trying to install Xubuntu 7.10 at my workplace.
Tried the Live CD installation but it doesn't work (hangs when I actually started the installation). So I downloaded the Alternate CD and tried the text based installation.
Everything works just fine until it tried to detect my disk drives. It said that I have to choose which driver would be appropriate for my disk drive. I think somehow Xubuntu can't detect my disk drive. I've tried continuing without the disk driver, arriving at the partitioning section, but there was no option regarding my disk drive.
Rebooted and checked whether my disk drive was corrupted, but it was fine and Win XP could start normally. Note that I don't want a dual boot, I was actually trying to reformat my computer, get rid of Win XP, and use Xubuntu.
My computer's specs: Pentium II 333MHz, 128MB RAM, S3 Trio3D display adapter, Fujitsu MPD3043AT hard disk, and a Toshiba CD-ROM XM6202B (this is one of the oldest computers I currently work with).
Tried browsing the documentation and this forum, but I still can't find a suitable answer to my problem. Any help would be much appreciated. Thank you.

Hannz

EDIT: Checked the Alternate CD for defects, and it passed. Nothing's wrong with the CD.

---

### Post by skeppstedt on 2008-03-31
Hello!

I've got the same problem, only i'm trying to install Ubuntu server 7.10. I've also got a Fujitsu MPD3043AT hard drive, which the installer seems to be unable to find a suitable driver for.

If anyone has a driver for this disk or some work around of any sort, please reply :)

---

### Post by haz2a on 2008-04-05
No disk was detected. Requested selection of disk driver, but ide-disk and ide-generic didn't work.

Used startup option nodma via F6 at first screen.
Hung with blank screen for about 1 minute (it was previously hanging for 2-3 minutes) but then started OK and detected hard disk.
Also used the irqpoll startup option, as suggested when I ran Check CD For Defects from the menu.
So I just do F6, then add on: nodma irqpoll

---

### Post by haz2a on 2008-04-05
1. When installation boots from hard disk, hit ESC as soon as Grub appears, to get to Grub's menu.
2. Highlight Recovery Mode > 'e' to edit > add 'nodma' to end of the 'kernel' entry
3. enter 'b' to boot
The new OS should now boot from the hard disk into recovery mode (as root).

4. Edit /boot/grub/menu.lst eg: with vi, pico, or other cmd line text editor
Add 'nodma' (and any other required boot options, separated by spaces) to the end of the '#kopt' line
5. Save the file and leave the editor
6. run the cmd: # update-grub
7. then do: # shutdown -r now
The system should now boot properly from the hard disk without intervention

---

