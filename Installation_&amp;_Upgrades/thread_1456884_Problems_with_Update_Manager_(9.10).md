---
title: "Problems with Update Manager (9.10)"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by tperwez on 2010-04-17
Hi Everyone,

I am having problems with my newly upgraded 9.10 distribution that keeps locking up. I had started a thread on that but along the way, I noticed another problem with the Update manager. I posted the following text in the same thread but realized that I must start a newer thread since it has its own issues (so sorry if you see this text in my other thread).


I had upgraded from 8.10 to 9.04 with ISO image and then to 9.10 with ISO image. In between, I did not reset anything in the Update manager (the upgrades were within one day of each other). Since the computer was connected to network during upgrades, I also let it fetch any newer packages as it needed them. 
 
After the upgrade, I started having system lock ups and it requires hard boot. I tried to check for any updates using Update Manager. It reported that system was up-to-date. However, I noticed in the Settings that cdrom was selected in Sources (perhaps because I had upgraded with ISO image). I unselected the cdrom and tried to update the packages. It gives these sorts of warnings:
 
 Error
 
 W. An error occurred during signature verification. The repository is not updated and previous index will be used.
 
 :
 :
 :
 
 And several such errors.
 
 It also says "Failed to fetch xxxxxx " (many such warnings)
 
 and
 
 "Some index files cannot be downloaded and ignored or old one used etc."
 
 
 Since I upgraded using ISO image, there is some problem here about recognizing the repository perhaps. Do you think my problem may have stemmed from upgrading twice using ISO images and not resetting the Update Manager in some fashion in between? Although the system did fetch upgraded packages during upgrades. How can I reset the update manager to start updating properly? Perhaps Authentication is an issue?

Of course, I am still having trouble with lock up. I am hoping that perhaps some package might have already fixed the problem.
Regards,

Tariq

---

### Post by zvacet on 2010-04-18
When you did first upgrade did you run update manager to be sure that system is up-to-date?Same question for second upgrade.Try

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by tperwez on 2010-04-19
> **zvacet said:**
> When you did first upgrade did you run update manager to be sure that system is up-to-date?Same question for second upgrade.Try

```
sudo apt-get update && sudo apt-get upgrade
```

Thanks for  your post.

Yes, I did open Update Manager and pressed the Check button and I was told that my system was up-to-date and version 9.10 was available. I did that with both upgrades.

One thing that might be relevant is this:  my upgrade from 8.10 to 9.04 was with ISO image. My computer was on the network and I let the system fetch any newer packages during the upgrade and it did so. After upgrade to 9.04, I did not change any settings in the Update Manager. Next day, I again opened the Update Manager and checked that the system was up-to-date before upgrade to 9.10 with iso image. It was only after 9.10 began to crash that I noticed that the Settings in Update Manager had also cdrom checked (as well as a repository). I did uncheck it but things do not work.

Is it possible that I needed to have unchecked the cdrom button AFTER 9.04 upgrade (before upgrade to 9.10) and then check for updates? Perhaps my system did not get properly updated before upgrade to 9.10?

I have run the commands you suggested not as you wrote but as:

sudo apt-get update

(which sometimes fetch 11.4 MB and on other times gives me Errors that "Failed to fetch ...." )

and then

sudo apt-get upgrade

(which simply says that 0 packages installed, 0 removed etc)

The Update Manager tells me that my information about the packages is old and newer packages are available and then returns similar errors about  failing to fetch a lot of packages. It does not tell me how to fix the issue of updating the index info.

One error I see is that some index file(s) are old and are being ignored.

In the meantime, the system keeps crashing. 

Regards,

Tariq

---

### Post by zvacet on 2010-04-19
> I have run the commands you suggested not as you wrote

I suggested you to run both commands in on line because it is faster then type twice.If you type** sudo apt-get update && sudo apt-get upgrade** that means that second command will be executed **if and only if** first command is executed correctly.

```
sudo apt-get update

(which sometimes fetch 11.4 MB
```

what that happened update your system.

Run 

```
sudo apt-get update && sudo apt-get upgrade
```
 and post output here.Also post output of 

```
cat /etc/apt/sources.list
```

---

### Post by tperwez on 2010-04-19
> **zvacet said:**
> I suggested you to run both commands in on line because it is faster then type twice.If you type** sudo apt-get update && sudo apt-get upgrade** that means that second command will be executed **if and only if** first command is executed correctly.

```
sudo apt-get update

(which sometimes fetch 11.4 MB
```

what that happened update your system.

Run 

```
sudo apt-get update && sudo apt-get upgrade
```
 and post output here.Also post output of 

```
cat /etc/apt/sources.list
```
 This si the output from

sudo apt-get update && sudo apt-get upgrade


tariq@tariq-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for tariq: 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg [354B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US [374B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US [380B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US [378B]
98% [2 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
73% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US [380B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US           
58% [Connecting to us.archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
39% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release.gpg [363B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Translation-en_US [383B]
41% [Connecting to us.archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Translation-en_US
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Translation-en_US [389B]
36% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Translation-en_US  
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Translation-en_US [387B]
32% [Connecting to us.archive.ubuntu.com (91.189.88.30)]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Translation-en_US    
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Translation-en_US [389B]
29% [Connecting to us.archive.ubuntu.com (91.189.88.30)]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Translation-en_US
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [362B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US [388B]
32% [Connecting to us.archive.ubuntu.com (91.189.88.30)]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US [382B]
29% [Connecting to us.archive.ubuntu.com (91.189.88.30)]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US [388B]
27% [14 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189bzip2: (stdin) is not a bzip2 file.
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US [386B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US   
25% [15 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189bzip2: (stdin) is not a bzip2 file.
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release.gpg [363B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US     
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Translation-en_US [389B]
28% [Connecting to us.archive.ubuntu.com (91.189.88.40)]bzip2: (stdin) is not a bzip2 file.
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Translation-en_US [383B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Translation-en_US  
26% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.                   
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Translation-en_US [389B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Translation-en_US        
25% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.                   
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Translation-en_US [387B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Translation-en_US  
24% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.                   
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release.gpg [364B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Translation-en_US    
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Translation-en_US [390B]
26% [Connecting to us.archive.ubuntu.com (91.189.88.40)]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Translation-en_US
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Translation-en_US [384B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Translation-en_US [390B]
28% [23 Translation-en_US bzip2 0] [Connecting to us.archive.ubuntu.com (91.189bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Translation-en_US       
24% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.                   
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Translation-en_US [388B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release [350B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Translation-en_US 
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release [359B]             
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [358B]              
30% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Translation-en_US
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release [359B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release [360B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                               
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages [372B]
34% [27 Release gpgv 359]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages [378B]
36% [28 Release gpgv 358] [Connecting to us.archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                       
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources [372B] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages          
  Sub-process /bin/bzip2 returned an error code (2)
38% [29 Release gpgv 359] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources [366B]      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release                       
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources [372B]           
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources          
  Sub-process /bin/bzip2 returned an error code (2)
41% [30 Release gpgv 360] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources [370B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release                      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                           
  Sub-process /bin/bzip2 returned an error code (2)
43% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages [376B]
44% [36 Sources bzip2 0] [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources                     
  Sub-process /bin/bzip2 returned an error code (2)
44% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.                 
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages [378B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
  Sub-process /bin/bzip2 returned an error code (2)
46% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Packages [381B]
47% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Packages [387B]
48% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Sources [381B]
50% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/restricted Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Sources [375B]
51% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Sources [381B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/main Sources                
  Sub-process /bin/bzip2 returned an error code (2)
52% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.                 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Sources [379B]
53% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Packages [385B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Sources            
  Sub-process /bin/bzip2 returned an error code (2)
54% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.                 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/universe Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Packages [387B]
55% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security/multiverse Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [386B]
56% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [380B]       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages           
  Sub-process /bin/bzip2 returned an error code (2)
57% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [386B]
58% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [384B]
59% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources [380B]
59% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources [374B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources           
  Sub-process /bin/bzip2 returned an error code (2)
60% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.                 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources [380B]
61% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources [378B]
62% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Packages [387B]
62% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Packages [381B]
63% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Packages [387B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Packages                
  Sub-process /bin/bzip2 returned an error code (2)
64% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Packages [385B]
64% [Connecting to us.archive.ubuntu.com (91.189.88.46)]bzip2: (stdin) is not a bzip2 file.
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Sources [381B] 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Packages            
  Sub-process /bin/bzip2 returned an error code (2)
65% [Connecting to us.archive.ubuntu.com (91.189.88.30)]bzip2: (stdin) is not a bzip2 file.
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Sources [375B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Sources          
  Sub-process /bin/bzip2 returned an error code (2)
65% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.                 
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Sources [381B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Sources                
  Sub-process /bin/bzip2 returned an error code (2)
66% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.                 
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Sources [379B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Sources          
  Sub-process /bin/bzip2 returned an error code (2)
67% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.                 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Packages [388B]
67% [Connecting to us.archive.ubuntu.com (91.189.88.30)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Packages         
  Sub-process /bin/bzip2 returned an error code (2)
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Packages [382B]     
68% [Connecting to us.archive.ubuntu.com (91.189.88.30)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Packages [388B]
68% [Connecting to us.archive.ubuntu.com (91.189.88.30)]bzip2: (stdin) is not a bzip2 file.
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Packages [386B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Packages
  Sub-process /bin/bzip2 returned an error code (2)
69% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Sources [382B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Packages           
  Sub-process /bin/bzip2 returned an error code (2)
69% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.                  
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Sources [376B]
Get:69 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Sources [382B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Sources         
  Sub-process /bin/bzip2 returned an error code (2)
70% [Connecting to us.archive.ubuntu.com (91.189.88.40)]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Sources
  Sub-process /bin/bzip2 returned an error code (2)
70% [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get:70 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Sources [380B]
70% [Working]bzip2: (stdin) is not a bzip2 file.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Sources
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 26.5kB in 1s (17.0kB/s)
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-security Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/restricted/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/multiverse/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-proposed/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources.bz2)  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.


And here is the output from

cat /etc/apt/sources.list

# added by the release upgrader
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main restricted
# added by the release upgrader
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe #Added by software-properties
# deb [http://lib.stat.cmu.edu/R/CRAN/bin/linux/ubuntu](http://lib.stat.cmu.edu/R/CRAN/bin/linux/ubuntu) hardy/ # Added manually by T. Perwez on June 1, 2008
# deb [http://lib.stat.cmu.edu/R/CRAN/bin/linux/ubuntu](http://lib.stat.cmu.edu/R/CRAN/bin/linux/ubuntu) intrepid/ # Added manually by T. Perwez on August 24, 2009 disabled on upgrade to jaunty


Anything interesting?

Regards,

Tariq

---

### Post by zvacet on 2010-04-19
I tried links and they work for me.Maybe you can try this source list

> #deb cdrom:[Ubuntu 9.10 _Karmic_Koala - Release i386 (20081029.1)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by tperwez on 2010-04-19
Thanks for providing the sources.list. After using your list, here is the ouput from

sudo apt-get update && sudo apt-get upgrade


Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US
Get:2 [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US    
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg [189B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Get:5 [http://archive.canonical.com](http://archive.canonical.com) karmic Release [9,347B]           
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [44.1kB]    
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release.gpg [189B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Translation-en_US    
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release [65.9kB]                        
Get:9 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages [4,984B]            
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [91.3kB]       
Get:11 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources [1,870B]            
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release [44.1kB]               
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release [37.1kB]             
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages [1,353kB]                
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]    
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [27.6kB]        
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]     
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [50.1kB]   
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [8,743B]    
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [1,666B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [577B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages [7,971B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources [640kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources [3,270B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages [5,133kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources [2,795kB]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages [190kB]            
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources [116kB]             
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages [201kB]          
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages [14B]      
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources [60.1kB]          
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources [14B]       
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages [125kB]      
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources [29.8kB]      
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages [7,354B]   
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources [4,036B]    
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Packages [67.7kB]       
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Packages [14B]    
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Packages [20.7kB]   
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Packages [14B]    
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Sources [24.8kB]        
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Sources [14B]     
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Sources [5,196B]    
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Sources [14B]     
Fetched 11.2MB in 16s (675kB/s)                                                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



I still do not see any packages being installed. This sort of output I had seen two days ago but then I started to get errors.

Does this suggest any clues? Regards.

---

### Post by tperwez on 2010-04-19
Also, the system froze again after I ran the sudo apt-get update && sudo apt-get upgrade on your source.list file. This lock-up probelm is where it all started.

I am just getting ready to do a clean intall this evening. Something more sinister has happened than can be resolved by this tricks. (Note to myself: NEVER EVER do do an upgrade with an iso image! This is a sure route to disaster. No wonder they recommend the network upgrade.) I am just glad I was able to retrieve almost all my data safely out of this potential black hole of a system. 

I do appreciate your help along the way. 

Regards.

---

### Post by zvacet on 2010-04-20
You didn't get language packages witch is not so bad.But that is not problem.Lock-up is something different.Speaking of upgrades,upgrading from iso is legitimate method to do it.Sorry if it doesn't work for you.I always do my upgrades with alternate CD,because sometimes network upgrade can go wrong.With alternate CD if something goes wrong(witch is really rare with this method) you always have CD for fresh install.Of course it is recommended to have separate home partition.If you don't have one make it following [this]("http://www.psychocats.net/ubuntu/separatehome") guide.If you are going for clean install then make separate home during install process.If you have any question just ask.

---

