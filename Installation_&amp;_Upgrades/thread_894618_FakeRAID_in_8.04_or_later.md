---
title: "FakeRAID in 8.04 or later?"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by flatline on 2008-08-19
Help? Hope this is in the right place...

I just put together a server for my home.  Partial specs:
[LIST]
[*]Asus P5E WS PRO (w/ Intel ICH9R)
[*]Xeon 3110 3.0GHz
[*]4GB PC 800 SDRAM
[*]80GB IDE (system drive)
[*]2x 1TB SATA fakeRAID1 (data)
[/LIST]

I first put Windows Home Server on the box, but that OS is far too dumbed-down for my purposes.  It was nice being able to stream media using TVersity, but the whole Drive Extender filesystem really started to grind my gears.  I am now going to try running 8.04 Server.  I did some googling, but reading _[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)_ was pretty daunting.  

I wasn't planning on trying to install to the RAID1 array, that seemed like asking too much.  I was hoping to be able to utilize my current fakeRAID setup though to mirror my data. Anyone out there know the current status of fakeRAID support in Hardy?

Thanks!

Matt

---

### Post by tamoneya on 2008-08-19
if this isnt going to be a dual OS system you are probably better off with a software raid.  I just set one up on my server. (it actually has RAID 0,1 and 5).

[http://knowledge76.com/index.php/Ubuntu_Server_Install_With_Software_RAID](http://knowledge76.com/index.php/Ubuntu_Server_Install_With_Software_RAID)

---

### Post by flatline on 2008-08-20
Is it possible to setup a software RAID after installation, using the system drive?  That is, say I decide to install the system on a 1TB drive, can I then blast the other 1TB drive and build a RAID1 mirror from it?

---

### Post by tamoneya on 2008-08-20
if you have your root partition on the raid you really want to set it up at the install. Otherwise you are only going to make a mess of things.

---

