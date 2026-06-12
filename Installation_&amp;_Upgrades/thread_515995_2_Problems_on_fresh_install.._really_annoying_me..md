---
title: "2 Problems on fresh install.. really annoying me."
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by scythetleppo on 2007-08-02
I am a beginner at linux and I have some previous experience with gentoo, but nothing fancy.

I decided to move to ubuntu mainly due to its popularity. I downloaded, burned and installed the 7.04 today, clearing off the 80gb hard drive and using the default full disk partitioning scheme.

During install it locks up at 'Installing Language Packs' and never gets past it unless I click 'skip'. After this everything seems to install fine.

Then I start up ubuntu and install the recommended updates.

I want to install a program called dosbox. On dosbox's website they say to search for the package by using the synaptic package manager. However when I try, it is not found. So I find that I may need to 'refresh' the list first. I try to refresh the list and it locks up, never finishing.

I discovered how to do basically what seems to be the exact same thing but from command line. Here is what it says:

> nathan@nathan-desktop:~$ sudo apt-get update
Password:
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Translation-en_CA                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_CA
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_CA    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Translation-en_CA         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release             
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release [50.9kB]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release   
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release [57.2kB]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Packages [53.4kB]
99% [6 Packages bzip2 0] [Waiting for headers] [Waiting for headers]           
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Packages       
  Sub-process bzip2 returned an error code (2)
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Packages [14B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages  
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Sources [18.8kB]
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Sources [14B]     
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Packages [1007kB]              
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources [9845B]         
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Packages [7628B]         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Packages                    
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources [953B]
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Sources [293kB]                
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages [21.0kB]   
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Sources [1710B]          
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources [2723B]     
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Packages [3754kB]          
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages [6101B]  
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Sources [1131kB]           
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources [1052B]   
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages [6403B]  
99% [22 Packages gzip 0] [7 Packages bzip2 0] [Waiting for headers]            
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages 
  Sub-process gzip returned an error code (1)
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Packages [148kB]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Packages
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Sources [51.3kB]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Sources
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Packages [7866B]
96% [25 Packages gzip 0] [7 Packages bzip2 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Packages        
  Sub-process gzip returned an error code (1)
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Packages [193kB]
96% [26 Packages gzip 0] [7 Packages bzip2 0] [Waiting for headers]            
gzip: stdin: not in gzip format
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Packages        
  Sub-process gzip returned an error code (1)
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Sources [63.5kB]         
97% [27 Sources gzip 0] [7 Packages bzip2 0]                        1091kB/s 0s
gzip: stdin: not in gzip format
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Sources                     
  Sub-process gzip returned an error code (1)
97% [7 Packages bzip2 0]     

at which point it just sits there forever until I exit it by using ctrl-c

This is a fresh install and the internet works fine. What could the problem be? This is discouraging =/

---

### Post by Alexander2007 on 2007-08-02
> **scythetleppo said:**
> I am a beginner at linux and I have some previous experience with gentoo, but nothing fancy.

I decided to move to ubuntu mainly due to its popularity. I downloaded, burned and installed the 7.04 today, clearing off the 80gb hard drive and using the default full disk partitioning scheme.

During install it locks up at 'Installing Language Packs' and never gets past it unless I click 'skip'. After this everything seems to install fine.

Then I start up ubuntu and install the recommended updates.

I want to install a program called dosbox. On dosbox's website they say to search for the package by using the synaptic package manager. However when I try, it is not found. So I find that I may need to 'refresh' the list first. I try to refresh the list and it locks up, never finishing.

I discovered how to do basically what seems to be the exact same thing but from command line. Here is what it says:



at which point it just sits there forever until I exit it by using ctrl-c

This is a fresh install and the internet works fine. What could the problem be? This is discouraging =/

Try reinstalling Ubuntu.
You can also check the disc for errors. (Upon CD Boot Menu)
Hope I was helpful. :)

---

### Post by scythetleppo on 2007-08-02
Hi, I have already reinstalled ubuntu and with the same result. However I haven't done the check utility. I will do that and then zero my disk and reinstall it if it checks out ok.

---

