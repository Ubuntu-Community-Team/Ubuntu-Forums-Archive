---
title: "Problems installing Ubuntu 14.04  and booting Live CD"
date: 2014-07-01
forum: Installation &amp; Upgrades
---

### Post by Ecchlesius on 2014-07-01
[TABLE]
[TR]
[TD="class: votecell"]     0     down vote          [favorite]("http://askubuntu.com/questions/489543/installing-ubuntu-14-04-problems-when-trying-to-start-live-cd?noredirect=1#")[/TD]
[TD="class: postcell"]                Hi there

I also posted this to [ask ubuntu]("http://askubuntu.com/questions/489543/installing-ubuntu-14-04-problems-when-trying-to-start-live-cd?noredirect=1#comment654225_489543"), but had no answer so far.
I recently wanted to make a clean new install on my PC with  Ubuntu 14.04 on which both Windows and Fedora were installed. When I  first tried to install Ubuntu after partitioning the hard drive, I came  to the "time zone" screen. But then I got the very helpful error message  "??????". [I think this is the same error, but I have no way of trying out the solution]("https://askubuntu.com/questions/455511/dual-boot-ubuntu-14-04-and-windows-7-on-fakeraid-installation-error-question-m#new-answer?newreg=f2b8bde40c8947f8ac8e3cedec0d1964").  As suggested in the link I think it has something to do with the RAID  on the hard drive, as it shows me 4 different RAID volumes. After exiting the installation I wasn't able to boot into any OS as  apparently the hard drive was already repartitioned (shouldn't that  happen at the very end of the installation process?).

  However now I can't boot into any live CD anymore. Everytime I start a  live CD (no matter if Knoppix, Debian or Ubuntu) I get the following  errors:
  ```
/scripts/casper-premount/20iso_scan: line 46: can't open /dev/sdc: No medium found
/scripts/casper-premount/20iso_scan: line 46: can't open /dev/sdd: No medium found
/scripts/casper-premount/20iso_scan: line 46: can't open /dev/sde: No medium found
/scripts/casper-premount/20iso_scan: line 46: can't open /dev/sr0: No medium found
```
  As there is obviously some kind of fault with the hard drive I  reformatted the whole drive (this was with a GParted Live CD before the  error above accured).
I am not entirely sure whether this is an software or hardware issue, so any advice on how to get to the source of the problem is highly appreciated.

  Anybody has any clue how to fix this? Thanks in advance!

      
              [/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2014-07-01
I am not sure, but I think I also get those messages as it is looking for additional drives and does not find them because they do not exist.

The error may be that you have not added nomodeset. With nVidia you have to add nomodeset to boot live installer and on first boot after install or until you install proprietary drivers.

With BIOS and installer at accessiblity screen (tiny icons of keyboard & person at bottom) press any key and then f6 to add nomodeset.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

            Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

