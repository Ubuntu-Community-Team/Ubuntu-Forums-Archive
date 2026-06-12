---
title: "grub broke after wubi upgrade"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by rkshack on 2010-08-18
I beleive I had version 9.x installed. I upgraded once and everything was fine. I went the upgrade manager again and it found some more upgrades. The upgrade messed with grub. It then told me there were no new upgrades. Then I rebooted and it says
 
Try (hd0,0): NTFS5
 
Then the screen clears and there is some text I can't read and then it says command not found. Then it reboots. 
 
Is there a way to fix this?
If not is there a way to recover the files from the disk image file.
 
rkshack

---

### Post by bcbc on 2010-08-18
You can certainly mount and copy data off the root.disk. If you have an Ubuntu CD you can boot it in Live CD mode (try without installing) and then mount the root.disk file and copy from there.

Or there are also tools available to view the contents of the file from Windows.

The [wubi-guide]("https://wiki.ubuntu.com/WubiGuide#How can I access the Wubi files from Windows?") has details. (you probably need the one that supports ext4 since 9.10 uses that)

I recommend backing up the root.disk (it's in c:\ubuntu\disks\ folder - or change c:\ if you installed to a different drive). Back it up outside of the c:\ubuntu directory otherwise if you uninstall/reinstall it will be lost.

I'm going to see if I can repair the current wubi. Can you describe in detail which updates you did? Are you still running 9.10 or did you upgrade to 10.04?

Did you install initially using 9.10? And if so, did you see this problem? [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

