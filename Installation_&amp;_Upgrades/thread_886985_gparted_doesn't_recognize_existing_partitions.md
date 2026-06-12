---
title: "gparted doesn't recognize existing partitions"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by giosetti on 2008-08-11
Dell 640M. 

These are the existing partitions:

[IMG]http://img390.imageshack.us/img390/3818/fdiskmodified2al9.png[/IMG]

And this is what gparted recognizes:

[IMG]http://img143.imageshack.us/img143/5273/gpartednq4.png[/IMG]

What's the problem?

---

### Post by Pumalite on 2008-08-11
Try Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by giosetti on 2008-08-11
I could do this but the problem remains because I want to replace my existing 7.10 by a clean install of 8.10, so the problem arises during the installation process. I might alter the layout of partitions (which by the occasion of clean install I want to perform) but I'm scared once I start the 8.10 installation the partition tool in the installer will again fail to detect the existing partitions.

---

### Post by Pumalite on 2008-08-11
With Gparted Live CD you can prepare your drive ahead of time, then go 'Manual' and use the prepared partitions.

---

### Post by giosetti on 2008-08-11
Yes, but "manual" doesn't recognize the existing paritions so I wonder why manual detects them after the changes. Anyway I'll give it a try - thanks for the suggestion.

---

### Post by giosetti on 2008-08-11
so I've downloaded, burned and performed Live gparted and it doesn't detect the partitions either.

---

### Post by Pumalite on 2008-08-11
Post your specs in detail. You will need some boot parameters it seems. 
You could try adding all_generic_ide at the end of your boot line in the Ubuntu Live CD.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by amlucent23 on 2008-11-05
sorry to res a dead thread but I am have this same problem with my ubuntu install. 

I had vista and 8.04 installed on my Dell XPS M1530.  I upgraded my 8.04 to 8.10 on release day but my 8.04 was really fairly custom and it borked some stuff and I just decided to blow it away and install 8.10 fresh over the existing copy (but still keep the vista partition).  When I boot up the live CD it only gives me the option of the entire disk.. if I go to manual there is no drive info listed just like in the guy aboves pic.

I dont understand what could be preventing gparted from reading my partition table. There is no encryption or anything on the disk.

Any suggestions are appreciated!

---

### Post by Les Oeufs on 2008-11-05
I'm having the exact problem. I have two drives. One 120 gb drive, one 300 gb drive. Before, my 300 gb was sda and had windows/ubuntu 7.04 (which was upgraded up to 8.04). No troubles installing. I wanted to upgrade, so I formatted the disk with gparted on the live cd, and formatted the 300 gb to NTFS. Then I installed Windows XP on it without trouble. I booted off the ubuntu live cd, and nothing recognizes whats going on with the 300 gb. Its seeing the 120 gb (a file storing drive I have) as sda, and knows that its NTFS. But it sees the 300 gb drive as sdb and 'unallocated' as far as the file system goes. The installer is also unaware that its already been formatted.
If I mount the 300 gb, I can browse the files and all the stuff on there. For some reason gparted and the installer are screwed.

---

### Post by amlucent23 on 2008-11-06
bump, has anyone else experienced this or found a fix?

---

### Post by amlucent23 on 2008-11-06
Bump bump bump

---

### Post by ubiubi on 2008-11-08
Hi
I have the same problem. Xp has installed and now functions without any problems (I did have a 'volume device' detected window pop up at every startup but I reintoduced my xp Disk and it loaded the necessary drivers/ files and so everything works great!) The real problem lies with linux. I have six or seven other partitions (three empty) dedicated to Ubuntu/swap/home partitions, another empty ex3 partition and an empty FAT partition. These were all origionally created under Gparted live cd. Since I changed the motherboard (now its ABIT for intel, the disk was prepared and operated perfectly with AM2 ASUS board) and all these problems have arrived. Windows started  with ne reinstallation necessary. Ubuntu refused. I tried to install Ubuntu again and it failed when it tried to prepare the disk for partitioning. PSclos reported there was no available space during an attempted install, and Fedora claimed my volume did not exist! Now Gparted gives the same screen and message as reported by peaople at the start of this thread. How can I reinstall Ubuntu (or any linus for that matter) ?
Mant thanks for any suggestions

---

### Post by Janherbergh on 2008-11-08
Same problem here. I have a dual boot (windows x and ubuntu 8.04) and wanted a fresh kubuntu 8.10 install. At the time of manual partition, the application doesn't recognize hda, which has 4 partitions (windows, ubuntu, swap and data).

---

### Post by GokuH12 on 2008-12-08
I have the exactly same problm, just installing ubuntu 8.10, i when i get to the partition part, it dont recognize all my partition, just show the disc like if it were new!, the odd thing its that i can see all my partition from the nautilus and navigate it!

---

### Post by damnhappy on 2008-12-20
I have the same exact problem on a Dell M1210.

---

### Post by kumquatkowboy on 2009-01-09
I have this problem too. Did anyone ever find a way round? I suppose not, given the deafening silence in here...:confused:

---

### Post by llamakc on 2009-01-20
> **Pumalite said:**
> Post your specs in detail. You will need some boot parameters it seems. 
You could try adding all_generic_ide at the end of your boot line in the Ubuntu Live CD.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)


Adding all_generic_ide solves this problem. Thanks, Pumalite.

---

### Post by cdoublejj on 2012-09-30
I'm having the opposite problem with Lubuntu 12.04, I have one big ntfs partition and 1 tiny 100mb partition and sees all kinds of non existent partitions, such as fat 32 and sda2 unkown etc.

I have a single wd 250gb drive.

---

### Post by coffeecat on 2012-09-30
Old thread closed.

@cdoublejj, please start your own thread for your problem giving full details of what you are seeing and what you want to achieve. 

They are not non-existent partitions. They would be hidden partitions associated with Windows and which Windows would not show. I suggest you include a screenshot of Gparted, if this is what is showing your partition layout, with your new post.

---

