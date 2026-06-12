---
title: "Urgent!! I cant install anything from the ubuntu software center"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by 006ruler on 2010-01-25
Oh crap. I cant install anything that is in the Ubuntu Software Center. Typing "sudo apt-get install codeblocks" doesnt installl anything. I can't even install Amor! 
I have no broken packages achording to synaptic. If i look at something from the Ubuntu Installer thingy, heres what it says:
Code::Blocks IDE

Not available in the current data
Licence: Open Source
Price: Free

try installing with sudo apt-get and this is what i get:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package codeblocks

Any help would be appreciated. Thanks!

---

### Post by earthpigg on 2010-01-25
what about other packages?

---

### Post by 006ruler on 2010-01-25
uh...
no. I mean that i cant install ANYTHING AT ALL.

sry, should have made that clear.

---

### Post by snowpine on 2010-01-25
Try:

```
sudo apt-get update
sudo apt-get install codeblocks
```

Post output here please. :)

---

### Post by 006ruler on 2010-01-25
IT WORKED!!!
Thank you so much, i can now get back to my C++ programing and editing of the Amor creatures.
Heres the output, if you still desire it so-

samuraibastard@ubuntu:~$ sudo apt-get update
[sudo] password for samuraibastard: 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [44.1kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release [65.9kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [44.1kB]    
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [54.9kB]    
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages [1,353kB]             
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [16.3kB]      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [21.9kB]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [3,944B]   
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [1,666B] 
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [575B]    
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages [7,971B]        
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources [640kB]                
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources [3,270B]         
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages [5,133kB]         
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources [2,795kB]          
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages [190kB]         
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources [116kB]          
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [158kB]       
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [14B]   
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources [48.1kB]       
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources [14B]    
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [93.0kB]  
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources [22.8kB]   
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [6,942B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources [3,831B] 
Fetched 10.8MB in 1min 7s (161kB/s)                                            
Reading package lists... Done
samuraibastard@ubuntu:~$ sudo apt-get install codeblocks
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcodeblocks0 libwxbase2.8-0 libwxgtk2.8-0
Suggested packages:
  libwxgtk2.8-dev wx-common codeblocks-contrib libgnomeprintui2.2-0
The following NEW packages will be installed:
  codeblocks libcodeblocks0 libwxbase2.8-0 libwxgtk2.8-0
0 upgraded, 4 newly installed, 0 to remove and 207 not upgraded.
Need to get 9,861kB of archives.
After this operation, 26.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libwxbase2.8-0 2.8.10.1-0ubuntu1 [689kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libwxgtk2.8-0 2.8.10.1-0ubuntu1 [3,455kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe libcodeblocks0 8.02-0ubuntu4 [1,521kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe codeblocks 8.02-0ubuntu4 [4,195kB]
Fetched 9,861kB in 1min 1s (161kB/s)                                           
Selecting previously deselected package libwxbase2.8-0.
(Reading database ... 114050 files and directories currently installed.)
Unpacking libwxbase2.8-0 (from .../libwxbase2.8-0_2.8.10.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libwxgtk2.8-0.
Unpacking libwxgtk2.8-0 (from .../libwxgtk2.8-0_2.8.10.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libcodeblocks0.
Unpacking libcodeblocks0 (from .../libcodeblocks0_8.02-0ubuntu4_i386.deb) ...
Selecting previously deselected package codeblocks.
Unpacking codeblocks (from .../codeblocks_8.02-0ubuntu4_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-icon-theme ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Setting up libwxbase2.8-0 (2.8.10.1-0ubuntu1) ...

Setting up libwxgtk2.8-0 (2.8.10.1-0ubuntu1) ...

Setting up libcodeblocks0 (8.02-0ubuntu4) ...

Setting up codeblocks (8.02-0ubuntu4) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
:D

---

### Post by omicron84 on 2010-02-04
I have the same problem, with sudo apt-get update not working
but when I tried sudo apt-get update, sudo apt-get install codeblocks, 
it returned the same error.
 
could someone help me?

---

### Post by snowpine on 2010-02-04
> **omicron84 said:**
> I have the same problem, with sudo apt-get update not working
but when I tried sudo apt-get update, sudo apt-get install codeblocks, 
it returned the same error.
 
could someone help me?

Please copy & paste the error message here, and I will try my best to help. :)

---

### Post by brucem9999 on 2010-02-04
I have same problem. I have reinstalled three times. Repartioned all three times. As soon as the system boots for the first time, I connect to the I-net, open firefox, open my email which immediately states that flashplayer is required. I click to install and get, "could not find package "flash plugin-installer".

I go to software center / sound video and try to down load Swfdec and get "Not available in the current data". Then every package I try to download gets the same message, "Not available in the current data".

---

### Post by snowpine on 2010-02-04
> **brucem9999 said:**
> I have same problem. I have reinstalled three times. Repartioned all three times. As soon as the system boots for the first time, I connect to the I-net, open firefox, open my email which immediately states that flashplayer is required. I click to install and get, "could not find package "flash plugin-installer".

I go to software center / sound video and try to down load Swfdec and get "Not available in the current data". Then every package I try to download gets the same message, "Not available in the current data".

Hi Bruce, it's advisable to start a new thread since you have a different problemm, maybe with a descriptive title like "Please help me install Flash." Or better yet use the Search feature. ;)

Since I'm already typing though, here is the solution:

```
sudo apt-get update
sudo apt-get install flashplugin-installer
```

(This is assuming you're using the 32 bit version of Ubuntu 9.10, if not, please post the full details in the new thread you're going to start.)

---

### Post by omicron84 on 2010-02-04
My message
****@ubuntu:~$ sudo apt-get update
[sudo] password for ****: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Reading package lists... Done
****@ubuntu:~$ sudo apt-get install codeblocks
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package codeblocks
****@ubuntu:~$

---

### Post by snowpine on 2010-02-04
Comparing your output with 006ruler's, it looks like you don't have the "Universe" repository in your Software Sources. Try:

```
gksu gedit /etc/apt/sources.list
```

See if there is a # symbol at the beginning of the line for Universe, and delete the # (to uncomment this line). Then save the file and try updating & installing codeblocks again. :)

---

### Post by brucem9999 on 2010-02-05
Thanks to snowpine for the reply.

This solved my problem.

But I wonder (rhetorically) why the first time (or two) I installed Umbuntu I didn't have this problem, but, using the same install disk, it popped up on a subsequent install??????

---

### Post by st0nes on 2010-03-01
I'm afraid it doesn't work for me, either.  Here's what I get:-
> mark@addy-laptop:~$ sudo apt-get update
[sudo] password for mark: 
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                                                                                        e
  Could not connect to 196.5.234.34:3142 (196.5.234.34). - connect (111: Connection refused)
Err [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release.gpg                                                                                       
  Could not connect to 196.5.234.34:3142 (196.5.234.34). - connect (111: Connection refused)
Err [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg                                                                                       
  Could not connect to 196.5.234.34:3142 (196.5.234.34). - connect (111: Connection refused)
Err [http://ftp.saix.net](http://ftp.saix.net) karmic Release.gpg  
Why is a common product like Lyx or Latex not available in the repositories?  Seems Ubuntu just gets worse and worse with every release.

---

### Post by snowpine on 2010-03-01
> **st0nes said:**
> I'm afraid it doesn't work for me, either.  Here's what I get:-

Why is a common product like Lyx or Latex not available in the repositories?  Seems Ubuntu just gets worse and worse with every release.

None of the 4 repositories in your error message are part of a default Ubuntu install. It is not Ubuntu's fault if the user adds software sources incorrectly. :)

Please read the instructions carefully at the medibuntu, geekconnection, virtualbox, and saix websites, if you want to use these unsupported software sources.

Lyx and Latex are, indeed, in the standard Ubuntu repositories. You just can't install them right now, because you broke your software sources. ;) Fix your user error and then you should be able to install applications again.

---

