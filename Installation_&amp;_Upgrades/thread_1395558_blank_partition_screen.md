---
title: "blank partition screen"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by jaycount on 2010-02-01
I'm installing Koala here on a 250gb Sata drive. I am looking to dual boot with Win7. I've got a 80gb Win7 partition and the rest is unallocated so I can install Ubuntu on to it. If I try to install, I get to the manual partition screen and it's blank. From what I can tell, Ubuntu isn't recognizing my hard drive at all. When I boot into the liveCD and run gparted, it says no devices found. Also when I boot gparted from a cd I get the same thing. BIOS sees the drive fine and the drive boots into Windows fine. 

When I run "sudo fdisk -l" I get nothing. I've tried several of the flags including all-generic-ide. Also tried removing dmraid. I'm at a loss here. Any ideas?

---

### Post by byStanderone on 2010-02-01
...take your time, anyway you have your win7, take a look at this guide, specially the section dealing with updates...refrain from doing steps that you are not sure of.

---

### Post by jaycount on 2010-02-01
What guide?

---

### Post by jaycount on 2010-02-01
I tried the alternate cd today and it said the drive could not be found and to select a driver.

Ideas?? :popcorn:

---

### Post by lindsay7 on 2010-02-01
I would boot into windows and use the windows partition tool to delete and reformat the unallocated or blank or empty partiton or whatever it is that is there.  After you make sure that windows sees the partitions and they are as you want them, try the manual ubuntu install again.

---

### Post by jaycount on 2010-02-02
Tried that. Still no dice. I have a new HD showing up later this week, I suppose we'll see what happens then.

---

### Post by darkod on 2010-02-02
> **lindsay7 said:**
> I would boot into windows and use the windows partition tool to delete and reformat the unallocated or blank or empty partiton or whatever it is that is there.  After you make sure that windows sees the partitions and they are as you want them, try the manual ubuntu install again.

If it's not the dmraid issue I have no idea what is the problem but just to remind the OP that any partitions created from windows are useless for linux. Even if windows is able to create a partition out of the unallocated space it will only be able to format it as ntfs. So all the guided options of the ubuntu installer would not be available and in fact you could only use manual partitioning in step 4 first to delete the ntfs partition, and then create your partitions for ubuntu instead, also manually.

---

### Post by neamhaol on 2010-02-02
Ok, I had this same problem a week ago. It has to do with certain sata controllers on certain motherboards not liking linux. The fix is not to big of a hassle.
 
First, when use alternate cd.
1. On CD menu hit F6 to bring up the extra boot options. I dont select any options and hit ESC. This shows an editable command line. You want to delete the -- and add the command pci=nomsi to the end of the line and hit enter. This will show hd in partitioner.
 
2. After install when grub loads and gives you your options of what to boot, highlight the normal boot option and hit e to edit it. There will be a line that ends with the word splash. Delete splash and again add pci=nomsi. If you do not do this then you will get a busybox prompt on boot.
 
3. After inside the OS you have to edit your grub file in the /etc/default/grub path. I forget the actual line but Im pretty sure it says splash again, should be semi-close to the top of the file. You need to add pci=nomsi and delete splash one last time to add it into the grub permenantly.(To edit this file I right click in the open space next to the file and go to open with root or something along those lines since this folder is readonly with root permissions. Afetr editing this file, open the terminal and type update-grub to save it.)
 
Id send you the link I used to get me started but I cant find it, plus it does not really apply to grub2 so it took some translating and trial and error to get where I did.

---

### Post by jaycount on 2010-02-03
> **neamhaol said:**
> Ok, I had this same problem a week ago. It has to do with certain sata controllers on certain motherboards not liking linux. The fix is not to big of a hassle.
 
First, when use alternate cd.
1. On CD menu hit F6 to bring up the extra boot options. I dont select any options and hit ESC. This shows an editable command line. You want to delete the -- and add the command pci=nomsi to the end of the line and hit enter. This will show hd in partitioner.
 
2. After install when grub loads and gives you your options of what to boot, highlight the normal boot option and hit e to edit it. There will be a line that ends with the word splash. Delete splash and again add pci=nomsi. If you do not do this then you will get a busybox prompt on boot.
 
3. After inside the OS you have to edit your grub file in the /etc/default/grub path. I forget the actual line but Im pretty sure it says splash again, should be semi-close to the top of the file. You need to add pci=nomsi and delete splash one last time to add it into the grub permenantly.(To edit this file I right click in the open space next to the file and go to open with root or something along those lines since this folder is readonly with root permissions. Afetr editing this file, open the terminal and type update-grub to save it.)
 
Id send you the link I used to get me started but I cant find it, plus it does not really apply to grub2 so it took some translating and trial and error to get where I did.

This fixed it. You da man!!:D

---

### Post by majomkutya on 2010-07-02
Hi all, 

I had a similar issue with Ubuntu 10.4 with my 40GB IDE HDD. What I started with was an NTFS file system and win xp professional on the drive.
When it came to partitioning the drive, the prepare partitions window (step 4 of 8) was blank and the buttons were inactive, grey...

My first guess was that I would need to make a partition with Linux exp3 file system. So I created one with Partition Magic 8. This did not help, the window in question was still useless.

The second thing I tried - and this one worked out - that I plugged the target drive as slave in another computer (win xp and Partition Magic 8. also) and formatted it for one partition and linux exp3 file system.

After this I could finish the installation of Ubuntu 10.4 in the original pc.
I hope this helps some of you :D

majomkutya (monkeydog)

---

