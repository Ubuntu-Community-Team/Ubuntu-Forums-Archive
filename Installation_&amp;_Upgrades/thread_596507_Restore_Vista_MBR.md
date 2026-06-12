---
title: "Restore Vista MBR?"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by Onay on 2007-10-29
I overwrote my MBR for my Vista install on my Lenovo T60. How can I restore it without the install DVD, since Lenovo does not ship it?

It would also help if I could fix the MBR to factor contents, including a working Rescue and Recovery. Thanks guys.

---

### Post by taurus on 2007-10-29
Maybe this helps, [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html).

---

### Post by It_Was_Luck on 2007-10-29
As he already answered, thats the link to a file called a SUperGrub disk, it pretty much takes Grub and puts it into a very usful disc which can be burned and run. The reason he gives you the link is because within that software there is a command that will do whats called a "FIXMBR" command, which will restore Vista (in your case) back to the primary boot.  

If you boot the CD/DVD then click Windows then "Fix Boot of Windows" it will do EXACTLY what typing in "FIXMBR" would do with the software.

Heres the site in case you want to read up on it...
[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)  (I't might be the same thing, but its just a different link)
and heres the download link...
[http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2](http://forjamari.linex.org/frs/download.php/605/sgd_0.9598.iso.bz2)


hth

---

### Post by Onay on 2007-10-29
Thanks so much for your replies. I have one more question though...

Is it okay to use super grub on a lenovo system? They have a certain way that the MBR is set up so that Rescue and Recovery can be accessed during reboot. If I use this to restore, am I almost guaranteed that at least windows will boot up?

---

### Post by meierfra on 2007-10-29
A little more information on this case:

[http://ubuntuforums.org/showthread.php?t=595467]("http://ubuntuforums.org/showthread.php?t=595467")
[http://ubuntuforums.org/showthread.php?t=595015]("http://ubuntuforums.org/showthread.php?t=595015")
[http://ubuntuforums.org/showthread.php?t=594223]("http://ubuntuforums.org/showthread.php?t=594223")
[http://ubuntuforums.org/showthread.php?t=594164]("http://ubuntuforums.org/showthread.php?t=594164")

---

