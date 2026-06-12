---
title: "Having trouble installing VLC and other programs"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by kratos777 on 2007-12-18
Hello, I am new to ubuntu and linux. I was trying to install VLC and I keep getting this error message:

This application conflicts with other installed software. To install 'vlc' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

I have no clue what to do in the package manager. Any help is greatly appreciated.

---

### Post by taurus on 2007-12-18
Post the complete output of these two commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install vlc
```

Also, post your /etc/apt/sources.list too.

```
cat /etc/apt/sources.list
```

---

### Post by stalker145 on 2007-12-18
> **kratos777 said:**
> Hello, I am new to ubuntu and linux. I was trying to install VLC and I keep getting this error message:

This application conflicts with other installed software. To install 'vlc' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

I have no clue what to do in the package manager. Any help is greatly appreciated.

From the sound of it, it is asking you to go to System ~> Administration ~> Synaptic Package Manager and choose the individual applications that are causing the problem. All you will need to do there is to track down the apps that are mentioned, click the square next to the name, and select to remove.

How are you trying to install these programs? Are you using a deb, tarball, command line? Personally, if you are doing anything other than the repositories, I would suggest that you move to the repositories and use them until you are comfortable with how this works.

Synaptic and Add/Remove (on your Applications menu) are probably the easiest way for newcomers to begin learning the system.

Check back if you are still having troubles.

---

### Post by kratos777 on 2007-12-18
> **taurus said:**
> Post the complete output of these two commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install vlc
```

Also, post your /etc/apt/sources.list too.

```
cat /etc/apt/sources.list
```
Here is all the stuff you asked for

acordova@acordova-laptop:~$ sudo apt-get update
[sudo] password for acordova:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US 
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US       
Get:3 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release.gpg [191B]       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy/main Packages
Fetched 3B in 1s (3B/s)  
Reading package lists... Done

acordova@acordova-laptop:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 0.8.6.release.c-0ubuntu5) but it is not going to be installed
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: ttf-dejavu but it is not installable
E: Broken packages

cordova@acordova-laptop:~$ cat /etc/apt/sources.list
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe

---

### Post by taurus on 2007-12-18
> **kratos777 said:**
> 
cordova@acordova-laptop:~$ cat /etc/apt/sources.list
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe

Can you post the whole thing, /etc/apt/sources.list, or is that all you have for /etc/apt/sources.list?

---

### Post by kratos777 on 2007-12-18
That is all I have

---

### Post by taurus on 2007-12-18
I bet you modified your /etc/apt/sources.list before.  Why don't you save it and then add more repos to it so you can install more stuff.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list
```
and remove everything in there.  Then, copy and paste these.

```

deb http://archive.ubuntu.com/ubuntu gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu gutsy universe
deb-src http://archive.ubuntu.com/ubuntu gutsy universe

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe

deb http://archive.ubuntu.com/ubuntu gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy multiverse

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy-commercial main 

```
Save it and close down gedit window.  Then, run

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install vlc
```

---

### Post by adityakavoor on 2007-12-18
```

sudo apt-get install -f

```
to remove broken packages

---

### Post by kratos777 on 2007-12-18
Thanks, It worked.

---

