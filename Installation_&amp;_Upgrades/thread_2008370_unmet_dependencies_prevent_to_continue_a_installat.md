---
title: "unmet dependencies prevent to continue a installation"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by masonTen on 2012-06-22
Hi all,
I already tried to find a solution on internet but nothing worked.

My SO: "Ubuntu 10.04"
My goal: install Wine. but I always get the message of unmet dependencies
Since it has dependecies I tried to installed them first with the same result: unmet dependencies.
[HTML]sudo apt-get install wine1.2
The following packages have unmet dependencies:
  wine1.2: Depends: ia32-libs (>= 1.6) but it is not going to be installed
           Depends: lib32asound2 (> 1.0.14) but it is not going to be installed
           Depends: libc6-i386 (>= 2.6-1) but it is not going to be installed
           Depends: lib32nss-mdns (>= 0.10-3) but it is not going to be installed
           Recommends: winbind but it is not going to be installed
E: Broken packages
[/HTML]
Then I tried to install "ia32-libs" which depends on lib32gcc1, when trying to install "lib32gcc1" shows:
[PHP]The following packages have unmet dependencies:
  lib32gcc1: Depends: gcc-4.4-base (= 4.4.3-4ubuntu5) but 4.4.3-4ubuntu5.1 is to be installed
             Depends: libc6-i386 (>= 2.5) but it is not going to be installed
[/PHP]
Not sure but I think it says that lib32gcc1 needs gcc-4.4-base (version = 4.4.3-4ubuntu5) BUT the "4.4.3-4ubuntu5.1" version is ALREADY installed.

I already tried:
- updated repositories
apt-get update
- Enabled all  "Ubuntu software" sources in Software sources
- fix broken issues
    apt-get -f install wine1.2
   

So how could I fix this?

Thanks.

---

### Post by Paddy Landau on 2012-06-23
Why are you installing specifically wine1.2?

You should really install the meta-package wine. Try:
```
sudo apt-get install wine
```(BTW, to include terminal code, don't use HTML code or PHP code, but just CODE — it's the "#" button on the toolbar.)

---

### Post by masonTen on 2012-06-23
Simply because it depends of 1.2
```
sudo apt-get install wine
The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages

```

---

### Post by Paddy Landau on 2012-06-24
I see something that I missed the last time: Broken packages.

This is not an area in which I am expert, but try these commands to see if they fix the problem.
```
sudo apt-get --fix-broken install
sudo dpkg --configure --pending
sudo apt-get update
sudo apt-get upgrade
```If they all work, try installing [[FONT=Lucida Console]wine[/FONT]]("apt:wine") (not [FONT=Lucida Console]wine1.2[/FONT]) again.

---

### Post by masonTen on 2012-06-24
I just applied them but it didn't work.

---

### Post by Paddy Landau on 2012-06-24
I don't understand why your system is complaining about [FONT=Lucida Console]lib32nss-mdns[/FONT] and [FONT=Lucida Console]gcc-4.4-base[/FONT], because they are not installed on my system.


[LIST]
[*] What version of Ubuntu are you using, and are you using 32-bit or 64-bit? If you aren't sure of the answers, post the output of the following two commands.```
uname --all
lsb_release --all
```
[/LIST]

[LIST]
[*]Have you changed your repository list at all?
[/LIST]

[LIST]
[*]I'd also like you to post the output of the following two commands:```
sudo apt-get update
sudo apt-get upgrade
```
[/LIST]

---

### Post by masonTen on 2012-06-24
1 - I have a 64bits pc, so I have installed Ubuntu 10.04 LTS Lucid Lynx 64bit.
2 - Not sure but I've installed other apps without issues.
3 - ```
apt$ sudo apt-get update
Hit http://archive.canonical.com lucid Release.gpg                                                 
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                            
Get:1 http://archive.ubuntu.com lucid Release.gpg [189B]                                            
Hit http://archive.canonical.com lucid Release                                                               
Get:2 http://archive.ubuntu.com lucid Release [57.2kB]                        
Get:3 http://ar.archive.ubuntu.com lucid Release.gpg [189B]                
Ign http://ar.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US               
Ign http://ar.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://archive.canonical.com lucid/partner Packages
Ign http://ar.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://ar.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:4 http://ar.archive.ubuntu.com lucid Release [57.2kB]
Get:5 http://archive.ubuntu.com lucid/main Sources [659kB]     
Get:6 http://ar.archive.ubuntu.com lucid/main Packages [1,383kB]
Get:7 http://archive.ubuntu.com lucid/restricted Sources [3,775B]                                                                     
Get:8 http://ar.archive.ubuntu.com lucid/restricted Packages [6,193B]                                                                                         
Get:9 http://ar.archive.ubuntu.com lucid/restricted Sources [3,775B]                                                                                          
Get:10 http://ar.archive.ubuntu.com lucid/main Sources [659kB]                                                                                                
Get:11 http://ar.archive.ubuntu.com lucid/multiverse Sources [119kB]                                                                                          
Get:12 http://ar.archive.ubuntu.com lucid/universe Sources [3,165kB]                                                                                          
Get:13 http://ar.archive.ubuntu.com lucid/universe Packages [5,430kB]                                                                                         
Get:14 http://ar.archive.ubuntu.com lucid/multiverse Packages [176kB]                                                                                         
Fetched 11.7MB in 48s (242kB/s)                                                                                                                               
Reading package lists... Done

``````
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by raja.genupula on 2012-06-24
have you see   wine in Ubuntu software center , type as wine in search box .

---

### Post by masonTen on 2012-06-24
Yes, I've tried that, synaptic PManager, and apt-get.
With same results, in Ubuntu Software Center it reads:
```
This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.
```
It has the same behaviour.

---

### Post by Curtis6767 on 2012-06-24
You could try to install 1a32-libs. That might resolve some of the issues. If you have Synaptic, then search for it there and/or try the following.

  	 	 	 	 	 	   ```
sudo apt-get install librtmp0/precise
```  Just be sure to substitute your release for 'precise'.

If that is successful, then you could try to install Wine again.

---

### Post by masonTen on 2012-06-24
ok, by "1a32-libs" I assume it should be ia32-libs, that leads to some uninstalled dependecies which lead to similar original problem.
```
The following packages have unmet dependencies:
  libc6-i386: Depends: libc6 (= 2.11.1-0ubuntu7) but 2.11.1-0ubuntu7.10 is to be installed

```
librtmp0 is not part of a repository (I already updated my repos update/upgrade)
```
E: Couldn't find package librtmp0
```

---

### Post by raja.genupula on 2012-06-24
[http://launchpadlibrarian.net/45033706/libc6_2.11.1-0ubuntu7_i386.deb](http://launchpadlibrarian.net/45033706/libc6_2.11.1-0ubuntu7_i386.deb)

that will give you the required dependent .

install it with the```
 sudo dpkg - i <filename.deb>
```

---

### Post by masonTen on 2012-06-29
Ok, the deb file gave me a hint which helped me to start to solve this.
I had to search the libc6 equivalent for 64bit, its installation was easy, without any issues.
So the next important one was ia32-libs, which I found in 
```
http://packages.ubuntu.com/lucid/amd64/ia32-libs/download
```
In that page they suggested to add a mirror to my sources.list
```
deb http://security.ubuntu.com/ubuntu lucid-security main universe

```Then I had to update the repositories
```
apt-get update
```
This command led me to execute an upgrade
```
apt-get upgrade
```
which made a general upgrade for many apps I had installed. This had unexpected results, nothing major but several apps were affected, (Firefox, the flash Plugin crashed, Chrome also the audio and video got corrupted so I had to reinstall my audio and video drivers).
In brief, I got really scared but I managed to resolve all issues.

So then I tried again to install wine, which to my surprise was installed among with its dependencies, but this time I didn't have to deal with unmet dependencies.
The installation was succesfull. So now 2 questions emerge to my mind:


1 - I had to download the libc6 .deb file from that site to install it, instead of use Synaptic, Ubuntu Software Center, dpkg, or apt-get. If I were a lazy guy, I could say: "Ok the next time I'll just download .deb files directlly it would be much more easy". I know that sounds stupid but it has a lot of sense, don't you think?


2 - Why did I have to add the main universe mirror to source.list? It seems to be a very fundamental source, since it solved all my dependencies issues. Shouldn't be part of source.list by default? (A very major lack if you ask me)

Thanks ;)

---

### Post by Paddy Landau on 2012-06-30
> **masonTen said:**
> Why did I have to add the main universe mirror to source.list?
Ah, that may explain it. I don't know why your universe was not there — it normally is, by default.

Open your Software Sources (from the System > Administration menu), and check that you have all of main, universe, restricted and multiverse checked.

A [brief tutorial]("http://www.liberiangeek.net/2010/06/configuring-software-sources-ubuntu-10-04-lucid-lynx-receive-updatespatches/") shows some suggested settings for 10.04.

---

### Post by masonTen on 2012-06-30
This is really strange, I had those main, universe, restricted and multiverse checked in Software sources.
Another problem that I found out when using the Sources, is that if  I uncheck those 4 mirror and later select them again the 
/etc/apt/source.list file is never recovers the mirrors that I have originally, to be more specific.

```
deb http://security.ubuntu.com/ubuntu lucid-security main universe
```
I'll try to avoid the use of this Software Source ;)

---

### Post by Paddy Landau on 2012-06-30
All I know, masonTen, is that somehow something went wrong with your set-up.

When the times comes for you to upgrade to 12.04, I hope that will be solved.

---

