---
title: "Always getting errors while updating repositories"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by ikovac on 2010-03-12
I am becoming desperate here. I *always* have errors when trying to do update. This was happening on 9.04 and it is the same on 9.10 (64bit server). It usually looks like this:

```
ikovac@localhost:~$ sudo apt-get update
[sudo] password for ikovac: 
Hit http://download.virtualbox.org karmic Release.gpg
Hit http://us.archive.ubuntu.com karmic Release.gpg                                                                                
Hit http://security.ubuntu.com karmic-security Release.gpg                                                                         
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                                      
Ign http://security.ubuntu.com karmic-security/main Translation-en_US                             
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US                                                      
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US                                                             
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US                                                               
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US                                                        
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US                                                      
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US                                                             
Ign http://download.virtualbox.org karmic/non-free Translation-en_US                                                             
Hit http://security.ubuntu.com karmic-security Release                                                                           
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Hit http://download.virtualbox.org karmic Release
Hit http://download.virtualbox.org karmic/non-free Packages
Hit http://security.ubuntu.com karmic-security/main Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages
Get:1 http://security.ubuntu.com karmic-security/main Sources [23.3kB]
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US      
Get:2 http://security.ubuntu.com karmic-security/main Sources [23.3kB]            
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US        
Get:3 http://security.ubuntu.com karmic-security/main Sources [23.3kB]
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US        
Get:4 http://security.ubuntu.com karmic-security/main Sources [23.3kB]              
Hit http://us.archive.ubuntu.com karmic Release                                     
Hit http://us.archive.ubuntu.com karmic-updates Release                             
Hit http://us.archive.ubuntu.com karmic/main Packages                                                    
Hit http://us.archive.ubuntu.com karmic/restricted Packages                         
Get:5 http://security.ubuntu.com karmic-security/main Sources [23.3kB]              
Hit http://us.archive.ubuntu.com karmic/main Sources                                
Hit http://us.archive.ubuntu.com karmic/restricted Sources                          
Hit http://us.archive.ubuntu.com karmic/universe Packages                           
Hit http://us.archive.ubuntu.com karmic/universe Sources                            
Get:6 http://security.ubuntu.com karmic-security/main Sources [23.3kB]              
Hit http://us.archive.ubuntu.com karmic/multiverse Packages                                                
Hit http://security.ubuntu.com karmic-security/restricted Sources                                 
99% [6 Sources bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.88.40)] [Connecting to security.ubuntu.com (91.189.88.37)]
bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://security.ubuntu.com karmic-security/main Sources                                                                    
  Sub-process /bin/bzip2 returned an error code (2)
Hit http://us.archive.ubuntu.com karmic/multiverse Sources                                                                     
Hit http://security.ubuntu.com karmic-security/universe Packages              
Get:7 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]                                    
Hit http://security.ubuntu.com karmic-security/universe Sources                                            
Hit http://security.ubuntu.com karmic-security/multiverse Packages            
Hit http://security.ubuntu.com karmic-security/multiverse Sources                  
Get:8 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]            
Get:9 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:10 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:11 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:12 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:13 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:14 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:15 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:16 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:17 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages           
Hit http://us.archive.ubuntu.com karmic-updates/main Sources                  
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources            
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages                 
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources                   
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages                
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources                 
99% [17 Packages bzip2 724992]                                                     
bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://us.archive.ubuntu.com karmic-updates/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 16.4kB in 1s (9,395B/s)
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```And here is my sources-list:

```
ikovac@localhost:~$ cat /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

deb http://download.virtualbox.org/virtualbox/debian karmic non-free
```I tried a lot of thing from this forum and fro elsewhere, but nothing permanently solves the issue. 
What am I doing wrong??

Cheers!

---

### Post by garvinrick4 on 2010-03-12
> **ikovac said:**
> I am becoming desperate here. I *always* have errors when trying to do update. This was happening on 9.04 and it is the same on 9.10 (64bit server). It usually looks like this:

```
ikovac@localhost:~$ sudo apt-get update
[sudo] password for ikovac: 
Hit http://download.virtualbox.org karmic Release.gpg
Hit http://us.archive.ubuntu.com karmic Release.gpg                                                                                
Hit http://security.ubuntu.com karmic-security Release.gpg                                                                         
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                                      
Ign http://security.ubuntu.com karmic-security/main Translation-en_US                             
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US                                                      
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US                                                             
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US                                                               
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US                                                        
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US                                                      
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US                                                             
Ign http://download.virtualbox.org karmic/non-free Translation-en_US                                                             
Hit http://security.ubuntu.com karmic-security Release                                                                           
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Hit http://download.virtualbox.org karmic Release
Hit http://download.virtualbox.org karmic/non-free Packages
Hit http://security.ubuntu.com karmic-security/main Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages
Get:1 http://security.ubuntu.com karmic-security/main Sources [23.3kB]
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US      
Get:2 http://security.ubuntu.com karmic-security/main Sources [23.3kB]            
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US        
Get:3 http://security.ubuntu.com karmic-security/main Sources [23.3kB]
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US        
Get:4 http://security.ubuntu.com karmic-security/main Sources [23.3kB]              
Hit http://us.archive.ubuntu.com karmic Release                                     
Hit http://us.archive.ubuntu.com karmic-updates Release                             
Hit http://us.archive.ubuntu.com karmic/main Packages                                                    
Hit http://us.archive.ubuntu.com karmic/restricted Packages                         
Get:5 http://security.ubuntu.com karmic-security/main Sources [23.3kB]              
Hit http://us.archive.ubuntu.com karmic/main Sources                                
Hit http://us.archive.ubuntu.com karmic/restricted Sources                          
Hit http://us.archive.ubuntu.com karmic/universe Packages                           
Hit http://us.archive.ubuntu.com karmic/universe Sources                            
Get:6 http://security.ubuntu.com karmic-security/main Sources [23.3kB]              
Hit http://us.archive.ubuntu.com karmic/multiverse Packages                                                
Hit http://security.ubuntu.com karmic-security/restricted Sources                                 
99% [6 Sources bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.88.40)] [Connecting to security.ubuntu.com (91.189.88.37)]
bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://security.ubuntu.com karmic-security/main Sources                                                                    
  Sub-process /bin/bzip2 returned an error code (2)
Hit http://us.archive.ubuntu.com karmic/multiverse Sources                                                                     
Hit http://security.ubuntu.com karmic-security/universe Packages              
Get:7 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]                                    
Hit http://security.ubuntu.com karmic-security/universe Sources                                            
Hit http://security.ubuntu.com karmic-security/multiverse Packages            
Hit http://security.ubuntu.com karmic-security/multiverse Sources                  
Get:8 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]            
Get:9 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:10 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:11 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:12 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:13 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:14 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:15 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:16 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Get:17 http://us.archive.ubuntu.com karmic-updates/main Packages [185kB]
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages           
Hit http://us.archive.ubuntu.com karmic-updates/main Sources                  
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources            
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages                 
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources                   
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages                
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources                 
99% [17 Packages bzip2 724992]                                                     
bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://us.archive.ubuntu.com karmic-updates/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 16.4kB in 1s (9,395B/s)
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-amd64/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
```And here is my sources-list:

```
ikovac@localhost:~$ cat /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

deb http://download.virtualbox.org/virtualbox/debian karmic non-free
```I tried a lot of thing from this forum and fro elsewhere, but nothing permanently solves the issue. 
What am I doing wrong??

Cheers!
Unless you use the source code:
Put a # in front of every line that says deb-src
You will then comment it out and not receive the source code.

sudo apt-get update && sudo apt-get upgrade


Then see what it says. (Must # while in root and save.) Alt/F2  then type in gksudo nautilus to get root GUI.

---

### Post by ikovac on 2010-03-12
Thanks for the tip! It looks a lot better now. So it were the sources all along, but I don't understand why...

---

### Post by brunolabs on 2010-03-12
Also had that problem with the Portuguese server.

---

