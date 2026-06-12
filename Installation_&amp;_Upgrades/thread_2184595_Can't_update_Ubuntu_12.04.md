---
title: "Can't update Ubuntu 12.04"
date: 2013-10-29
forum: Installation &amp; Upgrades
---

### Post by mikee.bowen on 2013-10-29
I am running Ubuntu 12.04. I have been unable to update for a few weeks now and strangely my background image disappeared yesterday and I can't put up a new one. I've searched the forums and have been unable to find anything that solves the problem.

When I try to update, I get the following message:

The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

I opened the terminal and entered "apt-get install -f" and I got the following message:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

So I tried "sudo apt-get install -f" and I got the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  nemo
The following packages will be upgraded:
  nemo
1 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
1 not fully installed or removed.
Need to get 0 B/938 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of nemo:
 nemo depends on nemo-data (= 2.0.1-20131021010006-precise); however:
  Version of nemo-data on system is 2.0.2-20131023010018-precise.
dpkg: error processing nemo (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 nemo
E: Sub-process /usr/bin/dpkg returned an error code (1)


If someone could let me know how to update that would be great. Let me know if you need more information. Thanks in advance!

---

### Post by Bashing-om on 2013-10-29
mikee.bowen; Hi !

Are you presently running the Cinnamon desktop ?
> 
Description-en: File manager and graphical shell for Cinnamon
 Nemo is the official file manager for the Cinnamon desktop. It allows
 to browse directories, preview files and launch applications associated
 with them. It is also responsible for handling the icons on the Cinnamon
 desktop. It works on local and remote filesystems.


If you are not currently using it .. Might be best to remove it, reverting back to unity ?

For now try:
```

sudo apt-get remove --purge nemo

```
If you want to keep Cinnamon, then (re-)install "nemo", and see what results:
```

sudo apt-get install nemo

```

Else: remove the Cinnamon desk top.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-10-29
I can try going back to Unity, although I'm not a big fan. But first I tried your other tips, but when I put sudo "sudo apt-get remove --purge nemo" I got the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 nemo-fileroller : Depends: nemo but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Then I typed "sudo apt-get install nemo" and got the following message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  nemo
1 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
1 not fully installed or removed.
Need to get 0 B/938 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: dependency problems prevent configuration of nemo:
 nemo depends on nemo-data (= 2.0.1-20131021010006-precise); however:
  Version of nemo-data on system is 2.0.2-20131023010018-precise.
dpkg: error processing nemo (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 nemo
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2013-10-29
mikee.bowen; Well,

Not the result I had anticipated.
Let's start drilling down and see if we can get to the bottom of this:
```

sudo apt-get remove nemo-data

```
I expect that result to provide a bit more info to indicate what is not taking place.

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-10-29
Ok, I entered the code and this is what a I got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cinnamon-settings-daemon : Depends: nemo-data but it is not going to be installed
                            Recommends: systemd-services but it is not installable
 nemo : Depends: nemo-data (= 2.0.1-20131021010006-precise) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Bashing-om on 2013-10-30
mikee.bowen; Not OK, but,

Show what is installed and installable from:
```

sudo dpkg -C
apt-cache policy nemo-data

```
As we go twisting about.

[INDENT][INDENT]we keep look'n
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-10-30
"sudo dpkg -C" gave me:

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 nemo                 file manager and graphical shell for Cinnamon

And "apt-cache policy nemo-data" gave me:

nemo-data:
  Installed: 2.0.2-20131023010018-precise
  Candidate: 2.0.2-20131023010018-precise
  Version table:
 *** 2.0.2-20131023010018-precise 0
        500 [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/) precise/main i386 Packages
        100 /var/lib/dpkg/status
     1.0.3-0ubuntu1~precise1 0
        500 [http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/](http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/) precise/main i386 Packages

---

### Post by Bashing-om on 2013-10-30
mikee.bowen; Well,

I may have an idea now as to what is going on.
Did you activate a PPA to install Cinnamon without removing that version that was installed from the repository ?
show us what your sources are: - place that output between code tags:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
//
Post the output of:
```

cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d

```

And not to leave ya in a bind, but I am done think'n for this session, and I must be out of town tomorrow.

Others will have to take up the baton, I will check back in tomorrow evening.

[INDENT][INDENT]not ubuntu's fault ?
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-10-30
"cat -n /etc/apt/sources.list" gave me:

     > 1    # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
     6    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    11    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    17    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
    18    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    19    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    27    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
    28    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    29    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    37    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
    38    
    39    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    40    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
    41    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe


    42    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
    43    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    44    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    51    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    56    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    57    deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
    58    deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free





And "ls -la /etc/apt/sources.list.d" gave me:
> 
total 44
drwxr-xr-x 2 root root 4096 Dec  8  2012 .
drwxr-xr-x 6 root root 4096 Oct 13 08:41 ..
-rw-r--r-- 1 root root   54 May  5 13:37 google-earth.list
-rw-r--r-- 1 root root   54 Dec  8  2012 google.list
-rw-r--r-- 1 root root   54 Dec  8  2012 google.list.save
-rw-r--r-- 1 root root  180 Dec  8  2012 google-talkplugin.list
-rw-r--r-- 1 root root  180 Dec  8  2012 google-talkplugin.list.save
-rw-r--r-- 1 root root  174 Dec  8  2012 gwendal-lebihan-dev-cinnamon-stable-precise.list
-rw-r--r-- 1 root root  174 Dec  8  2012 gwendal-lebihan-dev-cinnamon-stable-precise.list.save
-rw-r--r-- 1 root root  148 Dec  8  2012 merlwiz79-cinnamon-ppa-precise.list
-rw-r--r-- 1 root root  148 Dec  8  2012 merlwiz79-cinnamon-ppa-precise.list.save




Thanks for you help

---

### Post by mikee.bowen on 2013-10-30
I meant to edit the above post, but I can't delete this post now. I'm still looking for some help. Thanks

---

### Post by Bashing-om on 2013-10-30
mikee.bowen; Well,

You have duplicated sources for Cinnamon in /etc/apt/sources.list.d directory.
> 
-rw-r--r-- 1 root root 174 Dec 8 2012 gwendal-lebihan-dev-cinnamon-stable-precise.list
-rw-r--r-- 1 root root 174 Dec 8 2012 gwendal-lebihan-dev-cinnamon-stable-precise.list.save
-rw-r--r-- 1 root root 148 Dec 8 2012 merlwiz79-cinnamon-ppa-precise.list
-rw-r--r-- 1 root root 148 Dec 8 2012 merlwiz79-cinnamon-ppa-precise.list.save

Which one do you want to use ? as one of them must be removed.
//
also in your source list file there are entries for no longer existent repository "medibuntu" lines 57 and 58, these lines should also be removed.
Are you comfortable editing system files ?

I must depart you and catch ya later, prepare for my morrow.

[INDENT][INDENT]the lights just came on
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-10-30
I don't really care which one gets deleted. I'm using gnome anyway. 

I've never edited a system file before, but there's a first time for everything. How would I edit it? 

Have a good night, I hope you can help tomorrow :-)

---

### Post by Bashing-om on 2013-10-30
mikee.bowen; Hey, I am back.

Let's see what we can do about backing out of this.
run terminal command:
```

sudo add-apt-repository --remove ppa:gwendal-lebihan-dev/cinnamon-stable

```
If that runs with no errors, I want to see if the get file was also removed:
show me:
```

ls -la /etc/apt/sources.list.d

```

Bear in mind it is possible that the other PPA for Cinnamon may also require removing. We will see.

One thing at a time, get this PPA stable, then we will remove the medibuntu source lines.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-10-30
Hi Bashing-om, I'm glad you're back, you and the other people on this forum are a huge help!

Here's what I got from "sudo add-apt-repository --remove ppa:gwendal-lebihan-dev/cinnamon-stable"

> You are about to remove the following PPA from your system:
 This PPA contains the stable releases of cinnamon for Precise, Quantal, Raring and Saucy.

Cinnamon website : [http://cinnamon.linuxmint.com/](http://cinnamon.linuxmint.com/)
 More info: [https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable](https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable)
Press [ENTER] to continue or ctrl-c to cancel removing it

I pressed enter and it waited a sec and went to a new command line without anymore info.

Then I did "ls -la /etc/apt/sources.list.d" and got:

> 
total 44
drwxr-xr-x 2 root root 4096 Oct 30 18:27 .
drwxr-xr-x 6 root root 4096 Oct 13 08:41 ..
-rw-r--r-- 1 root root   54 Oct 30 18:27 google-earth.list
-rw-r--r-- 1 root root   54 Oct 30 18:27 google-earth.list.save
-rw-r--r-- 1 root root   54 Oct 30 18:27 google.list
-rw-r--r-- 1 root root   54 Oct 30 18:27 google.list.save
-rw-r--r-- 1 root root  180 Oct 30 18:27 google-talkplugin.list
-rw-r--r-- 1 root root  180 Oct 30 18:27 google-talkplugin.list.save
-rw-r--r-- 1 root root    0 Oct 30 18:27 gwendal-lebihan-dev-cinnamon-stable-precise.list
-rw-r--r-- 1 root root   89 Oct 30 18:27 gwendal-lebihan-dev-cinnamon-stable-precise.list.save
-rw-r--r-- 1 root root  148 Oct 30 18:27 merlwiz79-cinnamon-ppa-precise.list
-rw-r--r-- 1 root root  148 Oct 30 18:27 merlwiz79-cinnamon-ppa-precise.list.save

---

### Post by Bashing-om on 2013-10-30
mikee.bowen; Good deal,

Linux commands: a return of nothing means the system happily complied. If there were a problem the system would have advised.
Ok, now to deal with the medibuntu repository, and then see where we stand.
We are going to edit the source file, Always make a backup file anytime you edit any file for any reason. Murphy's law always applies ! .. Whatever can happen will happen and a power failure can be difficult to reconcile:
Do in terminal: - COPY and paste the commands into your terminal -
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-bak

```
Now to edit that file:
```

gksudo gedit /etc/apt/sources.list

```
Opens the text editor "gedit" with admin privileges with "sources.list" loaded.
cursor down to the last line(s) and with the "delete" key carefully delete both lines containing the phrase "http://packages.medibuntu.org/ hardy free non-free". Careful that you do not delete anything in the line above.

Save the file and exit back to terminal.

All good so far ? Any concerns, pause and ask ... nothing to it !

Ready to proceed ....Then in terminal:
```

sudo rm /etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list
sudo rm /etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list.save

```
ONLY If those return no errors, let's now see where we stand:
ELSE STOP ! .. We do not want to compound a dependency situation if there does still exist a problem with any of the source list files.
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT]possible, ubuntu is now setting pretty
[/INDENT]

---

### Post by mikee.bowen on 2013-10-30
Well I think we're getting there. I did "sudo cp /etc/apt/sources.list /etc/apt/sources.list-bak",  "gksudo gedit /etc/apt/sources.list", "sudo rm /etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list" and "sudo rm /etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list.save" and Ubuntu didn't return any errors. So far so good. Then I entered "sudo apt-get update" and got:

> 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                                                                                                      
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                                                                                 
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                                                                        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]                                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                            
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]                                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                                                                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex                                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                                                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex                                   
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [423 kB]                                                   
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                              
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                 
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [92.2 kB]                                                           
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,006 B]                                                    
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [98.8 kB]                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                                                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,354 B]                                
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [722 kB]                                
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]                             
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [29.3 kB]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,804 B]                                  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [353 kB]                              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                    
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]    
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [225 kB]                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                           
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.2 kB]                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [87.7 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,640 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Fetched 2,182 kB in 5s (379 kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


That seemed ok, it was really a bit too much for me to totally understand, but I didn't see any error or fail messages, so I entered "sudo apt-get upgrade" and got:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 nemo : Depends: nemo-data (= 2.0.1-20131021010006-precise) but 2.0.2-20131023010018-precise is installed
E: Unmet dependencies. Try using -f.



Should I use "apt-get -f install" like it says? I've tried that before and it didn't go anywhere.

---

### Post by Bashing-om on 2013-10-30
mikee.bowen; shucks.

First let's get the sources list straightened up. I do not know where now the duplication "http://dl.google.com/linux/earth/deb/ " is coming from.
Let's try this: Software Sources -> Other Software;
uncheck "google-earth.list"
and run "update" once more, If the packagae manager is still unhappy, uncheck the next google entry and see then what results, still with the error then uncheck that last google source "get" .

We get the package manager stable, then we can think about removing "nemo-data" and install the version required.

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-10-30
Ammm, this is probably a dumb question, but where do I find "Software Sources -> Other Software;"? Is it a command for the terminal? I have the "Ubuntu Software Center", but it says I need to update ubuntu before I use it.

---

### Post by Bashing-om on 2013-10-30
mikee.bowen; There is no such thing here as a dumb question !

I have not looked at a 12.04 GUI in a while, so my memory is hazy, but I am sure you are correct in the location, That it is in "software Sources".

OK, We can back door this ,,, this is one instance where the GUI is easier and faster than using the terminal... here it is back to the terminal to temporarily inhibit those google source files... but it is going to be tedious and trying. Good process of learning though.
Fire up the text editor once more. In these instances backup files already exist so we can skip that step.
do:
```

sudo gedit /etc/apt/sources.list.d/google-earth.list

```
place a "#" character at the start of the source line similar to this example:
> 
#deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

save that file and open another instance of the terminal (key combo ctl+alt+t ), in this new terminal run the update command and see what results. if errors -> back to the text editor and repeat the editing for the file " google.list" -> update.
If still with an error, last one - in the text editor edit "google-talkplugin.list" with the comment character "#" at the start of the lines.

Got to have the package manager stable before we can do much of anything !

Clear as mud ?
[INDENT][INDENT]ask for clarification and thou shalt receive [/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-10-31
I added th "#" to google-earth.list and I think the update worked:



Here's what I got for "sudo apt-get update":

> 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                                                                                                      
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                           
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                           
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                                      
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]                                                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                                                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                                                       
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [92.2 kB]                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex                                                         
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [423 kB]                                                   
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                        
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                            
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]                                                                            
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [29.3 kB]                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                                                                                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                                                        
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,804 B]                                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                                                             
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [353 kB]                                                                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                                            
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                       
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]                         
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [87.7 kB]                         
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,640 B]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en      
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,006 B]                                                                          
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                                        
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [98.8 kB]                                                                            
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                                     
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,354 B]                                                                          
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [722 kB]                                                                           
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                                        
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                                     
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]                                                                    
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [225 kB]                                                                       
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.2 kB]                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                                                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources                                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages                                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en                                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en                                                                                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Fetched 2,182 kB in 40s (54.3 kB/s)
Reading package lists... Done


So that seemed good so I entered "sudo apt-get upgrade" and got the same unmet dependencies problem as before:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 nemo : Depends: nemo-data (= 2.0.1-20131021010006-precise) but 2.0.2-20131023010018-precise is installed
E: Unmet dependencies. Try using -f.


And also I got the following message (it's a screenshot because it wouldn't let me select the text) when I tried to open the update manager:

[IMG]http://www.rayboneexperience.com/images/chance/Screenshot%20from%202013-10-30%2021%3A03%3A50.png[/IMG]

Should I run the partial update it recommends?

---

### Post by Bashing-om on 2013-10-31
mikee.bowen; Making progress !
Yeah looking good !!

Mike, as a general rule, a "partial upgrade" is to be avoided, but in this case, it might just fix things up for us.
With only the few dependency issues we have, I think that doing the "partial upgrade" is an acceptable risk.

Go ahead and see what results !

[INDENT][INDENT]hope , hope !
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-10-31
We are indeed making progress! First the good news. I did the partial upgrade and after a restart my background image was back and I used the update manager to check for updates and it didn't find any. The software center also is working again. 

There is one weird error that still hasn't gone away, though. The bar across the top of program windows that has the close X and the minimize and maximize buttons and you also use it to move windows around...sorry for the wordy description, I don't know the name of it. Anyway, it's gone. I can still open and close or maximize and minimize windows by right clicking on the program tab at the bottom, but I can't move any windows.

Does this have something to do with the nemo issue?

---

### Post by Bashing-om on 2013-10-31
mikee.bowen; Indeed making progress.

What DE are you using ? Cinnamon or unity ?
Be prepared, I have seen advisements that unity and Cinnamon do not play nicely together - in later versions of 'buntu. Presently I do not know about 12.04,

And -> once more I have reached my thresh hold of thinkability. Will have to continue this in my Am ... I no longer hold myself accountable for my thought processes !!

Nemo issue:
```

apt-cache policy nemo
apt-cache policy nemo-data

```

[INDENT][INDENT]down for the count
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-10-31
I'm with you, I gotta head to bed too. Before going to sleep though, I entered "apt-cache policy nemo" and what I got was

> 
nemo:
  Installed: (none)
  Candidate: (none)
  Version table:
     2.0.1-20131021010006-precise 0
        100 /var/lib/dpkg/status



And then for "apt-cache policy nemo-data" I got :

> 
nemo-data:
  Installed: 2.0.2-20131023010018-precise
  Candidate: 2.0.2-20131023010018-precise
  Version table:
 *** 2.0.2-20131023010018-precise 0
        100 /var/lib/dpkg/status



It didn't fix the issue with the bar at the top of windows goes, though.

As far as cinammon or unity goes, I'm using gnome so I'm not sure that I'm using either of them. 

Thanks for all the help, we've almost got my system back to normail :-)

---

### Post by Bashing-om on 2013-10-31
mikee.bowen; Hey,

My last was just to get an idea of the status, no fix in look'n. So we know Cinnamon is broke,: do you want to fix it ? Or, is Gnome your preference for a Desktop Environment ?
As Cinnamon is broke (for now) .. how bout we go ahead and remove Cinnamon as it may not play nice with any other DE installed, and fix Gnome ?

Whatever you want to do.

---

### Post by mikee.bowen on 2013-10-31
Hi Bashing, I'm back :-)

If you think removing cinnammon will fix gnome, then let's do that. I've actually been using Ubuntu for a few years now, but I lost my old ubuntuforum account, and I've tried unity, cinnammon, and gnome and I definitely like gnome the best, so losing cinnammon is no sweat off my back. All I need is the code :-D

---

### Post by Bashing-om on 2013-10-31
mikee.bowen; Hey,

This I do know, multiple desk tops installed can and do cause conflicts. Reducing the cause of conflicts is a good thing; and, as stated Cinnamon does not play nice. So yeah let's remove Cinnamon.
```

sudo add-apt-repository --remove ppa:merlwiz79/cinnamon-ppa

```
If that runs clean (no errors) THEN remove the source lists.
```

sudo rm /etc/apt/sources.list.d/merlwiz79-cinnamon-ppa-precise.list
sudo rm /etc/apt/sources.list.d/merlwiz79-cinnamon-ppa-precise.list.save

```

Addressing the desktop:
Show me:
```

echo $DESKTOP_SESSION
apt-cache policy ubuntu-desktop

``` so I have some idea of what version of Gnome(shell) (??) we are working with.

[INDENT][INDENT]s l o w l y step by step
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-10-31
OK, no more cinnamon! I ran "sudo add-apt-repository --remove ppa:merlwiz79/cinnamon-ppa", "sudo rm /etc/apt/sources.list.d/merlwiz79-cinnamon-ppa-precise.list " and "sudo rm /etc/apt/sources.list.d/merlwiz79-cinnamon-ppa-precise.list.save" without any errors.

Then I ran "echo $DESKTOP_SESSION" and got:

> 
gnome-classic


And then "apt-cache policy ubuntu-desktop" got me:

> 
ubuntu-desktop:
  Installed: 1.267.1
  Candidate: 1.267.1
  Version table:
 *** 1.267.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1.267 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages



I know I'm using the old style, but I just like it :-D

---

### Post by Bashing-om on 2013-11-01
mikee.bowen; Hey;

Desk tops, to each his own, one of the many reasons ubuntu is great ! .. I personally like xfce - simplicity and configure-ability.

Let's now do clean up and see where we stand;
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade


sudo dpkg -C
df -h
df -i
dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```

Looking good we can continue on.

[INDENT][INDENT]ain't nothing left but a thing
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-11-01
OK, I think that everything went well. But this is going to be a long post, so here goes.

"sudo apt-get autoclean" got me:


> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del muffin-common 2.0.1-20131011003005-precise [1,290 kB]
Del cjs 2.0.0-20131011020603-precise [10.4 kB]
Del nemo-data 2.0.1-20131021010006-precise [34.0 kB]
Del google-talkplugin 4.7.0.0-1 [11.1 MB]
Del cinnamon-session 2.0.1-20131021043004-precise [133 kB]
Del cinnamon-common 2.0.3-20131021040307-precise [1,728 kB]
Del python-problem-report 2.0.1-0ubuntu17.5 [9,466 B]
Del apport 2.0.1-0ubuntu17.5 [147 kB]
Del libmuffin0 2.0.2-20131021003031-precise [335 kB]
Del cinnamon-screensaver 2.0.1-20131021013003-precise [100 kB]
Del procps 1:3.2.8-11ubuntu6.1 [226 kB]
Del libcinnamon-desktop0 2.0.1-20131011011505-precise [148 kB]
Del gnome-settings-daemon 3.4.2-0ubuntu0.6.3 [477 kB]
Del gir1.2-muffin-3.0 2.0.1-20131011003005-precise [20.9 kB]
Del libcinnamon-desktop0 2.0.1-20131021011504-precise [148 kB]
Del python-apport 2.0.1-0ubuntu17.5 [81.1 kB]
Del cinnamon-translations 2.0.1-20131021040407-precise [3,212 kB]
Del nemo 2.0.1-20131021010006-precise [938 kB]
Del cinnamon-screensaver 2.0.0-20131011013003-precise [101 kB]
Del gir1.2-muffin-3.0 2.0.2-20131021003031-precise [20.8 kB]
Del cinnamon 2.0.2-20131011040307-precise [768 kB]
Del cinnamon-desktop-data 2.0.1-20131021011504-precise [249 kB]
Del cinnamon-settings-daemon 2.0.1-20131011004504-precise [2,008 kB]
Del libmuffin0 2.0.1-20131011003005-precise [335 kB]
Del cinnamon-settings-daemon 2.0.3-20131021004509-precise [2,008 kB]
Del muffin-common 2.0.2-20131021003031-precise [1,291 kB]
Del libcjs0c 2.0.0-20131021020602-precise [231 kB]
Del cinnamon-desktop-data 2.0.1-20131011011505-precise [247 kB]
Del cinnamon-translations 2.0.1-20131011040406-precise [3,225 kB]
Del nemo-fileroller 2.0.0-20131011020004-precise [6,846 B]
Del nemo-fileroller 2.0.0-20131021020004-precise [6,856 B]
Del gir1.2-cinnamondesktop-3.0 2.0.1-20131011011505-precise [76.6 kB]
Del cinnamon-session 2.0.1-20131011043004-precise [134 kB]
Del cinnamon 2.0.3-20131021040307-precise [774 kB]
Del apport-gtk 2.0.1-0ubuntu17.5 [9,200 B]
Del nemo 2.0.2-20131023010018-precise [938 kB]
Del libnemo-extension1 2.0.1-20131021010006-precise [15.7 kB]
Del cinnamon-common 2.0.2-20131011040307-precise [1,735 kB]
Del nemo-data 2.0.2-20131023010018-precise [34.0 kB]
Del gir1.2-cinnamondesktop-3.0 2.0.1-20131021011504-precise [76.7 kB]
Del libcjs0c 2.0.0-20131011020603-precise [231 kB]
Del cjs 2.0.0-20131021020602-precise [10.4 kB]


"sudo apt-get autoremove" got me:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded


"sudo apt-get clean" got no errors.

"sudo apt-get update" got:

> 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                   
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                                                              
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                              
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                                   
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B] 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                           
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]                       
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                       
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                                
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]                                                         
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                                                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                         
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [92.1 kB]                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [423 kB]       
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]                     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [29.3 kB]  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                      
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,804 B]         
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [353 kB]      
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]    
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [87.9 kB]   
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,640 B]     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,006 B]                                                                          
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [98.8 kB]                                                                            
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,354 B]                                                                          
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [722 kB]                                                                           
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]                                                                    
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [225 kB]                                                                       
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.2 kB]                                                                    
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]                                                                       
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]                                                                 
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]                                                                 
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                                                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources                                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages                                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                                                                                          
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [317 kB]                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en                                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en                                                                                
Fetched 2,512 kB in 19s (130 kB/s)                                                                                                                        
Reading package lists... Done


"sudo apt-get upgrade" got me:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  python-lazr.restfulclient
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 54.8 kB of archives.
After this operation, 9,216 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main python-lazr.restfulclient all 0.12.0-1ubuntu1.1 [54.8 kB]
Fetched 54.8 kB in 0s (109 kB/s)               
(Reading database ... 733175 files and directories currently installed.)
Preparing to replace python-lazr.restfulclient 0.12.0-1ubuntu1 (using .../python-lazr.restfulclient_0.12.0-1ubuntu1.1_all.deb) ...
Unpacking replacement python-lazr.restfulclient ...
Setting up python-lazr.restfulclient (0.12.0-1ubuntu1.1) ...


"sudo dpkg -C" got me no errors.

"df -h" got me:

> 
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        53G   48G  2.3G  96% /
udev           1000M  4.0K 1000M   1% /dev
tmpfs           403M  804K  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  156K 1007M   1% /run/shm


"df -i" got me:

> 
Filesystem      Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1      3514368 1038082 2476286   30% /
udev            215799     478  215321    1% /dev
tmpfs           219456     393  219063    1% /run
none            219456       3  219453    1% /run/lock
none            219456       7  219449    1% /run/shm


"dpkg -l | grep linux-image-" got me:

> 
ii  linux-image-3.2.0-29-generic-pae                3.2.0-29.46                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-31-generic-pae                3.2.0-31.50                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-32-generic-pae                3.2.0-32.51                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic-pae                3.2.0-33.52                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-34-generic-pae                3.2.0-34.53                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-35-generic-pae                3.2.0-35.55                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-36-generic-pae                3.2.0-36.57                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-37-generic-pae                3.2.0-37.58                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-38-generic-pae                3.2.0-38.61                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-39-generic-pae                3.2.0-39.62                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-40-generic-pae                3.2.0-40.64                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-41-generic-pae                3.2.0-41.66                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-43-generic-pae                3.2.0-43.68                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-44-generic-pae                3.2.0-44.69                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-45-generic-pae                3.2.0-45.70                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-48-generic-pae                3.2.0-48.74                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-49-generic-pae                3.2.0-49.75                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-51-generic-pae                3.2.0-51.77                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-52-generic-pae                3.2.0-52.78                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-53-generic-pae                3.2.0-53.81                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-54-generic-pae                3.2.0-54.82                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-55-generic-pae                3.2.0-55.85                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                         3.2.0.55.65                             Generic Linux kernel image


And finally "dpkg -l | grep linux-headers-" got me;

> 
ii  linux-headers-3.2.0-31                          3.2.0-31.50                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-31-generic-pae              3.2.0-31.50                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-32                          3.2.0-32.51                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-32-generic-pae              3.2.0-32.51                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-33                          3.2.0-33.52                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-33-generic-pae              3.2.0-33.52                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-34                          3.2.0-34.53                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-34-generic-pae              3.2.0-34.53                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-35                          3.2.0-35.55                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic-pae              3.2.0-35.55                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-36                          3.2.0-36.57                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-36-generic-pae              3.2.0-36.57                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-37                          3.2.0-37.58                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-37-generic-pae              3.2.0-37.58                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-38                          3.2.0-38.61                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-38-generic-pae              3.2.0-38.61                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-39                          3.2.0-39.62                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-39-generic-pae              3.2.0-39.62                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-40                          3.2.0-40.64                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic-pae              3.2.0-40.64                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-41                          3.2.0-41.66                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-generic-pae              3.2.0-41.66                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-43                          3.2.0-43.68                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-43-generic-pae              3.2.0-43.68                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-44                          3.2.0-44.69                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-generic-pae              3.2.0-44.69                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-45                          3.2.0-45.70                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-45-generic-pae              3.2.0-45.70                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-48                          3.2.0-48.74                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic-pae              3.2.0-48.74                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-49                          3.2.0-49.75                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic-pae              3.2.0-49.75                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51                          3.2.0-51.77                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic-pae              3.2.0-51.77                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52                          3.2.0-52.78                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic-pae              3.2.0-52.78                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-53                          3.2.0-53.81                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic-pae              3.2.0-53.81                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-54                          3.2.0-54.82                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic-pae              3.2.0-54.82                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-55                          3.2.0-55.85                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-55-generic-pae              3.2.0-55.85                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic-pae                       3.2.0.55.65                             Generic Linux kernel headers


OK, so that's what I've got so far.

---

### Post by Bashing-om on 2013-11-01
mikee.bowen; Hey, look'n better alla the time !

This, not good:
> 
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 53G 48G 2.3G 96% /
 96% usage means no overhead and may have been the source of lots of problems.
Hoping there is enough overhead for "apt-get" to work on removal of the kernels, else, other means will be employed. 
Fix:
```

uname -a ## note this kernel version, make SURE it is not deleted !
sudo apt-get --purge remove linux-image-3.2.0-{29,31,32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53}-generic-pae
sudo apt-get --purge remove linux-headers-3.2.0-{31,32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53}-generic-pae
sudo apt-get --purge remove linux-headers-3.2.0-{31,32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53}

```
Note that in the "image" list is version 29. version 29 is NOT in the headers list .. and it should have been on your system, is this a transcription error ?? Or perhaps another source of problems ?. The above code is per what your output shows.

With the removal of these old unneeded kernels we should have some overhead now to operate with.

And moving on (??),

[INDENT][INDENT]to that final thing
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-11-01
OK, so I did "uname -a ## note this kernel version, make SURE it is not deleted !" but I couldn't copy the results for you, because "sudo apt-get --purge remove linux-image-3.2.0-{29,31,32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53}-generic-pae" gave me a response so long I couldn't copy the whole thing, but here's what I was able to copy:

> 
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-49-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-49-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-48-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-48-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-44-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-44-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-43-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-43-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-41-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-41-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-40-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-40-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-39-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-39-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-16-generic
Found initrd image: /boot/initrd.img-2.6.38-16-generic
Found linux image: /boot/vmlinuz-2.6.38-15-generic
Found initrd image: /boot/initrd.img-2.6.38-15-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-38-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
Removing linux-image-3.2.0-39-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-39-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-49-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-49-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-48-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-48-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-44-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-44-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-43-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-43-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-41-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-41-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-40-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-40-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-16-generic
Found initrd image: /boot/initrd.img-2.6.38-16-generic
Found linux image: /boot/vmlinuz-2.6.38-15-generic
Found initrd image: /boot/initrd.img-2.6.38-15-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-39-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-39-generic-pae /boot/vmlinuz-3.2.0-39-generic-pae
Removing linux-image-3.2.0-40-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-40-generic-pae /boot/vmlinuz-3.2.0-40-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-40-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-40-generic-pae /boot/vmlinuz-3.2.0-40-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-49-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-49-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-48-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-48-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-44-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-44-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-43-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-43-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-41-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-41-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-16-generic
Found initrd image: /boot/initrd.img-2.6.38-16-generic
Found linux image: /boot/vmlinuz-2.6.38-15-generic
Found initrd image: /boot/initrd.img-2.6.38-15-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-40-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-40-generic-pae /boot/vmlinuz-3.2.0-40-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-40-generic-pae /boot/vmlinuz-3.2.0-40-generic-pae
Removing linux-image-3.2.0-41-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-41-generic-pae /boot/vmlinuz-3.2.0-41-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-41-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-41-generic-pae /boot/vmlinuz-3.2.0-41-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-49-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-49-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-48-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-48-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-44-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-44-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-43-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-43-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-16-generic
Found initrd image: /boot/initrd.img-2.6.38-16-generic
Found linux image: /boot/vmlinuz-2.6.38-15-generic
Found initrd image: /boot/initrd.img-2.6.38-15-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-41-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-41-generic-pae /boot/vmlinuz-3.2.0-41-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-41-generic-pae /boot/vmlinuz-3.2.0-41-generic-pae
Removing linux-image-3.2.0-43-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-43-generic-pae /boot/vmlinuz-3.2.0-43-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-43-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-43-generic-pae /boot/vmlinuz-3.2.0-43-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-49-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-49-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-48-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-48-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-44-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-44-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-16-generic
Found initrd image: /boot/initrd.img-2.6.38-16-generic
Found linux image: /boot/vmlinuz-2.6.38-15-generic
Found initrd image: /boot/initrd.img-2.6.38-15-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-43-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-43-generic-pae /boot/vmlinuz-3.2.0-43-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-43-generic-pae /boot/vmlinuz-3.2.0-43-generic-pae
Removing linux-image-3.2.0-44-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-44-generic-pae /boot/vmlinuz-3.2.0-44-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-44-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-44-generic-pae /boot/vmlinuz-3.2.0-44-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-49-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-49-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-48-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-48-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-16-generic
Found initrd image: /boot/initrd.img-2.6.38-16-generic
Found linux image: /boot/vmlinuz-2.6.38-15-generic
Found initrd image: /boot/initrd.img-2.6.38-15-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-44-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-44-generic-pae /boot/vmlinuz-3.2.0-44-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-44-generic-pae /boot/vmlinuz-3.2.0-44-generic-pae
Removing linux-image-3.2.0-45-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-45-generic-pae /boot/vmlinuz-3.2.0-45-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-45-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-45-generic-pae /boot/vmlinuz-3.2.0-45-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-49-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-49-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-48-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-48-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-16-generic
Found initrd image: /boot/initrd.img-2.6.38-16-generic
Found linux image: /boot/vmlinuz-2.6.38-15-generic
Found initrd image: /boot/initrd.img-2.6.38-15-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-45-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-45-generic-pae /boot/vmlinuz-3.2.0-45-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-45-generic-pae /boot/vmlinuz-3.2.0-45-generic-pae
Removing linux-image-3.2.0-48-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-48-generic-pae /boot/vmlinuz-3.2.0-48-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-48-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-48-generic-pae /boot/vmlinuz-3.2.0-48-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-49-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-49-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-16-generic
Found initrd image: /boot/initrd.img-2.6.38-16-generic
Found linux image: /boot/vmlinuz-2.6.38-15-generic
Found initrd image: /boot/initrd.img-2.6.38-15-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-48-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-48-generic-pae /boot/vmlinuz-3.2.0-48-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-48-generic-pae /boot/vmlinuz-3.2.0-48-generic-pae
Removing linux-image-3.2.0-49-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-49-generic-pae /boot/vmlinuz-3.2.0-49-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-49-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-49-generic-pae /boot/vmlinuz-3.2.0-49-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-16-generic
Found initrd image: /boot/initrd.img-2.6.38-16-generic
Found linux image: /boot/vmlinuz-2.6.38-15-generic
Found initrd image: /boot/initrd.img-2.6.38-15-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-49-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-49-generic-pae /boot/vmlinuz-3.2.0-49-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-49-generic-pae /boot/vmlinuz-3.2.0-49-generic-pae
Removing linux-image-3.2.0-51-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-51-generic-pae /boot/vmlinuz-3.2.0-51-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-51-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-51-generic-pae /boot/vmlinuz-3.2.0-51-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-16-generic
Found initrd image: /boot/initrd.img-2.6.38-16-generic
Found linux image: /boot/vmlinuz-2.6.38-15-generic
Found initrd image: /boot/initrd.img-2.6.38-15-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-51-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-51-generic-pae /boot/vmlinuz-3.2.0-51-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-51-generic-pae /boot/vmlinuz-3.2.0-51-generic-pae
Removing linux-image-3.2.0-52-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-52-generic-pae /boot/vmlinuz-3.2.0-52-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-52-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-52-generic-pae /boot/vmlinuz-3.2.0-52-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-16-generic
Found initrd image: /boot/initrd.img-2.6.38-16-generic
Found linux image: /boot/vmlinuz-2.6.38-15-generic
Found initrd image: /boot/initrd.img-2.6.38-15-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-52-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-52-generic-pae /boot/vmlinuz-3.2.0-52-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-52-generic-pae /boot/vmlinuz-3.2.0-52-generic-pae
Removing linux-image-3.2.0-53-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-53-generic-pae /boot/vmlinuz-3.2.0-53-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-53-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-53-generic-pae /boot/vmlinuz-3.2.0-53-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae
Found linux image: /boot/vmlinuz-2.6.38-16-generic
Found initrd image: /boot/initrd.img-2.6.38-16-generic
Found linux image: /boot/vmlinuz-2.6.38-15-generic
Found initrd image: /boot/initrd.img-2.6.38-15-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found linux image: /boot/vmlinuz-2.6.38-13-generic
Found initrd image: /boot/initrd.img-2.6.38-13-generic
Found linux image: /boot/vmlinuz-2.6.38-12-generic
Found initrd image: /boot/initrd.img-2.6.38-12-generic
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Purging configuration files for linux-image-3.2.0-53-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-53-generic-pae /boot/vmlinuz-3.2.0-53-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-53-generic-pae /boot/vmlinuz-3.2.0-53-generic-pae



"sudo apt-get --purge remove linux-headers-3.2.0-{31,32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53}-generic-pae" had a much more manageable sized response:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.2.0-31-generic-pae* linux-headers-3.2.0-32-generic-pae* linux-headers-3.2.0-33-generic-pae* linux-headers-3.2.0-34-generic-pae*
  linux-headers-3.2.0-35-generic-pae* linux-headers-3.2.0-36-generic-pae* linux-headers-3.2.0-37-generic-pae* linux-headers-3.2.0-38-generic-pae*
  linux-headers-3.2.0-39-generic-pae* linux-headers-3.2.0-40-generic-pae* linux-headers-3.2.0-41-generic-pae* linux-headers-3.2.0-43-generic-pae*
  linux-headers-3.2.0-44-generic-pae* linux-headers-3.2.0-45-generic-pae* linux-headers-3.2.0-48-generic-pae* linux-headers-3.2.0-49-generic-pae*
  linux-headers-3.2.0-51-generic-pae* linux-headers-3.2.0-52-generic-pae* linux-headers-3.2.0-53-generic-pae*
0 upgraded, 0 newly installed, 19 to remove and 0 not upgraded.
After this operation, 215 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 645603 files and directories currently installed.)
Removing linux-headers-3.2.0-31-generic-pae ...
Removing linux-headers-3.2.0-32-generic-pae ...
Removing linux-headers-3.2.0-33-generic-pae ...
Removing linux-headers-3.2.0-34-generic-pae ...
Removing linux-headers-3.2.0-35-generic-pae ...
Removing linux-headers-3.2.0-36-generic-pae ...
Removing linux-headers-3.2.0-37-generic-pae ...
Removing linux-headers-3.2.0-38-generic-pae ...
Removing linux-headers-3.2.0-39-generic-pae ...
Removing linux-headers-3.2.0-40-generic-pae ...
Removing linux-headers-3.2.0-41-generic-pae ...
Removing linux-headers-3.2.0-43-generic-pae ...
Removing linux-headers-3.2.0-44-generic-pae ...
Removing linux-headers-3.2.0-45-generic-pae ...
Removing linux-headers-3.2.0-48-generic-pae ...
Removing linux-headers-3.2.0-49-generic-pae ...
Removing linux-headers-3.2.0-51-generic-pae ...
Removing linux-headers-3.2.0-52-generic-pae ...
Removing linux-headers-3.2.0-53-generic-pae ...


And the I did "sudo apt-get --purge remove linux-headers-3.2.0-{31,32,33,34,35,36,37,38,39,40,41,43,44,45,48,49,51,52,53}" and got:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.2.0-31* linux-headers-3.2.0-32* linux-headers-3.2.0-33* linux-headers-3.2.0-34* linux-headers-3.2.0-35* linux-headers-3.2.0-36*
  linux-headers-3.2.0-37* linux-headers-3.2.0-38* linux-headers-3.2.0-39* linux-headers-3.2.0-40* linux-headers-3.2.0-41* linux-headers-3.2.0-43*
  linux-headers-3.2.0-44* linux-headers-3.2.0-45* linux-headers-3.2.0-48* linux-headers-3.2.0-49* linux-headers-3.2.0-51* linux-headers-3.2.0-52*
  linux-headers-3.2.0-53*
0 upgraded, 0 newly installed, 19 to remove and 0 not upgraded.
After this operation, 1,069 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 485235 files and directories currently installed.)
Removing linux-headers-3.2.0-31 ...
Removing linux-headers-3.2.0-32 ...
Removing linux-headers-3.2.0-33 ...
Removing linux-headers-3.2.0-34 ...
Removing linux-headers-3.2.0-35 ...
Removing linux-headers-3.2.0-36 ...
Removing linux-headers-3.2.0-37 ...
Removing linux-headers-3.2.0-38 ...
Removing linux-headers-3.2.0-39 ...
Removing linux-headers-3.2.0-40 ...
Removing linux-headers-3.2.0-41 ...
Removing linux-headers-3.2.0-43 ...
Removing linux-headers-3.2.0-44 ...
Removing linux-headers-3.2.0-45 ...
Removing linux-headers-3.2.0-48 ...
Removing linux-headers-3.2.0-49 ...
Removing linux-headers-3.2.0-51 ...
Removing linux-headers-3.2.0-52 ...
Removing linux-headers-3.2.0-53 ...


I have wondered what was taking up a bunch of my memory!

---

### Post by Bashing-om on 2013-11-01
mikee.bowen; OK !

One more look.
```

df -h
dpkg -l | grep linux-image
dpkg -l | grep linux-headers

```and see now if we have to "cut" the "rc" status files.

[INDENT][INDENT]we be look'n good
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-11-01
OK, it's almost there I can feel It! 

"df -h" gave me:

> 
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        53G   44G  6.8G  87% /
udev           1000M  4.0K 1000M   1% /dev
tmpfs           403M  832K  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  160K 1007M   1% /run/shm


Then "dpkg -l | grep linux-image" gave me:

> 
ii  linux-image-3.2.0-54-generic-pae                3.2.0-54.82                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-55-generic-pae                3.2.0-55.85                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                         3.2.0.55.65                             Generic Linux kernel image


And last but not least "dpkg -l | grep linux-headers" got me:

> 
ii  linux-headers-3.2.0-54                          3.2.0-54.82                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic-pae              3.2.0-54.82                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-55                          3.2.0-55.85                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-55-generic-pae              3.2.0-55.85                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-generic-pae                       3.2.0.55.65                             Generic Linux kernel headers


---

### Post by Bashing-om on 2013-11-01
mikee.bowen; Welp,
This:
> 
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 53G 44G 6.8G 87% /

Says still not a comfortable amount of space, The following command is useful for finding out which directories are using all your space...
```

du -h --max-depth=1 | sort -hr

```

[INDENT][INDENT]we still be look'n
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-11-01
Well this is weird "du -h --max-depth=1 | sort -hr" gave me a permission denied for some reason. I didn't use sudo, should I try it with sudo?


> 
du: cannot read directory `./.gconf': Permission denied
24G    .
19G    ./Pictures
1.3G    ./.thunderbird
1.1G    ./.local
615M    ./Documents
438M    ./.cache
236M    ./.adobe
214M    ./.mozilla
123M    ./googleearth-tmp
102M    ./.icons
93M    ./googleearth-deb
92M    ./Downloads
44M    ./.thumbnails
41M    ./.wine
20M    ./Videos
16M    ./.googleearth
13M    ./.kompozer.net
13M    ./.config
8.3M    ./.themes
4.9M    ./.moovida
3.9M    ./.compiz-1
3.0M    ./.cinnamon
2.5M    ./.python-eggs
1.6M    ./.launchpadlib
1.3M    ./.Skype
1.1M    ./.openoffice.org
1.1M    ./.Fontmatrix
1020K    ./.gstreamer-0.10
804K    ./.fonts
612K    ./.icedtea
460K    ./.gimp-2.6
248K    ./.kde
220K    ./.fontconfig
188K    ./.pulse
184K    ./.gnome2
84K    ./.shotwell
84K    ./.purple
76K    ./.macromedia
44K    ./.gconfd
36K    ./.pki
32K    ./.winff
24K    ./.xine
20K    ./.gnupg
20K    ./.dbus
16K    ./.gegl-0.0
12K    ./.netx
12K    ./.mission-control
12K    ./.lastpass
8.0K    ./.screenlets
8.0K    ./.outwit
8.0K    ./.mplayer
4.0K    ./Ubuntu One
4.0K    ./.ssh
4.0K    ./Music
4.0K    ./.icedteaplugin
4.0K    ./.gnome2_private
4.0K    ./.gconf
4.0K    ./Desktop
0    ./.gvfs


---

### Post by Bashing-om on 2013-11-02
mikee.bowen; Boy,

You are tight for space ! If you can not trim out some fat, time to think about moving into a larger partition. Maybe for now move some stuff out of Pictures. .. reason -> at 85% capacity, start trimming as at 90% fragmentation of the file system occurs !

And nope .. there be a problem with "du" not able to access .gconf; you should be able to access all in your home directory. Fixing this may even fix the buttons on the DE !
Let's look:
```

ls -la ~/.gconf

```
and let's see what we might be able to trim out of the /var directory:
```

sudo du -h --max-depth=1 /var

```
[INDENT][INDENT]we still be look'n
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-11-02
I'm backing up the photos now, but it'll take a minute then I'll delete them.

Here's what I got for "ls -la ~/.gconf"


> ls: cannot open directory /home/mikee/.gconf: Permission denied

Thanks doesn't look good :-( 

Here's what "sudo du -h --max-depth=1 /var" got me:

> 
5.2M    /var/backups
4.0K    /var/local
4.0K    /var/mail
149M    /var/cache
4.0K    /var/opt
68K    /var/spool
720K    /var/crash
8.0K    /var/tmp
4.0K    /var/games
203M    /var/lib
12M    /var/log
370M    /var


---

### Post by mikee.bowen on 2013-11-02
OK, I deleted 14GB worth of pictures (I have back ups so no biggie) and I ran "du -h --max-depth=1 | sort -hr" again and got:

> 
du: cannot read directory `./.gconf': Permission denied
9.2G    .
5.8G    ./Pictures
1.3G    ./.thunderbird
615M    ./Documents
435M    ./.cache
236M    ./.adobe
214M    ./.mozilla
123M    ./googleearth-tmp
102M    ./.icons
93M    ./googleearth-deb
92M    ./Downloads
72M    ./.local
45M    ./.thumbnails
41M    ./.wine
20M    ./Videos
16M    ./.googleearth
13M    ./.kompozer.net
13M    ./.config
8.3M    ./.themes
4.9M    ./.moovida
3.9M    ./.compiz-1
3.0M    ./.cinnamon
2.5M    ./.python-eggs
1.6M    ./.launchpadlib
1.3M    ./.Skype
1.1M    ./.openoffice.org
1.1M    ./.Fontmatrix
1020K    ./.gstreamer-0.10
804K    ./.fonts
612K    ./.icedtea
460K    ./.gimp-2.6
248K    ./.kde
220K    ./.fontconfig
188K    ./.pulse
184K    ./.gnome2
84K    ./.shotwell
84K    ./.purple
76K    ./.macromedia
44K    ./.gconfd
36K    ./.pki
32K    ./.winff
24K    ./.xine
20K    ./.gnupg
20K    ./.dbus
16K    ./.gegl-0.0
12K    ./.netx
12K    ./.mission-control
12K    ./.lastpass
8.0K    ./.screenlets
8.0K    ./.outwit
8.0K    ./.mplayer
4.0K    ./Ubuntu One
4.0K    ./.ssh
4.0K    ./Music
4.0K    ./.icedteaplugin
4.0K    ./.gnome2_private
4.0K    ./.gconf
4.0K    ./Desktop
0    ./.gvfs


Thanks for all your help!

---

### Post by mikee.bowen on 2013-11-02
Also "df -h" got:

> 
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        53G   30G   21G  59% /
udev           1000M  4.0K 1000M   1% /dev
tmpfs           403M  832K  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  160K 1007M   1% /run/shm


---

### Post by Bashing-om on 2013-11-02
mikee.bowen; Wierd !

Ok what about:
```

sudo ls -la ~/.gconf

```
That makes me question what else is messed up.
Show:
```

ls -la

```

In /var, not a thing we can do for trimming, looks good enough to me ! That leaves only your home directory to trim to get that head space. Remove all that is no longer of value of your personal files.

And once more I am at the end of my thinkability for this session.

[INDENT][INDENT]what to do what to do[/INDENT][/INDENT]
I will pick this back up in my AM.
-------------------
In my AM now;

I failed to "Submit Reply" .. see thinkability impaired !

Nothwithstanding the permission issues, we are looking great... almost there !

[INDENT]once more, we be look'n
[/INDENT]

---

### Post by mikee.bowen on 2013-11-02
Thanks for all the help Bashing! How did my system get so screwed up? Is it so screwed I should just start over and reinstall?

Either way, I'm deleting a bunch of stuff from home and I ran "sudo ls -la ~/.gconf" and got:

> 
total 88
drwx------  2 root  root   4096 Oct  6  2012 .
drwxr-xr-x 60 mikee mikee 81920 Nov  2 09:13 ..


and then "ls -la" got:

> 
total 31096
drwxr-xr-x 60 mikee mikee    81920 Nov  2 09:13 .
drwxr-xr-x  3 root  root      4096 Apr 19  2012 ..
drwx------  3 mikee mikee     4096 Nov 28  2010 .adobe
-rw-------  1 mikee mikee     2530 Nov  1 22:27 .bash_history
lrwxrwxrwx  1 mikee mikee       30 May  1  2011 .byobu -> /home/mikee/.local/share/byobu
drwx------ 26 mikee mikee     4096 Oct 29 19:23 .cache
drwxrwxr-x  5 mikee mikee     4096 Oct 29 19:23 .cinnamon
drwxrwxr-x  3 mikee mikee     4096 Oct  7  2012 .compiz-1
drwxr-xr-x 46 mikee mikee     4096 Oct 29 19:23 .config
drwx------  3 mikee mikee     4096 Nov 28  2010 .dbus
drwxr-xr-x  2 mikee mikee     4096 Oct 31 00:08 Desktop
-rw-r--r--  1 mikee mikee       85 Nov  2 09:13 .dmrc
drwxr-xr-x 39 mikee mikee     4096 Aug 17 14:16 Documents
drwxr-xr-x  3 mikee mikee     4096 May  5 13:31 Downloads
-rw-------  1 mikee mikee       16 Nov 28  2010 .esd_auth
-rw-r--r--  1 mikee mikee   537568 Jun 12  2012 Firefox_wallpaper.png
drwxr-xr-x  2 mikee mikee     4096 Aug 10 19:04 .fontconfig
drwxr-xr-x  4 mikee mikee     4096 Oct 25  2011 .Fontmatrix
drwxr-xr-x  2 mikee mikee     4096 Oct 25  2011 .fonts
-rw-r--r--  1 mikee mikee      139 Dec 29  2010 .fonts.conf
drwx------  2 root  root      4096 Oct  6  2012 .gconf
drwx------  2 mikee mikee     4096 Oct  7  2012 .gconfd
drwx------  4 mikee mikee     4096 Dec 29  2010 .gegl-0.0
drwxr-xr-x 22 mikee mikee     4096 Oct 20 17:38 .gimp-2.6
-rw-r-----  1 mikee mikee        0 Nov  1 22:08 .gksu.lock
drwx------ 10 mikee mikee     4096 Oct 19 09:00 .gnome2
drwx------  2 mikee mikee     4096 Nov 28  2010 .gnome2_private
drwx------  2 mikee mikee     4096 Nov 17  2012 .gnupg
drwx------  5 mikee mikee     4096 Aug 28 12:46 .googleearth
drwx------  4 mikee mikee     4096 Aug 28  2010 googleearth-deb
-rw-rw-r--  1 mikee mikee 30741694 Oct 30  2012 google-earth-stable_current_i386.deb
drwx------  5 mikee mikee     4096 Jul 30  2010 googleearth-tmp
-rw-------  1 mikee mikee        0 Oct 12 05:25 .goutputstream-029R4W
-rw-------  1 mikee mikee        0 May 28 18:53 .goutputstream-0AN2XW
-rw-------  1 mikee mikee        0 Dec 12  2012 .goutputstream-0KJAPW
-rw-------  1 mikee mikee        0 Oct 10  2012 .goutputstream-0MBWLW
-rw-------  1 mikee mikee        0 Jan 10  2013 .goutputstream-0N0IQW
-rw-------  1 mikee mikee        0 Mar  1  2013 .goutputstream-0O9KTW
-rw-------  1 mikee mikee        0 Sep 22 01:00 .goutputstream-0QTJ3W
-rw-------  1 mikee mikee        0 Jul 13 12:54 .goutputstream-0QZB0W
-rw-------  1 mikee mikee        0 May 31 08:07 .goutputstream-0SXXXW
-rw-------  1 mikee mikee        0 Oct 10 19:25 .goutputstream-15CV4W
-rw-------  1 mikee mikee        0 Apr 24  2013 .goutputstream-1DA4VW
-rw-------  1 mikee mikee        0 Mar 28  2013 .goutputstream-1JNQUW
-rw-------  1 mikee mikee        0 Oct  9  2012 .goutputstream-1P3SLW
-rw-------  1 mikee mikee        0 Aug 18 01:17 .goutputstream-1T9E2W
-rw-------  1 mikee mikee        0 Oct 14 22:47 .goutputstream-21J24W
-rw-------  1 mikee mikee        0 Aug  7 00:10 .goutputstream-22XI1W
-rw-------  1 mikee mikee        0 May 26 00:45 .goutputstream-242OXW
-rw-------  1 mikee mikee        0 Apr 21  2013 .goutputstream-27PRVW
-rw-------  1 mikee mikee        0 Oct 22 22:15 .goutputstream-29GK5W
-rw-------  1 mikee mikee        0 Mar 27  2013 .goutputstream-2JHMUW
-rw-------  1 mikee mikee        0 Oct 20  2012 .goutputstream-2MAXMW
-rw-------  1 mikee mikee        0 Feb 20  2013 .goutputstream-2UPUSW
-rw-------  1 mikee mikee        0 Jan  8  2013 .goutputstream-3425PW
-rw-------  1 mikee mikee        0 Aug 18 16:14 .goutputstream-3I541W
-rw-------  1 mikee mikee        0 Feb 13  2013 .goutputstream-3JL1RW
-rw-------  1 mikee mikee        0 Nov 21  2012 .goutputstream-3VT8NW
-rw-------  1 mikee mikee        0 Apr 19  2013 .goutputstream-3X93VW
-rw-------  1 mikee mikee        0 Oct 13  2012 .goutputstream-3XRXLW
-rw-------  1 mikee mikee        0 Jun 19 23:39 .goutputstream-3Y04YW
-rw-------  1 mikee mikee        0 Mar 14  2013 .goutputstream-400FUW
-rw-------  1 mikee mikee        0 May 27 23:52 .goutputstream-4TQRXW
-rw-------  1 mikee mikee        0 Aug  5 00:04 .goutputstream-4UYA1W
-rw-------  1 mikee mikee        0 Oct 28 18:19 .goutputstream-54M54W
-rw-------  1 mikee mikee        0 Oct 16  2012 .goutputstream-54O9LW
-rw-------  1 mikee mikee        0 Apr 27  2013 .goutputstream-55CUVW
-rw-------  1 mikee mikee        0 Aug 10 23:10 .goutputstream-58PK1W
-rw-------  1 mikee mikee        0 Dec 17  2012 .goutputstream-5BL2PW
-rw-------  1 mikee mikee        0 Feb  6  2013 .goutputstream-5K1KSW
-rw-------  1 mikee mikee        0 Nov 19  2012 .goutputstream-5X9UNW
-rw-------  1 mikee mikee        0 Nov 11  2012 .goutputstream-5Z8YNW
-rw-------  1 mikee mikee        0 Feb 25  2013 .goutputstream-6285SW
-rw-------  1 mikee mikee        0 Mar  6  2013 .goutputstream-695PTW
-rw-------  1 mikee mikee        0 Nov  3  2012 .goutputstream-6DODNW
-rw-------  1 mikee mikee        0 Dec 31  2012 .goutputstream-6GO8PW
-rw-------  1 mikee mikee        0 Aug 17 15:00 .goutputstream-6N6I1W
-rw-------  1 mikee mikee        0 Mar  1  2013 .goutputstream-6ONHTW
-rw-------  1 mikee mikee        0 Apr 22  2013 .goutputstream-6RL9VW
-rw-------  1 mikee mikee        0 Jul  9 01:18 .goutputstream-73PPZW
-rw-------  1 mikee mikee        0 Apr 24  2013 .goutputstream-75X5VW
-rw-------  1 mikee mikee        0 Sep 22 09:09 .goutputstream-7AHT3W
-rw-------  1 mikee mikee        0 Mar 15  2013 .goutputstream-7AQZTW
-rw-------  1 mikee mikee        0 Nov 24  2012 .goutputstream-7IJGOW
-rw-------  1 mikee mikee        0 Dec 11  2012 .goutputstream-7KDYOW
-rw-------  1 mikee mikee        0 Mar 25  2013 .goutputstream-7KLRUW
-rw-------  1 mikee mikee        0 Jul 21 18:39 .goutputstream-7L6N0W
-rw-------  1 mikee mikee        0 Feb 24  2013 .goutputstream-7XLVSW
-rw-------  1 mikee mikee        0 Nov 10  2012 .goutputstream-7Y6HNW
-rw-------  1 mikee mikee        0 Mar  5  2013 .goutputstream-7Y7RTW
-rw-------  1 mikee mikee        0 May 24 16:16 .goutputstream-8A4KXW
-rw-------  1 mikee mikee        0 Oct 11 04:03 .goutputstream-8KEQ4W
-rw-------  1 mikee mikee        0 Jun 11 23:41 .goutputstream-8OBTYW
-rw-------  1 mikee mikee        0 May 19 00:22 .goutputstream-8WEIXW
-rw-------  1 mikee mikee        0 Apr 26  2013 .goutputstream-918XVW
-rw-------  1 mikee mikee        0 Dec  9  2012 .goutputstream-91E4OW
-rw-------  1 mikee mikee        0 Aug  8 18:27 .goutputstream-9JIE1W
-rw-------  1 mikee mikee        0 Mar 23  2013 .goutputstream-9KM7TW
-rw-------  1 mikee mikee        0 Oct  2 07:59 .goutputstream-9XE53W
-rw-------  1 mikee mikee        0 Nov  3  2012 .goutputstream-9Y28MW
-rw-------  1 mikee mikee        0 Feb 14  2013 .goutputstream-A1ZASW
-rw-------  1 mikee mikee        0 Jan  6  2013 .goutputstream-A4LMQW
-rw-------  1 mikee mikee        0 Nov  8  2012 .goutputstream-A812MW
-rw-------  1 mikee mikee        0 Jan 26  2013 .goutputstream-ACOLRW
-rw-------  1 mikee mikee        0 Aug 20 00:26 .goutputstream-AFH51W
-rw-------  1 mikee mikee        0 Oct  7  2012 .goutputstream-AGMTLW
-rw-------  1 mikee mikee        0 Mar 14  2013 .goutputstream-AK8VTW
-rw-------  1 mikee mikee        0 Oct  5 09:22 .goutputstream-ALL14W
-rw-------  1 mikee mikee        0 Jun 22 00:40 .goutputstream-ANX4YW
-rw-------  1 mikee mikee        0 Aug 24 13:51 .goutputstream-AOG31W
-rw-------  1 mikee mikee        0 Feb 25  2013 .goutputstream-AXC3SW
-rw-------  1 mikee mikee        0 Jun 23 23:12 .goutputstream-AZ8XYW
-rw-------  1 mikee mikee        0 May  2  2013 .goutputstream-AZCIWW
-rw-------  1 mikee mikee        0 Oct 31  2012 .goutputstream-B5FKNW
-rw-------  1 mikee mikee        0 May  5 18:05 .goutputstream-BC6FWW
-rw-------  1 mikee mikee        0 Sep  2 18:41 .goutputstream-BDDS2W
-rw-------  1 mikee mikee        0 May 24 12:47 .goutputstream-BHVKXW
-rw-------  1 mikee mikee        0 May  3  2013 .goutputstream-BOBQWW
-rw-------  1 mikee mikee        0 Sep 25 20:01 .goutputstream-BRT83W
-rw-------  1 mikee mikee        0 May  7 06:43 .goutputstream-C69TWW
-rw-------  1 mikee mikee        0 Aug 15 23:57 .goutputstream-CAOX1W
-rw-------  1 mikee mikee        0 May  5 18:31 .goutputstream-CG4IWW
-rw-------  1 mikee mikee        0 Jan 17  2013 .goutputstream-CKWXQW
-rw-------  1 mikee mikee        0 Mar 13  2013 .goutputstream-CO14TW
-rw-------  1 mikee mikee        0 Sep  7 11:31 .goutputstream-CSAU2W
-rw-------  1 mikee mikee        0 Aug 22 07:59 .goutputstream-D21F2W
-rw-------  1 mikee mikee        0 Aug 29 15:08 .goutputstream-DJ761W
-rw-------  1 mikee mikee        0 Jun 12 23:46 .goutputstream-DM4FYW
-rw-------  1 mikee mikee        0 Apr 20  2013 .goutputstream-DX8XVW
-rw-------  1 mikee mikee        0 Dec 17  2012 .goutputstream-DXXGPW
-rw-------  1 mikee mikee        0 Feb  3  2013 .goutputstream-E3WJRW
-rw-------  1 mikee mikee        0 Aug 12 21:52 .goutputstream-E4PQ1W
-rw-------  1 mikee mikee        0 Apr 24  2013 .goutputstream-EBKVVW
-rw-------  1 mikee mikee        0 Apr  8  2013 .goutputstream-EEKFVW
-rw-------  1 mikee mikee        0 Aug 23 00:01 .goutputstream-ELMG2W
-rw-------  1 mikee mikee        0 Mar  3  2013 .goutputstream-ENUQTW
-rw-------  1 mikee mikee        0 Feb 15  2013 .goutputstream-ETNDSW
-rw-------  1 mikee mikee        0 Oct 24  2012 .goutputstream-EUJOMW
-rw-------  1 mikee mikee        0 Feb 12  2013 .goutputstream-EXXKSW
-rw-------  1 mikee mikee        0 May 22 00:19 .goutputstream-FACBXW
-rw-------  1 mikee mikee        0 Feb 18  2013 .goutputstream-FD3USW
-rw-------  1 mikee mikee        0 Jan 13  2013 .goutputstream-FK3ZQW
-rw-------  1 mikee mikee        0 May 18 12:13 .goutputstream-FTC1WW
-rw-------  1 mikee mikee        0 Sep 27 05:32 .goutputstream-G2J63W
-rw-------  1 mikee mikee        0 May 30 19:36 .goutputstream-G53TXW
-rw-------  1 mikee mikee        0 May 22 07:51 .goutputstream-G9HEXW
-rw-------  1 mikee mikee        0 Sep 10 00:54 .goutputstream-GN512W
-rw-------  1 mikee mikee        0 Mar 30  2013 .goutputstream-GRCWUW
-rw-------  1 mikee mikee        0 Mar  2  2013 .goutputstream-H0EETW
-rw-------  1 mikee mikee        0 Feb 20  2013 .goutputstream-H6A4SW
-rw-------  1 mikee mikee        0 Oct 27 23:14 .goutputstream-H6LD5W
-rw-------  1 mikee mikee        0 May 13 19:33 .goutputstream-HC69WW
-rw-------  1 mikee mikee        0 Jan  4  2013 .goutputstream-HH65PW
-rw-------  1 mikee mikee        0 Dec 22  2012 .goutputstream-HHQTPW
-rw-------  1 mikee mikee        0 Apr  4  2013 .goutputstream-HOPSUW
-rw-------  1 mikee mikee        0 Apr 29  2013 .goutputstream-HSJCWW
-rw-------  1 mikee mikee        0 Oct 16 21:17 .goutputstream-HZLT4W
-rw-------  1 mikee mikee        0 Dec 29  2012 .goutputstream-I0WSPW
-rw-------  1 mikee mikee        0 Jul 17 00:15 .goutputstream-I7OD0W
-rw-------  1 mikee mikee        0 Jun 29 18:31 .goutputstream-I91DZW
-rw-------  1 mikee mikee        0 Sep 23 21:28 .goutputstream-IANG4W
-rw-------  1 mikee mikee        0 Mar  5  2013 .goutputstream-ICLBTW
-rw-------  1 mikee mikee        0 Nov 28  2012 .goutputstream-IF4MOW
-rw-------  1 mikee mikee        0 Oct 31  2012 .goutputstream-INFMNW
-rw-------  1 mikee mikee        0 Nov 12  2012 .goutputstream-IP7XNW
-rw-------  1 mikee mikee        0 Nov  3  2012 .goutputstream-IPGCNW
-rw-------  1 mikee mikee        0 Oct 18  2012 .goutputstream-J2FQMW
-rw-------  1 mikee mikee        0 Dec 30  2012 .goutputstream-JAV2PW
-rw-------  1 mikee mikee        0 Nov  4  2012 .goutputstream-JO4JNW
-rw-------  1 mikee mikee        0 May 24 17:03 .goutputstream-JOOGXW
-rw-------  1 mikee mikee        0 Aug 23 23:30 .goutputstream-JQ9E2W
-rw-------  1 mikee mikee        0 Feb  7  2013 .goutputstream-JXHKSW
-rw-------  1 mikee mikee        0 Mar 28  2013 .goutputstream-K0FYUW
-rw-------  1 mikee mikee        0 Jun 15 15:25 .goutputstream-KJ0EYW
-rw-------  1 mikee mikee        0 May  2  2013 .goutputstream-KP5QWW
-rw-------  1 mikee mikee        0 May 27 19:44 .goutputstream-L6R5XW
-rw-------  1 mikee mikee        0 Apr  1  2013 .goutputstream-L8YZUW
-rw-------  1 mikee mikee        0 Aug 25 13:09 .goutputstream-LATI2W
-rw-------  1 mikee mikee        0 Apr  6  2013 .goutputstream-LOA4UW
-rw-------  1 mikee mikee        0 Apr 13  2013 .goutputstream-MG7IVW
-rw-------  1 mikee mikee        0 Mar 22  2013 .goutputstream-MJ4AUW
-rw-------  1 mikee mikee        0 Apr  8  2013 .goutputstream-MKOBVW
-rw-------  1 mikee mikee        0 Oct 11  2012 .goutputstream-MS0CMW
-rw-------  1 mikee mikee        0 May  8 07:51 .goutputstream-MSLUWW
-rw-------  1 mikee mikee        0 Jun 10 00:10 .goutputstream-MW3HYW
-rw-------  1 mikee mikee        0 Feb 28  2013 .goutputstream-MWH8SW
-rw-------  1 mikee mikee        0 May 10 19:01 .goutputstream-MXHZWW
-rw-------  1 mikee mikee        0 Feb  8  2013 .goutputstream-N4KJSW
-rw-------  1 mikee mikee        0 Aug  2 00:25 .goutputstream-N5JX0W
-rw-------  1 mikee mikee        0 Jan 19  2013 .goutputstream-N82XQW
-rw-------  1 mikee mikee        0 Aug 18 17:17 .goutputstream-NM7D2W
-rw-------  1 mikee mikee        0 Mar 18  2013 .goutputstream-NSUEUW
-rw-------  1 mikee mikee        0 Apr  2  2013 .goutputstream-NV5LUW
-rw-------  1 mikee mikee        0 Feb 14  2013 .goutputstream-O008RW
-rw-------  1 mikee mikee        0 Oct 21 20:43 .goutputstream-O0DP5W
-rw-------  1 mikee mikee        0 Sep 17 18:51 .goutputstream-O1KC3W
-rw-------  1 mikee mikee        0 Mar  7  2013 .goutputstream-O539SW
-rw-------  1 mikee mikee        0 Apr 27  2013 .goutputstream-O7MRVW
-rw-------  1 mikee mikee        0 Jun 21 20:12 .goutputstream-OFOGZW
-rw-------  1 mikee mikee        0 Oct 27  2012 .goutputstream-OGQWMW
-rw-------  1 mikee mikee        0 Nov 10  2012 .goutputstream-OHHJNW
-rw-------  1 mikee mikee        0 Apr 11  2013 .goutputstream-OKU7UW
-rw-------  1 mikee mikee        0 Mar 15  2013 .goutputstream-OO90TW
-rw-------  1 mikee mikee        0 Apr 30  2013 .goutputstream-OR6RWW
-rw-------  1 mikee mikee        0 May 11 14:45 .goutputstream-ORNRWW
-rw-------  1 mikee mikee        0 Dec 20  2012 .goutputstream-P78XPW
-rw-------  1 mikee mikee        0 Jul 25 23:33 .goutputstream-PN9Z0W
-rw-------  1 mikee mikee        0 Jun 24 23:14 .goutputstream-PRP8YW
-rw-------  1 mikee mikee        0 Feb 20  2013 .goutputstream-PRY0SW
-rw-------  1 mikee mikee        0 Nov  7  2012 .goutputstream-PWXINW
-rw-------  1 mikee mikee        0 Jul 15 19:22 .goutputstream-Q039ZW
-rw-------  1 mikee mikee        0 Feb 12  2013 .goutputstream-Q1L9RW
-rw-------  1 mikee mikee        0 Oct 31  2012 .goutputstream-Q4ZENW
-rw-------  1 mikee mikee        0 Sep  4 23:41 .goutputstream-Q7J62W
-rw-------  1 mikee mikee        0 May 10 22:37 .goutputstream-QOOSWW
-rw-------  1 mikee mikee        0 May  7 21:46 .goutputstream-QULZWW
-rw-------  1 mikee mikee        0 Jul 21 23:32 .goutputstream-QVNE0W
-rw-------  1 mikee mikee        0 Feb  7  2013 .goutputstream-QZEJSW
-rw-------  1 mikee mikee        0 Sep 25 00:25 .goutputstream-R6803W
-rw-------  1 mikee mikee        0 Jul 11 00:23 .goutputstream-R7MOZW
-rw-------  1 mikee mikee        0 May 15 00:15 .goutputstream-RAI0WW
-rw-------  1 mikee mikee        0 Sep 14 11:26 .goutputstream-RD0K3W
-rw-------  1 mikee mikee        0 Jun 11 19:46 .goutputstream-RRCEYW
-rw-------  1 mikee mikee        0 Oct 24 23:01 .goutputstream-RXV94W
-rw-------  1 mikee mikee        0 Mar 24  2013 .goutputstream-RY1XTW
-rw-------  1 mikee mikee        0 Oct 21  2012 .goutputstream-RZMZMW
-rw-------  1 mikee mikee        0 Feb 27  2013 .goutputstream-S2M8SW
-rw-------  1 mikee mikee        0 Dec 29  2012 .goutputstream-SAUMPW
-rw-------  1 mikee mikee        0 Jun  4 07:50 .goutputstream-SDENXW
-rw-------  1 mikee mikee        0 Apr 19  2013 .goutputstream-SGTQVW
-rw-------  1 mikee mikee        0 Feb  5  2013 .goutputstream-SGV6RW
-rw-------  1 mikee mikee        0 Mar 11  2013 .goutputstream-SN6BTW
-rw-------  1 mikee mikee        0 Dec 14  2012 .goutputstream-SPO3OW
-rw-------  1 mikee mikee        0 Nov 15  2012 .goutputstream-SY6PNW
-rw-------  1 mikee mikee        0 Jan 10  2013 .goutputstream-T00AQW
-rw-------  1 mikee mikee        0 Oct 28  2012 .goutputstream-T4SRMW
-rw-------  1 mikee mikee        0 Jan 19  2013 .goutputstream-TEF5QW
-rw-------  1 mikee mikee        0 Feb  3  2013 .goutputstream-TF0ORW
-rw-------  1 mikee mikee        0 Nov 17  2012 .goutputstream-TZ51NW
-rw-------  1 mikee mikee        0 Jan 26  2013 .goutputstream-TZURRW
-rw-------  1 mikee mikee        0 Aug 24 00:46 .goutputstream-U6VH2W
-rw-------  1 mikee mikee        0 Mar 23  2013 .goutputstream-U83EUW
-rw-------  1 mikee mikee        0 Jan 26  2013 .goutputstream-UEBIRW
-rw-------  1 mikee mikee        0 May 10 07:37 .goutputstream-UJDXWW
-rw-------  1 mikee mikee        0 Mar 29  2013 .goutputstream-ULFWUW
-rw-------  1 mikee mikee        0 Feb 20  2013 .goutputstream-UM6YSW
-rw-------  1 mikee mikee        0 Aug 29 14:55 .goutputstream-URFE2W
-rw-------  1 mikee mikee        0 Oct 10  2012 .goutputstream-V089LW
-rw-------  1 mikee mikee        0 Feb 13  2013 .goutputstream-VGAGSW
-rw-------  1 mikee mikee        0 Sep 20 00:27 .goutputstream-VMGM3W
-rw-------  1 mikee mikee        0 May 24 21:39 .goutputstream-VMIQXW
-rw-------  1 mikee mikee        0 Oct  9  2012 .goutputstream-WEOWLW
-rw-------  1 mikee mikee        0 Jan 27  2013 .goutputstream-WF0JRW
-rw-------  1 mikee mikee        0 Nov 21  2012 .goutputstream-WHAUNW
-rw-------  1 mikee mikee        0 Feb 28  2013 .goutputstream-WIOKTW
-rw-------  1 mikee mikee        0 Jun 22 11:50 .goutputstream-WXO8YW
-rw-------  1 mikee mikee        0 Jan 30  2013 .goutputstream-WYHDRW
-rw-------  1 mikee mikee        0 Oct  3 19:15 .goutputstream-WZ703W
-rw-------  1 mikee mikee        0 Apr 24  2013 .goutputstream-X1G2VW
-rw-------  1 mikee mikee        0 Nov 13  2012 .goutputstream-X3SRNW
-rw-------  1 mikee mikee        0 Jun 16 19:30 .goutputstream-X8CHYW
-rw-------  1 mikee mikee        0 Dec 16  2012 .goutputstream-XGZVOW
-rw-------  1 mikee mikee        0 Oct 12  2012 .goutputstream-XHFWLW
-rw-------  1 mikee mikee        0 Jun  8 15:34 .goutputstream-XJNFYW
-rw-------  1 mikee mikee        0 Jan  3  2013 .goutputstream-XM19PW
-rw-------  1 mikee mikee        0 Oct 19  2012 .goutputstream-XNFIMW
-rw-------  1 mikee mikee        0 Mar  9  2013 .goutputstream-XP6KTW
-rw-------  1 mikee mikee        0 Feb 16  2013 .goutputstream-XX3TSW
-rw-------  1 mikee mikee        0 Oct 13  2012 .goutputstream-Y1G6LW
-rw-------  1 mikee mikee        0 Sep 14 12:24 .goutputstream-Y6Q82W
-rw-------  1 mikee mikee        0 Dec 25  2012 .goutputstream-Y74QPW
-rw-------  1 mikee mikee        0 Mar 30  2013 .goutputstream-Y9H2UW
-rw-------  1 mikee mikee        0 May 10 23:56 .goutputstream-YMPLWW
-rw-------  1 mikee mikee        0 Apr 13  2013 .goutputstream-YNNIVW
-rw-------  1 mikee mikee        0 Sep 13 18:22 .goutputstream-YPLS3W
-rw-------  1 mikee mikee        0 Jan  2  2013 .goutputstream-YVTBQW
-rw-------  1 mikee mikee        0 Apr 20  2013 .goutputstream-Z1GSVW
-rw-------  1 mikee mikee        0 Oct 21  2012 .goutputstream-Z3WJMW
-rw-------  1 mikee mikee        0 Aug  1 00:36 .goutputstream-ZBI00W
-rw-------  1 mikee mikee        0 Sep 18 22:58 .goutputstream-ZNAL3W
-rw-------  1 mikee mikee        0 May 23 07:48 .goutputstream-ZNEFXW
-rw-------  1 mikee mikee        0 Dec  8  2012 .goutputstream-ZO71OW
-rw-------  1 mikee mikee        0 May 31 22:23 .goutputstream-ZUBUXW
-rw-------  1 mikee mikee        0 Jun 28 04:29 .goutputstream-ZZODZW
drwxr-xr-x  3 mikee mikee     4096 Oct 20 12:45 .gstreamer-0.10
-rw-rw-r--  1 mikee mikee      496 Nov  2 09:13 .gtk-bookmarks
dr-x------  2 mikee mikee        0 Nov  2 09:13 .gvfs
-rw-------  1 mikee mikee   180166 Nov  2 09:13 .ICEauthority
drwxrwxr-x  4 mikee mikee     4096 Aug 10 19:05 .icedtea
drwxr-xr-x  2 mikee mikee     4096 Mar 10  2011 .icedteaplugin
drwxr-xr-x 11 mikee mikee     4096 Dec 29  2010 .icons
drwx------  4 mikee mikee     4096 May 25  2011 .kde
drwx------  3 mikee mikee     4096 Dec 29  2010 .kompozer.net
drwxr-xr-x  3 mikee mikee     4096 Nov 15  2011 .lastpass
drwx------  3 mikee mikee     4096 May 24  2012 .launchpadlib
drwxr-xr-x  3 mikee mikee     4096 Nov 28  2010 .local
drwx------  3 mikee mikee     4096 Jul 29  2011 .macromedia
drwx------  3 mikee mikee     4096 Jun 28  2011 .mission-control
drwxr-xr-x  4 mikee mikee     4096 Jun  1  2012 .moovida
drwx------  4 mikee mikee     4096 Apr 29  2011 .mozilla
drwxr-xr-x  2 mikee mikee     4096 May 26  2012 .mplayer
drwxr-xr-x  2 mikee mikee     4096 May  3  2012 Music
drwxr-xr-x  3 mikee mikee     4096 Mar 10  2011 .netx
drwxr-xr-x  3 mikee mikee     4096 Dec 28  2010 .openoffice.org
-rw-rw-r--  1 mikee mikee        0 Oct 30 20:13 Other
drwxr-x---  2 mikee mikee     4096 Dec 10  2010 .outwit
drwxr-xr-x  9 mikee mikee     4096 Nov  1 21:25 Pictures
drwx------  3 mikee mikee     4096 Dec  8  2010 .pki
drwx------  2 mikee mikee     4096 Nov  2 09:13 .pulse
-rw-------  1 mikee mikee      256 Nov 28  2010 .pulse-cookie
drwx------  6 mikee mikee     4096 Nov 28  2012 .purple
drwxr-xr-x  9 mikee mikee     4096 Jun  1  2012 .python-eggs
drwxr-xr-x  2 mikee mikee     4096 Dec 29  2010 .screenlets
-rw-r--r--  1 mikee mikee        0 May  1  2011 .screenrc
drwxr-xr-x  5 mikee mikee     4096 Jan 22  2011 .shotwell
drwx------  6 mikee mikee     4096 Oct  7 22:47 .Skype
drwx------  2 mikee mikee     4096 Nov 17  2012 .ssh
-rw-r--r--  1 mikee mikee        0 Nov 28  2010 .sudo_as_admin_successful
drwxr-xr-x 36 mikee mikee     4096 Oct 15 18:44 .themes
drwx------  5 mikee mikee     4096 Oct  7  2012 .thumbnails
drwx------  4 mikee mikee     4096 Apr 27  2012 .thunderbird
drwxrwxr-x  2 mikee mikee     4096 Dec 20  2010 Ubuntu One
drwxr-xr-x  9 mikee mikee     4096 Sep 11 20:53 Videos
drwxr-xr-x  4 mikee mikee     4096 Nov 24  2011 .wine
drwxr-xr-x  2 mikee mikee     4096 Jun  1  2012 .winff
-rw-------  1 mikee mikee       79 Nov  2 09:13 .Xauthority
drwxr-xr-x  2 mikee mikee     4096 Oct  6  2012 .xine
-rw-------  1 mikee mikee     7264 Nov  2 10:20 .xsession-errors
-rw-------  1 mikee mikee     9397 Nov  1 23:33 .xsession-errors.old


---

### Post by Bashing-om on 2013-11-02
mikee.bowen; Not at all what I had "feared" as to permissions.

Your system is not screwed up .. just an accumulation over time.
Two things on the to-do-list
a) change that permission of the .gconf directory back to you. All else looks good.
```

sudo chown mikee:mikee -R ~/.gconf

```
b) The ".goutputstream-XXXXX" files are a bug that to this time has no solution. Periodically remove those files:
```

rm ~/.goutputstream-*

``` which with the wildcard "*" will remove all instances of that file. Note that the file size is 0, is owned by you and is in your home directory, thus no elevated privileges are required to deal with them.

That done, reboot and let's 

see if the buttons now work in Gnome's DE.

[INDENT][INDENT]are we done now ?
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-11-02
It's a relief it's not that screwed up. 

Ok, I ran "sudo chown mikee:mikee -R ~/.gconf" and got no errors.

Then I ran "rm ~/.goutputstream-*" with no errors either. and after a restart I have the bar back and I think my system might be back to normal :-)

I have two questions though:

How do I have a 60 GB hard drive (it's an old laptop) and my home folder is only taking up 6.7 GB now, but I only have 22.8 GB free? I mean I know the system takes a chunk of memory, but that seams like a lot of memory.

Do I need to periodically run "rm ~/.goutputstream-*" to clear ".goutputstream-XXXXX" files from my system?

---

### Post by Bashing-om on 2013-11-02
mikee.bowen; Well, that all is good news.

As to disk space usage, your /home directory is but one of several. In your file manager you see several directories, each takes up a bunch of space.. and not explicit is the fact that the system takes 5% for its use that you have no direct access to. The only real things you can control are what is installed from 3rd parties - not an advocate at all myself -, and additional applications installed from the repository. Routinely do the housecleaning - inclusive of removing old kernels, The system has no way to know what the administrator may want to do with old kernels and will not remove them. That is left as a maintenance item for the administrator, along with the general house cleaning, that is in fact very light. Be aware of what and why you are installing any software. There is a reason why disk space usage is reported to you when anything is to be installed onto the system by the package manager (CLI ). 

And of course remove from your home directory old obsolete personal files that no longer serve a meaningful purpose.

If you get tight on space routinely, one can control the number of old log files kept on the system. These old compressed files, there are a lot of them, can take up huge amounts of space, If one does modify the cron routine, then it is on the administrator to pay closer attention to all the log files.

> 
Do I need to periodically run "rm ~/.goutputstream-*" to clear ".goutputstream-XXXXX" files from my system?

Not "really" required, their presence does no harm and takes very little space individually, but do in time mount up. These useless files "cloud" the picture when looking at things in the file system. So, remove them when doing that house cleaning.

One last thing I have noticed:
> 
drwxrwxr-x 5 mikee mikee 4096 Oct 29 19:23 .cinnamon

remains, why the package manager missed it , I do not know, but as you have removed Cinnamon from your system, may as well delete this directory also.
```

rm -R ~/.cinnamon

```

I like my system clean and simple as possible.

[INDENT][INDENT]simple is better
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-11-03
Thanks for all your help Bashing! I ran "rm -R ~/.cinnamon" and got no errors. I've been doing some house cleaning, removing unused programs etc., but I used synaptic package manager and it looks like the old kernals have been removed. I think I can safely mark this as solved :-)

---

### Post by Bashing-om on 2013-11-03
mikee.bowen; Outstanding ! You do good work.

I too am satisfied your system is now stable, and you know how to keep it stable.

I hope you have learned a lot in learning to live with your ubuntu !

Yeah, go ahead and mark this thread as solved [1st post -> thread tools](thanks), pending any additional closing remarks.
But, do come back often !


Keep this in mind:
[INDENT][INDENT]if it ain't broke, you have not tweaked it enough
It is all a process of learning
[/INDENT][/INDENT]

---

### Post by mikee.bowen on 2013-11-04
I have learned a lot for sure. i didn't realize the old kernals just sat there and took up space. I'm still completely in the dark about commands though. Is there a resource that lists all of the commmands and what they do? Where did you learn so much about Ubuntu?

---

### Post by Bashing-om on 2013-11-04
mikee.bowen;

Pleased you have an interest. The true power of the operating system can only be realized from the command line.

There are literally thousands of commands ,, and as many combinations of these commands to perform a given function. No one knows all of them. We only know the ones we use. I have a reference file for many of the more obscure but useful commands. As well a reference file of useful links in my continuing effort to learn this operating system.

See the "NewDocs" link in my signature, you will find many links to useful commands, as well as the sticky at the Absolute Beginners subforum.

"Where did I learn so much about ubuntu ?" -> believe it or not but right here on this forum !
(but I must admit I have been messing with computers and operation systems since the 1960's [and yeah that gives my age away]. Lots of exposure and ubuntu is my operating system of choice, ubuntu meets every demanding need I have in an operating system !)
Then there is also google -> hey it's true, google is your friend.

To this day,, If I find myself with time on my hands I return to "NewDocs" and see where my interest leads, and follow any inclination.   

And last but not at all least, do your home work and ask here ! A wealth of knowledge available here on this forum to be shared - just for the asking!

[INDENT][INDENT]this is open source at it's best
[/INDENT][/INDENT]

---

