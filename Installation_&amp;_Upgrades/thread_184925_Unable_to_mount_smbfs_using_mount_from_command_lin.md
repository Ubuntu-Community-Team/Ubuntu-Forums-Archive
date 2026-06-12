---
title: "Unable to mount smbfs using mount from command line (gnome connect to server works)"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by Maytag on 2006-05-30
I have been completely unsuccessful at mounting a smbfs share via the command line (and therefore fstab). The share I'm mounting is hosted on a file server running Gentoo, and I have no problem connecting to it via my WinXP, Mac OSX 10.3.9, and other Gentoo system. But Ubuntu seems to not be able to do it.
I use the following command:
> sudo mount -t smbfs -o username=$username,password=$password,uid=$UbuntuUsername,gid=$Ubuntuusername //$serverip/$sharename /mnt/fileserver Hopefully it's clear that I use real values in all the $ cases.
This command seems to work; it does not return an error. However, when I try to ls the directory I get > ls: /mnt/fileserver: Input/output error When is ls -al the parent directory it returns: > ?---------  ? ?    ?       ?                ? [COLOR=Red]fileserver[/COLOR] When I unmount the share that directory returns to normal permissions and directory status, and is owned by my username:groupname.
I have tried the information here: [https://wiki.ubuntu.com/SettingUpSamba?highlight=%28Samba%29]("https://wiki.ubuntu.com/SettingUpSamba?highlight=%28Samba%29")
but this does not seem to make any difference. 

The real kicker is that going to Places-->Connect to Server and navigating to the share *WILL* mount the share. That doesn't allow for boottime mounting via fstab though, and isn't my goal. 

Could it be that smbfs support is not compiled into the kernel? It is listed in the file /proc/filesystems. The kernel is the latest official for 6.06.

Any help would be appreciated.

---

### Post by ephoenix on 2006-05-30
You need to install smbclient package. You can install it with Synaptic.

And verify that smbfs package is installed too.

I used it every day at work with dapper 6.06...

---

### Post by Maytag on 2006-05-30
I have smbclient and smbfs installed already. samba, samba-common, libsmbclient, and libsmbclient-dev also.

I really don't see a reason why this shouldn't work--which is why I posted here, I suppose. Hopefully someone in the community has some more ideas.:-D

---

### Post by ipguru99 on 2006-05-30
Same kind of problem.. [http://www.ubuntuforums.org/showthread.php?t=184428&highlight=mount+smbfs](http://www.ubuntuforums.org/showthread.php?t=184428&highlight=mount+smbfs)

Nothing changed but the upgrade.. but I CAN ONLY type it... mine doesn't work for a file I put on my wife's pc.  She has been clicking on it since Warty.. when I upgraded to Dapper, it takes everything down with it.  I can't even hit the caps lock.

---

### Post by ZagiFlyer on 2006-07-11
Sorry, this is a "me too" -- I don't have a solution. My thread is [here]("http://www.ubuntuforums.org/showthread.php?t=212964").

I've been able to mount the remote share though with this command:
[COLOR="Blue"]$ sudo mount -t smbfs -o username=<my username>/<source machine workgroup> //<source machine IP address>/<share name> /mnt/<mount point>[/COLOR]

But after awhile, the mount just "goes away" and copies stall and $ls returns "Input/Output error" as you encountered.

I didn't explicitly install smbclient, I just installed smbfs. I'll try installing smbclient (if it's not already there) but I don't expact that to make any difference.

---

### Post by rburki on 2006-11-13
Hi there

I had a similar problem: access through gnome to my XP machine worked, but I could not mount.
I tried mount -t smbfs //maquina_windows/share /mount_point
without success.

After seeing the thread: 
[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)

I tried with credentials, and tried using smbmount. Here I found out, that smbmount wasn't installed, so did a install of smbfs with synaptics.

now with credentials and smbmount, it works. I use:
sudo smbmount //aserver/home /mnt/aserver/home/ -o credentials=/home/auser/.smbpasswd,dmask=777,fmask=777

where aserver is the XP machine.

Hope this helps, read the howtomountsmbfs!

Gruess
R

---

### Post by jwolter on 2007-10-16
Maytag, did you ever get this working?  

I've got two versions of ubuntu running as VMs on a Windows system.  In 6.06 I'm having the same problem.  In 7.04, I can mount from the command line no problem.  I checked and I've got the same samba-related packages installed in both VMs.  So I'm pretty confident it's not a package missing problem.  But it still could be an O/S or a configuration problem.  Unfortunately, I'm having compatibility problems with other software in 7.04, so I can't take the easy route and just use 7.04. If anyone learned anything about the original problem, I'd love to hear it.

---

### Post by gotthardt on 2007-11-06
I finally got the answer that works for me:
use cifs instead of smbfs:
mount -t **cifs** //server/xxxx /mnt/xxxx

---

### Post by R%&amp;92GH&amp; on 2007-11-24
I have exactly the same problem with samba, since I updated my samba server version in a Debian machine (using an ubuntu client). Meanwhile it works with the command you provided (cifs).. but I still don't understand why it stopped working with "mount -smbfs"

any idea anyone?

---

