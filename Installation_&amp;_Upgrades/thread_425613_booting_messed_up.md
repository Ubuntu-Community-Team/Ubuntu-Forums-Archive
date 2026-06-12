---
title: "booting messed up"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by Amilius on 2007-04-27
I just messed up my 'puter. I had Kubuntu installed on my computer together with Windows XP, I wanted to upgrade my kubuntu Dapper to Edgy, so I googled how to do it, changed the sources.list to edgy and used the dist-upgrade... total failure... it started alright, and then it just stopped downloading the packages and didn't let me upgrade anything... all packages that I tried to upgrade thru GUI seemed to break... so I restart my computer and Kubuntu didn't want to load up. So here's when I mess things up even more, thru Windows XP I deleted the partition that had Kubuntu installed and now it seems that the GRUB wants to load but a message saying Error 17 appears and it stops right there... now I can't load kubuntu nor Windows XP. Is there anyway to eliminate GRUB so I can directly boot to Windows? if I Install Ubuntu using live CD, will it overwrite that grub if I use the partition where the last kubuntu installation was?

---

### Post by HansKloss on 2007-04-27
If windows partition is the only one left, boot from your WinXp CD and choose Repair option when prompted.
next you should be given option to login to your existing windows partition and dropped to command line.
type fixmbr and that should do it.

---

### Post by birdman3131 on 2007-04-27
you can do 2 things

1 reinstall and grub should reconize windows again

2 using the recovery console for windows (on your xp cd) type fixmbr and it should repair the mbr to just windows

---

### Post by raja on 2007-04-27
If you dont want to reinstall linux, you can try to repair the MBR with the xp cd. Or you can use an alternative boot-up manager -[ supergrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") for example. If you reinstall Linux with a live cd, there should be no problem at all. Grub will be installed again and should list windows for booting.

---

