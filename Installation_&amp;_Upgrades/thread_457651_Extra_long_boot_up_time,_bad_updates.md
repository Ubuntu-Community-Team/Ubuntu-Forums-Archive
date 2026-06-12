---
title: "Extra long boot up time, bad updates?"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by calou on 2007-05-28
Since  I loaded some new updates this morning (I believe there were 11 of them, don't remember what they were) its taken in excess of 5 minutes for Ubuntu to boot up (go from the splash screen to the log in screen) and when it finally does come up I noticed some interesting side-effects;  like I now have to click twice to exit from Ubuntu and I can now not see my NTFS (Windows drive, I have a dual boot system) from Ubuntu. I've also noticed that while its loading Ubuntu reports "Loading hardware drivers . . . . . fail", it also indicates it can't mount a drive but the message goes by so fast I haven't been able to record the message. Since I'm a newbee to Linux/Ubuntu I have no idea whats going on nor how or if I can back out the suspected updates. Has anyone else experienced similar problems since updating software today (5/28/07)?  Is there a log file somewhere I could check to see exactly whats happening?  Any help to this newbee would be greatly appreciated.  BTW I'm using Ubuntu 7.04, Beryl on a dual boot system (Ubuntu/Windows XP), with VirtualBox.   I have 2 megs of memory, 3 disk drives (2 ext3 drives dedicated to Linux, one NTFS drive dedicated to Windows XP).  Prior to today's updates Ubuntu came up within 1 minute and I could read and write to the NTFS drive.  :)
Reply With Quote

---

### Post by KNY on 2007-05-29
I am having the exact same problems. I updated today (16 total updates) and since I rebooted, there has been nothing but trouble. I lost access to two of three non-root drives (one of the missing ones doesn't even show up in `sudo fdisk -l`). Additionally, my ethernet-based network connection has died, and I've never had trouble with that before.

Please keep this thread updated.

UPDATE: I tried rebooting to the previous kernel on the GRUB menu (2.x.15, IIRC) and everything appears to be fixed.

---

