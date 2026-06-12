---
title: "Update ubuntu (12.04.3 LTS to 13.10?)"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by Niemil on 2013-11-16
I have an DELL inspiron 1525 laptop that's quite old, I currenlty running 12.04.3 LTS and it works great. However, I wanna check out the very new ubuntu version (13.10 right?), I don't mind if everything would be wiped off this computer because I have no important files or so.
I had thought of just try make an live USB (which I did when I installed this ubuntu version, but from Windows). But, I have no USB memory stick here right now and I also aren't sure how to make a live USB (or whatever called) with ubuntu. I had some simple software for Windows that made all job to me when I installed ubuntu, not sure if anything like that existing on ubuntu.

So anyway, I wanna update from the computer instantly if that's possible? and if so, how?
I been searching on google yesterday, but I didn't find anything that worked for me. I found a couple of commands that I typed (" [FONT=Ubuntu Mono]sudo do-release-upgrade -d ").
Somebody also written I have to change a file in release upgrade folder/file. But it's a readme file and not sure how to change that.[/FONT]

---

### Post by fantab on 2013-11-16
Instead of removing 12.04.3, if you have free space or partition on your HDD, you can install 13.10 to that space. All you need is about 15-25GB of free space.

To upgrade to 13.10 you have to upgrade to 12.10 -> 13.04 -> 13.10. Trust me, it will be tedious process. Clean install will be much simpler. Consider the above option.

---

### Post by Niemil on 2013-11-16
okey, yeah well I don't really care if I do the update or new installation.
I just wanna try out 13.10 to be sure if that's what I will dual boot install with windows 7 on my main computer at home.

Any of these methods, is it possible without USB and CD?
[edit]
Well, I found a USB I can format.
Problem though is to do this via ubuntu, haven't done it really.

---

### Post by efflandt on 2013-11-16
If you know how to get into the applications in Dash (upper left corner in Unity) look for Startup Disk Creator. That can format if necessary (FAT32) your USB memory (to clear anything from it) and put the 13.10 iso on it (that you downloaded) so it is bootable. However, make sure that you have the proper device (which on a laptop with only 1 hard drive is likely /dev/sdb, but you would would format/install it to partition /dev/sdb1). If you want to and have room, you can set persistent data with a slider, so it can retain things like wireless security and timezone between boots from it (or even install additional programs, but not drivers or updates).

Then you either need to change your BIOS boot order, or sometimes also need to hit a hotkey during BIOS splash screen to select to boot from the USB. If you need to set any parameters for the USB boot just hit any key when you see some symbols at the bottom (one looks like a keyboard). One common parameter is nomodeset if you have graphics issues while booting it. Booting from USB memory will be rather slow, so give it time when it seems to blank out for awhile.

---

### Post by Niemil on 2013-11-16
Yeah I fixed this, found it out. Thanks
Got some weird error at first when I did this, my mouse pointer were gone after installing, but additional I installed some other thing within gnome, so may be that who caused problems. I had to reinstall whole OS again, but now it's working alright.

---

