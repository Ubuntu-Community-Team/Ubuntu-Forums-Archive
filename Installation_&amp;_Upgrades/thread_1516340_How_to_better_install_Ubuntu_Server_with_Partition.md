---
title: "How to better install Ubuntu Server with Partitions"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by konradson on 2010-06-23
Hi, I'm starting with Linux. I've already installed RHE5, and I was told that it was better to sepparate System files in different partitions
 
/
Swap
/var
/opt 
 
and so on... /home
 
I've seen this as well in Solaris and in other UNIX. Yesterday I installed Ubuntu 8.04 (64 bits version) in a Dell PE1950 Had no problems at all, but the OS decided how to be installed. How can I define the sizes of root, swap, var and so on???
 
What do you recommend me for them? in a machine with 4 gigabytes, and 146 gbytes (RAID1) disk space? 
 
:confused::confused::confused:
 
Is it possible to have an SSH server installed during the installation, so I can access the machine remotely?
 
By the way, I use to work with Windows Server, but my boss decided it was time for me to learn UNIX (He has been a SOLARIS tech for almost two decades).
 
Thanks in advance for your advice...

---

### Post by konradson on 2010-06-25
NO Ideas? no way? 
 
still waiting... pleaseee help...
 
:confused::popcorn::confused:

---

### Post by mikewhatever on 2010-06-25
To define the partitions the way you want, go with the manual partitioning option, create each partition the size you want and mount accordingly, in other words, /, /var, /home, etc. 
I don't know if ssh server is or is not included in the server edition by default. It would make sense if it was. You can install it after booting the server for the first time.

---

### Post by konradson on 2010-06-25
Thanks for your help. I'll try this way. When I looked up the Manual partitioning, they showed the ext2, ext3... and so on formating...
 
I expected to find something simmilar to Solaris, where they give you the chance of formating for several OSes, but later you have the / swap /var and so on... in a different point, the next one... So I thought that it was going to find something simmilar. I allowed Ubuntu to format the disk as they suggested, and I hoped to find a way to organize the Linux partitions... but it did it all by itself. It is sad that the Dell Installation doesn't allow you to install Ubuntu (but helps you with RHE 4 and 5, as well as SuSe, helping you to describe all this points before the installation, like with windows). 
 
In the point of SSh, in a big outsourcing company, like the one I work for, is the only way to attack a UNIX (SOLARIS, AIX, UX, Linux...) because all other ways (ex: telnet) are closed... so it is extrange to find out that you don't have SSH working. Maybe I have to start the service, or whatever. But I think it is not installed, and I have to install OpenSSH or simmilar...

---

