---
title: "Instalation fails"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by adstri on 2012-03-12
Hi Guys

Absolute Ubuntu beginner here! I wish to install Ubuntu as a separate  boot to windows 7 on my PC. I have made an install disk I put it in my  computer. When I come to install it doesn't recognise that there is  another OS installed or that it is on a partition on the drive. If I go  into Disk Utility this can see that the drive is fromatted to have 100GB  windows recovery, 215GB windows, 215GB free and 1.6TB free (this is the  place I intend to place /home upon install). I have another Harddrive  which is a SSD that I was going use for swap (16GB) and / install. 

How can i get this to install so that i dont lose the currently installed windows 7 partition? 

Another issue that I have had is that I tried backing up windows and then letting Ubunu [SIZE=1]install and I alway end up with an error:
[/SIZE][B][SIZE=1]Code:
Executing 'grub-install /dev/sda' failed[/SIZE][/B]



I don't know how to solve this and it leaves computer in an unusable state. 



My laptop is running Ubuntu which I really enjoy using hence the change  on the Desktop, mainly because windows crashed and lost quite a lot of  work that was unrecoverable and ubuntu has never let me down in this  way, until now when I try to install it, HELP? 



Thank you guys  

Sorry if i havent provided enough info!


Adam :smile:

---

### Post by adstri on 2012-03-12
-bump-

---

### Post by adstri on 2012-03-13
Anyone know how to solve this? Please help

---

### Post by Bucky Ball on 2012-03-13
Which release are you using? If you are using 12.04 LTS, don't. It is pre-release, still testing and not a good place for a newcomer to start (unless you know what you are doing or intend going on a steep learning curve). 10.04 LTS might be a better bet; the current long-term support release, supported until April 2013, rock solid (unless there is a specific reason you need to use a newer release I would try it anyway). 

16Gb is waaay to big for swap. You only need around 2Gb.

When you get to the partitioning section of the install, choose 'Something Else' and manually partition. If it sees the NTFS partitions, fine. Just avoid them and create / (20Gb is plenty), /home (big as you want) and the /swap. Once installed if windows is on a partition somewhere and still doesn't show in the grub list at boot, running:

sudo update-grub

... should pick it up and add it. There are other tools to fix boot but we can cover that when you get there (if required).

Please wait 24 hours before bumping in future, thanks (forum etiquette). ;)

I can't help with your error but perhaps you could start by scouring this until someone bobs up that can help:

[http://au.search.yahoo.com/search?p=Executing%20%27grub-install%20%2Fdev%2Fsda%27%20failed%20ubuntu&fr=altavista&fr2=sfp]("http://au.search.yahoo.com/search?p=Executing%20%27grub-install%20%2Fdev%2Fsda%27%20failed%20ubuntu&fr=altavista&fr2=sfp")

---

### Post by adstri on 2012-03-13
Hi Bucky Ball, thanks for the reply. I was trying to use 10.04 as that is what I currently have running on my laptop, I also tried an 11.10 disk to see if this gave the same issue and it did. I shall make sure that I have a smaller swap when I try it then, thank you for the advice. 
 
The issue I get is that when I go into the installer and choose something else setting it doesnt see that the drives are partitioned at all and wants me to create a new file system, do I do this or do you know if there is a way that I can get around this error? Ubunutu disk utility can see that the drive is partitioned but the installer cannot, any ideas? 
 
So if i wipe the drives do the Ubuntu install and it is missing the grub as long as i boot it so it is off the disk I just open terminal and type in sudo update-grub 
 
Thanks Adam :)

---

### Post by Bucky Ball on 2012-03-13
Well, Windows won't make EXT* (EXT2, 3 or 4) type partitions which Linux uses so forget formatting drives to install Ubuntu to with Windows (if that's what you are doing). Where you want to put Ubuntu, leave free space, not NTFS partitions. It is probably asking to create a new filesystem because it cannot go on any of the existing ones (FAT or NTFS). 

Does it see the existing NTFS partitions when you choose 'Something Else'? The one where Windows is installed, for instance? You are probably saying this already but I'm just not hearing you, sorry. ;)

Once you have Ubuntu installed you run:

```
sudo update-grub
```

Once you have Ubuntu installed it will hopefully have picked it up anyhow. When you have finished the partitioning section (when you get there) during install you should be asked whether you want to add the existing OS to the Grub menu. ;)

---

### Post by adstri on 2012-03-13
The installer isn't detecting the Windows NTFS partition, the space where I want to put ubuntu I left as ''free disk space''. I will post up screen shots of what I get when I get back so you can hopefully see what is happening and I hope someone will know how to solve it (Bucky Ball). 
 
I maybe being very silly but I don't think so...haha. 
 
Thank you for all your help! :)

---

### Post by Bucky Ball on 2012-03-13
Do you already have four primary partitions??? If so, that is the limit. Re-reading your first post it looks like you don't but thought I'd confirm that ...

---

### Post by adstri on 2012-03-13
There are only 3 partitions but the installer cant see any of them?

---

### Post by adstri on 2012-03-13
Hi Bucky Ball I have uploaded images and a sudo fdisk -lu terrminal command in a different thread if you would be able to have a look for the that would be great!! Thank you in advance 

[http://ubuntuforums.org/showthread.php?t=1940167](http://ubuntuforums.org/showthread.php?t=1940167)

Adam

---

