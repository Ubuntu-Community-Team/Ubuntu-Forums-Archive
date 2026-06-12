---
title: "Installing 11.04 Alt 64 on Mesh Nero Matrix - Sata HDD not detected"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by steveodeevo on 2011-05-12
I figured I would post this here, as I recently installed Ubuntu 11.04 on a Mesh Nero Matrix PC (Hex Core 4GB, Nvidia 430 geforce, 500GB SATA).

I have always had problems detecting my SATA disks on the PC the primary 500GB drive never seems to get detected, despite changing BIOS settings to ACHI and so on as per guides in this forum, my solution has always been to run a separate smaller SATA drive I have which the installers saw first time.

With 11.04 I noticed the Main 500GB SATA was in the recovery options on the CD, my old install refused to upgrade as I had used some third party software and was running on proposed updates and not the official versions and so I figured download the alt CD and see if I can get it on the main drive, and as I had just installed the 430 geforce I figured a fresh install would be good too.

After much copying and backing up of files I got to the stage where I was installing, and once again the installer seemingly did not see my drive, which was confusing as it had seen it in the recovery options the other day.

I ran through the guides puzzled as to why it was not working, and here perhaps although I feel quite stupid I might be able to help someone else who is lost as to why their drive was not found, after reading a forum post I decided to try not "activating serial ATA  RAID devices" when asked, and suddenly my 500GB drive was visible.

Stupid as it sounds when I reached the point in the installer when it asks do you want to activate serial ATA RAID drives, I had always chosen yes, as I figured this was the right option for a SATA drive, and that all my drives would be displayed.

Well, I feel very dumb, but at least its finally on the main disk (god knows how long ago I could have installed there!), and maybe this post will help someone else who has the same problem.

---

