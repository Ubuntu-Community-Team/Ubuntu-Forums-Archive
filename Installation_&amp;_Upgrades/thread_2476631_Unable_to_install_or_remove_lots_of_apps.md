---
title: "Unable to install or remove lots of apps"
date: 2022-07-01
forum: Installation &amp; Upgrades
---

### Post by esso10 on 2022-07-01
lately, I can't install or remove lots of apps, and I have this message:

Error while installing package: trying to overwrite '/usr/lib/-python3.10/_sysconfigdata_linux_x86_64_linux-gnu.py', which is also in package libpython3.10-minimal

---

### Post by ActionParsnip on 2022-07-01
What is the output of
```

apt-cache policy libpython3.10-minimal; lsb_release -a; uname -a

```
Thanks

---

### Post by esso10 on 2022-07-01
> **ActionParsnip said:**
> What is the output of
```

apt-cache policy libpython3.10-minimal; lsb_release -a; uname -a

```
Thanks
```

libpython3.10-minimal:
  Installed: 3.10.4-1+focal1
  Candidate: 3.10.5-1+focal1
  Version table:
     3.10.5-1+focal1 500
        500 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu focal/main amd64 Packages
 *** 3.10.4-1+focal1 100
        100 /var/lib/dpkg/status
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.4 LTS
Release:    20.04
Codename:    focal
Linux lava 5.13.0-39-generic #44~20.04.1-Ubuntu SMP Thu Mar 24 16:43:35 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by #&amp;thj^% on 2022-07-01
What does this show, paste back please:
```
sudo apt install -f -y
```

---

### Post by ActionParsnip on 2022-07-01
Yep, a PPA. CAn smell them a mile away. Contact the PPA maintainer and explain the issue. You can also remove the ppa-purge and remove the PPA and use the official packages that will have fewer issues.

---

### Post by DuckHook on 2022-07-01
> **ActionParsnip said:**
> Yep, a PPA. CAn smell them a mile away. Contact the PPA maintainer and explain the issue. You can also remove the ppa-purge and remove the PPA and use the official packages that will have fewer issues.
+1

@OP

If you are new to Linux/Ubuntu, please reconsider your use of PPAs. They are dangerous vectors for malware, bugs and system breakage.

When you add a PPA, you are basically letting a stranger have full root access to your system. That's what PPAs do.

Unless you know the PPA's author and have full confidence that the PPA is not only safe but properly maintained and up&#8209;to&#8209;date, do not add them to your system.

---

### Post by esso10 on 2022-07-01
> **1fallen said:**
> What does this show, paste back please:
```
sudo apt install -f -y
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libpython3.10-minimal libpython3.10-stdlib
The following packages will be upgraded:
  libpython3.10-minimal libpython3.10-stdlib
2 upgraded, 0 newly installed, 0 to remove and 157 not upgraded.
5 not fully installed or removed.
Need to get 0 B/2,567 kB of archives.
After this operation, 62.5 kB disk space will be freed.
(Reading database ... 279196 files and directories currently installed.)
Preparing to unpack .../libpython3.10-stdlib_3.10.5-1+focal1_amd64.deb ...
Unpacking libpython3.10-stdlib:amd64 (3.10.5-1+focal1) over (3.10.4-1+focal1) ..
.
dpkg: error processing archive /var/cache/apt/archives/libpython3.10-stdlib_3.10
.5-1+focal1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/python3.10/_sysconfigdata__linux_x86_64-linux-gnu
.py', which is also in package libpython3.10-minimal:amd64 3.10.4-1+focal1
Preparing to unpack .../libpython3.10-minimal_3.10.5-1+focal1_amd64.deb ...
Unpacking libpython3.10-minimal:amd64 (3.10.5-1+focal1) over (3.10.4-1+focal1) .
..
dpkg: error processing archive /var/cache/apt/archives/libpython3.10-minimal_3.1
0.5-1+focal1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/python3.10/typing.py', which is also in package l
ibpython3.10-stdlib:amd64 3.10.4-1+focal1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libpython3.10-stdlib_3.10.5-1+focal1_amd64.deb
 /var/cache/apt/archives/libpython3.10-minimal_3.10.5-1+focal1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by esso10 on 2022-07-01
> [ActionParsnip]("https://ubuntuforums.org/member.php?u=1079078") 	 
 						[IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]  					 					 						Ubuntu Member 					 					 						[IMG]https://ubuntuforums.org/images/rank_ubuntumember_2013-02.png[/IMG] 					                                           					 					 						 							     						
 					 				
 			
 			 				 					Join DateMay 2010Beans2,325 					 					 				
 			 		
 	  	 		 		 		 		[h=2]Re: Unable to install or remove lots of apps[/h] 		 				 				 		 			 				[INDENT] 					Yep, a PPA. CAn smell them a mile away. Contact the PPA maintainer  and explain the issue. You can also remove the ppa-purge and remove the  PPA and use the official packages that will have fewer issues. 				[/INDENT] 			
  			   		
 			 				 			 			 			 		
 	
 	 		 			 				 				 				 					[[IMG]https://ubuntuforums.org/clear.gif[/IMG]]("https://ubuntuforums.org/newreply.php?do=newreply&p=14102556&noquote=1")


I don't understand, I'm just a simple user.

---

### Post by #&amp;thj^% on 2022-07-01
Just comment out or remove this PPA "ppa.launchpad.net/deadsnakes"
From your "/etc/apt/sources.list." or in sources.list.d

---

### Post by DuckHook on 2022-07-01
> **esso10 said:**
> I don't understand, I'm just a simple user.
The important part of ActionParsnip's advice was this:
> **ActionParsnip said:**
> &#8230;remove the PPA&#8230;
And since ActionParsnip's whole reply is both succinct and instructive, let me parse it for you:
> Yep, a PPA. CAn smell them a mile away&#8230;
Translation: PPAs are trouble. Those who add them are doing so without adequate knowledge of their many pitfalls.
> &#8230;Contact the PPA maintainer and explain the issue&#8230;
Translation: Find the author of the PPA on Launchpad. Inform them that their PPA breaks the latest update.
> &#8230;You can also remove the ppa-purge and remove the PPA&#8230;
Translation: You can install the package *ppa-purge* from the repositories. This package helps you remove PPAs from your system. It is a command line app, so you will need to read its man page a figure out how to use it. *ppa-purge* can be added with:```
sudo apt install ppa-purge
```
> &#8230;and use the official packages that will have fewer issues.
Translation: Don't use the PPA and stick to the official package in the repos. The repo package is tested to work properly with your system. PPAs are not. Refraining from adding PPAs is good general advice for all PPAs. See my post #6.

---

### Post by esso10 on 2022-07-02
> **DuckHook said:**
> The important part of ActionParsnip's advice was this:

And since ActionParsnip's whole reply is both succinct and instructive, let me parse it for you:

Translation: PPAs are trouble. Those who add them are doing so without adequate knowledge of their many pitfalls.

Translation: Find the author of the PPA on Launchpad. Inform them that their PPA breaks the latest update.

Translation: You can install the package *ppa-purge* from the repositories. This package helps you remove PPAs from your system. It is a command line app, so you will need to read its man page a figure out how to use it. *ppa-purge* can be added with:```
sudo apt install ppa-purge
```

Translation: Don't use the PPA and stick to the official package in the repos. The repo package is tested to work properly with your system. PPAs are not. Refraining from adding PPAs is good general advice for all PPAs. See my post #6.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 python3.10 : Depends: libpython3.10-stdlib (= 3.10.5-1+focal1) but 3.10.4-1+focal1 is to be installed
 python3.10-minimal : Depends: libpython3.10-minimal (= 3.10.5-1+focal1) but 3.10.4-1+focal1 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```


is that ok?

---

### Post by DuckHook on 2022-07-02
> **esso10 said:**
> is that ok?No, it isn't. Your attempt to update is still choking on the libpython3.10 library.

Every respondent has instructed you to ***remove the offending PPA.***

Have you done this???

If yes, then confirm to us that it has been done. If not, then do so. Follow 1fallen's instructions in his post #9, above.

Your problem can't be solved until the bad PPA is removed.

---

### Post by #&amp;thj^% on 2022-07-02
> **DuckHook said:**
> 

Your problem can't be solved until the bad PPA is removed.
+1
Here it is in one line to ease your confusion.
```
sudo ppa-purge ppa:deadsnakes/ppa
```
Now report any errors left over from running this **one line at a time.**
```
sudo apt clean
sudo apt update
sudo apt full-upgrade

```
Stop and post back on the first error you see.

---

### Post by esso10 on 2022-07-03
> **1fallen said:**
> +1
Here it is in one line to ease your confusion.
```
sudo ppa-purge ppa:deadsnakes/ppa
```
Now report any errors left over from running this **one line at a time.**
```
sudo apt clean
sudo apt update
sudo apt full-upgrade

```
Stop and post back on the first error you see.

sudo ppa-purge ppa:deadsnakes/ppa

sudo: ppa-purge: command not found
-------------------------------------------------------------------------
sudo apt clean

--------------------------------------------------------
sudo apt update
 Hit:1 [http://deb.anydesk.com](http://deb.anydesk.com) all InRelease
Hit:2 [http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) focal InRelease       
Hit:3 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                  
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                      
Hit:5 [http://ppa.launchpad.net/dartsim/ppa/ubuntu](http://ppa.launchpad.net/dartsim/ppa/ubuntu) focal InRelease              
Hit:6 [http://ppa.launchpad.net/deadsnakes/ppa/ubuntu](http://ppa.launchpad.net/deadsnakes/ppa/ubuntu) focal InRelease
Hit:7 [http://archive.linux.duke.edu/ubuntu](http://archive.linux.duke.edu/ubuntu) focal InRelease                     
Hit:8 [http://archive.linux.duke.edu/ubuntu](http://archive.linux.duke.edu/ubuntu) focal-updates InRelease
Hit:9 [http://archive.linux.duke.edu/ubuntu](http://archive.linux.duke.edu/ubuntu) focal-backports InRelease
Hit:10 [http://archive.linux.duke.edu/ubuntu](http://archive.linux.duke.edu/ubuntu) focal-security InRelease
Hit:11 [http://packages.microsoft.com/repos/code](http://packages.microsoft.com/repos/code) stable InRelease               
Hit:12 [https://packages.microsoft.com/repos/vscode](https://packages.microsoft.com/repos/vscode) stable InRelease            
Ign:13 [https://storage.googleapis.com/download.dartlang.org/linux/debian](https://storage.googleapis.com/download.dartlang.org/linux/debian) stable InRelease
Hit:14 [https://storage.googleapis.com/download.dartlang.org/linux/debian](https://storage.googleapis.com/download.dartlang.org/linux/debian) stable Release
Reading package lists... Done
Building dependency tree       
Reading state information... Done
159 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: Skipping acquire of configured file 'main/source/Sources' as repository 'https://packages.microsoft.com/repos/vscode stable InRelease' does not seem to provide it (sources.list entry misspelt?)
--------------------------------------------------------------------------------------------------------------------------------------------------
sudo apt full-upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 python3.10 : Depends: libpython3.10-stdlib (= 3.10.5-1+focal1) but 3.10.4-1+focal1 is installed
 python3.10-minimal : Depends: libpython3.10-minimal (= 3.10.5-1+focal1) but 3.10.4-1+focal1 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

---

### Post by tea for one on 2022-07-03
> **esso10 said:**
> ```
sudo ppa-purge ppa:deadsnakes/ppa
sudo: ppa-purge: command not found
```

```
edited@edited:~$ sudo ppa-purge ppa:deadsnakes
[sudo] password for edited: 
sudo: ppa-purge: command not found
edited@edited:~$ ppa-purge
Command 'ppa-purge' not found, but can be installed with:
[COLOR="#0000FF"]sudo apt install ppa-purge[/COLOR]
edited@edited:~$ 
```
Try again after installing ppa-purge

---

