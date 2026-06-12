---
title: "Dual boot install made XP run slow"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by scttburns on 2007-03-06
Hi all,
  I'm not a Linux newbie (software engineer at an embedded Linux company) but I am way out of date on Windows.

  My wife got an Acer laptop with XP home installed.  It came partitioned with a compaq(???) diagnostics partition, an 18 gig fat32 partition with XP Home, and a 16 gig D: drive, also fat32.  I have no idea what they were thinking.

  Over the weekend I installed Dapper on the old D: drive, /dev/hda3.  I took a tarball of what was there ( an MYOB file or two, and what looked like Windows metadata, then repartitioned for / (/dev/hda3) and swap (/dev/hda4).  Dapper now runs quite nicely.

  However, when she rebooted to XP to use MYOB (accounting package) she found it would boot but was excruciatingly slow.  I checked this morning, and I couldn't even shut it down - the windows with options for restart/shutdown/hibernate would not show up.  I couldn't get to the device manager until I rebooted into safe mode.  Apparently, starting MYOB crashes the machine.

  She knows not to suspend when switching operating systems (worked with the suspend2 kernel guy for a while), and a windows scandisk shows no errors.

  Has anyone experienced this before?

Scott

---

### Post by holmb101 on 2007-04-23
I had something very similar to me happen.  I found this tutorial this weekend and it worked perfectly.
It seems that windows changes the transfer mode for the hard drive aftera few disc errors occur.  

You can check this by going to Control Panel -> System -> Hardware -> Device Manager -> IDE Controllers -> Right mouse click on Primary channel -> Properties -> Advanced settings ->Then look at the current transfer mode. 

If it says PIO, then this is what happened.  

[http://users.bigpond.net.au/ninjaduck/itserviceduck/udma_fix/]("http://users.bigpond.net.au/ninjaduck/itserviceduck/udma_fix/")

Hope this helps.

---

