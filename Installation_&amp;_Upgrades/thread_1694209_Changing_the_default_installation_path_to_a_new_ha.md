---
title: "Changing the default installation path to a new hard disk installed on Ubuntu"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by bodhgaya on 2011-02-24
Hi,

I am currently working on a dual OS PC. I am using Windows XP and Ubuntu 10.04 Lucid Lynx released in April 2010.

The allocated partition to Ubuntu that I am making use of has almost exhausted. Current memory allocations on the PC wrt Ubuntu OS looks like this:-

```
bodhgaya@pc146724-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             8.6G  8.0G  113M  99% /
none                  998M  268K  998M   1% /dev
none                 1002M  580K 1002M   1% /dev/shm
none                 1002M  100K 1002M   1% /var/run
none                 1002M     0 1002M   0% /var/lock
none                 1002M     0 1002M   0% /lib/init/rw
/dev/sda1              25G   16G  9.8G  62% /media/C
/dev/sdb1              37G  214M   35G   1% /media/ubuntulinuxstore
bodhgaya@pc146724-desktop:~$ cd /tmp

```I am trying to mount a 40GB(/dev/sdb1 - given below) new hard disk along with my existing Ubuntu system to overcome with hard disk space related issues.

I referred to the following tutorial to mount a new hard disk onto the system:-  [http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux%20/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux%20/)

I was able to successfully mount this hard disk for Ubuntu 0S. I have this new hard disk setup in /media/ubuntulinuxstore directory.

The current partition in my system looks like this:-

```
bodhgaya@pc146724-desktop:/media/ubuntulinuxstore$ sudo fdisk -l
[sudo] password for bodhgaya: 

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x446eceb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        3264    26210047+   7  HPFS/NTFS
/dev/sda2            3265        4385     9004432+  83  Linux
/dev/sda3            4386        4863     3839535   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfa8afa8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4862    39053983+   7  HPFS/NTFS
bodhgaya@pc146724-desktop:/media/ubuntulinuxstore$ 
```Now,

I have a concern wrt the _**"location"**_ where the new softwares will be installed. Generally softwares are installed via the terminal and by default a fixed path is used to where the post installation set up files can be found( I am talking in context of the Drive).

This is like the typical case of Windows, where softwares by default are installed in the C drive. These days people customize their installations to a drive which they find apt to serve their purpose(generally based on availability of hard disk space).  I am trying to figure out how to customize the same for Ubuntu.

As we all know the most softwares are installed via commands given from the Terminal. My road block is how do I redirect the default path set on the terminal where files get installed to this new hard disk.

This if done will help me overcome space constraints I am currently facing wrt the partition on which my Ubuntu is initially installed. I would also by this, save time on not formatting my system and reinstalling Ubuntu and other softwares all over again.

Kindly help me on this..

Your suggestions would be really handy..

---

### Post by sanderd17 on 2011-02-24
In linux, a drive can be mounted to any location. 

So what you need to do is follow a tutorial like this: [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

Use the baobab application (or compare directories with nautilus) to see what is the biggest directory of your system. If it's /home, you can move /home by just following the tutorial. If it is another directory, replace all occurences of /home to the other directory in that tutorial.

Before you start to do this, you should undo the procedures you've followed before. you can't mount a disk twice. You should also backup everything before you start.

Oh, and if you get an error, please mention the command you used here and give us the error. Don't procede when you get errors.

---

### Post by bodhgaya on 2011-02-24
Hi sanderd17 ,

Thank you for your answer, I am sorry, I have already tried something else which seems to have zeroed down my chances of getting back Ubuntu up & running for me now on my PC.

Every time now I try booting Ubuntu, I guess due to lack of space it no more boots on my PC. All this happened after I made one change in the system mount file located at /etc/fstab.


I changed the default location where my new hard disk was originally mounted. Originally it was mounted in /media/ubuntulinuxstore, I changed it to /usr. In other words I mounted /usr on this new hard disk and I guess also ended up making it a mount point for the hard disk. 

Very soon after, the entire behavoir of Ubuntu OS and various simple commands like sudo, vi etc. stopped functioning. Files could no longer be detected from how they were initially. I couldn't undo the changes I made to /etc/fstab as I was no more the su wasn't working any more and hence making me devoid of all write permissions wrt system files..

I thought in this position a reboot would be the only last resort  kind of a rescue.

I was in a position of having only around 10 MB free on my Ubuntu system. I tried booting it, the booting didn't succeed , it seemed to be stuck. This could be now because the /dev/sda2 was now 100% full leaving no memory ( may be virtual in particular to boot the OS ).

I performed a memory test wrt Ubuntu OS, that was 100% successful for me, but of no avail. This test I could perform wrt an option I got in the GRUB when starting my PC.

I tried booting via Ubuntu recovery mode, which I always get through GRUB as an option while starting my PC, this initially took me to a kind of interface. I tried vi /etc/fstab... to edit the mount location of the new hard disk( /dev/sdb1 ) to what it was originally ( /dev/sdb1              37G  214M   35G   1% /media/ubuntulinuxstore - as shown in the question above). But the only command that worked for me at that point of time was cat /etc/fstab. Even pico /dev/sdb1 didn't work for me.


I also via GRUB typed 'e'( for edit ) and then tried to edit the kernel( again made use of 'e' ) with the intention to boot for a single user( I typed single next to the already existing lines written for a file that I obtained on typing 'e' wrt the kernel). Finally on pressing enter, I was at a step higher, at the parent directory where the option of kernel was originally present , from there I entered option b( to boot ). But this didn't help at all.

Now finally every time i try booting Ubuntu via the grub, I am put in a loop due to errors wrt hard disk and I end up back at the original GRUB option. All this atleast didn't have an impact on my Windows OS. But it seems that I have almost lost Ubuntu and have to format it now freshly.

I even tried out a whacky idea of disconnecting the new hard disk from the Cpu, but that went in vain and my problem still continues to persist..

Only seems like a miracle will save me now to retain Ubuntu.
Any feedback or tips which I can carry to avoid such blunders in the future? 

I know this leaves me with almost no hope of getting back Ubuntu, but still I would gather some courage to ask one last time.. is there a way around this..??

Thank you very much for your patient reading and for any feedback obtained wrt my post..

---

### Post by sanderd17 on 2011-02-24
boot via a live CD, check your fstab and be sure that the contens of /usr is on the place where /usr is mounted.

---

### Post by bodhgaya on 2011-02-25
How can I ensure( by manually editing the /etc/fstab file ) that /usr will now be mounted from the original location. I can make sure that my /dev/sdb1 is mounted from the original mount point which is /media/ubuntulinuxstore( by making the appropriate changes to /etc/fstab ) , will this automatically take care of booting /usr to its original location.

Do I need to use a command like sudo mount /dev/sda1 /usr to mount /usr back to its original location.

Thanks again..:)

---

### Post by bodhgaya on 2011-02-25
Hi,

I tried what option you recommended booting via a live cd..

My /etc/fstab looks like this:

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0


This is not how my original /etc/fstab looked originally. Here as you can observe there is no trace of /dev/sda1 and /dev/sda2..

Also there is no trace over here of /dev/sdb1.

I tried to refer to this link: [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

There an option of partition editor is suggested to be used, I couldn't find the same option when I booted Ubuntu via live cd. May be that has a relation with me not being able to edit my original /etc/fstab file and make changes there.

Any idea how deal with this issue now..?

---

### Post by sanderd17 on 2011-02-26
when you boot the live CD, the /etc/fstab is that one from the live cd (thus the cd mounted as /)

your hdd is normally mounted under /media, and there you can find the fstab file.

so it is under a directory like /media/*name of HDD*/etc/fstab

the same for your /usr and the hdd you wanted to mount as /usr is mounted under /media in the live CD.

---

