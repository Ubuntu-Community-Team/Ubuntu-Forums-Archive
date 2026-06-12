---
title: "cannot restart after installing to new partition"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by Mel_K on 2012-01-07
Hello
I have a new dell inspiron 620. I set up windows 7 and from within windows partitioned as much as I could for ubuntu 11.10. (my old dell runs 10.04) my husband uses windows as a remote desktop to occasionally work from home.

After switching the pc to boot from disc, I inserted my 11.10 cd and followed the usual install prompts. upon restarting, I was brought to the screen to select ubuntu or windows to boot and when I select ubuntu,  the screen momentarily goes purple, then black, the jungle welcome song plays, my webcam is recognised, but still the screen is black. at first I suspected that the install did not go well because of the install cd, so I downloaded again, and made a new cd and burned at 16x- the slowest speed I can. 

I then re-installed and selected the install 11.10 and remove old 11.10 option. No change from the above, but when I look in windows disk management, I now have two additional partitions to the windows and planned ubuntu partitions and both are 5.98GB which I assume are the two installs. Neither these smaller partitions nor the planned ubuntu partition have a file system format (like NTFS or ext)windows 7 is functioning correctly.

How can I get ubuntu to install to the planned partition and how can I get it to work? Can I delete the two smaller new partitions?

---

### Post by 2F4U on 2012-01-08
What are your hardware specs? Can you boot the liveCD without problems and get to a working desktop?

---

### Post by darkod on 2012-01-08
Did the option literary say it will remove the old one? As far as I know, linux never removes installations. If you want to install onto existing partitions, you have to use the Manual (Something Else) option, not any of the auto options. The auto options just create one new install on top of the ones already there.

You need to start the install again, use the Manual option and delete all ubuntu partitions (watch out not to delete windows), and create root and swap with the sizes you want.

As for the problem with not booting OK, did you check if the ubuntu cd is running in live mode without any problems? Sounds like video driver issue. Before install it's always better to run it in live mode to check if everything will load correctly.

---

### Post by Mel_K on 2012-01-09
Hi,
Many, many thanks for your efforts. 

Since posting, I unintentionally deleted some partitions and more  and upon start up I had an * error unknown file system, grub rescue>* and needed to call my IT friend to come over and sort things out, which thankfully worked.

I do appreciate your attempts to assist.

---

