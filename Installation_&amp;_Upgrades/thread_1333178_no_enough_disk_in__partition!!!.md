---
title: "no enough disk in / partition!!!"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by eAi-T0ky0 on 2009-11-21
hello

  I have use ubuntu for 3 years now and I know that / partition must have a good space for installation and upgrade bla bla bla .. and I make it 36 GB for partition / it have my home folder too . so now it tell me you have not enough disk I can't install any apps or save any thing in desktop.

  may i delete any other partition in my hd and give the space for / partition without reinstall the ubuntu??? thinking I have old kernel may it take the space of / , don't know!! any idea will help me!

this is my OUTPUT!! use Ubuntu Hardy

```
bac@Linux:~$ df -ha
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              10G  8.5G  996M  90% /
proc                     0     0     0   -  /proc
/sys                     0     0     0   -  /sys
varrun               1013M  232K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
procbususb               0     0     0   -  /proc/bus/usb
udev                 1013M   60K 1013M   1% /dev
devshm               1013M   20K 1013M   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
lrm                  1013M   20M  994M   2% /lib/modules/2.6.24-23-generic/volatile
none                     0     0     0   -  /proc/bus/usb
securityfs               0     0     0   -  /sys/kernel/security
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon       10G  8.5G  996M  90% /home/eai-tokyo/.gvfs
/dev/sdb              952M  468K  951M   1% /media/THE-ANSWER
/dev/sda7              48G   40G  8.7G  82% /media/disk
/dev/sda6              48G   41G  7.2G  86% /media/disk-1
```


idea? :(

---

### Post by phillw on 2009-11-21
Hi,

try ```
sudo apt-get autoremove
sudo apt-get autoclean
```This will remove old installed archives, also, post the output of /var  -- you'd be suprised how many logs you can accumulate over 3 years !!

Phill.

---

### Post by phillw on 2009-11-21
```
sudo apt-get clean
```

Will remove all the current install archives as well - this doesn't affect anything - just menas that if you re-install something, your system will have to go and get a new copy of it - It should free some more room up for you.

Regards,
Phill.

---

### Post by phillw on 2009-11-21
> and I make it 36 GB for partition / it have my home folder too

Your / partition shows as being 10GB ...

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              10G  8.5G  996M  90% /


Not sure what you have on sda6 & sda7 .. I'm surmising windows or music/vids etc. all three partitions show as pretty full, so it may be time to consider getting another hard-drive, or a decent sized memory stick to put music / photo's etc onto and free up your hard-drive.

Phill.

---

### Post by eAi-T0ky0 on 2009-11-27
thanks for all help

  I'm sorry , I tell that my / partition is 36 but I was wrong I make it 10 GB and have other 3 partition every one is 36 , Can I have format one of them TO MAKE MY / partition BIG?

is it possible to do that , I just want to make my Ubuntu partition or / partition big than 10 GB and I tell you this , I can delete or format any partition of the other 3 I have copy my data , but I don't want to lose the data in / partition? :(

---

### Post by Wittiga on 2009-11-27
The question here is: How can i tell the upgrade thing to save all the .deb files in my big /home partition instead in /? I also need 2.5 GB but i can't make more room.

---

### Post by Wittiga on 2009-11-28
Or is it possible to use an external drive to upgrade, or at some point i will need more space in /?

---

### Post by eAi-T0ky0 on 2009-11-28
YES , I have 5 partition OK?

1 for /   (10GB)
2 for swap
3 for windows
4 for data music / films etc (48 GB)
5 for data music / films etc (48 GB)

the number 1 partition is have no enough space , I want to make it big??

I can format or remove any thing from 4 , 5 partition because i have save those data in those partition to other USB partitions , NOW THE QUESTION IS , Can I take some space from 4,5 and give it to 1 partition to make it big without losing data in 1 / partition?

---

### Post by phillw on 2009-11-28
> **eAi-T0ky0 said:**
> YES , I have 5 partition OK?

1 for /   (10GB)
2 for swap
3 for windows
4 for data music / films etc (48 GB)
5 for data music / films etc (48 GB)

the number 1 partition is have no enough space , I want to make it big??

I can format or remove any thing from 4 , 5 partition because i have save those data in those partition to other USB partitions , NOW THE QUESTION IS , Can I take some space from 4,5 and give it to 1 partition to make it big without losing data in 1 / partition?

Hi, can u post the output of 
```
sudo fdisk -l
```and 
```
df -ha
```
Thanks,

Phill.

---

### Post by eAi-T0ky0 on 2009-11-28
ok , the output for:

```
sudo fdisk -l
```


```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac91ac91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1307    10498446   83  Linux
/dev/sda2            1308       13932   101410312+   f  W95 Ext'd (LBA)
/dev/sda3   *       13933       19457    44379562+   7  HPFS/NTFS
/dev/sda5            1308        1438     1052226   82  Linux swap / Solaris
/dev/sda6            1439        7685    50178996    7  HPFS/NTFS
/dev/sda7            7686       13932    50178996    7  HPFS/NTFS

```

and 

```
bac@Linux:~$ df -ha
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              10G  7.7G  1.9G  81% /
proc                     0     0     0   -  /proc
/sys                     0     0     0   -  /sys
varrun               1013M  224K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
procbususb               0     0     0   -  /proc/bus/usb
udev                 1013M   56K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
lrm                  1013M   20M  994M   2% /lib/modules/2.6.24-23-generic/volatile
none                     0     0     0   -  /proc/bus/usb
securityfs               0     0     0   -  /sys/kernel/security
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon       10G  7.7G  1.9G  81% /home/eai-tokyo/.gvfs
```

---

### Post by phillw on 2009-11-28
Hmmm.... go into Places - you should see the other partitions listed there, mount them and run the > df -ahagain, so we can see how much spare room you have.
The data areas are not auto mounting  (This is Not a problem - I just want to see how much spare room they have)

Regards,

phill.

---

### Post by phillw on 2009-11-28
If - and only IF you are SURE that you have backups of two data areas, I can advise you on how to remove them, one at a time - take a backup of your / area and allocate their area to / --- I need to know you have backups. I've never had a re-partition fail on me - but that'll be because I ALWAYS take a backup !!!

Regards,

Phill.

---

### Post by eAi-T0ky0 on 2009-11-29
don't know how to back up / , I don't want to lose my apps and what ever there in / partition , it sound mean you will tell me to format / partition I don't know all I know that if imposable to make / partition big size without format it? and I don't really know how to back up the / partition??


```
bac@Linux:~$ df -ah 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              10G  7.7G  1.9G  81% /
proc                     0     0     0   -  /proc
/sys                     0     0     0   -  /sys
varrun               1013M  228K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
procbususb               0     0     0   -  /proc/bus/usb
udev                 1013M   56K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
lrm                  1013M   20M  994M   2% /lib/modules/2.6.24-23-generic/volatile
none                     0     0     0   -  /proc/bus/usb
securityfs               0     0     0   -  /sys/kernel/security
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon       10G  7.7G  1.9G  81% /home/eai-tokyo/.gvfs
/dev/sda7              48G   41G  7.7G  84% /media/disk
/dev/sda3              43G   35G  8.2G  81% /media/disk-1
/dev/sda6              48G   36G   13G  75% /media/disk-2
```

---

### Post by phillw on 2009-11-29
> **eAi-T0ky0 said:**
> don't know how to back up / , I don't want to lose my apps and what ever there in / partition , it sound mean you will tell me to format / partition I don't know all I know that if imposable to make / partition big size without format it? and I don't really know how to back up the / partition??


```
bac@Linux:~$ df -ah 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              10G  7.7G  1.9G  81% /
proc                     0     0     0   -  /proc
/sys                     0     0     0   -  /sys
varrun               1013M  228K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
procbususb               0     0     0   -  /proc/bus/usb
udev                 1013M   56K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
lrm                  1013M   20M  994M   2% /lib/modules/2.6.24-23-generic/volatile
none                     0     0     0   -  /proc/bus/usb
securityfs               0     0     0   -  /sys/kernel/security
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon       10G  7.7G  1.9G  81% /home/eai-tokyo/.gvfs
/dev/sda7              48G   41G  7.7G  84% /media/disk
/dev/sda3              43G   35G  8.2G  81% /media/disk-1
/dev/sda6              48G   36G   13G  75% /media/disk-2
```

I am NOT telling you to delete or format your / partition - do NOT delete or format your / partition !!!!!

You said that you had a backup of the data area ? If this is so - and you are SURE you have, then we can allocate one of them to /. Also so note that your sda7 and sda3 partitions are fast approaching the 90% FULL limit -at which point linux may well lock you out of putting any more data on them until you free up some space. From your mounted systems there is pecious little free space left ANYWHERE, so, we need to free some up before you can allocate it to /

Hope that makes it a bit clearer - And, don't worry - I WILL give you a backup script for you / partition - they're just TOO important to not backup when you re-size !!!

Regards,

Phill.

---

### Post by oldfred on 2009-11-29
While it may be possible to move things around, it not the real issue that the entire drive is close to full. Every partition is at least 75% used. With hard drive prices as low as they are now and the desire to store lots of media it may be time to plan on a new larger drive.

---

### Post by phillw on 2009-11-29
> **oldfred said:**
> While it may be possible to move things around, it not the real issue that the entire drive is close to full. Every partition is at least 75% used. With hard drive prices as low as they are now and the desire to store lots of media it may be time to plan on a new larger drive.

As I mentioned - 1st priority IS get some disk space ;-)

phill.

---

### Post by eAi-T0ky0 on 2009-11-29
I don't need more space I can live with this space!!!!!!!

Just want to move space from any other partition to / partition!!!!

---

### Post by oldfred on 2009-11-29
Well if you just want to move partitions you probably can. You will have to make space at the beginning of your extended partition and then move the extended right and enlarge sda1.

To make space in the extended partition delete swap and move sda6 right to give a little more space. Then move extended partition right and increase primary sda1. Then move sda7 left to make space for a new swap. You can only shrink sda6 & sda7 so much but it should work. Make sure you have backups and because there is little extra space to moving of partitions may take a long time. I would do it in steps and make sure everything is ok after each step. 

You may also want to run windows tools and the NTFS data partitions to make sure there are no errors before starting. chkdsk, defrag etc.

Edit:  Moving swap will change its UUID and sdax number. You will have to manually edit etc/fstab with the new UUID.

---

### Post by phillw on 2009-11-30
> **eAi-T0ky0 said:**
> I don't need more space I can live with this space!!!!!!!

Just want to move space from any other partition to / partition!!!!

So is this statement true, or not ?

> YES , I have 5 partition OK?

1 for /   (10GB)
2 for swap
3 for windows
4 for data music / films etc (48 GB)
5 for data music / films etc (48 GB)

the number 1 partition is have no enough space , I want to make it big??

I can format or remove any thing from 4 , 5 partition because **i have save those data in those partition to other USB partitions** , NOW THE QUESTION IS , Can I take some space from 4,5 and give it to 1 partition to make it big without losing data in 1 / partition?

You are really pushing the limits of your capacity - by backing up / to the partition with 13GB space you can remove your swap area and allocate it to / and possibly 1GB from one of the other partitions. That will give / enough room - but you will be really pushing what little disk space you have left.

Phill.

---

### Post by eAi-T0ky0 on 2009-12-01
I have all data of the partition sda 7 and sda 6 in my external USB HD , I have all data of those partition in my usb HD , THAT SOUND MEAN , that mean I need to move space from sda to / partition without lose / partition data , because I don't back up data of / partition and I don't want to remove it , bro :(

---

### Post by phillw on 2009-12-01
> **eAi-T0ky0 said:**
> I have all data of the partition sda 7 and sda 6 in my external USB HD , I have all data of those partition in my usb HD , THAT SOUND MEAN , that mean I need to move space from sda to / partition without lose / partition data , because I don't back up data of / partition and I don't want to remove it , bro :(

Hi, welcome back

Can we remove the data from sda6 and use some for your / area and the rest for sda7, or do you want to keep a small sda6 area?

As you point out - you do not have a backup of your /  area - it would only take up, even when we make it bigger, a maximum of 20GB on your usb drive - just in case your main hard drive were to fail on you (Bad things can happen to good disks) - As I will giving you a script specifically for **your** system, I can make it so it backs up your / area to your usb drive, if you want me to.

Phill.

---

### Post by Wittiga on 2009-12-01
Guys guys, the problem here is "not enought disk when you try to upgrade", is a temporary thing. You are happy the way you have set your partitions, a / partition too big is wasted space. Therefore you have to tell the upgrade manager to save those debs that will download in some place, not in the / partition. My 5GB / partition is big enough to use my laptop, but cant handle upgrading.
There is a problem does anybody know how to do that?

Thank you.

---

### Post by phillw on 2009-12-01
> **Wittiga said:**
> Guys guys, the problem here is "not enought disk when you try to upgrade", is a temporary thing. You are happy the way you have set your partitions, a / partition too big is wasted space. Therefore you have to tell the upgrade manager to save those debs that will download in some place, not in the / partition. My 5GB / partition is big enough to use my laptop, but cant handle upgrading.
There is a problem does anybody know how to do that?

Thank you.

Wittiga - if you have a problem, please post a new thread, it is the forum 'etiquette'. In your case a 5GB install is too low. That is for a minimal install - as soon as you add programmes, save data etc - Or, in your case, try to update then it will 'bite you in the bum' 9GB is the recommended minimum. Which this OP has, he does however have additional programmes and data in his 9GB area, and a VERY full disk. It is for this reason we are discussing options to get his / area enlarged and preventing him hitting the 90% full marker which will make his entire installation VERY unhappy

The solution for you is simple - make your 5GB area into 9GB and it will serve you well for years - unless you add lots of programmes and save lots of data on there - the OP does have seperate areas for his data - which is a GOOD idea, however with additional programmes and data in his /home directory he is pushing the limit of even a standard 9GB instal.

Regards,

Phill.

---

### Post by Wittiga on 2009-12-01
> **phillw said:**
> Wittiga - if you have a problem, please post a new thread, it is the forum 'etiquette'. In your case a 5GB install is too low. That is for a minimal install - as soon as you add programmes, save data etc - Or, in your case, try to update then it will 'bite you in the bum' 9GB is the recommended minimum. Which this OP has, he does however have additional programmes and data in his 9GB area, and a VERY full disk. It is for this reason we are discussing options to get his / area enlarged and preventing him hitting the 90% full marker which will make his entire installation VERY unhappy

The solution for you is simple - make your 5GB area into 9GB and it will serve you well for years - unless you add lots of programmes and save lots of data on there - the OP does have seperate areas for his data - which is a GOOD idea, however with additional programmes and data in his /home directory he is pushing the limit of even a standard 9GB instal.

Regards,

Phill.

Thanx for your explanation, but i did not open a new thread because i have the same problem the OP has:
> 
I have use ubuntu for 3 years now and I know that / partition must have a good space for installation and upgrade bla bla bla ..

But from a different aproach, i dont wanna make my  / partition any bigger. Im using 2,7 GB. I just want upgrade manager to save those deb files somewhere else, if possible.

Thank you.

---

### Post by phillw on 2009-12-01
> **Wittiga said:**
> Thanx for your explanation, but i did not open a new thread because i have the same problem the OP has:


But from a different aproach, i dont wanna make my  / partition any bigger. Im using 2,7 GB. I just want upgrade manager to save those deb files somewhere else, if possible.

Thank you.

You're going to have to ask someone else for that - I can 'do' the removing of old and current backups of applications you have added ```
 apt-get clean
``` that removes them all - It means that the computer will need to go to repositry to reload them if you select re-install from synaptics.

We have people stuck in 2.5GB hell - there are well written HowTos as to how to escape from that. With current hard drives, if you cannot afford 10GB space for Ubuntu - your disk drive is already pretty full - and Win operating systems start to get unhappy past to 90% mark - the reason it is no longer a 'block' is that 10% of a 1TB drive, is still a lot of room - however - less than 10% will most likely stop a de-frag from being able to take place, it also complicates the re-allocation of 'bad' areas of a hard drive.

I, personally, will support on a 1-2-1 basis when needed a system with a 10GB instal (9GB system, 1GB swap) - any less than  that + it all gets a little too complicated, for the sake of a few GB of hard disk area... I ask ... is it *really* worth the hassle and grief. It isn't for me, hence my not supporting such installs. That is not say that you cannot run ubuntu in a small area - you can have a version of ubuntu that sits in about 2.0GB of hard drive it is 9.10 (not an old one) and only needs 256Mb of RAM - It's just I don't have that system, so I cannot give people advice when they have problems. It is called xubuntu & lives over here --> [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

Regards,

phill.

---

### Post by Wittiga on 2009-12-02
Ok.

---

### Post by eAi-T0ky0 on 2009-12-04
I don't know , but all I know that if I can give some space for / partition . or move space from "sda6 or sda7" to / partition , it's only 10 GB and I want to make it big than 10 GB , how can I do that without lose my .debs file or software in / partition?

---

### Post by phillw on 2009-12-04
>  				 				**Re: no enough disk in / partition!!!** 			
 			 			 		   		 		 		 	Quote:
 	 	 		 			 				 					Originally Posted by **eAi-T0ky0** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8419220#post8419220") 				
 				*I have all data of the partition sda 7 and sda 6 in my external USB HD , I have all data of those partition in my usb HD , THAT SOUND MEAN , that mean I need to move space from sda to / partition without lose / partition data , because I don't back up data of / partition and I don't want to remove it , bro :sad:*
 			 		 	 	 
Hi, welcome back

Can we remove the data from sda6 and use some for your / area and the rest for sda7, or do you want to keep a small sda6 area?

As you point out - you do not have a backup of your / area - it would only take up, even when we make it bigger, a maximum of 20GB on your usb drive - just in case your main hard drive were to fail on you (Bad things can happen to good disks) - As I will giving you a script specifically for **your** system, I can make it so it backs up your / area to your usb drive, if you want me to.


 		                   		  		  		 		 			 				

Phill.

---

### Post by eAi-T0ky0 on 2009-12-06
can you tell me how to do that ? :( I'm newbie in this :(

---

### Post by phillw on 2009-12-07
> **eAi-T0ky0 said:**
> can you tell me how to do that ? :( I'm newbie in this :(

With the greatest of pleasure.

Please post the following WITHOUT your external drive plugged in

```
sudo fdisk -l
```
and
```
df -ah | grep dev
```
(Yes I know you've already posted them, but I want them and the next in one place !!)

Then, plug in your external drive - If it does not Auto mount then Select Places from the top bar and click on the drive.

Then please run the two commands again and post the output.

This will let me know the device name of your external drive & how much room it has.

One question you have not answered - either sda6 or sda7 are going to be removed. Please let me know which one you'd rather keep - and make sure that you have a backup of that one.

I will then give you instructions and a command to run that will backup your **/** TO the external drive. Once that is done, I will let you know how to allocate some of either sda6 or sda7 to **/** and the rest of it to the remaining data area.

I Promise - I will NOT tell you to delete, or put at risk ANY data until we are both SURE that you have a backup.

Regards,

Phill.

---

### Post by phillw on 2009-12-08
> 
 	Code:
 	bac@Linux:~$ df -ah | grep dev
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              10G  7.7G  1.9G  81% /
udev                 1013M   56K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
/dev/sda7              48G   41G  7.7G  84% /media/disk
/dev/sda3              43G   35G  8.2G  81% /media/disk-1
/dev/sda6              48G   36G   13G  75% /media/disk-2 
The questioner here wants to increase his **/** size. The problem ? ... look at the free space that he has left. Remember the rule about % full. Now, where on earth am I going to back his **/** to ? 
Well, he has an external hard-disk with a backup of of his sda6 and sda7 areas on. So, what we are to do is to backup his **/** to that. Then we will remove one of the media partitons, allocate 5 - 10 GB of that space to his **/** area and share the the remainder to his two other media areas. That will take them all to well below the 80% level. 		 		  		  		 		  		  		  		 		 			 				 				

So, I just need to know what the external drive mounts as (/dev/sdb) and how much room there is on it to backup the **/** onto it.

---

### Post by eAi-T0ky0 on 2009-12-16
sorry man , that is the OUTPUTS with my extran USB HD in it

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac91ac91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1307    10498446   83  Linux
/dev/sda2            1308       13932   101410312+   f  W95 Ext'd (LBA)
/dev/sda3   *       13933       19457    44379562+   7  HPFS/NTFS
/dev/sda5            1308        1438     1052226   82  Linux swap / Solaris
/dev/sda6            1439        7685    50178996    7  HPFS/NTFS
/dev/sda7            7686       13932    50178996    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    c  W95 FAT32 (LBA)
```

```
bac@Linux:~$ df -ah | grep dev
/dev/sda1              10G  7.7G  1.8G  82% /
udev                 1013M   64K 1013M   1% /dev
devshm               1013M  612K 1013M   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
/dev/sda6              48G   40G  8.9G  82% /media/disk
/dev/sda7              48G   40G  8.1G  84% /media/disk-1
/dev/sdb1             233G  108G  126G  47% /media/My Passport
/dev/sdc1             233G  109G  125G  47% /media/My Passport_
```

---

### Post by eAi-T0ky0 on 2009-12-16
I want to tell you that I don't have backup for my / partition and I don't lose my Apps or my .debs file or anything in / parition if it posimble to give it some space from some where??????????

---

### Post by drs305 on 2009-12-16
> **eAi-T0ky0 said:**
> I want to tell you that I don't have backup for my / partition and I don't lose my Apps or my .debs file or anything in / parition if it posimble to give it some space from some where??????????

I am having a bit of trouble following this part of the thread, but if you just want to take space away from one partition and put it into /, here is a guide that may help. It dicusses taking space from Windows and putting it into Ubuntu, but the principles are the same (unmounted, LiveCD, unmounting swap, etc) no matter which partitions are involved.

[Expanding an Ubuntu System Partition ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by phillw on 2009-12-16
> **eAi-T0ky0 said:**
> sorry man , that is the OUTPUTS with my extran USB HD in it

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac91ac91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1307    10498446   83  Linux
/dev/sda2            1308       13932   101410312+   f  W95 Ext'd (LBA)
/dev/sda3   *       13933       19457    44379562+   7  HPFS/NTFS
/dev/sda5            1308        1438     1052226   82  Linux swap / Solaris
/dev/sda6            1439        7685    50178996    7  HPFS/NTFS
/dev/sda7            7686       13932    50178996    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    c  W95 FAT32 (LBA)
``````
bac@Linux:~$ df -ah | grep dev
/dev/sda1              10G  7.7G  1.8G  82% /
udev                 1013M   64K 1013M   1% /dev
devshm               1013M  612K 1013M   1% /dev/shm
devpts                   0     0     0   -  /dev/pts
/dev/sda6              48G   40G  8.9G  82% /media/disk
/dev/sda7              48G   40G  8.1G  84% /media/disk-1
/dev/sdb1             233G  108G  126G  47% /media/My Passport
/dev/sdc1             233G  109G  125G  47% /media/My Passport_
```

Excellent !!

There is plenty of room to back up **/**.

Boot from the Live CD. Have the drive called My Passport ready to plug in.

Once you have plugged the drive in we need to mount the **/** and the My Passport.

```

cd /
sudo mkdir /oldroot
sudo mkdir /backup
sudo mount /dev/sda1 /oldroot
sudo mount /dev/sdb1 /backup

```Carrying out ```
df -ah | grep dev
```Should show this

/dev/sda1              10G  7.7G  1.8G  82% /oldroot
/dev/sdb1             233G  108G  126G  47% /backup

Amongst others.

From your LiveCD you can log back on here & confirm you have these two areas showing.

Once you've done that, You can just copy and paste a command i will give you and that WILL backup your precious **/** area onto your external drive.

Regards,

Phill.
P.S. - To drs - He's stuffed for overall hard disk space on sda - As he has a backup of sda6 & sda7, we're going to nuke one of them - allocate some to / and some to the other data partition. He DOESN'T have a backup of /, and - very understandibly - wants one !!

So, It's mount his sda1, one of his usb drives & pop sda1 onto there with a quick cpio for safe keeping.

---

### Post by eAi-T0ky0 on 2009-12-17
thank you


I will try this steps out and hope it works!!!!!!!

---

