---
title: "Work around =&gt; Ubuntu 12.04 Error installation (Importing Document Setting)"
date: 2012-07-24
forum: Installation &amp; Upgrades
---

### Post by aimwin on 2012-07-24
Update 28 july 2012
New Ubuntu [COLOR="Red"]**_[SIZE="3"][12.04.1 LTS (built 20120727) and [URL="http://cdimage.ubuntu.com/daily-live/"]Quantal 12.10 (20120727.1)]("http://cdimage.ubuntu.com/precise/daily-live/") solve this bug[/URL][/SIZE]_**[/COLOR]. 
I have tested new 12.04.01 LTS and Quantal 12.10 in the same environment as 12.04 LTS.
No menu come up for "migrating of your old account" at all,
so no issue for this bug.

from
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/995126/comments/9](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/995126/comments/9)

Dmitrijs Ledkovs (dmitrij.ledkov) wrote on 2012-07-25: 	#9

The migration assistant has been removed from Quantal and has been
removed for 12.04.1.

[B][SIZE="3"]You can use this installation media:
_Precise (12.04.1) Daily Live:_ [http://cdimage.ubuntu.com/precise/daily-live/](http://cdimage.ubuntu.com/precise/daily-live/)
Quantal Daily Live: [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)[/SIZE][/B]
=============================================================


Work around => Ubuntu 12.04 Error installation at Importing Document Setting point. 
(for details please go to Errors Descriptions section below)

Ubuntu 12.04 LTS will exit installation and will not update your grub menu, after that "error" or "failed" installation.
Though it has message "Installation Complete"

So you will see only old Grub boot menu or what ever your last boot menu.
And you cannot boot in to that "error" or "failed" Ubuntu 12.04 installation.[COLOR="Blue"][SIZE="3"][B]

If you still want to use that "installation".

You can work around this grub update error by[/B][/SIZE][/COLOR]

1. Installing [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") in the USB live and use Boot Repair to update Grub that has option to boot into new "fail" Unbuntu 12.04 installation.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

2. Boot into existing "Good" Ubuntu partition 
and Install [Grub Customiser]("http://ubuntuforums.org/showthread.php?t=1664134") to write to MBR the new update,
with new "fail"Ubuntu 12.04 installation
(Boot Repair did not allow us to update grub, it told me to do the no.1 so I did that successfully)
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

The "fail" Ubuntu 12.04 after this work around perform well with no sign of crippled Ubuntu.
I can install many other programs including Epson TX series and use it perfectly.
Wifi function ok.
I would say 100% working so far.
==========================================

Errors Descriptions

My Installation of Ubuntu 12.04 under certain environment,
will produce Error "failed to unmount partitions" (file attached).
And
after we click on goback, 
(since that is the only choice to continue for me, continue will just repeat the same error message)

It produce the second error message, "Error migrating documents and settings" (file attached).

Then it will go on and tell you "Installation Complete"(file attached).
But in fact it is not.

You won't be able to boot into new "eror" Ubuntu 12.04 installation.
You will just see what ever your boot option that exist before installation.

Reference to these errors.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/995126](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/995126)

and zebul666 (zebul666) wrote on 2012-05-05:
[http://ubuntuforums.org/showthread.php?t=1973810](http://ubuntuforums.org/showthread.php?t=1973810)
[http://ubuntuforums.org/showthread.php?t=1965802](http://ubuntuforums.org/showthread.php?t=1965802)

---

