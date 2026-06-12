---
title: "Veritas Netbackup client install on Unbutu"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by jholzman on 2006-06-07
Has anyone attempted or been able to install Veritas Netbackup client 6.0 on Unbutu?  Veritas states it is suppored in Debian Linux but not for Unbutu Linux. :confused: 

If so Please tell my how.

If not does anyone have a different way to run backups of directories/files using incrementals and fulls?  

Has anyone got a way to run backups to a tape library?

BackupPC does not support Tape library to best of my knowledge, but can support a stand alone drive.  This will not meet my needs.  

I have thousands of files and many GB's that need to go to tape for offsite storage.

---

### Post by jar on 2006-06-28
[QUOTE=jholzman]Has anyone attempted or been able to install Veritas Netbackup client 6.0 on Unbutu?  Veritas states it is suppored in Debian Linux but not for Unbutu Linux. :confused: 

If so Please tell my how.
[/QUOTE]

Have you tried it yourself? And what problems did you encounter?

We have bought Netbackup 6.0 and I'll need to be able to backup Dapper Drake servers...

---

### Post by thusi02 on 2006-08-31
Have you guys had any luck installing the Veritas backup client on ubuntu?

Please let me know

Cheers, 
Thusi02

---

### Post by ServerSlayer on 2006-09-12
I am about to embark on this journey also for netbackup. If anyone has info it would be greatly appreciated. I will post as soon as I get results good or bad.

Cheers

---

### Post by jar on 2006-09-15
I have been successfull in testing NetBackup 6.0 on Ubuntu Dapper 6.06.

However I am running AMD64 so these instructions are for that architecture:

I used the NB_60_UClients.tar.gz file for my installation

 sudo apt-get install xinetd

 sudo apt-get install libc6-i386

 # this is for i386 (no amd64 availible) so we have to force it!
 # get libstdc++2.10-glibc2.2_2.95.4-24_i386.deb from a local mirror!
 wget [http://ftp.acc.umu.se/mirror/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb](http://ftp.acc.umu.se/mirror/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb)

sudo dpkg --force-architecture -i libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

untar NB_60_Uclients.tar.gz and change row 1062 in

 cd NB_60_CLIENTS_20050906a
 vi NBClients/anb/Clients/usr/openv/netbackup/client/Linux/RedHat2.4/cp_to_client

so that the install can find and restart xinetd, I removed the rc.d part!

sudo ./install

should install the client, I did choose the Redhat2.4 version

After this I had to apply the MP3 patch to NetBackup 6.0 so I downloaded NB_CLT_60_3_M_284127.tar from support.veritas.com and   untarred into a directory. 

sudo ./Vrts_pack.install

should install the patch.

Good luck!

---

### Post by thusi02 on 2006-09-29
Hello, 

I have also been successful setting up the veritas version 6.0. As this apparently supports Debian thus since ubuntu and debian are closely related i presume thats why it works. 

But hey, 

I am happy it works. 

cheers, 

thusi02
[http://letstalkcoding.com](http://letstalkcoding.com)

---

### Post by uggy on 2006-10-10
Thank you..
It worked fine for me too...

For i386, I used 
sudo apt-get install libstdc++2.10-glibc2.2

---

### Post by phlegm on 2007-03-21
Thanks. Just tried it and it still works in 2007 with Netbackup 6.

---

### Post by niekko on 2007-07-02
I also successfully installed the client v6.0 4_M to Ubuntu 6.06.1.

But when I try to connect to the client from the server, I get the error "(24) socket write failed". netstat -a lists open ports and there are four Veritas related ports open.

Any suggestions?

---

### Post by jholzman on 2007-07-06
Dude,

    Jar's method works for 6.10, but not 7.04.  7.04 is still missing some thing.  Your probably missing dependencies.


I have been able to get the Netbackup version 6.0 you need the patch  VrtsNB_CLT_60-4M.  I have this client installed and working on a base 7.10 Unbuntu desktop server.  I have not been able to get the Netbackup 6.5 client to work at all on Unbuntu.  My Netbackup Master server is on Redhat ES Linux and is a the Netbackup v6.5.

):P

---

### Post by syberghost on 2008-01-03
Got this to work on 7.10.  Here's what I did:

I'd already installed it and it didn't work, so I went into /usr/lib and created a symlink pointing libstdc++-libc6.2-2.so.3 -> libstdc++.so.6.0.9.  Then I installed xinetd, copied the two daemon configs from a working box, and started xinetd.  It's backing up now.

---

