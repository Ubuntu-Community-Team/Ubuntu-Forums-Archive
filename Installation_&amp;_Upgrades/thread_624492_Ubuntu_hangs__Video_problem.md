---
title: "Ubuntu hangs : Video problem?"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by pbhat on 2007-11-27
Hello List,

I am motivating and helping a friend to install Ubuntu on his Dell Latitude D610 Notebook.He has problem running ubuntu.He says it has ATI mobility radeon x300 and 512MB RAM,apart from others.He says it hangs in the middle of activity.He cannot remain on for 5 mins.When hung,nothing works except mouse.We are far off and I cannot guess what could be going on.

I thought of among possible reasons - his wireless driver or video driver.
I asked him to disable wireless and use wired connection which did not solve.My reason for counting video driver among possible causes is ATI graphics generally gives problems.But even to expolre with him this reason,he remains to be on for sometime and able to execute what I suggest,which he cannot do.

Is there a way to boot into X with VESA or such driver passing any parameter to kernel? I want him to enable ATI restricted driver,but he cannot remain on for that long.

Has anybody had similar problems with this videocard - ATI mobility radeon x300?

How to track down this problem?

What to suggest my friend?He doesn't have CLI friendliness.

Any help would be appreciated.Thanks in Advance.

Parameshwara Bhat

---

### Post by Rmantingh on 2007-11-27
If CLI is not an option then perhaps logging into a "Fail Safe GNOME" session may help.
From the login screen select Options -> Select Session -> Fail Safe GNOME.

If that doesn't help then I'm afraid (as far as I know) some CLI will be necesary.
If CLI is possible I suggest to do one of following:-
1) Boot to command prompt (recovery mode) and do a sudo dpkg-reconfigure xserver-xorg
   This will go through the X setup again.
   Accept all default answers except when asked to autodetect the video say yes but
   when presented with a list of drivers, choose "vesa".
2) Alternatively edit the file /etc/X11/xorg.conf directly with your preferred editor.
   Find the section called "Device"
   Replace the driver in there (usually "ati" or "nv") with "vesa"

Then reboot using the vesa driver which should allow you to use the desktop
for hopefully a longer time.

Good luck.

---

### Post by pbhat on 2007-12-05
Thanks Rmantingh,

Enabling ATI restricted drivers solved my friend's problem.I have tried VESA modes as you explained(for experimentation),which also worked for me.

---

