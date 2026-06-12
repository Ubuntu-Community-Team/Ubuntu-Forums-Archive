---
title: "[SOLVED] Newbie - NFTS files deleted - pre-installation problem"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by luangwa on 2008-08-05
In trying to install Ubuntu 8.04 I somehow managed to delete important files on my second harddrive. It happened when I merged two partitions on the drive and formatted for nfts. I assumed that the files on the nfts partition would remain untouched....BIG MISTAKE....should have back up files. Hind sight is always 20/20 but in the heat of moment:    

I am running off of Ubuntu CD since I started thisI have downloaded Foremost with the hope of files recovery but I am unable to install it to a DVD. I get, I wasn't able to extract it from the tar file. TI kept getting "Can't find "burn///Foremost" is it that I need to use a CD? he reason that I was trying to extract to a DVD was to not write over the lost files on the second hard drive. 

I wasn't able tried to download TestDisk to see if I could run it to resurrect the lost files but wasn't able to unload. 

I have used the Gnome Terminal and added myself with administrative privelege so that I could use the sudo command. 

Is there any way that I can recover the lost files as some of them were old scanned photo's for our genealogical records.(We no longer have the photo's so a rescan is out of the question. 

I hope that there is a method to correct my error. Thanks :confused:

---

### Post by logos34 on 2008-08-05
> **luangwa said:**
> I wasn't able tried to download TestDisk to see if I could run it to resurrect the lost files but wasn't able to unload. 

System>admin>software sources>enable **universe** repository

sudo apt-get install testdisk

sudo testdisk

... 

>  Is there any way that I can recover the lost files as some of them were old scanned photo's for our genealogical records.(We no longer have the photo's so a rescan is out of the question. 

If you just want to recover the files vs. the whole partition, try [PhotoRec ]("http://www.cgsecurity.org/wiki/PhotoRec")

---

### Post by tamoneya on 2008-08-05
the easiest way to install testdisk is through terminal with apt-get.  Run these commands:```
sudo apt-get update
sudo apt-get install testdisk
gksudo testdisk
```

---

### Post by luangwa on 2008-08-05
Logos 34
Thanks for your response...Here is what I received when I typed the commands into the terminal.
ubuntu@ubuntu:~$ System>admin>software sources>enable universe repository
bash: System: command not found
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ sudo testdisk
sudo: testdisk: command not found

I am running Ubuntu from the CD...afraid that it might install over the deleted files. I have added myself in the Users and Group with administrative priveledges. 
Did I type in the System command file incorrectly.

---

### Post by luangwa on 2008-08-05
tamoneya
Thanks for your response..Here is what I received when I typed in the commands you sent. 

ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                     
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US   
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [189B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]      
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages [293kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [51.8kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6636B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [11.9kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [908B]      
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages [6636B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources [84.8kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources [908B]
Fetched 574kB in 4s (133kB/s)                      
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ pksudo testdisk
bash: pksudo: command not found
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 


ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                     
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US   
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [189B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]      
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages [293kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [51.8kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6636B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [11.9kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [908B]      
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages [6636B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources [84.8kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources [908B]
Fetched 574kB in 4s (133kB/s)                      
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ pksudo testdisk
bash: pksudo: command not found
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 

I am running Ubuntu from the CD...afraid that it might install over the deleted files. I have added myself in the Users and Group with administrative priveledges.
Did I type in the System command file incorrectly.

---

### Post by luangwa on 2008-08-05
tamoyea

Sorry about the duplication...I only did the terminal commands once. I did not use the System command with your terminal instructions, I used the System command with the list of terminal instructions that logos34 had sent me.

Why aren't the terminal commands working

---

### Post by logos34 on 2008-08-05
no, it's not a command, they're directions on the live cd desktop.  The menus on the panel at the top>System>Admin(istration)....

Here's the exact command (I never use so don't remember it):

gksudo software-properties-gtk

---

### Post by luangwa on 2008-08-05
Thank you for your patience and help. I will try it again and let you know how the results.

---

### Post by tamoneya on 2008-08-05
> **luangwa said:**
> tamoyea

Sorry about the duplication...I only did the terminal commands once. I did not use the System command with your terminal instructions, I used the System command with the list of terminal instructions that logos34 had sent me.

Why aren't the terminal commands working

its most likely because not all the repositories are enabled.  Go into system-> admin -> software source.  Make sure that everything is checked.  I just tried it on my system and it found the package so it definitely exists.  Then start from the apt-get update command.

EDIT: also please change the last command to "sudo testdisk"

---

### Post by luangwa on 2008-08-05
logus34

I was able to launch test disk. Here are the results of the test:

  
Disk /dev/sdb - 60 GB / 55 GiB - CHS 7300 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  7297 254 63  117242307
D HPFS - NTFS              0   1  1  7298 254 63  117258372
D HPFS - NTFS              0   1 10  3648 254 63   58621113
D Linux                 3656   0 62  5333 254 63   26957009 [Linux]
D Linux                 3656   1  1  5333 254 63   26957007 [Linux]
D HPFS - NTFS           3656   1  7  5333 254 63   26957001
D HPFS - NTFS           5333 254 63  7011 254 63   26957071
D Linux Swap            5334   1  1  5421 254 63    1413657
D HPFS - NTFS           5334   1  1  5421 254 63    1413657
D Linux                 5422   0  1  7298 254 63   30154005
D HPFS - NTFS           5422   0  1  7298 254 63   30154005


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS found using backup sector!, 60 GB / 55 GiB

The drive was 60Gb and had two partitions, one was to be for Ubuntu. I believe the partitions were around. I don't know how to read the partition tables that were found. What is the next step?

---

### Post by logos34 on 2008-08-05
Notice how some of those partitions overlap?  You need to highlight the ones corresponding to your last partition table before you formatted and messed it up.  Read the step by step and other docs over at Cg security.  Also this:
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

---

