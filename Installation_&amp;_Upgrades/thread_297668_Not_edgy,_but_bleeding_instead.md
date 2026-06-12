---
title: "Not edgy, but bleeding instead"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by xhantt on 2006-11-11
What follow is rant, so if don't like please skip it.

I was more or less a happy user of Kubuntu since Breezy, later updated to Dapper. Everything was fine, movies, music, pictures. Not all hardware was supported, but it was because the vendor doesn't provide linux support and I can't blame Ubuntu about that. So far so good.

Later this september I upgrade to beta version of Kubuntu Edgy Eft, the upgrade was difficult, package breaking dependencies, missing packages, but it's a beta version anyway this is expected to happen. A few days later everything was fine, al dependencies were fixed, and I was happy as I was with Dapper.

But the last weeks previous to the final release, somehow the problems start poping up. First some upgrade stopped hibernate to work, this is really bad for a laptop. My fault this is still a beta version. I loose one session, and my swap partition. After some tweaking I get back my partition, but can't hibernate because it was broken...

Final release come in the expected time, I upgraded to Edgy, but problems arise with other patitions, swap not being recognized, and I've to install it manually with every boot. The ntfs partition doesn't show up, after adding it to the list of automatically mounted partitions on boot.

But then appeared the worst problem... "soft lock up cpu #0"...  My computer turn to a solid rock, you can't boot, you don't get command line, you can't upgrade/downgrade your kernel. You can't compile a kernel by hand (it worst that the X server problem in Dapper do you remember that?)

Ok, my fault, I was using Edgy from beta version, and maybe something broken in the way... Time to make a clean installation.

Everything was fine... I loose my settings but I won't cry for that... 

Seriously upstart kick ***, now I prefer it instead of hibernate, wich is really slow... but...

But now the problem here is that sometimes can't shutdown properly... I just get a blank screen, or the splash if I was lucky with the progress bar stuck... leds are still on... no disk activity... I've to login into a console Ctrl+Alt+F1, and run shutdown... But sometimes I can't login into a console... and must cut the power after waint several minutes... Seriously I don't know hibernate seems to work but is really slow, or shutdown but I don't know if this will work....

Moreover, guess what "soft lock up cpu #0" appear again... Please don't point me to a forum entry, I tried all of them. There's a bug in the kernel (or in the blobs distributed along). This is a nasty bug, one day it appeared 7 "seven" times in a row, then I give up, other days it doesn't popup.

Finally, on one lucky day that I can boot I compiled an stock kernel from kernel.org (v2.6.18.2). Something don't work because I don't have the blobs but at least I can use internet, music, movies, as previously...

BTW: In kubuntu "system places" is broken media storage points to /media instead of media:/ . Some mounted units that show in Desktop doesn't offer a "Safely Remove". CDs and DVDs just show up as "cdrom0" instead of the label as in Dapper, usb drives appears as usbdisk or as sdb dependending where you are looking, which is confusing at least. When you can't umount a unit from the context menu there's no message if it failed, just the unit remains mounted. One day I closed every program I've open and still can't umout an usb unit. K3B can't verify if it burned the CD/DVD correctly. When I close my session if something crash then Krash popup, and the session doesn't close until I dismiss this dialog, so I've to wait it close the session just to be sure...

But at least they get rid of the purple theme.

Plain ubuntu... instead, no thanks.

---

