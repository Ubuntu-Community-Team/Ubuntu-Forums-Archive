---
title: "Deleted Ubuntu, But It Still Shows Up"
date: 2012-10-01
forum: Installation &amp; Upgrades
---

### Post by UniversalCyborg on 2012-10-01
I did a dual boot with Ubuntu & Windows 7. I have Win7 on the C partition and had Ubuntu on my E partition. I installed Ubuntu via wubi, but later on decided to remove it, so I deleted all the files that were Ubuntu related on the E partition and deleted wubi which was on the C partition without uninstalling anything. I guess that's when everything went wrong, you're suppose to uninstall it.

Everything works fine, but when am trying to log into Windows, Ubuntu still shows up as if I were dual bootin. What I've done so far is that I reinstalled Ubuntu via wubi on the E partition on a LiveUsb and uninstall wubi, but it didn't work. I then made a Windows repair disc to repair MBR and ran the following 2 commands on the command prompt: bootrec /fixmbr & bootrec fixboot, but it didn't work either.

I have read about something called super grub 2, but haven't tried it, nor do I know if it will work. Am also afraid that I might make it worse if I use it cause I don't have much knowledge when it comes to fixing computer issues. Anyone have any idea on how I can fix this?

---

### Post by MG&amp;TL on 2012-10-01
Problem is that Wubi doesn't make a partition *per se*, but it does make an entry in the Windows bootloader (note not the MBR). I have no idea how to rectify that, try uninstalling it. To my knowledge, it should still be in the programs thing.

---

### Post by UniversalCyborg on 2012-10-01
That's the problem, I can't find the wubi file anywhere, not even if I enable "show hidden files, folders, and drives". I've tried doing a search for it, but nothing.

It's weird because when I reinstalled Ubuntu on the E partion I installed it with an option of 16 gigs, but the size was bigger as if there is still something on that particular partition. I formatted the E partition, but it didn't help.

---

### Post by deadflowr on 2012-10-01
It should be in your add/remove program stuff.
Wubi is a program, not a file.

---

### Post by bcbc on 2012-10-01
Check this out: [http://askubuntu.com/a/145605](http://askubuntu.com/a/145605)

It shows how to remove the entry from the BCD.

---

### Post by critin on 2012-10-01
How did you install Wubi?  It should be on the same partition as Windows.

[https://wiki.ubuntu.com/WubiGuide#How_do_I_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_uninstall_Wubi.3F)

---

### Post by UniversalCyborg on 2012-10-01
No, it is not on add/remove programs list.

I didn't really install wubi, it installed it for me when I used the live cd.

Anyway, I fixed the problem. I did what the thread said that bcbc pointed me to and it worked. Thanks!

---

