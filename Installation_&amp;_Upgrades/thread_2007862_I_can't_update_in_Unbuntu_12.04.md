---
title: "I can't update in Unbuntu 12.04"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by SharkBreeder on 2012-06-21
Every time I try updating (via both the terminal and update manager) I get these errors:

```
Get:65 http://mirror.steadfast.net precise-proposed/multiverse Translation-en [14 B]
Err http://mirror.steadfast.net precise/restricted Sources                     
  500  Internal Server Error
Err http://mirror.steadfast.net precise/universe Sources                       
  404  Not Found
Err http://mirror.steadfast.net precise/multiverse Sources                     
  404  Not Found
Err http://mirror.steadfast.net precise/main i386 Packages                     
  404  Not Found
Err http://mirror.steadfast.net precise/multiverse i386 Packages               
  500  Internal Server Error
Err http://mirror.steadfast.net precise/universe i386 Packages                 
  404  Not Found
Get:66 http://mirror.steadfast.net precise-updates/main Sources [142 kB]       
Get:67 http://mirror.steadfast.net precise-updates/main Sources [142 kB]       
Get:68 http://mirror.steadfast.net precise-updates/restricted i386 Packages [2,665 B]
Get:69 http://mirror.steadfast.net precise-updates/multiverse i386 Packages [1,847 B]
Get:70 http://mirror.steadfast.net precise-updates/universe i386 Packages [94.5 kB]
Get:71 http://mirror.steadfast.net precise-updates/universe i386 Packages [94.5 kB]
Get:72 http://mirror.steadfast.net precise-security/main Sources [23.7 kB]
Get:73 http://mirror.steadfast.net precise-security/universe Sources [6,928 B]
Get:74 http://mirror.steadfast.net precise-proposed/universe Sources [9,414 B] 
Get:75 http://mirror.steadfast.net precise-proposed/multiverse Sources [20 B]  
Get:76 http://mirror.steadfast.net precise-proposed/restricted i386 Packages [20 B]
Get:77 http://mirror.steadfast.net precise-proposed/main i386 Packages [174 kB]
14% [77 Packages gzip 0 B] [Waiting for headers]            13.8 kB/s 13min 41sW: GPG error: http://mirror.steadfast.net precise-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: Unable to parse package file /var/lib/apt/lists/partial/mirror.steadfast.net_ubuntu_dists_precise-proposed_main_binary-i386_Packages.decomp (1)
Get:78 http://mirror.steadfast.net precise/main Translation-en [893 kB]        
Get:79 http://mirror.steadfast.net precise/main Translation-en [893 kB]        
Get:80 http://mirror.steadfast.net precise/multiverse Translation-en [112 kB]  
Get:81 http://mirror.steadfast.net precise/multiverse Translation-en [112 kB]  
Get:82 http://mirror.steadfast.net precise/multiverse Translation-en [112 kB]  
Get:83 http://mirror.steadfast.net precise/universe Translation-en [3,341 kB]
Err http://mirror.steadfast.net precise-updates/restricted Sources             
  404  Not Found
Err http://mirror.steadfast.net precise-updates/main Sources
  404  Not Found
Err http://mirror.steadfast.net precise-updates/universe Sources
  500  Internal Server Error
Err http://mirror.steadfast.net precise-updates/multiverse Sources
  500  Internal Server Error
Err http://mirror.steadfast.net precise-updates/main i386 Packages
  500  Internal Server Error
Err http://mirror.steadfast.net precise-backports/main i386 Packages
  404  Not Found
Get:84 http://mirror.steadfast.net precise-backports/restricted Translation-en [20 B]
Err http://mirror.steadfast.net precise-security/restricted i386 Packages
  500  Internal Server Error
Err http://mirror.steadfast.net precise-security/multiverse i386 Packages
  500  Internal Server Error
Get:85 http://mirror.steadfast.net precise-security/universe Translation-en [11.3 kB]
Get:86 http://mirror.steadfast.net precise-proposed/universe Translation-en [11.1 kB]
Ign http://mirror.steadfast.net precise/main Translation-en_US
Get:87 http://mirror.steadfast.net precise/main Translation-en [893 kB]        
Ign http://mirror.steadfast.net precise/main Translation-en                    
Ign http://mirror.steadfast.net precise/multiverse Translation-en_US
Ign http://mirror.steadfast.net precise/restricted Translation-en_US
Get:88 http://mirror.steadfast.net precise/restricted Translation-en [10.2 kB]
Ign http://mirror.steadfast.net precise/universe Translation-en_US
Ign http://mirror.steadfast.net precise/universe Translation-en
Ign http://mirror.steadfast.net precise-updates/main Translation-en_US         
Get:89 http://mirror.steadfast.net precise-updates/main Translation-en [864 kB]
Get:90 http://mirror.steadfast.net precise-updates/main Translation-en [864 kB]
Get:91 http://mirror.steadfast.net precise-updates/main Translation-en [864 kB]
Get:92 http://mirror.steadfast.net precise-updates/main Translation-en [864 kB]
Ign http://mirror.steadfast.net precise-updates/universe Translation-en
Get:93 http://mirror.steadfast.net precise-security/restricted Translation-en  
Ign http://mirror.steadfast.net precise-proposed/restricted Translation-en
Fetched 1,097 kB in 25min 31s (716 B/s)
W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise/restricted/source/Sources  500  Internal Server Error

W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror.steadfast.net_ubuntu_dists_precise_main_source_Sources  Hash Sum mismatch

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise/universe/source/Sources  404  Not Found

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise/multiverse/source/Sources  404  Not Found

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise/multiverse/binary-i386/Packages  500  Internal Server Error

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise/universe/binary-i386/Packages  404  Not Found

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise-updates/restricted/source/Sources  404  Not Found

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise-updates/main/source/Sources  404  Not Found

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise-updates/universe/source/Sources  500  Internal Server Error

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise-updates/multiverse/source/Sources  500  Internal Server Error

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise-updates/main/binary-i386/Packages  500  Internal Server Error

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise-backports/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise-security/restricted/binary-i386/Packages  500  Internal Server Error

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise-security/multiverse/binary-i386/Packages  500  Internal Server Error

W: Failed to fetch gzip:/var/lib/apt/lists/partial/mirror.steadfast.net_ubuntu_dists_precise-proposed_main_binary-i386_Packages  

W: Failed to fetch copy:/var/lib/apt/lists/partial/mirror.steadfast.net_ubuntu_dists_precise-updates_main_i18n_Translation-en  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

[IMG]http://i50.tinypic.com/2helyyw.png[/IMG]

Is there something wrong with Ubuntu's servers? Any help would be much appreciated.

---

### Post by 2burke on 2012-06-22
Having the same prob.

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'


 ubuntu-bug -w

(apport-gtk:3006): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
greg@greg-HP-Compaq-dx2200-MT:~$ 
-------------------------------------------------------------

greg@greg-HP-Compaq-dx2200-MT:~$ gksudo synaptic
greg@greg-HP-Compaq-dx2200-MT:~$ whereis synaptic
synaptic:
greg@greg-HP-Compaq-dx2200-MT:~$ sudo apt-get install synaptic
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
greg@greg-HP-Compaq-dx2200-MT:~$ 

And it crashes. The monitor has vertical lines through it on the blue . Will not boot.
Leave it for a day or so and the lines arew gone and it reboots



Any Help

---

### Post by zombifier25 on 2012-06-22
Did you try using a different mirror? Open Software Sources, choose a different mirror from the list.

---

### Post by fantab on 2012-06-22
This is not an unusual issue and has been addressed by the forum a zillion times. Please make it a habit to search the forum before you ask for help.

First of all using update manager change the SERVER you are using to MAIN or Anything. Then check your Software sources and remove by unchecking the cdrom-source. Then in terminal run following commands one after another.

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
exit

Also make sure you are connected online.

---

### Post by SharkBreeder on 2012-06-24
> **fantab said:**
> This is not an unusual issue and has been addressed by the forum a zillion times. Please make it a habit to search the forum before you ask for help.

First of all using update manager change the SERVER you are using to MAIN or Anything. Then check your Software sources and remove by unchecking the cdrom-source. Then in terminal run following commands one after another.

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
exit

Also make sure you are connected online.


I followed everything, down to the "t." I still get the same results. And yes, I'm connected to the internet.

---

### Post by SharkBreeder on 2012-06-25
There's a bug in Ubuntu that prevents users from switching off system-wide proxy settings. I looked into it, and fixed the problem. Close this thread.

---

### Post by mörgæs on 2012-06-25
Better if you mark the thread 'solved' using 'thread tools'.

---

### Post by SharkBreeder on 2012-06-25
> **mörgæs said:**
> Better if you mark the thread 'solved' using 'thread tools'.

Gotcha.

---

### Post by autopro2001 on 2012-06-30
So how do you solve this problem

---

