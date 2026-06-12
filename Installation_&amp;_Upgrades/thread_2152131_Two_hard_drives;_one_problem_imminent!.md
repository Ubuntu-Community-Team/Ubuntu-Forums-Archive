---
title: "Two hard drives; one problem imminent!"
date: 2013-06-06
forum: Installation &amp; Upgrades
---

### Post by Vormeph on 2013-06-06
[B]Currently, I am a Windows user who through another laptop already uses Linux and am ready to migrate my main laptop from Windows to Linux. I have been using Linux for almost a year now and am familiar with most of the functionality it provides; however when it comes to managing partitions/memory I have always been lax in understanding such a concept, including on Windows.
[/B]
I want to explain my situation very carefully since it's quite complicated:

I have two hard drives. They are both 500 GB. Both hard drives serve a purpose under my current Windows installation in which the second drive serves as extra memory for anything like games, music, or else multimedia related and the first hard drive serves as the basis of the Windows installation. For obvious reasons, most of my games won't work on Linux: I would format my second hard drive beforehand. Wherefore, I want the first hard drive to be where Xubuntu is installed on and thereafter use the extra memory from the second hard drive as spare memory rather than something disowned/ignored by the new operating system. There is a problem though, and it concerns how I should get Xubuntu to access the memory on my second hard drive. How do I go about this? I don't really want to create partitions but rather Xubuntu to include the memory of my second hard drive. That way, my hard drives will behave as though they were literally one single hard drive with a total memory of 1 TB. 

One solution I had was to use gParted and explicitly allocate the extra memory from the second hard drive, although I was not aware how. Already I am unsure as to what to do and am not willing to install Linux until I am absolutely clear as to what I need to do the moment I boot into my new installation. I do not want to boot into a Linux installation and find out that my second hard drive isn't being used at all; I want to find some way in getting Xubuntu to use my second hard drive so that it is able to configure the second hard drive and recognise it like the first hard drive. Infact, I would go as far as to say that I would install programs/multimedia on my first hard drive and have a /home folder use all the memory from the second hard drive. There are various ways to go about this, but I don't know where to start and it is indeed a gap in my knowledge herein which I seek to resolve.

What must I do to make the /home folder use all memory from the second hard drive, assuming that the **first** hard drive will be the sole hard drive for program/multimedia installation?

Thank you - sorry for the long post.

---

### Post by ahallubuntu on 2013-06-06
~

---

### Post by Vormeph on 2013-06-06
I think you misunderstood me. I want to replace Windows as my operating system with Xubuntu. I am under the impression that relevant partitions are created automatically by the installation. I require instructions as to how I can make use of my second hard drive's storage for use in the /home folder.

---

### Post by steeldriver on 2013-06-06
I haven't installed Xubuntu since 11.04 however it shouldn't be a problem to select 'something else' and manually partition everything however you want

Having said that, if you put /home on one of the 500GB disks, the other 500GB is way more than you probably need for 'everything else' - so you may want to look at using the alternate install iso, which should allow you to set up an LVM volume spanning *both* disks, and then do a regular single partition install on that - probably that would be my choice for your situation

[http://cdimage.ubuntu.com/xubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/xubuntu/releases/12.04/release/)

---

### Post by Vormeph on 2013-06-06
Can't I just set up VLM through the standard installation and have that span both disks? It would be much better if it did, and when I attempted so I could only select one of the hard drives through the standard installation. :-/

---

### Post by oldfred on 2013-06-06
I am not a fan of LVM. More because one of the disadvanages is if one drive fails you lose all data. I actually want and have a system on every drive including every flash drive. I have every drive fully bootable without any other and have data in other drives but linked back into my /home so it is just about seemless.

 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
lvm info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by Vormeph on 2013-06-07
That post confused me even more. So what's better? LVM or manual partitioning? I might use manual partitioning but only after the installation of Xubuntu. In which case, I need to link the /home folder to the second hard drive. I am still rather puzzled as to how I should do this though.

---

### Post by darkod on 2013-06-07
To join two disks in one logical storage area you would usually use LVM (although raid0 is an option too). The disadvantage is what oldfred mentioned, if one disk dies, you lose the data. For raid0 this is definitely true, I'm not 100% for LVM.

But if you make regular backups of all the important data, you probably can take the risk and simply use LVM.

The decision is yours. As long as you make backups of the important stuff, you should be fine. If you really insist on having the storage space as one continuos space, I would use LVM.

---

### Post by Vormeph on 2013-06-07
I want to explore all the options first. I am aware that LVM allows storage to span both my hard drives which is ideal, albeit the disadvantage does appear quite logical since both hard drives behave as one, which is what I intended. Although, I think knowing more about how to manually partition my drives after installation may also be beneficial, without the need for LVM. The only problem with manual partitioning is that it requires unmounting and mounting drives if in the event I want to use more space from one drive to another. Because I would have an empty 500 GB drive as my second hard drive, its storage can easily be allocated to the root partition and/or having a completely separate /home partition that so happens to use the storage from the second hard drive. Given the abundance of storage I have, it is unlikely I'm going to allocate more space than required unless it's absolutely necessary. 

I'm currently looking for a guide that allows me to create a separate /home partition, but a few guides appear to be out of date.

---

### Post by oldfred on 2013-06-07
Once you want data partitions, I suggest no separate /home as that is what I use. My /home is about 2GB so easy to backup and all my data is in data partitions. Then folders in the data partitions are linked into my /home. I replace standard Video, Documents, etc with links to folders in the data partitions. See post #6 on splitting /home for details on how and other comments.

---

### Post by darkod on 2013-06-07
Be careful in your planning. It sounds to me like you think the empty disk can be used later to expand root or /home into it. A partition will NOT be able to span two different physical disks. That's the role of LVM where the Volume Group spans different disks and the Logical Volumes use as much space as you allocate to them. You then use the LVs as mount points. You can expand LVs while the system is running which is a benefit. That's why you start with small LVs and grow them as you need them.

In any case a simple partition can NOT span two disks, have that in mind.

---

### Post by Vormeph on 2013-06-07
Assuming that the integrity of my hard drives remain intact, LVM is probably the safest option for me. Although, when I do select an LVM installation through the standard Xubuntu installation, I still need to select ONE of the 500 GB hard drives. Am I missing something here?

---

### Post by darkod on 2013-06-07
I don't think it uses more than one disk with the automatic method. Have you tried selecting both disks? If there is a text menu, you select with Space bar.

One option is to install using LVM using the first disk, and then add the second disk to the LVM yourself.

Or, install using the manual partitioning, which will allow you to select both disks (the partition on them) as part of the LVM and install like that.

---

### Post by Vormeph on 2013-06-07
I tried both methods - neither allow me to select both hard drives. I suspect this is something I have to configure in post-installation stage regardless of the configuration being LVM or otherwise.

---

### Post by darkod on 2013-06-07
I just remembered, are you using the alternate cd or the standard live cd? The LVM support was earlier included only on the alternate cd. Now days I think the live cd also offers LVM installation but I think with limited possibilities.

You can definitely use two disks for LVM in the alternate installer. But for 13.04 and maybe 12.10 the alternate cd seems to have been dropped. I use the 12.04 LTS version because it has long term support, and it still has the alternate image for download.

Without the alternate cd you would have to install on one disk and later expand the LVM, or boot into live mode, add the lvm2 package (if not already there), and prepare the LVM before starting the installer. Then when you start it, the LVM using both disks will already be there.

---

### Post by Vormeph on 2013-06-07
> **darkod said:**
> I just remembered, are you using the alternate cd or the standard live cd? The LVM support was earlier included only on the alternate cd. Now days I think the live cd also offers LVM installation but I think with limited possibilities.

You can definitely use two disks for LVM in the alternate installer. But for 13.04 and maybe 12.10 the alternate cd seems to have been dropped. I use the 12.04 LTS version because it has long term support, and it still has the alternate image for download.

Without the alternate cd you would have to install on one disk and later expand the LVM, or boot into live mode, add the lvm2 package (if not already there), and prepare the LVM before starting the installer. Then when you start it, the LVM using both disks will already be there.

So I have to use the alternate installation in order to use LVM on both disks at ease? It appears to be more complicated to use LVM via the standard installation, but maybe that's just my lack of experience in anything to do with hard disks anyway.

---

### Post by darkod on 2013-06-07
Talking about easy or difficult is subjective. Setting up lvm in terminal in live mode is not very difficult too, but I guess the alternate installer helps you do things simpler, which which is what you need when new to these things.

---

### Post by Vormeph on 2013-06-07
> **darkod said:**
> Talking about easy or difficult is subjective. Setting up lvm in terminal in live mode is not very difficult too, but I guess the alternate installer helps you do things simpler, which which is what you need when new to these things.

I don't know how to set up LVM through the terminal; I require knowledge of which commands to execute. In the end, it's really something I have to choose nonetheless.

---

### Post by darkod on 2013-06-07
This should get you started:
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

Note in the second link that personally I don't like creating partitions with fdisk as they did. It's better to use parted in terminal or Gparted in GUI. Since you will be doing the preparations from live mode, you can use Gparted for creating the partitions if GUI is easier for you. After that continue with the lvm tutorial in the terminal.

---

### Post by Vormeph on 2013-06-07
How does your method of setting up LVM differentiate from the way LVM is setup through the standard installation window?

EDIT: I've just run an experiment on VirtualBox:

I have created three hard drives in Session 1 and Session 2. The hard drives are approximately equal in storage. I used Xubuntu 13.04 64-bit.

In Session 1, I have used your method, following the instructions through the terminal and successfully setting up LVM as required. I then used system-config-lvm to allocate the extra space from the second and third hard drives of the VirtualBox to the first hard-drive. This too was successful and I managed to expand the lv-root/home whatever partitions I created before. 

In Session 2, I decided to use the standard installation menu and use LVM through the radio button. I got my system up and running and then used system-config-lvm and did the exact same steps as before. I am not sure what the differences internally are, but as far as I am concerned both results are practically the same. 

Is one way of setting up LVM superior to another?

---

### Post by darkod on 2013-06-08
Both results turned out same because in the first option you created the LVM from one disk too. The idea was to create it from both disks right away, as you want it to be. So, it would be something like this:

Both disks will have a single big partition taking the whole disk, /dev/sda1 and /dev/sdb1.
Mark them as physical devices for LVM with:
sudo pvcreate /dev/sda1 /dev/sdb1
Make the VG use both of them right away:
sudo vgcreate VGname /dev/sda1 /dev/sdb1

After that create the LVs you want with the size you want for each. That should be little different from your previous test. Try it in VBox.

---

### Post by Vormeph on 2013-06-08
Does it really make any difference as to whether I write a whole partition on both disks or the method in which I use the standard LVM installation and then simply add the remaining storage from the second hard drive to the /root partition on the first hard drive?

---

### Post by darkod on 2013-06-08
No, it doesn't. Just different ways to get to the same result. If you set up the LVM to take both disks during installation, you don't need to expand it right away. Other than that, no real difference.

And at least one partition will have to exist on both disks anyway. I don't know how exactly are you adding the second disk to the LVM and whether the process creates the partition automatically, or it's already there (because it needs to be created only once). But a partition has to exist.

In fact, you might be able to add a whole disk to the LVM without making a partition, but that's not good practice. Partitions like /dev/sda1 and /dev/sdb1 have to exist, that's the best way.

After that, whether you include both of them in the LVM right away, or only one and add the second after the system is running, it makes no big difference.

---

### Post by rewyllys on 2013-06-09
> **Vormeph said:**
> Does it really make any difference as to whether I write a whole partition on both disks or the method in which I use the standard LVM installation and then simply add the remaining storage from the second hard drive to the /root partition on the first hard drive?
It seems to me that you've set your heart on using LVM, but it also seems to me that you feel somewhat daunted by the complexities involved in setting LVM up.

I recommend that you take a moment to re-consider OldFred's suggestion, in post #10, of using a small separate /home partition coupled with several /data partitions.  

This arrangement has a substantial number of advantages, both with respect to the initial establishment of the arrangement and also with respect to the ease of maintaining the arrangement through successive updates and/or installations of your OS.  The arrangement is also seamless to you when you are managing your data.

Please give it at least a few minutes' careful consideration.  You might well wind up being very glad you did so.

---

### Post by Vormeph on 2013-06-09
> **rewyllys said:**
> It seems to me that you've set your heart on using LVM, but it also seems to me that you feel somewhat daunted by the complexities involved in setting LVM up.

I recommend that you take a moment to re-consider OldFred's suggestion, in post #10, of using a small separate /home partition coupled with several /data partitions.  

This arrangement has a substantial number of advantages, both with respect to the initial establishment of the arrangement and also with respect to the ease of maintaining the arrangement through successive updates and/or installations of your OS.  The arrangement is also seamless to you when you are managing your data.

Please give it at least a few minutes' careful consideration.  You might well wind up being very glad you did so.

I don't understand. :S Can you please give me instructions?

EDIT: I've managed to create a link in the home folder to the second hard drive, and that's not what I want sorry. I don't like this manual partitioning method; it makes my folders too cluttered and confusing.

---

