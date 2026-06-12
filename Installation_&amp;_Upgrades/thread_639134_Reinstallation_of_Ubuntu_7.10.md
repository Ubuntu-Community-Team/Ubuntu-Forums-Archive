---
title: "Reinstallation of Ubuntu 7.10"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by anilbhx on 2007-12-12
I have a working Ubuntu installation . However I feel that somewhere I have created problems with the configuration. 
Some of the problems are :
1. Blender dies on startup .
2. Another program K3d does not have its main features working. 
3. The printer/scanner( HP PSC1315 ) was recognized and installed by Ubuntu , then it stopped installing the Printer and I got it back again after downloading and installing HPLIP from the sourceforge site. Not through apt.

I had started off by installing a version prior to 7.10 and upgraded over broadband.
 
Later I burnt a 7.10 live CD ( checked for integrity md5sum etc. ) 

[B]Now the problem is that when I try to install it just does not get further "*than detecting filesystems". *I have tried this about 3 or 4 times . 
This problem was there when installing the previous version . However on the 2nd attempt it used to go through ( [/B]for various reasons I had to install more than once on the same partition ) .

---

### Post by src2206 on 2007-12-12
While reinstalling, do you choose to partition and format againor you chose to keep the existing data?

---

### Post by anilbhx on 2007-12-13
I choose to format as I have a backup.

---

### Post by src2206 on 2007-12-13
In these kind of situations, I personally feel that you should try to install agin and afresh.

---

### Post by anilbhx on 2007-12-14
that is what I am trying to do . It is getting stuck at "detecting file systems" while starting afresh ...

---

### Post by src2206 on 2007-12-16
Do you have a number of partitions in your HDD? In that case sometimes Ubuntu needs a little bit more time than normal to detect all the partitions.

See I am not a geek in any way and I faced a similar problem. And I have a non geeky solution which worked for me. 
I have used GParted (the free partition manager) to delete the partition where Ubuntu was originally installed and also the SWAP partition (you should have a separate partition for SWAP file of about double the size of your RAM). So I had two unpartitioned free spaces. Then I rebooted using Ubuntu Live CD and the free spaces were easily recognized.  
You can try this method. There is a pictorial link in my sig for GParted, you can try that if needed. :)

---

