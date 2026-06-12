---
title: "errors that I do not understand doing apt-get"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by kystorms on 2007-06-10
Hi
I get the following error code when ever I try to download any program or file, even updates in update manager

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Can someone please tell me where i need to go to learn how to rectify this problem, as I can not update or load any programs in this.

This install is fresh from a disk sent by ubuntu fiesty 7.04, not a downloaded disk

thank you:(

---

### Post by KitChy on 2007-06-10
> W: You may want to run apt-get update to correct these problems

Have you tried what it said in the error? ^

---

### Post by taurus on 2007-06-10
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```
Otherwise, post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by kystorms on 2007-06-10
this is what i get when i do sudo apt-get update 

W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


and this is my files you asked for:

lisac@lisac-desktop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb [http://ftp.debian.org](http://ftp.debian.org) sarge main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
lisac@lisac-desktop:~$

---

### Post by Jussi Kukkonen on 2007-06-10
> 
This install is fresh from a disk sent by ubuntu fiesty 7.04
Are you sure you haven't edited *sources.list*? It looks like the file is screwed up at least in a couple of ways... 

You probably have at least a duplicate entry there, and the mention of [http://ftp.debian.org/](http://ftp.debian.org/) is scary -- I hope you know what you are doing if you mix Ubuntu and Debian package sources. It might be best if you paste the contents of */etc/apt/sources.list* here.

EDIT: I see you already pasted it. Can you tell why you have the Debian Sarge line there? That is potentially dangerous...

---

### Post by kystorms on 2007-06-10
i sure have no idea how to do things on my own, so i just put the disk in, and this is what istarted getting right off the bat...
how do i get that list you asked for?

---

### Post by kystorms on 2007-06-10
i have no idea!!!!!!!!!
can someone tell me how to remove this?

---

### Post by Jussi Kukkonen on 2007-06-10
> **kystorms said:**
> i sure have no idea how to do things on my own, so i just put the disk in, and this is what istarted getting right off the bat...
how do i get that list you asked for?
kystorms the list is correct, but the first sentence is not true. You installed at least Automatix, and somehow added the debian.org line...

---

### Post by kystorms on 2007-06-10
okay , what i meant was that nothing is on here that did not come from using the programs to get them, i meant i did not add any lines on my own

is there a way to fix this?

---

### Post by taurus on 2007-06-10
Personally, I would edit /etc/apt/source from a terminal

```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from all the repos.   Then, remove these last lines from it as well.

```
deb http://ftp.debian.org sarge main
deb http://www.getautomatix.com/apt feisty main

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
```
Save the changes and close the gedit window.  Then, run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by kystorms on 2007-06-10
please understand I am a new user, I dont mean to bug anyone here, but this is the only place i have to go to ask for help

thank you

---

### Post by diatribe on 2007-06-10
you were just told what to do; and if you are asking for help you need to be honest about what you have/have not done otherwise the help people try to offer could make things worse, or not have their desired effect

---

### Post by kystorms on 2007-06-10
not meaning to sound stupid here, but do you mean to remove only the "us." itelf from each repo, or the repo line  in total?

---

### Post by taurus on 2007-06-10
> **kystorms said:**
> not meaning to sound stupid here, but do you mean to remove only the "us." itelf from each repo, or the repo line  in total?

Just remove the **us.** from all the lines (BUT not the whole lines) that have it.  Then, remove those last lines as in my previous post.

---

### Post by kystorms on 2007-06-10
> **diatribe said:**
> you were just told what to do; and if you are asking for help you need to be honest about what you have/have not done otherwise the help people try to offer could make things worse, or not have their desired effect

I was not being intentionally dishonest, i am a 44 year old woman who has never done this kind of thing before and its hard for me to discribe what my problems with this are, and i made a mistatment. i am very sorry

---

### Post by kystorms on 2007-06-10
> **taurus said:**
> Just remove the **us.** from all the lines (BUT not the whole lines) that have it.  Then, remove those last lines as in my previous post.

okay, thanks i will do and hopefully be back here to thank you again

:KS

---

### Post by kystorms on 2007-06-10
okay, removed the us. and the last lines

saved then did sudo apt-get update

and got this error
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

and then did the sudo-apt-get upgrade and it said 

lisac@lisac-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lisac@lisac-desktop:~$

---

### Post by taurus on 2007-06-10
Run those two commands again.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by arnieboy on 2007-06-10
> **kystorms said:**
> okay, removed the us. and the last lines

saved then did sudo apt-get update

and got this error
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

and then did the sudo-apt-get upgrade and it said 

lisac@lisac-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lisac@lisac-desktop:~$
Please thanks everyone else in this thread for their help (which was for the most part misguided) and simply do the following:
```
sudo gedit /etc/apt/sources.list
```
and delete whatever's there in it and replace it with the following:
> ####################################
### Official Ubuntu Repositories ###
####################################

# Feisty Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse

# Feisty Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

# Feisty Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse

# Feisty Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

# Ubuntu Commercial
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
save and close the file and do a:
```
sudo apt-get update
```

---

### Post by kystorms on 2007-06-10
ran again with same results

W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
lisac@lisac-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lisac@lisac-desktop:~$

---

### Post by arnieboy on 2007-06-10
> **taurus said:**
> Run those two commands again.

```
sudo apt-get update
sudo apt-get upgrade
```

dude.. once and for all: removing the automatix repository section really never serves any purpose (as you have seen here and in the past but you will end up asking users to do it anyways ).. because automatix adds whatever is **MISSING**.. You need to look above the Automatix section to figure out whats causing the duplication which Synaptic and other sources add later because their algorithms don't check for duplicates. I would really appreciate it if you tried to understand this.. since you are such a prolific poster in the beginner's section which deals with broken sources.list.

---

### Post by kystorms on 2007-06-10
> **arnieboy said:**
> Please thanks everyone else in this thread for their help (which was for the most part misguided) and simply do the following:
```
sudo gedit /etc/apt/sources.list
```
and delete whatever's there in it and replace it with the following:

save and close the file and do a:
```
sudo apt-get update
```

did as you suggested - and got this at the end of all the codes


Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
lisac@lisac-desktop:~$

---

### Post by kystorms on 2007-06-10
should i just try to copy my files i have made so far of my own stuff to disk and do a fresh install again?

thanks

---

### Post by arnieboy on 2007-06-10
> **kystorms said:**
> did as you suggested - and got this at the end of all the codes


Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
lisac@lisac-desktop:~$

you havent done as I suggested quite obviously since apt is still trying to connect to security.ubuntu.com . Please paste the result of the following command:
```
cat /etc/apt/sources.list
```
I had said, "DELETE" whatever is in it and replace it with the repositories in quotes.

---

### Post by arnieboy on 2007-06-10
> **kystorms said:**
> should i just try to copy my files i have made so far of my own stuff to disk and do a fresh install again?

thanks

NO fresh install is required. Just read my instructions carefully and you will sail through. Read post #19 carefully again.

---

### Post by kystorms on 2007-06-10
lisac@lisac-desktop:~$ cat /etc/apt/sources.list
####################################
### Official Ubuntu Repositories ###
####################################

# Feisty Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse

# Feisty Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

# Feisty Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse

# Feisty Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

# Ubuntu Commercial
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main 

lisac@lisac-desktop:~$

---

### Post by arnieboy on 2007-06-10
alright now simply do:
```
sudo apt-get clean
```
```
sudo apt-get update
```
and paste the results of the second command here (all of it)

---

### Post by kystorms on 2007-06-10
lisac@lisac-desktop:~$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US                  
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Get:3 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages [30.2kB]        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US              
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages             
Get:10 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US
Get:11 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release [7232B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages                     
Fetched 37.6kB in 7s (5214B/s)                                                 
Reading package lists... Done
lisac@lisac-desktop:~$

---

### Post by arnieboy on 2007-06-10
As you can see there are no errors now though you have the medibuntu repositories lurking in an apt sub folder but thats ok. 
You are all set now.
Thank me and move on. :)

---

### Post by kystorms on 2007-06-10
oh cool!!!!    thanks so very very much..............:KS

---

