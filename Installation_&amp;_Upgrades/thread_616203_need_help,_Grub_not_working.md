---
title: "need help, Grub not working"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by johndavid400 on 2007-11-18
Let me first say that I have installed Ubuntu more times than I care to count and each time, grub has always worked fine and I have never had any problems. 
However, I just bought another 250gb sata drive to add to my other (2) 250gb drives, one sata and one pata. So now I have 3 and was planning to use them in this fashion:

250gb sata 1:
50gb partition for Windows XP
the rest for storage

250gb sata 2:
48gb partition for Ubuntu
2gb partition for swap
the rest storage

250gb pata:
storage

I previously had the same setup but with one less sata drive and ubuntu installed on the pata drive. All was well.

I just re-partitioned everything and was re-arranging for this new setup, but when I installed Ubuntu on the new sata drive, grub would not boot Ubuntu. I played with the settings and found that it established the wrong drive to boot ubuntu from [it had (hd0,0) when it needed (hd1,0)]. So I changed it and it worked. But then I couldn't boot windows [even after changing the boot drive to (hd0,0),(hd1,0), and (hd2,0) just to make sure I had tried each drive]. So I used Super Grub Disk to fix-boot windows, then it booted windows BUT Grub was gone. SO re-install grub using SGD and Windows wont boot!!!!!!!!!!

It is like I can have one or the other, but it wont give me the option to boot windows from grub like i have for the last 2 years. And when I re-install grub, it wipes out NTLDR or some other file that allows windows to boot.

Any Ideas? I wouldnt mind loading grub on a floppy and booting from that if I could find a tutorial that worked.

thanks in advance

---

### Post by logos34 on 2007-11-18
I'd do this to straighten things out:

1. Restore windows bootloader to sata1 using SGD like you did before.
2.  Set the ubuntu (sata2) drive first in the Bios hard disk boot priority.  [Reinstall Grub]("http://www.google.com/search?q=how+to+install+grub+live+cd+catlett&ie=utf-8&oe=utf-8&aq=t&rls=Swiftfox:en-US:unofficial&client=firefox-a") to the mbr of the ubuntu drive.  The 'root' lines in /boot/grub/menu.lst should be '(hd0,0)'.   
3.  Add [mapping to your windows menu.lst entry]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk"), since it is second in the bios order.  

Note: you may have to change /boot/grub/device.map to correspond to new setting.

Doing it like that will preserve the windows bootloader if you ever want or need to boot into xp directly (by changing the bios hard disk boot order).

---

### Post by johndavid400 on 2007-11-18
ok, I stumbled across an idea that fixed my problem...

way back on the ubuntuguide.org EDGY page, I used to add this to my menu.lst and deleted the other windows options:

title           Windows XP on SATA drive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1


I remembered this and added it... somehow it worked wonderfully. Now I can boot Windows Xp and Ubuntu from Grub.

Hope this can help someone...

---

