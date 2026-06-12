---
title: "Installation on SSD"
date: 2018-04-20
forum: Installation &amp; Upgrades
---

### Post by gk021176 on 2018-04-20
Hello Team,

My system configuration (Home Purpose Desktop)

AMD Fx CPU
24 GB RAM
1 TB + 1 TB + 1TB = 3 TB HDD

I have installed Ubuntu 17.10 Desktop and have partitioned as below.

/dev/sda1 - /boot
/dev/sda2 - /root
/dev/sda3 - Swap

/dev/sdb1 - /home (Important directories for me is Documents, Pictures and Videos)

/dev/sdc1 - /backup

I have one more external 1.5 TB HDD, which, I use it again for backing up *.tar file created in /backup partition.

Now, I have got new 120GB Kingston UV400 SSD.

I have read "https://sites.google.com/site/easylinuxtipsproject/ssd". Here they have mentioned, it is written for Linux Mint. Hope this is true for ubuntu as well !!

My current requirement and my plan is as below,

Ubuntu 18.04 LTS Desktop[INDENT]/root - 120 GB SSD (Do, I have to create any other partitions such as /boot, /var)
Swap - Do, I need to have this partition ? If yes, Can, I add it along side of /home partition in one of the 1 TB HDD ?
/home - 1TB HDD
/backup - 1TB HDD
[/INDENT]
Ubuntu 18.04 LTS Server one of the 1 TB HDD[INDENT]KVM
SSH Server
File Server
Backup Server[/INDENT]

Please provide me your suggestions on my current requirement.

Thanks
Ananda

---

### Post by kerry_s on 2018-04-20
sounds okay to me. no you don't need a swap on the ssd. ubuntu will use a swap file anyway.

for the server you can add swap just in case. really depends on what kinda load your going to put on it.

---

### Post by gk021176 on 2018-04-20
Thanks for your quick reply.

Load on the server will not be that much, as, I will be using mainly for

KVM - One Virtual Machine
Backup Server - Will be doing mostly weekly backup.
File Server - Will connect to my pi (which will be acting as Media Player)

I will never be doing all at a time.

---

### Post by oldfred on 2018-04-20
If you are using multiple installs better to keep /home inside / (root). Changes to /home then will not create changes in other installs. You can then use a shared /mnt/data or /media/data partition for all your data. Whats left in /home is tiny (less than 2GB).
And desktops do not need /boot unless using LVM or LVM with full drive encryption. 
New versions of Ubuntu do not use swap partition, but use a swap file. Swap partition will be used if found during install on any drive.

Tar not really recommended. See comments by TheFu.
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)

 The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting](https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting) 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by gk021176 on 2018-04-20
Thanks for your reply.

Oh man, I don't know so many things. I am lucky to be here with the community, where you are all guiding me to build an robust desktop, which, I want to use it as my production desktop until it lasts.

---

