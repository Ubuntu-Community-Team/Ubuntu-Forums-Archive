---
title: "Problem with wubi install."
date: 2011-07-01
forum: Installation &amp; Upgrades
---

### Post by twids on 2011-07-01
Hey all decided to try and dual boot my system and i get this error

[IMG]http://i51.tinypic.com/91grqt.png[/IMG]

system specs for if you need anyway :)

[IMG]http://i53.tinypic.com/mc6re0.png[/IMG]

---

### Post by pawhtiobo on 2011-07-01
Hi,

Have you checked the information in the wubi-11.04-rev211.log? (picture)

If you don't manage to solve the Wubi issue in W7 64 you can always do a side-by-side install, and using Wubi you are not dual-booting, you are installing Ubuntu inside Windows.

[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) (choose step 4 show me how)

See ya...

---

### Post by Rubi1200 on 2011-07-01
Hi and welcome to the forums twids :)

I suggest you download the wubi.exe and Desktop ISO image for the version you want. Place them in the same folder on your computer and then run the executable.


> For 10.04 use [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) 

For 10.10 use [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/) 

For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

If you decide to install somewhere other than the C drive, make sure the wubildr and wubildr.mbr files are on the correct partition.

Let us know if this helps.

---

### Post by twids on 2011-07-01
> **Rubi1200 said:**
> Hi and welcome to the forums twids :)

I suggest you download the wubi.exe and Desktop ISO image for the version you want. Place them in the same folder on your computer and then run the executable.



If you decide to install somewhere other than the C drive, make sure the wubildr and wubildr.mbr files are on the correct partition.

Let us know if this helps.

Just tried this and i got the same error :( going to to the post above anyway ill report back and let you know.


Quick edit: just checked the log and it lost me if you want me too upload too paste bin for you too check?

---

### Post by Rubi1200 on 2011-07-01
Yes, upload it to pastebin and then give us the link so we can take a look at it.

Also, can you check in the Disk Management utility on Windows and tell us if the disks are reported as being Basic or Dynamic.

Thanks.

---

### Post by collisionystm on 2011-07-01
> **twids said:**
> Hey all decided to try and dual boot my system and i get this error

[IMG]http://i51.tinypic.com/91grqt.png[/IMG]

system specs for if you need anyway :)

[IMG]http://i53.tinypic.com/mc6re0.png[/IMG]


Are you trying to install Wubi to your D: drive? Try installing it to C: and see if it works.

---

### Post by bcbc on 2011-07-01
If you are using dynamic drives, don't install Ubuntu (Wubi or otherwise). Ubuntu appears to ignore these and so you can end up losing your data or causing problems on Windows.

You can tell if you are using dynamic drives through the Windows Disk Management tool.

---

