---
title: "Lost grub2 boot"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by deeppow on 2010-06-05
Installed Win7 on new SSD, NTFS drive C;.  Ubuntu was on separate hard drive. There are also NTFS partitions (D: and E:) on a second hard drive so if I boot from Live CD and do an "fdisk -l" then I see

/dev/sdb1 .... NTFS
/dev/sda2 .... NTFS
..
/dev/sdb5 ... Linux
/dev/sdb6 ... Linux swap

Doing it from memory, but I'm sure the Linux partition was sdb5.

How do I replace the grub2 that was lost due to the Win7 install so I can boot either Ubuntu or Win7?  If the procedure exists somewhere (a dummies version), please point me to it.

Thanks for any assistance.:)

---

### Post by kansasnoob on 2010-06-05
Look here for general instructions:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But if you need more detailed help please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by deeppow on 2010-06-05
I did the first one and it didn't work (of course I might have screwed up).  Should I be restoring it to "sba"?  

I'm assuming Win7 is on sba since I only see what appears to be the two partitions on my hard drive.

---

### Post by karthick87 on 2010-06-05
Look here this may help you,

[http://ubuntuforums.org/showthread.php?t=1502430](http://ubuntuforums.org/showthread.php?t=1502430)

---

### Post by oldfred on 2010-06-05
Post the script kansasnoob suggested as then we can give specific suggestions.

Do you have BIOS set to boot sda or sdb? I like to have my boot loaders on the same drive as the install but with your SSD do you want to boot sda all the time?

---

