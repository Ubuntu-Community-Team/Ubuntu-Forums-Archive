---
title: "FSlint has no permission to access NFS share on synology NAS"
date: 2022-10-30
forum: Installation &amp; Upgrades
---

### Post by gertversteeg1956 on 2022-10-30
this week I upgraded Ubuntu from 22.04 to 22.10
Unfortunately audio was not working.
Probably due to move from pulseaudio to pipewire
Since it seems to be impossible to undo an upgrade I installed 22.04 on a fresh new partition.
audio is working fine now, but FSlint is not.
I'm using this tool for several years for doing maintenance on my NAS shares (they are mounted with NFS)
This works fine, even in the 22.10 installation, but not  in the new 22.04 installation.
It gives me permission denied errors.
fstab configuration is the same in both installations.
Any tips how I can make this work again?

---

### Post by TheFu on 2022-10-30
Likely a simple file permissions issue.  The userid running the fslint process needs to have access to the files on the NFS storage.

Basically, check the 'ls -al' output for the problem files/storage.

---

### Post by gertversteeg1956 on 2022-10-31
Thanks TheFu
Unfortunately it is not that simple
gert@GV6-X570-AORUS-ELITE:~/ZZ1GV7$ ls -al
totaal 28
drwxrwxrwx  5 gert gert 4096 okt 27 14:50 .
drwxr-x--- 22 gert gert 4096 okt 30 19:33 ..
drwxrwxrwx  9 root root 4096 jul 12  2021 Homes
drwxrwxrwx  7 root root 4096 okt 24 17:16 Music
drwxrwxrwx  8 root root 4096 dec 26  2021 web
gert@GV6-X570-AORUS-ELITE:~/ZZ1GV7$ sudo chown gert Homes
[sudo] wachtwoord voor gert: 
chown: veranderen van de eigenaar van 'Homes': Actie is niet toegestaan
gert@GV6-X570-AORUS-ELITE:~/ZZ1GV7$ 
User gert should have access. It has access from Nautilus. 
But not from FSlint

It has from other installations, but not from a fresh installation of 22.04

I'll check again from a 22.10 installation on the same (Multi boot) machine

---

### Post by gertversteeg1956 on 2022-10-31
This is a listing from a 22.10 installation

gert@GV6:~/ZZ1GV7$ ls -al
totaal 28
drwxr-xr-x  5 gert gert 4096 aug 10  2019 .
drwxr-xr-x 63 gert gert 4096 okt 31 09:07 ..
drwxrwxrwx  9 root root 4096 jul 12  2021 Homes
drwxrwxrwx  7 root root 4096 okt 24 17:16 Music
drwxrwxrwx  8 root root 4096 dec 26  2021 web
gert@GV6:~/ZZ1GV7$ 


All 3 subdirectories are NFS mounts to the same Synology NAS

The fstab entries are the same in both installations

192.168.1.10:/volume1/music /home/gert/ZZ1GV7/Music nfs rw,hard,intr,rsize=8192,wsize=8192,timeo=14 0 0
192.168.1.10:/volume1/homes /home/gert/ZZ1GV7/Homes nfs rw,hard,intr,rsize=8192,wsize=8192,timeo=14 0 0
192.168.1.10:/volume1/web /home/gert/ZZ1GV7/web nfs rw,hard,intr,rsize=8192,wsize=8192,timeo=14 0 0

I'm probably overlooking something.
Any other suggestions?

---

### Post by gertversteeg1956 on 2022-10-31
Some extra comparisons
  	 	 	 	  Op 22.10
 gert@GV6:~/ZZ1GV7$ cd Homes
 gert@GV6:~/ZZ1GV7/Homes$ ls
  admin   eliza   gert   plex  '#recycle'
 gert@GV6:~/ZZ1GV7/Homes$ ls -al
 totaal 452
 drwxrwxrwx  9 root root    4096 jul 12  2021  .
 drwxr-xr-x  5 gert gert    4096 aug 10  2019  ..
 drwxrwxrwx  4 1024 users   4096 jun  7  2020  admin
 drwxrwxrwx  4 1027 users   4096 nov 27  2019  eliza
 drwxrwxrwx 67 1026 users 421888 okt 31 17:27  gert
 drwxrwxrwx  3 1028 users   4096 jul 12  2021  plex
 drwxrwxrwx  2 root root    4096 jun 19 10:11 '#recycle'
 drwxrwxrwx  5 1024 users   4096 dec 27  2020  .Trash-1000
 [EMAIL="gert@GV6"]gert@GV6[/EMAIL]:~/ZZ1GV7/Homes$

  	 	 	 	  
Op 22.04
 gert@GV6-X570-AORUS-ELITE:~/ZZ1GV7$ cd Homes
 gert@GV6-X570-AORUS-ELITE:~/ZZ1GV7/Homes$ ls -al
 totaal 452
 drwxrwxrwx  9 root root    4096 jul 12  2021  .
 drwxrwxrwx  5 gert gert    4096 okt 27 14:50  ..
 drwxrwxrwx  4 1024 users   4096 jun  7  2020  admin
 drwxrwxrwx  4 1027 users   4096 nov 27  2019  eliza
 drwxrwxrwx 67 1026 users 421888 okt 31 17:27  gert
 drwxrwxrwx  3 1028 users   4096 jul 12  2021  plex
 drwxrwxrwx  2 root root    4096 jun 19 10:11 '#recycle'
 drwxrwxrwx  5 1024 users   4096 dec 27  2020  .Trash-1000
 gert@GV6-X570-AORUS-ELITE:~/ZZ1GV7/Homes$

---

### Post by TheFu on 2022-10-31
Please show the mount options used.
If you use the a file manager to force the mount, it won't be NFS, 99.9999% of the time, so the comparison isn't valid.

I don't have a synology. I use Ubuntu for my NFS servers.  I tested 20.04 and 22.04 with NFS and autofs mounting NFS and didn't see issues.
I've not used 777 permissions in decades nor do I swash root nor force any specific users ... since that would defeat the purpose of using NFS, IMHO.  NFS provides native file permissions. That's the primary reason we use it besides performance and low overhead.

I'll pull a 22.10 distro down and test it. Look for my post tomorrow afternoon. In the meantime, I'd check the synology forums for any specifics. NAS devices like those are often not full NFS implementations, but there have been some issues found with IPv6 edge cases recently by people using avahi or mDNS rather than a real DNS or just /etc/hosts settings.

---

### Post by gertversteeg1956 on 2022-11-01
Picked up my grandchildren today. Will check your answer, which is much appreciated, tomorrow evening (after 21:00 CET)

---

### Post by TheFu on 2022-11-01
So, I installed an Xubuntu 22.10 system today.
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.10
Release:	22.10
Codename:	kinetic
```

#### On the client machine:
```
sudo apt install nfs-common
sudoedit /etc/idmapd.conf   # put my local domain inside it.
```

#### On the NFS-server, modified a line to the /etc/exports ... because I'm lazy:
```
/TV     172.22.22.20/24(rw,async)
```
I use exact IPs almost always, but I didn't move the new system to a static IP or put it into DNS or do the 10 other things to make it part of the network, so it is using a limited DHCP address. After changing the exports file, I need to restart the NFS server
```
sudo service nfs-server restart
```

Back on the client, check that the new export is seen, then run the mount command:
```
sudo showmount -e istar
sudo mkdir /mnt/TV
sudo mount -t nfs istar:/TV TV/

$ df -Th /mnt/TV
Filesystem     Type  Size  Used Avail Use% Mounted on
istar:/TV      nfs4  294G  140G  154G  48% /mnt/TV
```

Seems to be working.
```
$ ll The_IT_Crowd-*
-rw-rw-r-- 1 tf plocate 818320602 Oct 22 23:28 The_IT_Crowd-206-Men_Without_Women.mkv
-rw-r--r-- 1 tf plocate         3 Oct 16 09:39 The_IT_Crowd-302-Are_We_Not_Men-long.en.srt
-rw-rw-r-- 1 tf plocate 433082102 Oct 22 23:28 The_IT_Crowd-302-Are_We_Not_Men.mkv
-rw-rw-r-- 1 tf plocate 571692470 Oct 22 23:29 The_IT_Crowd-304-The_Speech.mkv
-rw-rw-r-- 1 tf plocate 569550567 Oct 29 22:13 The_IT_Crowd-306-Calendar_Geeks.mkv
```

The group doesn't make sense, but that's because on the new system, plocate maps to the jellyfin group on the NFS/jellyfin server.  Just for fun, I installed a media player, mpv, then watched some of the The_IT_Crowd-306-Calendar_Geeks.mkv TV show.  Worked fine.

I opened the file manager for xubuntu, told it to go to /mnt/TV and double clicked on a 60 Minutes episode from Sunday that I don't recall watching.  It opened a media player and started working.

So ... I'm back to the Synology being the issue.

I'll leave it around until tomorrow, if there are any specific things you'd like me to check.
The nfs-server, istar, is running 20.04 and was fully patched last Saturday.  I patch weekly.

---

### Post by gertversteeg1956 on 2022-11-02
Hi TheFu
Thanks for you're extensive listing.
I'll do the same steps from my fresh 22.04 installation and from my upgraded 22.10 installation.
Synology is called GV7 and acts as an NFS server
Client is the Ubunu server; FSlint works fine on the upgraded system and not on the fresh 22:04 instalation
Quick conclusion: I made a configuration error on the fresh 22.04 installation :-(
```
gert@gv6:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:    22.04
Codename:    jammy

gert@gv6:~$ sudo apt install nfs-common
[sudo] wachtwoord voor gert: 
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
De statusinformatie wordt gelezen... Klaar 
nfs-common is reeds de nieuwste versie (1:2.6.1-1ubuntu1.1).

gert@gv6:~$ cat /etc/idmapd.conf
[General]

Verbosity = 0
# set your own domain here, if it differs from FQDN minus hostname
# Domain = localdomain

[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup

gert@gv6:~$ sudo showmount -e gv7
Export list for gv7:
/volume1/homes  *
/volume1/web    *
/volume1/webnfs *
/volume1/music  192.168.1.1/255.255.255.0
/volume1/nfsmap 192.168.1.8

** my shares are mounted in fstab

gert@gv6:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda10 during installation
UUID=****** /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda4 during installation
UUID=D006-DDAC  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
GV7:/volume1/music /home/gert/ZZ1GV7/Music nfs rw,hard,intr,rsize=8192,wsize=8192,timeo=14 0 0
GV7:/volume1/homes /home/gert/ZZ1GV7/Homes nfs rw,hard,intr,rsize=8192,wsize=8192,timeo=14 0 0
GV7:/volume1/web /home/gert/ZZ1GV7/web nfs rw,hard,intr,rsize=8192,wsize=8192,timeo=14 0 0


gert@gv6:~$ df -Th /home/gert/ZZ1GV7/Homes
Bestandssysteem    Type Grootte Gebruikt Besch Geb% Aangekoppeld op
GV7:/volume1/homes nfs4     11T     8,1T  2,8T  75% /home/gert/ZZ1GV7/Homes
```

I'll logon to my 22.10 installation now and do the same steps
```
 gert@GV6:~$ lsb_release -a
 No LSB modules are available.
 Distributor ID:	Ubuntu
 Description:	Ubuntu 22.10
 Release:	22.10
 Codename:	kinetic
 
 
 gert@GV6:~$ sudo apt install nfs-common
 [sudo] wachtwoord voor gert:  
 Pakketlijsten worden ingelezen... Klaar
 Boom van vereisten wordt opgebouwd... Klaar
 De statusinformatie wordt gelezen... Klaar  
 nfs-common is reeds de nieuwste versie (1:2.6.1-2ubuntu4).
 
 
 gert@GV6:~$ cat /etc/idmapd.conf
 [General]
 
 
 Verbosity = 0
 # set your own domain here, if it differs from FQDN minus hostname
 # Domain = localdomain
 
 
 [Mapping]
 
 
 Nobody-User = nobody
 Nobody-Group = nogroup
 
 
 gert@GV6:~$ sudo showmount -e 192.168.1.10
 Export list for 192.168.1.10:
 /volume1/homes  *
 /volume1/web    *
 /volume1/webnfs *
 /volume1/music  192.168.1.1/255.255.255.0
 /volume1/nfsmap 192.168.1.8
 
 
 gert@GV6:~$ cat /etc/fstab
 # /etc/fstab: static file system information.
 #
 # Use 'blkid' to print the universally unique identifier for a
 # device; this may be used with UUID= as a more robust way to name devices
 # that works even if disks are added and removed. See fstab(5).
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 # / was on /dev/sdb6 during installation
 UUID=****** /               ext4    errors=remount-ro 0       1
 # /boot/efi was on /dev/sdb5 during installation
 UUID=09E9-7D28  /boot/efi       vfat    umask=0077      0       1
 
 
 /swapfile                                 none            swap    sw              0       0
 192.168.1.10:/volume1/music /home/gert/ZZ1GV7/Music nfs rw,hard,intr,rsize=8192,wsize=8192,timeo=14 0 0
 192.168.1.10:/volume1/homes /home/gert/ZZ1GV7/Homes nfs rw,hard,intr,rsize=8192,wsize=8192,timeo=14 0 0
 192.168.1.10:/volume1/web /home/gert/ZZ1GV7/web nfs rw,hard,intr,rsize=8192,wsize=8192,timeo=14 0 0
 
 
 gert@GV6:~$ df -Th /home/gert/ZZ1GV7/Homes
 Bestandssysteem             Type Grootte Gebruikt Besch Geb% Aangekoppeld op
 192.168.1.10:/volume1/homes nfs4     11T     8,1T  2,8T  75% /home/gert/ZZ1GV7/Homes
  
```

---

### Post by gertversteeg1956 on 2022-11-02
There are some minor (in my opinion) differences and I'll try to eliminate them
[LIST=1]
[*]release
[LIST]
[*]can not be eliminated 
[/LIST]
  
[*]client name in uppercase letters vs lowercase letters
[LIST]
[*]have to figure out how to change that 
[*]Use "sudo nano /etc/hostname" to change the hostname 
[*]No improvement 
[/LIST]
  
[*]version of nfs-common
[LIST]
[*]Is probably related to ubuntu version -> dont change it 
[/LIST]
  
[*]GV7 not in hosts file in 22.10 installation
[LIST]
[*]add GV7 to hosts file and modify fstab accordingly 
[*]or remove GV7 from hosts file and modify fstab accordingly 
[/LIST]
    
[/LIST]

Will keep you posted asap

---

### Post by TheFu on 2022-11-02
In theory, hostnames are case insensitive.  In reality, there are thousands of scripts created by thousands of different people of different skills.  When comparing hostnames, some programs are better than others at handling the case - I typically use tolower on both sides, then compare the result.  I'd be perhaps 10% of all programs don't do that.  

So .... my 25+ yrs as an admin tell me 1 thing.  Always, always, always, make hostnames and domain names lower case everywhere.  Period. No exceptions.  Being a good admin is about avoiding issues before they can happen.

Another common issue from the old days is that end-of-file and end-of-line aren't the same, so always, always, always, put an extra blank line at the end of every text file - configs, yamls, xml, json, csv, tables, whatever.  Always.  After having the last option in config files ignored because the line wasn't added after it, I learned.  Add an extra, empty, line to the end. Always.

Use static IPs, setup on the system, not via DHCP reservations, when ever possible.  Some enterprises use DHCP only methods for a number of good reasons, until they get burned and have 50% of their systems not working 1 time because the DHCP servers have failed. The only time I use DHCP reservations is when the network device interface doesn't support setting a static IP locally or when the system is portable and commonly moved between different networks - like a laptop.  Desktops, servers, all get locally set static IPs.  Period.

There are lots of little things that admins learn over their careers through experience.  With 100 base-tx and slower connections we had lots of other things that don't apply anymore, thankfully. I'm just happy that I don't need ethtool to always manually set options for each NIC port anymore.
```

GV7:/volume1/music /home/gert/ZZ1GV7/Music nfs rw,hard,intr,rsize=8192,wsize=8192,timeo=14 0 0
GV7:/volume1/homes /home/gert/ZZ1GV7/Homes nfs rw,hard,intr,rsize=8192,wsize=8192,timeo=14 0 0
GV7:/volume1/web /home/gert/ZZ1GV7/web nfs rw,hard,intr,rsize=8192,wsize=8192,timeo=14 0 0
```

I wouldn't use hard mounts, nor would I set rsize/wsize for the last 15 yrs.  NFS automatically negotiates the best parameters and has for a very long time.  
And I definitely wouldn't mount any NFS under any user's HOME.  That is asking for problems, as stated above.

---

### Post by gertversteeg1956 on 2022-11-04
I will try to reconfigure everything from scratch (in 22.10 and in 22.04) with your steps and try to figure out where I made a mistake

---

### Post by gertversteeg1956 on 2022-11-04
I found the issue :-)
Did not create the mountpoints with sudo.
creating them with sudo solves the issue.
Thanks for helping

---

### Post by gertversteeg1956 on 2022-11-05
Hi TheFu,
will follow these advises; (from an ex colleague; I retired a few months ago) as well. Not so familiar with the internal from linux yet. Never needed it since 2006;Thanks again for your effort to help me.
With 2 issues now, I will study the Ubuntu server guide thoroughly as well.

---

