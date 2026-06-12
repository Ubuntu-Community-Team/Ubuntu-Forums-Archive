---
title: "Gutsy broke wireless, totem"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by mindstalk on 2007-10-19
Hardware: Compaq Presario C500 laptop.

Had installed Feisty.  When I tried to run WMA files I was told "don't have the driver, would you like to fetch them?" and did so automatically when approved.  Wireless didn't work, but there were instructions for fixing that manually.  Plugging in headphones doesn't mute the speakers, and I haven't tried the steps to fix that.

I'd also installed kubuntu-desktop and xubuntu-desktop to play with them, but ended up sticking with GNOME; partly because their media players did not go fetch WMA codecs.  xubuntu even uses totem, I think, but somehow couldn't find the installed tools.

Upgraded to Gutsy last night.  Compared to other reports, the process was pretty smooth.  But the aftermath: I was prompted to turn on restricted drivers for wireless, and after doing so, wireless didn't work, and repeated attempts made the keyboard stop working until I rebooted.
Totem no longer plays WMA files, and doesn't go fetch the codecs it needs.  And headphones *still* don't mute the speakers, a problem which has been reported for only months and months now.

Conclusion: upgrading has made no visible improvements for me (other than turning gaim into pidgin) and has made things worse.

---

### Post by mindstalk on 2007-10-19
In addition: restart seems to freeze.  Not sure where the first time; second time it was after "Disabling" eth0 and eth1.

Closing the lid no longer makes it enter sleep mode, I think.  Screen does black out, but I don't get a password prompt anymore when I open it.

Manual hibernate does work, though, though it takesl ike 30 second to go down.

---

### Post by mindstalk on 2007-10-19
Good news: blacklisting bcm seemed to get wireless working again, without going through the whole process again.  Now to get WMA/AVI files playing... (why would upgrade kill the codecs?  And why won't Totem or GNOME or whatever go fetch them the way it did for Feisty?)

---

### Post by erikringmar on 2007-10-19
Hi, I have similar problems -- gutsy upgrade killing wifi ... I'm interested in what you said about "blacklisting BCM" ... what does that mean? (and how do you do it?)

yours,

Erik

---

### Post by mindstalk on 2007-10-20
Added 'blacklist bcm43xx' to the end of /etc/modprobe.d/blacklist.  The installation process had asked if I wanted to overwrite the modified file with the new one, and I'd said yes but made a copy first, so when things were screwy I put it back and rebooted and things worked.  BCM because my laptop has Broadcom wireless, I think.

---

