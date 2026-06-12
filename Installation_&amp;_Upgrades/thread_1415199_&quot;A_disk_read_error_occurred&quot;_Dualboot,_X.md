---
title: "&quot;A disk read error occurred&quot; Dualboot, XP &amp; Ubuntu 9.10"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by uthamx84 on 2010-02-24
Hello everybody.
I'm in trouble again :confused:


[LIST=1]
[*]I started out by installing Windows XP on my desktop.
[*]Then I installed Ubuntu 9.10 from the live CD. Ubuntu automatically repartitioned or resized my harddrive and Installed itself side-by-side XP.
[/LIST]
I've done this plenty of times before with previous versions of ubuntu and that has always worked. But now I get this message when I choose Windows XP in the Grub menu.

**"A disk read error occurred" press ctrl+alt+del**

Ubuntu runs very smooth, and I am able to mount the windows xp partition inside ubuntu, so the disk can't be broken. 

Does anybody here have a cure for my problem??, cause I really don't feel like re-installing everything again. 

Thank you for your time....

---

### Post by oldfred on 2010-02-25
Ubuntu boots ok? So this is a windows error. I would try chkdsk first.

To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
chkdsk C: /R
Thread with this and other repair suggestions
[http://ubuntuforums.org/showthread.php?t=1393848](http://ubuntuforums.org/showthread.php?t=1393848)
Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

---

### Post by uthamx84 on 2010-02-26
Hi,
Thank you for the reply.
I tried out to fix windows, but ended up deleting the grub. So I re-installed everything.
This time I installed windows on 40% of my harddrive and left the rest unpartitioned. Then installed ubuntu on the free space. 

Now everything runs perfect.
Once again thank you for the reply, and I wish you a great weekend.

---

