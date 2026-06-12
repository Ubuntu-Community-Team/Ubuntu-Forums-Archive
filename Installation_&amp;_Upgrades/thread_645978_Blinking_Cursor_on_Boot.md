---
title: "Blinking Cursor on Boot"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by shendric on 2007-12-20
Ok,

I replied to a post on absolute beginner talk about a similar issue, but I got no response, and it seems that it's better suited for this forum, anyway.

So, I installed 7.10 from the Desktop CD.  The installation seemed to go fine.  I restarted the machine, removed the CD, as requested, and hit enter.

The computer restarted, but it never gets to the boot splash screen, because it just sits there on a blinking cursor.

Now, I tried doing the following after booting up the LiveCD again:

sudo grub
find /boot/grub/stage1
root (hd1,1)
setup (hd1)
quit

Then I rebooted and got the same thing.

Someone else posted that one should remove usplash, while others said to make some changes to usplash.  However, I'm not sure how to go about doing that.  If I boot up the LiveCD, am I actually able to get access to the hard disk itself, or just the LiveCD image?  I tried to go to /boot/grub and adjust the menu.lst, but it said that this file doesn't exist.

I'm really confused.  I've used Linux for 4 years or so, but I'm getting really frustrated.

Any help you could give me would be appreciated.

-----Well, I installed again, and (so far) things seem to be going ok.

---

### Post by mperry on 2007-12-20
This happened to me on Xubuntu recently.  I had to reboot the system with a rescue or live CD and redo the grub stanzas for the root drive.  It somehow placed the wrong values and gave me a root drive which would never work.  You may want to check the actual stanzas in the menu.lst file and make sure it matches your hardware.  When I changed the stanza it was all fine after that and the system booted with no problems.

---

