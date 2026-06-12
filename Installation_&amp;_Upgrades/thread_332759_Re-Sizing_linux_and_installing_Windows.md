---
title: "Re-Sizing linux and installing Windows?"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by JackDamian on 2007-01-06
So I got my new computer a bit ago and just installed Ubuntu on it. I figured I could live without Windows and didn't need a dual boot.

Obviously since I'm posting this.. I'm in need of Windows again. And I'd like to dual boot. But I'm not exactly sure how.

I've read somewhere that if I make a new partition and install Windows, it'll mess up the Grub loader.
I guess this should be in the beginners section because I have no idea what I'm doing. I'm on the Edgy version. I have no idea where the partition manager is.. although I have yet to actually look.
](*,)

Any help on what to do would be **greatly** appreciated.

---

### Post by floke on 2007-01-06
From what I've read its extremely difficult to install Windows alongside Linux once Linux is already on the system. Apparently Windows automatically wants to take over the entire hard drive. You might be better off clearing it all off; installing Windows on the entire drive; and reinstalling Ubuntu on top of Windows to get a dual boot setup that way.

Good luck

---

### Post by confused57 on 2007-01-06
Here's a thread by someone who was able to install Windows after Ubuntu:
[http://www.ubuntuforums.org/showthread.php?t=225583&page=2](http://www.ubuntuforums.org/showthread.php?t=225583&page=2)

---

### Post by UpsideDownFace on 2007-01-06
To install Windows after linux, the easy way is to 
1.Backup anything you don't want to risk losing
2.Backup again to somewhere else
3.Copy the Master Boot Record to somewhere safe,
   sudo dd if=/dev/hda of=/home/<user>/mbr_backup bs=512 count=1
4.Make room for Windows, the easiest way is to install another hard drive if possible,
   or use something like parted to reduce the Linux partition make about 10GB for Windows.
5. Install Windows into the new space.
6.Use a Live CD to give a Linux system to Copy the Master Boot Record back from the safe place
   sudo dd if=mbr_backup of=/dev/hda bs=512 count=1
7.Go away and weep, because nothing now works.
8. Buy a book like "Linux Desktop Hacks" by Petreley & Bacon, pub O'Reilly (GBP 17, USD 24)
9 Next time, put Windows on first, on a separate partition or better a separate hard disk
10. Next Next Time, get a cheap second hand machine for Windows

If you think this is not very encouraging, You have got the message.

---

