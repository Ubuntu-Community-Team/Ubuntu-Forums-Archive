---
title: "System dead from Gusty install attempt"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by dsiddens on 2007-10-20
I used the update notification on my Feisty laptop to begin the Gutsy upgrade.  After the  files were obtained it began replacing to the Gutsy versions.  As the files were being written, I noticed quite a few depencencies errors with their messages that a given file (program) would not be installed or might not work properly.  This message suggested that I file a bug report.  A bit further on into this upgrade process I noticed that there were messages giving me the option to "compare the differences" between the file I had and the new file.  So on one of these messages, I don't know which one, I selected "D" and was given a command line screen that described stuff I did not know about and then sat there saying "end".

I figured that hitting enter would return me to the install process.  Not so.  The machine was sitting at the command prompt waiting for, I don't know what.  Eventually I thought if I did a power down/up that the install process would pick up from where it left off.  Again, not so.  I tried booting from the regular kernal choice and from the recovery mode, neither of which yeilded a working computer.

From the screens that stopped on the boot attempts I wrote down the last screen of each attempt.  The significant lines are:

For the kernel 2.6.22-14 (recovery mode)
[10.960197]/build/buildd/linux-source-2.6.22-2.6.22/drivers/ftc/hc.tosys.c: unable to open rtc device(rtc0)
[10.973499] input: AT Translated Set 2 keyboard as /class/input/input1
[11.063970] VFS: Cannot open root device "UUID =adc16267-58e2-4882-9850-9da2e35d482" or unknown-block (0,0)
[11.064022] Please append a correct "root=" boot option; here are the available partitions:
[11.064075] Kernel panic - not sysncing: VFS: Unable to mount root fs on unknown-block (0,0)

For the kernel 2.6.22.14-generic 
[16.798468] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[17.014051] Kernal panic-not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

at the bottom  of the screen:
Kernel alive
kernel direct mapping tables up to 100000000@8000-d000

I had other boot choices which I went through and tried them all with the result that I was brought to a light blue screen with a cursor that I could  move around but no text or sign-in boxes.  

The machine in question is a laptop AMD64.  It was running fine with the Feisty software.
I'm on our secod laptop hoping that some one can give me a newbie's, detailed instruction to get Gutsy up and running.

Thank you, Doug

---

### Post by Hoppiesbox on 2007-10-20
I had a somewhat similar problem, you can read about it here:
[http://ubuntuforums.org/showthread.php?t=582616](http://ubuntuforums.org/showthread.php?t=582616)

As you can see, I ended up having to interrupt(?) the upgrade process also. What I did not include in my post was the error you got when starting back up:
[11.064075] Kernel panic - not sysncing: VFS: Unable to mount root fs on unknown-block (0,0)

I "fixed" (and I'm not recommending you do this because my system isn't in much better shape) it by selecting another, older kernel from the grub menu.

The last kernel did load up to the point I described after trying to switch users - which is to say a blank screen with a "waiting" cursor, with no login window.

I pressed ctrl-alt-F1 to get a command prompt, logged in, and found out my packages were all messed up. I'm not sure of the exact message, or where I even saw it (I'm not as skilled as some others with saving messages and finding the relevent info) - dpkg, dselect, or apt reported several of my packages as being severely messed up. 

'dpkg --configure -a' just spews out errors/warnings saying dependencies are not met, and configuration having to exit with status 127(wth **is** that?)

At any rate - our problem seems to have the same cause.

---

