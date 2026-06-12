---
title: "update broke gui login bc Gnome power management"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by chris1497 on 2011-08-21
here's the error I get

"The configuration has not installed correctly for Gnome power management"

Updated my 11.04 install via the update manager last night.  When I turned my computer on today it wouldn't boot into the normal gui desktop.  Where my normal login screen usually appears a different login screen appears with my username.  I login.  Screen flickers black for a few seconds and a page with a ton of text shows up for a fraction of a second ( too short of a time to read a single word). more flickering.  Then I am returned to the slightly different login screen once again with the error.

tried booting into failsafeX gui mode. same issue.

---

### Post by chris1497 on 2011-08-25
bump?

---

### Post by chris1497 on 2011-08-25
I've reinstalled ubuntu-desktop via apt-get.

I've unistalled ubuntu-dekstop and gnome-power-manager via apt-get.  The original error notification no longer appears but I'm still unable to boot/login to the gui

I've changed the permissions on /tmp ( in the event that something deleted it and recreated it with the wrong permissions)

Other people with this problem have had their hard drives filled up.  Usually by cpanel, eaccelerator or other programs.  I have none of these installed.

I've tried the following command to see if any processes are using files in /tmp

lsof | grep /tmp 


it seems my /tmp folder is full and the only thing in it  is pulse-PkdhtXMmr18n -- removed this


The output of df -h 
is 
dev/loop0     size: 29G    used 28G   Avail: 0    use 100%

Not sure how it got to this point.  pretty sure I had 3 gigs free last time I was logged in.  I'm having trouble freeing up space.  I am having trouble accessing a flash drive or ext drive through cli to move stuff.  Live cds are out of the question.

---

