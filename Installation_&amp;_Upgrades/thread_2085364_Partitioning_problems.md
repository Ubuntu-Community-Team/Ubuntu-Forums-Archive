---
title: "Partitioning problems"
date: 2012-11-17
forum: Installation &amp; Upgrades
---

### Post by gallicbear on 2012-11-17
Hi there. I am trying to install Ubuntu 12.10 64bit on free (unallocated) space, to dual boot with windows. The problem I am running into is that Ubuntu is unlike Fedora, which does the partitioning automatically. I clicked on 'something else'. When I choose the free space, it becomes very unfriendly. I followed a guide from linuxbsdos and started by creating 250 MB space as etx2, with  /boot as mounting point. Then the rest of the free space is now 'unusable'. Crazy. How do I get out of that dilemma? I guess I should use 'install alongside windows', but I really wanted Ubuntu to be entirely on the free space. I do NOT have gParted.  Was hoping the installer can do the job. Thanks for your help.

---

### Post by Bashing-om on 2012-11-17
gallicbear; Hi ! Welcome back.

GParted: available on the Desktop install cd; Dash->search term GParted-> icon
dual booting with windows:
1. A new computer ? Is uefi a factor
2. Partitioning: is GPT a factor (if so alternate utility for partitioning other than GPareted) ?
these links for dual boot guides:
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

if UEFI or GPT applies:
[http://ubuntuforums.org/showthread.php?t=2064761](http://ubuntuforums.org/showthread.php?t=2064761)
post #5 applies
[INDENT]let us know how it goes, post back with any additional questions.
[INDENT]just try'n to help <== BDQ
[/INDENT][/INDENT]

---

### Post by Avce on 2012-11-18
I'm having the same problem about the unusable space but I'm pure ubuntu I dont have a windows in it

---

### Post by darkod on 2012-11-18
1. When you use the "install along windows" and there is unallocated space on the disk, IT DOES use that space entirelly. The only thing is that installs with only root and swap (so no way to have a separate /home) for example.
By using the manual partitioning you control the partitions and their size, and also where the bootloader goes which is sometimes very important if you have multiple disks.

2. One reason why the remained space can become unusable after you create a partition is if you already have 3 primary partitions and you create /boot as primary. On disks with msdos table the limit is 4 partitions. That is why it's better to create all ubuntu partitions as logical, not primary, since it works just fine on logical partitions too.

Apart from this, if there is any error or corruption in the partitions table it can start acting weird and not showing the partitions correctly.

If you are in doubt, you can boot the ubuntu cd in live mode first and post the output of:
sudo fdisk -l (small L)
sudo parted -l (small L)

---

### Post by gallicbear on 2012-11-18
Thank you all for trying to help. After several tries, I haven't reached anything except for error messages. Using GParted assumes that you have a Linux system running. I tried PartedMagic. It doesn't allow you to divide up the unallocated free space the way you want to. Once you are done assigning one, the rest is untouchable. I have used Easeus partition Manager in Windows to divide up the space, but there are still sizing errors. It's a tedious job. Why can't ubuntu handle it automatically? Frustrating. I'll give it another try, but don't know... One other question: Yes, I will dual boot with Windows 8, but I do not run it in UEFI mode. As far as bootloader, can I assign sda1 Windows 8 (loader), or should I use a different scenario, like just sd1? Thanks again.

---

### Post by darkod on 2012-11-18
The ubuntu cd in live mode has Gparted on it, so you don't need to have already installed system to use it. You have it on the ubuntu cd if you boot it in Try ubuntu.

For bootloader you would usually use grub2 since windows bootloader can't boot linux. And the bootloader usually goes to the MBR of the disk which has no numbers in the device name, like /dev/sda. If it has a number, like /dev/sda1, that means the first partitions on the disk. So, the bootloader grub2 should go to /dev/sda.

You didn't mention how many primary partitions you already have, and how are you trying to create them. Yes, you can do all you need with the installer. And don't play around too much with partitioning and windows software, watch out not to get something messed up.

It would be good to post the otuput of the fdisk and parted commands I posted earlier, so we can see the current disk layout. Like this, we are speaking blind.

---

### Post by NikTh on 2012-11-18
Hi , 
if you can , boot from Ubuntu Live CD/DVD ("Try Ubuntu") , open Gparted program and take a screenshot . Then attach the srceenshot here in forums so we can see whats going on. 
[See here on how to attach a file]("http://i.stack.imgur.com/0E6qS.png") 

Thanks

---

### Post by gallicbear on 2012-11-18
Thanks, NikTh. Still no success. Ubuntu 12.10 is very unfriendly. I do not find GParted to launch it. There are shortcuts for Open Office, Firefox, etc, and shortcuts for the different drives, but Application folder like in Fedora, where you can choose from the different installed programs. 
I do not see how to take a screenshot either. 
Coming back to the install screen, this is what I have as far as partitioning:
Swap: 41.2 MB
/Boot: 518 MB
/ : 33 MB
and /Home, 62 GB.
And when I click on install after all that, it's giving me an error message: Some of your partitions are less than /2.7GB. Your install might fail. Now why it also shows an / with the 2.7GB, I do not know. 
Frustrating.

---

### Post by darkod on 2012-11-18
You just wrote in your post that / is 33MB. Is that correct or you wanted to say 33GB?

Because it can't install on / of only 33MB.

As for looking for applications in the new Unity interface, just click on the ubuntu logo icon on top of the left side interface, and that will open a search box called Dash. You can also open it by hitting the windows logo key on the keyboard.

In the search line just start typing the program you want to find, and it will show it. You can easily open it from there.

---

### Post by NikTh on 2012-11-18
> **gallicbear said:**
> Thanks, NikTh. Still no success. Ubuntu 12.10 is very unfriendly. I do not find GParted to launch it. There are shortcuts for Open Office, Firefox, etc, and shortcuts for the different drives, but Application folder like in Fedora, where you can choose from the different installed programs. 
I do not see how to take a screenshot either. 
Gparted included in Live-Ubuntu , just click on Dash (Ubuntu icon up left - first in Launcher) and write: gparted 

Screenshot  you can take by pressing [PrtScr] button , or call the appropriate  program (also included) , write in Dash : screenshot
> **gallicbear said:**
> Coming back to the install screen, this is what I have as far as partitioning:
Swap: 41.2 MB
/Boot: 518 MB
/ : 33 MB
and /Home, 62 GB.
And when I click on install after all that, it's giving me an error message: Some of your partitions are less than /2.7GB. Your install might fail. Now why it also shows an / with the 2.7GB, I do not know. 
Frustrating.
Well this is correct. You have to resize your partitions to fit the minimum requirements. Are too shot right now. 
Why you don't let Ubuntu partitioning for you ? I mean , do not follow the "hard" partitioning way , but when you click "something else" just click the partition you made for Ubuntu and the click "Install Now" . The Only thing you might want to do is to create a swap area (3GB is good I think) and all other space , mount it to root / . 
A /home will be created inside root. You have allocated plant of space. 
So , in short. 

1) delete anything you created . /boot , swap , /home etc.. 
2) Create a space 3 GB and mount it to swap area
3) Rest of space , mount it to root (/) 
4) Click "Install Now" 
Done.

Thanks

---

### Post by darkod on 2012-11-18
NikTh, if the OP wants separate /home partition, there is no need to get rid of it. But the sizes of other partitions needs to be adjusted unless the MB is a typo and is supposed to be GB.

I wouldn't get rid of /home since it gives you the option for clean installs in future without loosing your Home folder and the data inside. It's very useful.

PS. Also, if I may add, you put swap as 41MB which is so low that you shouldn't really bother. Either make it 1GB or 2GB, or don't use swap partition at all (it can install without swap). Making it 41MB is pointless.

---

### Post by gallicbear on 2012-11-18
Thanks, darkod and NikTh. I'm gonna call it quits. Ubuntu is just too difficult to install. 
After reworking the sizing, I had this: 
~ 4500 MB Swap
518 MB for boot
33 MB for /
61 GB for Home
It STILL gave me /2.7GB error.

So I followed the directions of NikTh and wiped everything and created a swap area of almost 5000 MB. It had still over 60 GB for the rest. Then it gave me another error message: The partition sda6 assigned to / starts at an offset of 1536 bytes from the minimum alignment, which may lead to poor performance... 
Useless. I wanted Ubuntu 12.10 because of how complete it is, compared to other LInux distros, but not at the price of that frustration.

---

### Post by darkod on 2012-11-18
> **gallicbear said:**
> Thanks, darkod and NikTh. I'm gonna call it quits. Ubuntu is just too difficult to install. 
After reworking the sizing, I had this: 
~ 4500 MB Swap
518 MB for boot
[COLOR="Red"]33 MB for /[/COLOR]
61 GB for Home
It STILL gave me /2.7GB error.

So I followed the directions of NikTh and wiped everything and created a swap area of almost 5000 MB. It had still over 60 GB for the rest. Then it gave me another error message: The partition sda6 assigned to / starts at an offset of 1536 bytes from the minimum alignment, which may lead to poor performance... 
Useless. I wanted Ubuntu 12.10 because of how complete it is, compared to other LInux distros, but not at the price of that frustration.

It gave you the same error because you still had only 33MB for / which is the most important, system partition. And it needs about 4.7GB at least.

As for the other message at which sector it starts, that looks only as information message and warning that performance could be affected, which is true. Usually these days disks need to be aligned to 2048 sectors (earlier it was 512) for best performance.

I have rarely seen this message since by default the installer should apply the 2048 rule. Maybe you forced it to create partitions in a strange setup.

---

### Post by NikTh on 2012-11-18
> **darkod said:**
> NikTh, if the OP wants separate /home partition, there is no need to get rid of it. But the sizes of other partitions needs to be adjusted unless the MB is a typo and is supposed to be GB. 
This is correct , but due to multiple problems , is better (for start) to leave the partitioning with separate /home /root etc , and do a simpler partitioning schema. 
Except of that, we don't know how many primary partitions OP has , if has MBR of GPT , because in case of MBR an extedend partition will be needed if primary partitions exceeds 4. 

> **gallicbear said:**
> 
So I followed the directions of NikTh and wiped everything and created a swap area of almost 5000 MB. It had still over 60 GB for the rest. Then it gave me another error message: The partition sda6 assigned to / starts at an offset of 1536 bytes from the minimum alignment, which may lead to poor performance... 
The following message is the answer I would give. But a question here: Didn't have a suggestion after the message ? 
> **darkod said:**
> 
As for the other message at which sector it starts, that looks only as information message and warning that performance could be affected, which is true. Usually these days disks need to be aligned to 2048 sectors (earlier it was 512) for best performance.

Thanks

---

### Post by gallicbear on 2012-11-19
Thanks again for all your help. I took a new look at it, started out from scratch with just free space. Now I know. I had to click on the + to edit the size assigned to the different partitions, like boot and home and root. It worked the first time, like a charm. And the dual-boot part works, too, even though I've got Windows 8.

---

