---
title: "Change temp directory for feisty upgrade?"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by Mets on 2007-04-27
I was just wondering if there was a way while upgrading to Feisty Fawn to change the temporary directory where the upgrade files are downloaded to.  I continue to receive errors about not enough disk space, and I'm assuming that this is the reason.  I dual boot Ubuntu with Windows, and so my Ubuntu partition is only about 6 gigs in size.  I don't feel like uninstalling everything just to upgrade, and I have a 250gb external plugged in.  Is there a way I can force it to download the needed upgrades to that?

---

### Post by Mets on 2007-04-27
Ok, my cd burner appears to be broken, so I downloaded the Alternate CD and unpacked into a directory on my external hard drive.  I would like to run the upgrade program from there, as that has plenty of space.  The location of the "cd" is ```
/media/WDC Combo/alternatecd
```.  I tried typing
```
gksu "sh /media/WDC\ Combo/alternatecd/cdromupgrade"
``` and I get ```
[: 25: Combo/alternatecd/dists/stable/main/dist-upgrader/binary-all//feisty.tar.gz: unexpected operator
Could not find the upgrade application in the archive, exiting
tar: /media/WDC: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Combo/alternatecd/dists/stable/main/dist-upgrader/binary-all//feisty.tar.gz: Not found in archive
tar: Error exit delayed from previous errors

``` 
The external has a space in between WDC and Combo, so I've tried lots of combinations of the above, including using double " ",  going to the directory and just typing gksu "sh cdromupgrade", etc. and I just get errors.  If I try ```
gksu "sh cdromupgrade"
``` from the directory cdromupgrade is located in I just get ```
Could not find the upgrade application archive, exiting

```  Any ideas?  I'd really like to upgrade without having to blank my hard drive.  Thanks

---

### Post by zvacet on 2007-04-28
[http://ubuntuforums.org/showthread.php?t=308027&highlight=install+from+external]("http://ubuntuforums.org/showthread.php?t=308027&highlight=install+from+external")

---

### Post by Mets on 2007-04-28
hey thanks, I'm not looking at installing it on the external, I just want to either install it FROM the external (i.e. as if the external was the install CD) or to change my apt-cache directory to the external.

---

### Post by Mets on 2007-05-01
bump - anybody know how I can either change the directory Fiesty downloads upgrade install files too or how I can run the Alternate CD off of my external hard drive (with the intention of installing it onto my hard disk)

---

### Post by Mets on 2007-05-08
bump...sigh

---

### Post by Topsiho on 2007-05-08
Sorry.

I know what you are asking, and am really sorry I, and it seems no one, can help you out. On my test computer I too can not upgrade this way, because of lack of memory: the downloaded replacement files of the new version are taking too much space.

The only thing I could do was downloading the CD and do a fresh install from that. I had to use the alternate CD because the Live CD (desktop) did not boot on that computer, but that was an other problem.

Good luck,

Topsiho

---

### Post by Mets on 2007-05-09
Thanks Topsiho, I guess I'll just have to grin and bear it and do that

---

### Post by Topsiho on 2007-05-10
Grinning should do, bearing is not necessary :)

Topsiho

---

