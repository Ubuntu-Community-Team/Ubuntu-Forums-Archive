---
title: "Two Post Install Issues Wubi"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by Don544 on 2010-10-18
First this is a new system I built and I had tried Ubuntu in a past dual boot system with not much problem so I have no problem starting over if I have to as this system has nothing on it but the OS x two,windows 7 and Ubuntu.
On my first try to install as dual boot I ended up scrubbing everything and starting over as a failed install caused the machine to have no monitor after repeated attempts to repair the install unless I booted from the Ubuntu cd.
On the second try I decided to go with Wubi at first to see what goes on
1: as you should be able to see from the attached Photo when I boot I am presented with several options to boot to, five Ubuntu and windows, only four of the Ubuntu actually do anything, line one leads to a sign in screen that asks for my password ( more on that next)
line two leads to a recovery mode command prompt, line four auto loads ubuntu with no password required ,line five ends in another command prompt and line six leads no where but seems to be pointing to the first attempt to install Ubuntu on this machine even tho the drive was reformatted.
2: I hesitate to bring it up as several members have an almost visceral response to the subject of passwords but here goes anyway.
On install I am asked to choose a password, I do so.
At boot if I choose line four I am booted into the os with no prompts for name and password, but my password does not work for any commands that require authentication, sign in name appears at the top of the screen right hand corner of the desktop as if I had signed in. 
If I choose line one and am presented with a sign in screen my password does not work either.
Anyone know of a way to install without a password?
3: As I use the same password for all my non secure testing I had no doubt that I was using the correct password but as it was easy enough to do I uninstalled Ubuntu and reinstalled with no change as the password still not authenticate after boot.
4: Every time I uninstall and reinstall the order in which the boot menu is presented changes, windows was not even shown in the first two installs,any suggestions there?

Thank for reading.
Don

---

### Post by oldfred on 2010-10-18
You have to install with a password as you have to use the password to do any system work, install applications etc. You can set it to not require password on boot, but will have to remember it anytime you have to use sudo.

run this so we can see what is where, if you can boot then from that or from a liveCD:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

