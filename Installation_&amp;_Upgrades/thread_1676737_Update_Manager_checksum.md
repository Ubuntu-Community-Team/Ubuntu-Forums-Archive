---
title: "Update Manager checksum"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by lupo1939 on 2011-01-27
Currently running 10.04...
I realize that there are other similar problems posted here, but this problem persists and I need to find a solution.  For the last 2 months, or so, when I try to run an update larger that about 100kb, a 'checksum mismatch' message is returned.  I see download speeds as low as 21kb/s on the failed updates but on successful updates speeds sometimes reach 170kb/s.  I have tried some of the fixes listed in Forums but none work.  Speedtest shows an up and down of about 1.3mb/s, so transmission is probably not the problem.  I recently read multiple posts that indicate some of the source locations are having data accuracy problems.  If so can you suggest a reliable location?  I have tried several,currently using server for U.S.  Can the source location cause this 'throttling' problem? 

  I would like to go to 10.10 but have tried to download it without success.  What's my solution, to buy a disk?

---

### Post by sikander3786 on 2011-01-28
Go to System > Administration > Software Sources and select Main server for downloads.

Then from Applications > Accessories > Terminal, post the _complete_ output of this command.

```
sudo apt-get update && sudo apt-get upgrade
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags as it would be a long output.

---

### Post by lupo1939 on 2011-01-28
ted@Teds:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for ted: 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release                  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages [5,448kB]
99% [1 Packages bzip2 0B] [Connecting to archive.ubuntu.com (91.189.92.171)]   
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages                       
  Sub-process /bin/bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources                         
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [436kB]            
99% [2 Packages bzip2 0B] [Waiting for headers]                     68.5kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages                      
  Sub-process /bin/bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources                
Fetched 5,884kB in 1min 13s (80.6kB/s)                                         
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by sikander3786 on 2011-01-28
Try refreshing your list files. You've switched mirrors and they might have been already refreshed but lets rule out the possibility here.

```
sudo mv /var/lib/apt/lists /var/lib/apt/lists.old
sudo mkdir /var/lib/apt/lists /var/lib/apt/lists/partial
sudo touch /var/lib/apt/lists/lock
sudo apt-get update
```

If it still encounters the same error, please post it and also post the output of this command.

```
cat /etc/apt/sources.list
```

---

### Post by lupo1939 on 2011-01-28
Message received from 1st line of code is
mv: cannot stat `/var/lib/apt/lists': No such file or directory
What does it want?

---

### Post by sikander3786 on 2011-01-28
> **lupo1939 said:**
> Message received from 1st line of code is
mv: cannot stat `/var/lib/apt/lists': No such file or directory
What does it want?
Then it might be the real problem causing troubles here. Proceed to the 2nd command and the 3rd and 4th ones and see if it changes anything.

---

### Post by lupo1939 on 2011-01-29
Tried the second line which produced
mkdir: cannot create directory `/var/lib/apt/lists': File exists
mkdir: cannot create directory `/var/lib/apt/lists/partial': File exists

---

### Post by lupo1939 on 2011-01-29
ted@Teds:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg [198B]
Get:4 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Get:5 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [8,215B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release [57.2kB]
Get:7 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages [11.8kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [44.7kB] 
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release [44.7kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages [1,386kB]                 
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages [6,208B]            
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources [659kB]                    
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources [3,775B]             
99% [12 Sources bzip2 0B] [13 Sources 43B/3,775B 1%]                39.7kB/s 0s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                               
  Sub-process /bin/bzip2 returned an error code (2)
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages [5,448kB]             
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources [3,165kB]              
70% [14 Packages bzip2 0B] [15 Sources 882B/3,165kB 0%]       23.6kB/s 2min 13s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages                          
  Sub-process /bin/bzip2 returned an error code (2)
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages [180kB]             
98% [15 Sources bzip2 6,681kB] [16 Packages 25.3kB/180kB 14%]       44.4kB/s 3s
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources                           
  Sub-process /bin/bzip2 returned an error code (2)
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources [119kB]              
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [436kB]           
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [3,240B]    
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources [177kB]            
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources [1,443B]     
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages [181kB]       
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources [64.8kB]       
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages [8,436B]    
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources [4,372B]     
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages [128kB]          
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages [14B]      
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources [42.7kB]          
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources [14B]       
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages [60.3kB]     
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources [17.6kB]      
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages [2,003B]   
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources [660B]      
Fetched 12.3MB in 4min 58s (41.1kB/s)                                          
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

Looks like there is a problem with Zip.  How do I deal with it

---

### Post by sikander3786 on 2011-01-29
I suspect you didn't type the commands properly because when deleting the same directories, it said that file doesn't exist whereas creating the same directory reports that the files already exist.

I would request to copy/paste the commands from here straight to your Terminal instead of re-typing them and try all of the commands once more.

Or, if you already copy/pasted the commands, please post the output of this command.

```
ls -l /var/lib/apt
```

---

### Post by lupo1939 on 2011-01-30
In all cases I have copied the commands you have provided, not keyed them.

Per your last instructions
ted@Teds:~$ ls -l /var/lib/apt
total 76
-rw-r--r-- 1 root root   203 2008-09-13 22:48 cdroms.list
-rw-r--r-- 1 root root 36887 2011-01-27 13:40 extended_states
drwxr-xr-x 2 root root  4096 2008-07-02 05:16 keyrings
drwxr-xr-x 3 root root  4096 2011-01-30 10:21 lists
drwxr-xr-x 3 root root 16384 2011-01-28 11:29 lists.old
drwxr-xr-x 3 root root  4096 2008-07-02 05:16 mirrors
drwxr-xr-x 2 root root  4096 2008-09-13 15:23 periodic
ted@Teds:~$

---

### Post by dino99 on 2011-01-30
all seem normal, about downloading, is this on wireless ? if so, again this normal.

maybe clean the sources:

sudo rm /var/cache/apt/archives/*

then update, upgrade again

---

### Post by lupo1939 on 2011-02-02
Yes, ISP is wireless.
Tried to run the above command.  Got this response:
ted@Teds:~$ rm /var/cache/apt/archives/*
rm: remove write-protected regular file `/var/cache/apt/archives/base-files_5.0.0ubuntu20.10.04.3_i386.deb'? 

What does it want for a reply?

---

### Post by debd on 2011-02-02
I have a problem regarding package updates.
whenever I try  
sudo apt-get update
it returns an error 
 > [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6

the complete output is here:

> Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick Release.gpg
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/main Translation-en       
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/main Translation-en_IN    
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/multiverse Translation-en 
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/multiverse Translation-en_IN
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/restricted Translation-en 
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/restricted Translation-en_IN
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/universe Translation-en   
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick/universe Translation-en_IN
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates Release.gpg               
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/main Translation-en
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/main Translation-en_IN
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en                 
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_IN              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN           
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en          
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_IN       
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/multiverse Translation-en_IN
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/restricted Translation-en_IN
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/universe Translation-en
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-updates/universe Translation-en_IN
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security Release.gpg              
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/main Translation-en
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/main Translation-en_IN
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/multiverse Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/multiverse Translation-en_IN
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/restricted Translation-en
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/restricted Translation-en_IN
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/universe Translation-en
Ign [http://ubuntu.oss.eznetsols.org/ubuntu/](http://ubuntu.oss.eznetsols.org/ubuntu/) maverick-security/universe Translation-en_IN
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick Release                           
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates Release                   
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security Release                  
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/main Sources                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/restricted Sources                
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/universe Sources                  
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/multiverse Sources                
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/main i386 Packages                
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/restricted i386 Packages          
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/universe i386 Packages            
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick/multiverse i386 Packages          
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/main Sources              
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/restricted Sources        
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/universe Sources          
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/multiverse Sources        
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/main i386 Packages        
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/restricted i386 Packages  
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/universe i386 Packages    
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-updates/multiverse i386 Packages  
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/main Sources             
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/restricted Sources       
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/universe Sources         
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/multiverse Sources       
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/main i386 Packages       
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/restricted i386 Packages 
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/universe i386 Packages   
Hit [http://ubuntu.oss.eznetsols.org](http://ubuntu.oss.eznetsols.org) maverick-security/multiverse i386 Packages 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable/non-free Translation-en            
Ign [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable/non-free Translation-en_IN         
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                    
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,087B]                  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [307B]
Ign [http://ppa.launchpad.net/fta/ubuntu/](http://ppa.launchpad.net/fta/ubuntu/) lucid/main Translation-en
Ign [http://ppa.launchpad.net/fta/ubuntu/](http://ppa.launchpad.net/fta/ubuntu/) lucid/main Translation-en_IN          
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [57.3kB]                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources/DiffIndex                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main i386 Packages/DiffIndex                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main i386 Packages                          
Fetched 2,939B in 9s (323B/s)                                                  
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6

any help is appreciated.

---

### Post by sikander3786 on 2011-02-02
@ **debd**:

Try adding the missing GPG key by,

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 632D16BB0C713DA6
```

Or if that still gives some error, disable the offensive Launchpad PPA from Software Center > Edit > Software Sources.

---

### Post by lupo1939 on 2011-02-05
I have an impressive list of updates for Linux (kernel, etc.) and Open Office that will not run.  Anything bigger that 1mb. fails.  A previous message from Silkander indicated that there might be a problem with files that exist on my HD.  Is there a way to run a scan of my HD, something like the old MS chkdsk?

---

### Post by dino99 on 2011-02-05
sudo shutdown now -R

will perform a fsck on next boot

---

### Post by dino99 on 2011-02-05
> **debd said:**
> I have a problem regarding package updates.
whenever I try  
sudo apt-get update
it returns an error 
 

the complete output is here:



any help is appreciated.

dont mix lucid & maverick repo: clean the sources.list (check into synaptic, and set to "main server" for better experience (yours might be down at the moment)

---

### Post by lupo1939 on 2011-02-09
Sudo command produced the following.

ted@Teds:~$ sudo rm /var/cache/apt/archives/*
[sudo] password for ted: 
rm: cannot remove `/var/cache/apt/archives/partial': Is a directory
ted@Teds:~$ 

How do I respond?

---

