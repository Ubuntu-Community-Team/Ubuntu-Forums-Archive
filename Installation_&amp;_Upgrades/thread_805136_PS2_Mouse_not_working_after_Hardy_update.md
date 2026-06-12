---
title: "PS/2 Mouse not working after Hardy update"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by JuiceyBananas on 2008-05-23
My mouse has been working fine on Hardy Heron up until I was told some "updates" needed to be installed. After I installed all these updates not only does my machine run slower but my mouse no longer wants to move up and down. It works left to right fine, but I can tell when something is loading on initial startup the mouse starts to crap out.

I'm very new to Linux so I have no idea how to kill processes so that I can one by one eliminate the problem. Also no idea what the keyboard shortcuts are except maybe ALT F1 to get to the menu.

Never thought I'd experience a Microsoft like shaft via the updates. Kind of wondering about the future of Ubuntu....

---

### Post by stoian on 2008-12-10
see here, this worked for me:

[https://lists.ubuntu.com/archives/ubuntu-users/2006-August/091809.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-August/091809.html)

Quote:

Code: 

sudo gedit /etc/rc.local 



then type in:

modprobe -r psmouse
modprobe psmouse proto=imps


Place this before the exit 0 line

save and restart - should have your ps/2 mouse back

---

### Post by babeliak on 2009-06-23
The way above did not work for ME (editing /etc/rc.local).
 
Disabling USB mouse support in BIOS (leaving USB controller enabled ;) ) solved MY problem with PS2 mouse not working/freezed.
[SIZE=4][SIZE=4]see this: [https://bugzilla.redhat.com/show_bug.cgi?id=223606#c21](https://bugzilla.redhat.com/show_bug.cgi?id=223606#c21)[/SIZE][/SIZE]
 
Thanx anyway

---

