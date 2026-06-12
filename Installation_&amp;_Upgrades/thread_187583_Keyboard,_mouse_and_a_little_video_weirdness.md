---
title: "Keyboard, mouse and a little video weirdness"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by beow on 2006-06-03
After upgrading from Breezy to Dapper using "sudo apt-get dist-upgrade", I've had frequent problems with the input system. I.e. suddenly a terminal window strat to scroll, like you would be pressing the "Return" button all the time. If I have several terminal windows, this behaviour shift such that the if I focus on a scrolling window, that window stops scrolling and the next starts scrolling... Weird:confused: 

When in this state of confusion, "funny" things can happen with mouse actions too: If I select the Gnome System menu and drags to the right to get for example the Preferences menu, all kinds of windows pops up, just like if I was hitting return all the time. 

When I Ctrl-ALT F1 to a console window, this window has ugly fonts and it is not possible to log in due to corrupted keyboard input (like a Return coming in the middle of the input).

I've tried to dpkg-reconfigure xserver-xorg with a lot of different alternatives (also manually edited) but gets the same behaviour. Also did dpkg-reconfigure gdm to no avail.

Any good ideas? Otherwise I need instructions on how to downgrade to Breezy... :(

---

### Post by Dave2 on 2006-06-04
Do you have plptools (Psion utilities) installed? If so, this is what's causing the problem; remove that package (see [this forum thread](http://ubuntuforums.org/showthread.php?p=597263) and [this bug report](https://launchpad.net/distros/ubuntu/+source/plptools/+bug/40956) for more details - unfortunately this bug wasn't fixed).

If not, I have no clue, sorry.

---

### Post by beow on 2006-06-05
Yes maybe. I remeber I toyed with some Psion utilities quite a while ago. Nevertheless, it was such an ugly problem that I backed up my home directory and did a clean install of dapper. Have had no problems since (apart from reconfiguring everything... )

Thank anyway.

---

### Post by patrick295767 on 2006-07-19
I have same problems.
Dapper is buggy with plptools
I had to return to Breezy to make it  working fine !
[http://www.ubuntuforums.org/showthread.php?p=1274567#post1274567](http://www.ubuntuforums.org/showthread.php?p=1274567#post1274567)

---

