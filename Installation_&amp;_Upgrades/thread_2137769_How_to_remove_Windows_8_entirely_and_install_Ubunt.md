---
title: "How to remove Windows 8 entirely and install Ubuntu 12.10 solely."
date: 2013-04-21
forum: Installation &amp; Upgrades
---

### Post by rephaelhermon on 2013-04-21
I have a Windows 8 laptop and I first created a Ubuntu 12.10 DVD to test it out. I liked it so much that I installed it alongside Windows 8. Can someone help me with how I can basically remove Windows 8 entirely and leave Ubuntu 12.10 running solely on the laptop? Do I have to reinstalled Ubuntu 12.10 or is there another way? Thanks!

---

### Post by carl4926 on 2013-04-21
> [COLOR=#000000]Do I have to reinstalled Ubuntu 12.10[/COLOR]Ideally yes

---

### Post by oldfred on 2013-04-22
It depends on your partition layout and how you may want it going forward. As carl4926 says it will make the reorganization cleaner. But it does not necessarily have to be done.

May be best to still make a full backup of your Windows 8 partition. Some users like Ubuntu but then find one program or game that they cannot live without and want Windows back. Full backup makes it a lot easier to reinstall.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Post this and we can suggest some alternatives.
      
  sudo parted /dev/sda unit s print

---

### Post by fantab on 2013-04-22
I'd say, "hang on to your Windows", at least until such time that you are comfortable with Ubuntu and you no longer miss Windows. Keep Dual-Booting. After all you must've paid for your Windows copy. Though I haven't visited Windows 7 in more than 2 years, I still have it around. 

My two cents...

---

### Post by slickymaster on 2013-04-22
Besides all the good advises mentioned above, you might also see this one:
[How To Remove Windows]("https://help.ubuntu.com/community/HowToRemoveWindows")

---

### Post by rephaelhermon on 2013-04-22
Thank you everyone! Originally, this software of Windows 8 came with the Windows 8 pc so I didn't really buy it separately. I really don't have a need for it anymore, it's VERY slow compared to Ubuntu 12.10 and there's nothing holding me to need to keep Windows at the moment. If I make the partition for Windows 8 of a smaller size, would it affect the functioning of Windows 8 if I ever needed to use it and decided to keep it around?

---

### Post by fantab on 2013-04-22
Particularly Windows works best if the c: or partition with system files has atleast 25% of free space, after everything. Use ONLY windows tool to SHRINK the Win8 partition. Don't try to create Linux partitions with it. You can later use Gparted partitioning tool from Ubuntu CD/USB to create/expand those later. 

Ubuntu 13.04 will be released shortly. I suggest you go for it. And preferably do a clean install. Its better than 12.10, IMO.

By the way, you have paid for Win8 even if it came pre-installed and you just were not billed for it separately. Its Microsoft. But thats not the point. 

Good Luck...

---

### Post by rephaelhermon on 2013-04-22
Alright I'll try that. I'm going for 13.04 when it comes out in the release. Microsoft............. :|. lol

---

### Post by slickymaster on 2013-04-22
> **fantab said:**
> Particularly Windows works best if the c: or partition with system files has atleast 25% of free space, after everything. Use ONLY windows tool to SHRINK the Win8 partition. Don't try to create Linux partitions with it. You can later use Gparted partitioning tool from Ubuntu CD/USB to create/expand those later...

Solid +1 on fantab's advice.
Also, and merely as a guideline, consider 16GB for Win8 x86 and 20GB for Win8 x64, as minimum partitions sizes.

---

