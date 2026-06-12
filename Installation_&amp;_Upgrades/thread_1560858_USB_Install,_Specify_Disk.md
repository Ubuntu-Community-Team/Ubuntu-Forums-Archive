---
title: "USB Install, Specify Disk?"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by jqdennis on 2010-08-25
Hi,
I'm installing from USB to an NTFS drive.  The drive I want to use is /dev/sda, but it doesn't show in the 'Prepare disk space' screen.

---

### Post by lechien73 on 2010-08-25
If the disk is not showing in the dropdown box, as per the attached screenshot, then you could try the following procedure. Others have reported similar problems and, even though they don't have a RAID system installed, this seems to work:

[LIST]
[*]Boot from the Ubuntu CD and select to "Try Ubuntu without Installing"
[*]Once it has booted, open a terminal window and type:
```
sudo apt-get remove dmraid
```
[*]This will remove the dmraid driver.
[*]Double click on the Install icon on the desktop and see if your hard disk now appears.
[/LIST]

---

### Post by jqdennis on 2010-08-25
My bad, I want to install to unpartitioned space on /dev/sda, but don't see how to get there.  (the rest of the disk has windows stuff)

---

### Post by oldfred on 2010-08-25
Try chkdsk in windows.

I was able to boot XP without any issues on sda but gparted would not see it. I went back into windows and ran chkdsk, then gparted saw it just fine. I do not know if it was pending updates or a error not yet seen in XP that gparted saw but it solved my problem.

---

