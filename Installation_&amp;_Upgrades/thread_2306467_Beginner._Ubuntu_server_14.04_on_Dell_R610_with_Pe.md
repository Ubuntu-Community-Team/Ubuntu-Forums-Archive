---
title: "Beginner. Ubuntu server 14.04 on Dell R610 with Perc h700 and 6 hard drives"
date: 2015-12-15
forum: Installation &amp; Upgrades
---

### Post by m_adnan08 on 2015-12-15
First of all i would like to thank everyone who will read this post.

I got my hands on Dell Poweredge R610 server with six hard drives 2 Seagate and 4 Toshiba  (SAS drives).
I am planning on setting my home media server and webserver. 
I have been reading about setting up RAID 5 on 4 toshiba 300GB SAS drives. 
I have dedicated hardware RAID perc h700 card installed and working. I have tried to setup raid 0 for boot drives and raid5 for media files. 
I did basic install of ubuntu server with static ip and was able to boot with Ubuntu server 14.04. After that i had no idea how to mount the RAID 5 drives and enable SAMBA and save files on the RAID 5. 

I will really appreciate if anyone of you can guide me with this problem. I will be online for most of the time and would message back and will be able to provide any information that is needed. 
Although right now i have erased all the partitions and creating RAID 0 and RAID 5 partition through PERC H700 configuration utility. Started the initialization of both RAID partitions. Will wait for any advise to how should i go ahead and perform installation and setup my UBUNTU Server.

---

### Post by deepakdeshp on 2015-12-17
Setting up software  RAID

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

You can install minimum GUI for server and follow the following for RAID 1
[http://askubuntu.com/questions/505446/how-to-install-ubuntu-14-04-with-raid-1-using-desktop-installer](http://askubuntu.com/questions/505446/how-to-install-ubuntu-14-04-with-raid-1-using-desktop-installer)

---

### Post by m_adnan08 on 2015-12-22
Deepak, 
thank you for your reply. I am more interested in True Hardware Raid instructions for Ubuntu Server 14.04 on Dell R610. I am using DELL PERC H700 card for setting up RAID harddrrives. I have seen installation videos of Windows Server on Dell R610 with Hardware Raid and after setting up through Dell configuration utility the RAID drives just show up in the Windows for use, But was not able to find any instructions for Ubuntu server. What i have read so far is that I don't have to setup any software raid, just set it up in Dell Utility and install OS and i should see my RAID 5 drive to setup as File Server. 
I will appreciate if you can provide some help regarding TRUE HARDWARE RAID setup in Ubuntu server 14.04. 

Cheers

---

