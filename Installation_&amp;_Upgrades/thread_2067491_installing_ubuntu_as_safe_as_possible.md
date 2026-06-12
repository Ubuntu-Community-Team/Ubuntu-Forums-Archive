---
title: "installing ubuntu as safe as possible"
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by coolrocks86 on 2012-10-06
Hello, I'm sorry if you have seen this question a thousand times, I've googled everything but just can't seem to get a straight answer. so here's my problem:


[LIST]
[*]I can't install ubuntu using wubi because after reboot, it says cannot mount due to operating system crash or not clean and all that, can't run chkdsk /r either. And yes my windows 7 is recovered from a problem before and now the disk has 3 partitions: C:\, D:\System Reserved, and one more without a label (can only be seen in disk management)
[/LIST]


[LIST]
[*]My SSD currently doesn't have a free unallocated space so I tried shrinking C: using windows 7 disk management, but I can't do that either because the shrink button is greyed out. it says something about cannot move unmoveable files. I already defrag the disk and nothing changed. I'm afraid to use GParted because a forum said that there's a risk of unable to boot to windows if you shrink windows using GParted.
[/LIST]


[LIST]
[*]I have a bootable usb stick with ubuntu in it, an once it let me choose the option "install side by side" but during copying files I decided to cancel the progress because it hasn't offered me to choose free space. Now the option disappear.
[/LIST]
Right now I can't risk losing my windows 7 installation because I have so little time, I can manage to create recovery disk, but before that, what is the problem with my disk? What can I do to make it "clean" and dualboot ubuntu safely?



Any help would be greatly appreciated! Thanks!:)

---

### Post by Herman on 2012-10-07
:) There is really no 'safe' way to set up a dual boot, especially if you don't have  any access to basic operating system maintenance and repair tools such  as CHKDSK and BOOTREC.  If you can't get a Windows Repair CD for your version of Windows or newer you may need to be prepared to pay somebody to do those kinds of jobs for you who has the right tools and know-how.

It's true that Windows Disc Management doesn't have the ability to move the so-called 'immovable files'. GParted can easily do that for you but I don't think GParted will touch your Windows drive anyway though, if the file system is 'dirty'. You will most likely need to run CHKDSK first. Then there's the question of how many primary partitions you have already. 

Perhaps it would be better in your case to forget about dual booting, actually.

One way to have both operating systems fairly safely would be not to dual boot but instead to go get another HDD or SSD if you can afford one and install Ubuntu in that one, avoiding any interaction between the two operating systems completely.
You could remove the Windows drive and insert the new drive for Ubuntu and install Ubuntu in it as a straight single operating system installation.  It's pretty easy to swap drives in most laptops with just one small screwdriver, and for some laptops you don't even need any screwdriver. 

If you have a desktop PC you could add an extra drive (most desktops have room for extra drives). In that case you could probably dual boot on two drives if you want to, or get your computer repair shop to add an extra drive for you. In that case you might even be able to get them to set up your dual boot for you since they would have the right repair and maintenance software and knowledge to go with it. It sounds like your Windows is very sick and needs help desperately. 
Personally, I would shelf it and just use Ubuntu, but that's just me and my opinon. :)

---

### Post by coolrocks86 on 2012-10-07
hi thank you for the reply, as soon as I read it, I decided to give up and install it on virtualbox instead. the reason I want to dualboot is I don't like how slow it is (being installed inside windows) and I want to take full advantage of using my 6gb of ram. I'm only doing this for homework and seems like my ssd and existing windows installation are giving me a hard time.

here are "several" of my attempts to avoid virtualbox:

[LIST]
shrink via diskmgmt.msc finally worked by defragmenting disk using 3rd party software, so I left it as unallocated space and follow step-by-step installation in here [http://www.avoiderrors.net/dual-boot-windows-7-and-ubuntu-12-04-not-wubi/]("http://www.avoiderrors.net/dual-boot-windows-7-and-ubuntu-12-04-not-wubi/") and a new problem arises, a fatal error when trying to install bootloader, so i've tried everywhere still failed. some "misleading" info on the net said to convert disk to dynamic, so i did, and don't do this, this is undoable, because the only way to convert it back to basic is by deleting the entire thing. and it doesn't help with the bootloader problem since now the partition is shown "unusable"
[/LIST]

[LIST]
wubi is basically not a dualboot, but i tried it anyways, it showed the busybox "cannot mount bla bla bla" and by accident i typed exit at the command prompt and it brought me to the installation screen, only to show me "no root system is defined", and then i tried this again (forgot what I did different this time) and it let me choose two option "erase disk" or "something else".
[/LIST]

[LIST]
I've tried both the 32bit and 64 bit in case that's the issue, or in case the ISO file is damaged
[/LIST]

[LIST]
I've managed to get the "install alongside them" option by shrinking the volume using diskmgmt.msc, by leaving the free space unallocated and formatted to NTFS and FAT32, then installer crashed
[/LIST]

[LIST]
I've tried installing ubuntu hundreds of times, it's either the installer crashed or failed to install bootloader
[/LIST]

guess how many hours I spent doing these

---

### Post by critin on 2012-10-07
> guess how many hours I spent doing this

Those hours are never wasted though since you're learning.  
I ditto the suggestion of adding another hdd for ubuntu.

---

### Post by coolrocks86 on 2012-10-07
> **critin said:**
> Those hours are never wasted though since you're learning.  
I ditto the suggestion of adding another hdd for ubuntu.

haha thank you, I'm thinking expresscard, seems practical

---

### Post by lazarojhr16 on 2012-10-07
don't format the unallocated space to Ntfs if your going to install linux to it since linux uses ext4 not ntfs like windows. on windows 7 use program called virtual clone drive to format the hard drive, this is safe. then leave a partition with at least 4.5 gbs of free space and install ubuntu alongside win 7. remember a hard drive can only have up to 4 primary partitions.

---

### Post by coolrocks86 on 2012-10-09
> **lazarojhr16 said:**
> don't format the unallocated space to Ntfs if your going to install linux to it since linux uses ext4 not ntfs like windows. on windows 7 use program called virtual clone drive to format the hard drive, this is safe. then leave a partition with at least 4.5 gbs of free space and install ubuntu alongside win 7. remember a hard drive can only have up to 4 primary partitions.

I have downloaded virtual clone drive but there doesn't seem to be an option to format harddrive. Though I managed to convert my ssd from dynamic to basic by using EaseUs Partition Manager without having to reinstall windows 7 (back-up just in case), then install ubuntu again by shrinking the partition with windows 7 in it. Right before installation finished, it showed fatal error again and ask me to pick a place to install bootloader, so I chose something that said "ubntu device mapper" with the size that's the same with the total of space I have on my harddisk (includes all partitions). Then it showed a box that installation has finished then rebooted. But it doesn't show grub instead it went straight to windows 7.

I have used unebootin to make a bootable Boot-Repair, but it was stuck on something that says "SYSLINUX bla bla peter et al". Before that I also tried to sudo apt boot repair but an error showed that I was low on free space(my usb stick) so I cannot install anything. then I checked the usb, there was 3.16gb free space. 

Do you think this is just a bootloader problem or more problem?

---

### Post by oldfred on 2012-10-10
Post link to BootInfo report from this:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by coolrocks86 on 2012-10-10
> **oldfred said:**
> Post link to BootInfo report from this:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

hi I ran boot repair once again, this time with advanced option and by checking windows 7 as default os to boot. and now I have succesfully installed ubuntu as a dualboot with windows 7!

i had problems installing the dualboot on dev/mapper, so that seems to fix the problem.

but now ubuntu keeps telling me i'm low on disk space, probably that's because I chose "install them side by side" so it reserved more space for swap than ext4

---

### Post by YannBuntu on 2012-10-12
Welcome among us :)

> **coolrocks86 said:**
> it reserved more space for swap than ext4

it should have not.
Please open a terminal (Ctrl+Alt+T), and indicate the output of the following commands:
```
sudo parted -l
df -h
```

---

