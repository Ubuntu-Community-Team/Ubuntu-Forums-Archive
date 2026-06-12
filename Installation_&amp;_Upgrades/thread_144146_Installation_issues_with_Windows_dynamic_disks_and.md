---
title: "Installation issues with Windows dynamic disks and SATA"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by Placid on 2006-03-13
I'm not actually looking for help because I managed to limp through the issues I had but felt I needed to post some of my findings.

In your bios you may have considerable issues if your IDE controllers are configured in enhanced mode such that you can use two IDE controllers as well as SATA controllers. Ubuntu installs fine but after the first reboot it loses the plot and GRUB dies with an error 17. You need to change your bios to compatible mode which means you lose one of your IDE controllers. This is a drag if you have more than one IDE drive as you won't be able to keep it and a CD/DVD drive.

Windows dynamic disks are not supported. This was a huge pain in the arse because I wanted to install Linux on a separate drive then migrate data from NTFS partitions. This quite likely contributed to the GRUB problems I mentioned above. In my case I was able to get around it by doing a sector hack to change the disk type from 42 to 07 but that won't work in a lot of cases.

The bios issue is presumably hard to detect but I think the installer should check for dynamic disks and warn the user at the beginning of the install process that they are going to have a big problem if they were intending to access the disks from linux.

Eventually I worked through these problems but there was distinct lack of clear information available and I was close to blowing Ubuntu off.

Cheers

---

### Post by Placid on 2006-03-13
Oh I should note that Ubuntu was much smarter than Windows in detecting my SATA drive connected to a Promise 378 controller on my ASUS P4C800-E motherboard. Windows required a driver while Ubuntu worked out of the box.

Cheers

---

