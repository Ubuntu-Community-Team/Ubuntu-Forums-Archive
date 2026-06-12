---
title: "Ubuntu 10.04 LTS on Dell PowerEdge 2600"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by endirock on 2010-05-22
Alrighty, I have a very weird issue that is confounding me. I am trying to install Ubuntu 10.04 LTS (32 bit) on a Dell PowerEdge 2600. I pop the cd in, fire the box up... fans whoosh, disks spin, I have a nice blue status light and lots of green lights everywhere else; everything is good. The machine proceeds through the normal boot process, then right after I see the Ubuntu installation start to kick in ("ISOLINUX 3.63 Debian-2008-07-15 Copyright (C) 1994-2008 ... Loading ...") the monitor loses signal. I can tell (I think) that the installation is still running, I just can't see it.

I have about googled this to death and can't find the solution. Some things suggested out on the interwebs that I've tried: 
[LIST]
[*]making sure processors, cards, memory etc are all seated well,
[*]updating BIOS, ESM, and the PERC4/Di to the latest versions,
[*]running the Dell Diagnostic Utility from MS-Dos (all tests passed),
[*]disabling console redirection in the BIOS,
[*]making sure DRAC if present (it isn't) is disabled,
[*]disabling the NIC just in case DRAC is hiding,
[*]disabling USB controller in the BIOS,
[*]trying multiple monitors,
[*]making sure the case was on and secured,
[*]keeping the hammer securely locked away in the garage.
[/LIST]

Any suggestions / help would be appreciated. This machine was just pulled from production with no issues (running Windows 2000) in an equipment refresh cycle, so I know this has to be something simple I am going to hang my head in disbelief about once it is figured out.

Thank You!

---

### Post by dino99 on 2010-05-22
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

