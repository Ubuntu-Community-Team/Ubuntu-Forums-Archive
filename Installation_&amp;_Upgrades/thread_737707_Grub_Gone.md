---
title: "Grub Gone?"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by Ethangar on 2008-03-27
Decided to take the plunge into Linux and downloaded and burned the iso. 

My computer came with a SataII drive. (windows and recovery partitions. sd0?)
I brought my 300 gig from my old computer with me since it had all my data on it. Its an ATA drive so its hd0
I went and bought a SataII 320 gig and installed it. I just left it as it was since I was going to let linux partition it at install. I went with 100 gig for root and a 5 gig swap partition. The install seemed to go with out a hitch. It said to remove the live CD and finish the reboot.

And it went straight to winXP. No grub just straight in. I did some digging around and guessed that it defaulted to installing grub on the ide drive instead of my sata drive. I killed off all the partitions on the new sata drive so it was completely blank again and thought that I would be smart and just unplug the 300 gig ide drive so that it COULDN'T see it. Another liveCD install and no a hitch. Rebooted and had the grub menu. Thinking myself smart and once I had rebooted into both OS's to make sure that they worked. I shut down and plugged the IDE drive back in.

And grub didn't like it. It spit out an error 17. As long as that drive is off it works fine. But that kind of defeats the purpose since that is where a lot of the windows programs that I use and all the data is. So leaving it off isn't an option. I saw the advanced button on the install and when I clicked it it shows hd0. I thought that might be what I need to change but was a little to unsure to go playing with it. I've since wiped the linux partitions and repaired the MBR so that it boots XP with all the drives attached.

Is there a way to make it install grub in the right spot on my primary sata drive and let me leave all the drives attached? I've got the liveCD and a blank 320 gig sataII drive. If someone could point me in the right direction I would appreciate it.

---

### Post by Rocket2DMn on 2008-03-27
You will need to reinstall GRUB, it is OK to overwrite your windows bootloader, too. - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

