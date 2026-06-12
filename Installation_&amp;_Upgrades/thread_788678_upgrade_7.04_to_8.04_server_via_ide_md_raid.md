---
title: "upgrade 7.04 to 8.04 server via ide md raid"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by djlawler on 2008-05-09
Did an upgrade on an old machine with a via chipset (via82cxxx driver) with 2 ide hard drives that were mirrored with md.  Now the machine will not boot.  Fortunately I am still able to boot into the old 2.6.22-14-server kernel and everything is fine.  I think this is caused by the change from the via82cxxx driver to the pata_via driver.  Either the new driver does not work well....OR....the devices got renameed from hd* to sd* and the md raid config cannot deal with this.  Short of booting into the old kernel for the rest of my life...does anyone have any suggestions on how I can fix this?  Right now I get dumped into a busybox prompt after a long delay if I boot the 2.6.24-16 kernel.

Thanks for ANY help/pointers!

David

---

### Post by lemming465 on 2008-05-10
The obvious thing is to check /etc/mdadm/mdadm.conf for any explicit device builds that mention /dev/hd some-thing-or-other.  However, a quick web search on "linux 2.6.24 mdadm" turned up a whole bunch of kernel, debian, mdadm, and ubuntu bug reports, so you may be up against something a lot more stubborn.

If you aren't interested in participating in the troubleshooting, maybe stay on the older kernel until the 8.04.1 respin and then try apt-get update (or whatever your favorite patch method is).  If you do want to help troubleshoot it, persevere, haunt launchpad, and file bug reports for any new symptoms, or add your voice to any existing reports matching your symptoms.

---

### Post by Pumalite on 2008-05-10
Maybe enabling ALL your repos might help. I dealt and solved a lot of issues doing just that. Include backports, proposed, partner and all updates. Then sudo aptitude update, sudo aptitude upgrade.

---

### Post by djlawler on 2008-06-07
Ok - for anyone else who might run into this I found the problem.  (Yes I know this took a long long time - this is only the second day I've had time to really look at the issue).  When I hooked up the new hard drives I used nice 80 pin cables.  Apparently you must jumper all the devices to cable select and make sure you have the master devices at the end of the cable (black connector).  As soon as I did this...pata-via was instantly happy and my raid re-appeared thanks to the fact that the md array used uuid's NOT device names to configure itself.  The only issue I had then was to undo all the odd stuff I did - including taking the pata-via module out of the blacklist (I had tried using the old via82cxxx module), and re-running sudo update-initramfs -u -k `uname -r`.  Being hopelessly old fashioned, I had set the hard drives to Master and the cdrom to slave.  This would have worked (maybe) with an old 40 wire cable....but not with the 80 pin kind.

So - in the end - if I had done everything 'right' the upgrade from 7.10 to 8.04 server would have been PAINLESS.  Oh well.

Regards,

David

---

