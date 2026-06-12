---
title: "dual boot - windows goes bsod/reboots"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by inshadow on 2011-01-09
I have a Toshiba F30-114 laptop on which I want to have a dual boot Windows XP/xubuntu configuration.
The problem is that when I install Xubuntu as dual boot, Windows XP gives a blue screen of death for a second and then reboots in the begining of the windows boot sequence.
I can choose Safe Mode, Safe Mode With Networking, Safe Mode With Command Prompt, Boot With Last Good Configuration, and Start Windows Normally. But nomatter which one I choose it will result in a bsod following a reboot
(same as this description: [http://ubuntuforums.org/showthread.php?p=7858747](http://ubuntuforums.org/showthread.php?p=7858747)).
The Xubuntu installation works fine.
I tried to remove the Xubuntu partition, which somehow also resulted in removing the XP installation. I then put the harddrive in an external case and used EASEUS Partition Recovery 5.0.1 on another machine which got back the Windows partition. Now Windows works again without any bsod.
I tried installing Xubuntu twice, with the same outcome.
Any ideas why this is happening, and what I can do to succesfully install a dual boot system?

---

### Post by Mark Phelps on 2011-01-11
My guess would be that installing Xubuntu, during the partitioning step, is corrupting the XP setup.

That would only be true if:
1) The initial drive is entirely allocated for XP
2) You're allowing the Ubuntu installer to allocate the filespace using the side-by-side option.

If you're manually partitioning the drive to leave unallocated space at the end for Xubuntu, and then letting the Xubuntu installer format that space, you should not be encountering these problems.

Are you trying to install via Wubi (inside XP)?

---

### Post by inshadow on 2011-01-11
My memory comes back to me what I did at what point.
> **Mark Phelps said:**
>  Are you trying to install via Wubi (inside XP)?
I started out trying the Wubi installer which worked fine, but then I decided to go with a real dual boot side-by-side installation instead.

> **Mark Phelps said:**
> My guess would be that installing Xubuntu, during the partitioning step, is corrupting the XP setup.

That would only be true if:
1) The initial drive is entirely allocated for XP
2) You're allowing the Ubuntu installer to allocate the filespace using the side-by-side option.

Are you talking about allowing the Ubuntu installer to resize the partition?
I remember doing that the first time.

> **Mark Phelps said:**
> 
If you're manually partitioning the drive to leave unallocated space at the end for Xubuntu, and then letting the Xubuntu installer format that space, you should not be encountering these problems.

Next time I tried to install Ubuntu, I manually used the unallocated space where Ubuntu was installed last time.
Is that what you are suggesting?
This resulted in the same problem though.

Thanks.

/Stig

---

