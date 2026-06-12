---
title: "Ubuntu 9.10 Does Not Detect Partitions"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by riku88 on 2009-11-16
Hello, I'm trying to install Ubuntu 9.10. I am currently trying Ubuntu before installing it, via DVD; and running the "Install Ubuntu" shortcut on the desktop.
I've gone through the steps and reached number 4, where it asks you where to install it. All that is says is my harddrive, and no partitions. I try specifying the partitions, but there are none there, aside from something called /dev/sda
I have 4 partitions: Windows, Data, Music, and Ubuntu. I want to install ubuntu on the Ubuntu partiton. How do I do this? Or do I delete that partition and leave free space?

Thanks in advance,
-Riku

---

### Post by weaselnet on 2009-11-17
Open synaptic package manager, search for dmraid, uninstall top two listed and restart the install.

---

### Post by riku88 on 2009-11-17
Should I "try ubuntu before installing" again? Or just install it there?

---

### Post by weaselnet on 2009-11-17
Try and after the previous steps launch the install from the desktop.

---

### Post by riku88 on 2009-11-17
I tried that, and it's still the same. No partitions or anything.

---

### Post by weaselnet on 2009-11-17
I booted to the live CD. When trying to install it would not recognize my drives. I quit the install, but never rebooted. Went to synaptic package manager and removed the top two dmraid options that were listed from a search. Then started the install over and my partitions showed.

---

### Post by darkod on 2009-11-17
I don't have any idea about the problem with not showing the partitions, but just to point out something further.
You said you already have Ubuntu partition that you want to install onto. If you created this from windows (ntfs partition), you will still have to use manual partitioning, delete the whole partition and set up ext4 partition(s) for Ubuntu.
The minimum you need / (root) partition with filesystem ext4 and swap partition the filesystem is called just swap too. You might wanna think whether you want separate /home.
Since you already have 3 windows partitions, if all of them are primary, when installing ubuntu at the manual partitioning you need to start creating the above mentioned ubuntu partitions as logical. You can't have 5 primary partitions (3 windows + / + swap).

---

### Post by riku88 on 2009-11-17
@weasel
I restarted the computer, and then ran the install. The two dmraids weren't there, but do you think it could have done anything?

@darkod 
So I should delete the partition, and make a new ext4 partition? Or logical?
I'm pretty sure their all logical partitions. But I may just have one for Windows.
/home? I didn't see that anywhere
Wait...
So this is what I think you told me:
Delete the ubuntu partition, and turn the space to make a new partition in the "Choose you're own partition" choice in the Ubuntu installer.

Is this right?
-riku

---

### Post by riku88 on 2009-11-17
Fixed! I got it to work by making some unallocated space in Windows, and using "all continuos free space" to install Ubuntu.
Thanks!
-riku

---

