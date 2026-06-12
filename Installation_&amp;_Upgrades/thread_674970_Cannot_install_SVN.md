---
title: "Cannot install SVN"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by Contess on 2008-01-22
Hello

NEWBIE PROBLEM


I am trying to install subversion (svn) but I am getting an error message saying that svn could not be installed because it would conflict with another software.

root@contessa:/home/contessa# apt-get install subversion build-essential linux-headers-`uname -r`Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package subversion is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package subversion has no installation candidate

root@contessa:/home/contessa# su contessa
contessa@contessa:~$ sudo aptitude update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy Release.gpg [191B]                                                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe Translation-en_CA
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/multiverse Packages                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources                                                
Fetched 3B in 6s (0B/s)                                                                                         
Reading package lists... Done

contessa@contessa:~$ sudo aptitude install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for subversion
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      

root@contessa:/# apt-get install subversion build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package subversion is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package subversion has no installation candidate
root@contessa:/# cd /usr/src/
root@contessa:/usr/src# svn -r 2834 checkout [http://svn.madwifi.org/madwifi/trunk/](http://svn.madwifi.org/madwifi/trunk/) madwifi-ng
The program 'svn' is currently not installed.  You can install it by typing:
apt-get install subversion
bash: svn: command not found

root@contessa:/usr/src# apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package subversion is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package subversion has no installation candidate

############

I then went into synaptic package manager and looked for something obvious but I failed.

Someone here (in another thread, pointed out that I should visit subversions site and follow their install method (building from source) But I couldn't figure it out.



Thanks

Contessa

---

### Post by Contess on 2008-01-22
Well.. now I have tried to install "RapidSVN" using the "Add/Remove Applications" function.
When I tick the checkbox to install RapidSVN, an error pops up, saying the following:

############################################
CANNOT INSTALL 'rapidsvn'
This application conflicts with other installed software.
To install'rapidsvn' the conflicting software must be removed first.

SWitch to the 'synaptic' package-manager to resolve this conflict.
############################################

Well, I did that but I don't know what to look for since I am a Ubuntu newbie. I am also not overly familiar with unix processes, just rying to make the switch away from Microsoft products.
This installation is totally fresh, on a previously formatted hard drive and no dual-boot. The only things that were installed after the Ubuntu setup, were the automatic updates (177 of them) recommended by the system.

Can someone tell me how to find this conflicting piece of software so that I can install subversion. ?

Many thanks

---

### Post by Contess on 2008-01-24
:popcorn: Anyone here ;-) just kidding. .. but would be great if someone could help me get going with SVN.

Many thanks

Contessa

---

### Post by Partyboi2 on 2008-01-24
what happens if you
```
sudo apt-get install -f
```

Edit:  What Happens if you download the subversion package from [here]("http://packages.ubuntu.com/gutsy/devel/subversion")
and install it manually.

---

### Post by Contess on 2008-01-25
> **Partyboi2 said:**
> what happens if you
```
sudo apt-get install -f
```

Edit:  What Happens if you download the subversion package from [here]("http://packages.ubuntu.com/gutsy/devel/subversion")
and install it manually.


Hello

after following your link and manually grabbing all the dependet packagages on that page, subversion installed fine :popcorn: , thank you very much

There is one more thing I would like to ask you:

When I selected db4.4-util because this ws a dependency for subversion, I got a warning saying:
"YOU ARA ABOUT TO INSTALL SOFTWARE THAT CAN'T BE AUTHENTICATED
DOING THIS COULD ALLOW A MALICIOUS INDIVIDUAL TO DAMAGE OR TAKE
CONTROL OF YOUR SYSTEM"

I accepted to install db4.4-util since without it, subversion would not install and this is a test setup computer not a production machine. Can you comment on that warning ?

Regards

Contessa

---

### Post by Partyboi2 on 2008-01-25
It means that the repositories that you are trying to access are not verified by the gpg key. Here is some more info on [gpg]("https://help.ubuntu.com/community/SecureApt")

---

### Post by Contess on 2008-01-26
got it :)

thx

---

### Post by danoglam on 2008-02-19
The solution, I mean, the easy way:

+ Go to *System>Administration>Software Sources* 
+ **check** the option "Canonical-supported Open Source Software"
+ When you press close, you got an update from the sources.

Now open a terminal and just type:

$ sudo apt-get install subversion

cheers.

---

