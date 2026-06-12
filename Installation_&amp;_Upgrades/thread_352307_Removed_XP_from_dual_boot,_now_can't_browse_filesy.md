---
title: "Removed XP from dual boot, now can't browse filesystem"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by t930 on 2007-02-03
I changed my dual-boot XP/Ubuntu notebook by removing the NTSF partition (hda1), then moving the EXT3 partition (hda2) to the beginning of the drive, and then growing hda2 to fill the drive...

and now, I can't browse the filesystem. 

When I click Computer>>Filesystem, the location lists as "computer:///" and I get this error message:

You do not have the permissions necessary to view the contents of "/".

Can someone point me in the right direction?  Right now I'm Googling "fstab" and "mount", though I have almost entirely no idea what I'm doing.

Also, the GRUB menu still shows up on power-up, even though XP is no longer installed.

Are the two issues related?

---

### Post by dave_567 on 2007-02-03
Have you looked through the online documentation yet?  These pages may be of help.  :) 

From the desktop guide:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html)

This is a page that may help you out:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch10s03.html)

or this information may help you as well: 
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/other-hardware.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/other-hardware.html)

---

### Post by quark_77 on 2007-02-03
I assume when you installed Ubuntu you put the entire ext3 file system on hda2 i.e. you didn't do what I did and put home on one partition and / (the root) on another?

If this is the case, the fact that GRUB is still loading is reassuring - it means you ext3 is intact. Grub is installed to /boot/ with /boot/grub/menu.lst being the file it uses to tell it how and what to boot.. and whilst GRUB itself is installed to the MBR (Master Boot Record) Stage 1.5 is on your ext3 file system. Hence if you had stuffed up ext3 you wouldn't see Grub.

Assuming you still have the GRUB list, you could try the recovery console mode. This logs you in as root automatically, and you can navigate to the root of the filesystem (cd /). If this doesn't work something is wrong with the filesystem itself (not an expert here!). If this does work, which I think it will, then it could be a permissions problem. One way to get around this is by typing adduser temp [create a temporary user] and try logging in via that user to see if the new user can access the file system, in which case it is a permissions problem. 

If so, two ways round it. Add a new user and add this user to the sudoers list, or reset your own privileges from the recovery console (not sure how to do this, think it is related to chmod).

---

### Post by t930 on 2007-02-03
Thanks, Dave.  I did read through the documentation, but none of it seems relevant to what's happening on my machine.  Could be a case of not knowing what I'm looking at.

And thanks, Quark.  So I'll just not worry that GRUB comes up with XP as a boot-up option, even though it's not there.

***Update:** I removed the XP section from the GRUB menu.list *

My File System is there and I can browse it in recovery mode and also in regular start-up mode through the terminal via:

cd /
sudo dir

If I try to add my user name to the admin group via:

sudo adduser [me] admin

it tells me I'm already in the admin group.

It seems to be just a problem with the graphical file system browser. 

***Update:** Duh.  I just CHMOD the root to 777 and all is fine.  Or maybe I shouldn't have done that.  Probably a question for a different forum.*
 
Many thanks.

---

