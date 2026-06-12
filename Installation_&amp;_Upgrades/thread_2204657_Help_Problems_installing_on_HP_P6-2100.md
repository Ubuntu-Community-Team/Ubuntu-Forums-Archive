---
title: "Help Problems installing on HP P6-2100"
date: 2014-02-09
forum: Installation &amp; Upgrades
---

### Post by xkainx2 on 2014-02-09
I baught an HP P6-2100 for my son and windows in this house has always been a swear word. He grew up on Ubuntu and we are having a heck of a time installing it on his computer. It came with windows 7 home premium on it but when we try to boot the install cd it hangs wile the installer GUI is starting and freezes (numlock froze, no typing, no mouse) at the brown screen. Any help would be appreciated, thanks in advance.

---

### Post by fantab on 2014-02-09
Are you trying to dual boot Windows and Ubuntu?

Start with checking the integrity of your ubuntu.iso with [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") or [SHA256Sum Check]("https://help.ubuntu.com/community/HowToSHA256SUM"). Re-download the .iso if the check sum fails.

Reburn the .iso to another DVD or USB.

Boot Ubuntu DVD and 'Try Ubuntu Without Installing'. Open Terminal [Ctrl+Alt+T], run the following commands and post thier output here:
```
sudo parted -l
sudo fdisk -l
```

If you have Win7 then probably you have 'Legacy/MBR' boot. MBR/msdos disk partitioning scheme can have ONLY four Primary partitions. HP uses up all the four. More after we see the output from the above commands.

---

### Post by xkainx2 on 2014-02-10
Actually nope Im wanting to completely remove windows, everything else seems to check out. trying ubuntu does the same thing, i may try it with nomodset here shortly and see if that helps

---

### Post by sudodus on 2014-02-11
If the live CD/DVD/USB drive seems to have graphics problems I suspect the graphics chip/card 'AMD Radeon HD 6410D Integrated Graphics' according to

[http://compreviews.about.com/od/budgetdesk/fr/HP-Pavilion-p6-2100.htm](http://compreviews.about.com/od/budgetdesk/fr/HP-Pavilion-p6-2100.htm)

Am I correct about the graphics hardware?

So nomodeset can help you run it well enough to try a proprietary driver.

Which version of Ubuntu are you trying? Maybe another version will work better with that hardware.

---

