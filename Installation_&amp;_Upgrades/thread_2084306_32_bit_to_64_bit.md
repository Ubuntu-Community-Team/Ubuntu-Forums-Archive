---
title: "32 bit to 64 bit"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by Jacob-Gates on 2012-11-15
I put a thread up a while about about my computer being 32 bit but this is a different question. I wanted to update my computer with 12.10 64 bit but I have no idea if I do it if I will lose my files (pictures, music, etc.). Will I? If so how do I do this to keep my files?

---

### Post by Pand5461 on 2012-11-15
Hi!
I'd suggest to back up your home directory (do not forget the hidden directories) to some external media (USB hard disk, DVD, whatever). This will back up the files and also your preferences which are usually stored in hidden text files in the home dir. After reinstalling the system, all you have to do is copy the saved data back to the home dir.
If your home directory is on a separate partition, the things are even simpler. Then you'll have to choose that partition for use as /home at installation and do not format it. All files will be totally safe (although backing up is never a bad idea).
You'll probably have to install the program you use once again after reinstallation.

---

### Post by Jacob-Gates on 2012-11-15
> **Pand5461 said:**
> Hi!
I'd suggest to back up your home directory (do not forget the hidden directories) to some external media (USB hard disk, DVD, whatever). This will back up the files and also your preferences which are usually stored in hidden text files in the home dir. After reinstalling the system, all you have to do is copy the saved data back to the home dir.
If your home directory is on a separate partition, the things are even simpler. Then you'll have to choose that partition for use as /home at installation and do not format it. All files will be totally safe (although backing up is never a bad idea).
You'll probably have to install the program you use once again after reinstallation.

Okay, how do I find out if my /home directory is on a separate partition or not? Also I have a dual boot system, will any of this affect the windows side? (a friend of mine set all this up for me because I wanted to learn so I am still learning).

---

### Post by oldos2er on 2012-11-15
> **Jacob-Gates said:**
> I put a thread up a while about about my computer being 32 bit but this is a different question. I wanted to update my computer with 12.10 64 bit but I have no idea if I do it if I will lose my files (pictures, music, etc.). Will I? If so how do I do this to keep my files?

If your processor is 32-bit, 64-bit won't install. ```
cat /proc/cpuinfo
``` will let us know if its 32- or 64-bit.

Backup any files you want to save first.

---

### Post by Mr_JMM on 2012-11-15
> **Jacob-Gates said:**
> Okay, how do I find out if my /home directory is on a separate partition or not?.

Please copy result of ```
sudo fdisk -l
```

Also, if you use something like disks or gparted app these will give you an idea.

---

### Post by Jacob-Gates on 2012-11-16
> **oldos2er said:**
> If your processor is 32-bit, 64-bit won't install. ```
cat /proc/cpuinfo
``` will let us know if its 32- or 64-bit.

Backup any files you want to save first.
my computer is definitely 64 bit. I have a dual boot with windows 64 bit on the other side. For some reason my friend put 32 for ubuntu.

> **Mr_JMM said:**
> Please copy result of ```
sudo fdisk -l
```

Also, if you use something like disks or gparted app these will give you an idea.

Here you go:
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcffc1206

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2           80325    30800324    15360000    7  HPFS/NTFS/exFAT
/dev/sda3   *    30800325   453404740   211302208    7  HPFS/NTFS/exFAT
/dev/sda4       453406718   625141759    85867521    5  Extended
/dev/sda5       453406720   616839167    81716224   83  Linux
/dev/sda6       616841216   625141759     4150272   82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 16005464064 bytes
64 heads, 32 sectors/track, 15264 cylinders, total 31260672 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
```

---

### Post by varunendra on 2012-11-16
> **Jacob-Gates said:**
> For some reason my friend put 32 for ubuntu.I would have done the same thing a couple of years ago, due to my doubts about 64 bit's compatibility and stability. But now I've grown smarter :)

> **Jacob-Gates said:**
> ```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2           80325    30800324    15360000    7  HPFS/NTFS/exFAT
/dev/sda3   *    30800325   453404740   211302208    7  HPFS/NTFS/exFAT
/dev/sda4       453406718   625141759    85867521    5  Extended
[COLOR=DarkRed][B]/dev/sda5       453406720   616839167    81716224   83  Linux
[/B][/COLOR] [COLOR=Navy]**/dev/sda6       616841216   625141759     4150272   82  Linux swap / Solaris**[/COLOR]

```
As you may figure out yourself, you have [COLOR=DarkRed]**only one**[/COLOR] linux partition, the other one is swap partition. Means no separate /home.

Just boot off the live cd, and copy the **/home/*<your id>*** directory onto an external media, done!

---

### Post by Jacob-Gates on 2012-11-17
> **varunendra said:**
> I would have done the same thing a couple of years ago, due to my doubts about 64 bit's compatibility and stability. But now I've grown smarter :)


As you may figure out yourself, you have [COLOR=DarkRed]**only one**[/COLOR] linux partition, the other one is swap partition. Means no separate /home.

Just boot off the live cd, and copy the **/home/*<your id>*** directory onto an external media, done!

okay, awesome! thank you so much. You just helped me more than anyone else ever has with linux so THANK YOU very much.

---

### Post by varunendra on 2012-11-17
Anytime !

And..> **Jacob-Gates said:**
> [COLOR=DarkRed]**You**[/COLOR] just helped me..I take it as "[COLOR=DarkRed]**all of you**[/COLOR]".. because you just quoted me while the help was offered by others, I  just read out to you the result :)

Feel free to ask questions, starting threads in relevant sections, whenever you need help with Ubuntu.

Hope you'd enjoy the OS and the community here too !

---

### Post by Jacob-Gates on 2012-11-17
> **varunendra said:**
> Anytime !

And..I take it as "[COLOR=DarkRed]**all of you**[/COLOR]".. because you just quoted me while the help was offered by others, I  just read out to you the result :)

Feel free to ask questions, starting threads in relevant sections, whenever you need help with Ubuntu.

Hope you'd enjoy the OS and the community here too !

yeah I definitely meant everyone, I'm bad about just quoting the last post. haha thank you for clearing that.

---

