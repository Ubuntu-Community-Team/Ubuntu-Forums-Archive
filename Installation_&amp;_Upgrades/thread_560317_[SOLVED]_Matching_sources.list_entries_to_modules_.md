---
title: "[SOLVED] Matching sources.list entries to modules being upgraded"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2007-09-26
I am trying to get around an upgrade problem from 6.06 to 6.10. My upgrade fails after the last module fetched, which is number 21. However, there are not 21 entries in sources.list. I need to comment out the "fetch" that failed, but cannot correlate the failing fetch with an entry in sources.list. 

How do I correlate what is in sources.list with what is being fetched during the upgrade?

---

### Post by Jussi Kukkonen on 2007-09-26
You probably have multiple repositories specified on one line. Please copy-paste the commands you used (if you're on the command line) and output you get here if you want more specific help. The contents of sources.list may also be useful.

---

### Post by cmnorton on 2007-09-26
Many thanks. 

Here is the command I am using:

gksu "update-manager -c -d"

Here is my sources.list.

---------------------------sources.list begin--------------------------------------------------------

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# James Cameron's PPTP GUI packaging
# deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---------------------------srouces.list end ----------------------------------------------------------

---

### Post by Jussi Kukkonen on 2007-09-26
So the update-manager seemed to change the sources.list already... and it looks fine to me. Can you try a *"sudo apt-get update"* and paste the output? That should give you the exact error message if the problem is still there.

---

### Post by cmnorton on 2007-09-26
> **Jussi Kukkonen said:**
> So the update-manager seemed to change the sources.list already... and it looks fine to me. Can you try a *"sudo apt-get update"* and paste the output? That should give you the exact error message if the problem is still there.

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B] 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]                
Ign [http://quozl.netrek.org](http://quozl.netrek.org) ./ Release.gpg                                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                                             
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Ign [http://quozl.netrek.org](http://quozl.netrek.org) ./ Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://quozl.netrek.org](http://quozl.netrek.org) ./ Packages                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release                                            
Hit [http://quozl.netrek.org](http://quozl.netrek.org) ./ Packages                                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Fetched 3B in 3s (1B/s)                                
Reading package lists... Done

---

### Post by Jussi Kukkonen on 2007-09-27
That doesn't match the sources.list  you gave earlier. Are you sure you copy-pasted */etc/apt/sources.list* in your previous post?

---

### Post by cmnorton on 2007-09-27
> **Jussi Kukkonen said:**
> That doesn't match the sources.list  you gave earlier. Are you sure you copy-pasted */etc/apt/sources.list* in your previous post?

There may be a confusion I introduced into this. Mea Culpa. I have two Ubuntu 6.06 LTS systems to upgrade. Both exhibit the same problem. It is quite possible I posted the wrong sources.list.

I think it's better for me to re-post the file. 

--------------------------------- begin sources.list ------------------------------------------

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# James Cameron's PPTP GUI packaging
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./ 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
--------------------------------- end sources.list

---

### Post by Jussi Kukkonen on 2007-09-27
That sources.list-file is fine, update-manager really should be able to upgrade that (although you may want to comment the [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) -line out before running the upgrade)... 

Try the upgrade again: the problem could have been just a server that was down. If the problem is still there, copy paste the actual error message here, then we can actually start solving it...

---

### Post by cmnorton on 2007-09-27
Before posting, I wish to express my genuine appreciation for all the help here and through launchpad. Now, here is the information from the latest attempt:

Here's what I get from the command-line.

cnorton@linux-testU:~$ sudo "update-manager -c -d"
sudo: update-manager -c -d: command not found
cnorton@linux-testU:~$ gksu "update-manager -c -d"
cnorton@linux-testU:~$ gksu "update-manager -c -d"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmpyR3o2p/edgy.tar.gz'
authenticate '/tmp/tmpyR3o2p/edgy.tar.gz' against '/tmp/tmpyR3o2p/edgy.tar.gz.gpg'

Here is the error:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

Here is the modified sources.list as mentioned:

-------------------------- begin -------------------------------

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# James Cameron's PPTP GUI packaging
# deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
-------------------------- end ----------------------------------

---

### Post by Jussi Kukkonen on 2007-09-27
Ok, now we're getting somewhere. I believe apt has downloaded the file mentioned in the error message, but it was somehow broken and gzip won't open it (and apt won't re-download cause it's already downloaded) -- IIRC this is a known bug in old apt versions.

Try removing some cached package lists:
```
sudo rm /var/lib/apt/lists/partial/*
```
and then try the update again.

---

### Post by cmnorton on 2007-09-28
> **Jussi Kukkonen said:**
> Ok, now we're getting somewhere. I believe apt has downloaded the file mentioned in the error message, but it was somehow broken and gzip won't open it (and apt won't re-download cause it's already downloaded) -- IIRC this is a known bug in old apt versions.

Try removing some cached package lists:
```
sudo rm /var/lib/apt/lists/partial/*
```
and then try the update again.

When I ran the remove partial command, there were no files in the lists partial directory. 
I get the same error as before.

I've commented out the last two universe lines, and after a couple of failed upgrades, the partial directory was filled, and I ran the sudo rm command. Here is the error as a result of doing that:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

I commented out two more universe lines and got the upgrade screen:

------------------------------------------- begin new sources.list -------------------------------------------------------------

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# James Cameron's PPTP GUI packaging
# deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

------------------------------------------------------ end new sources.list --------------------------------------------------------------

I am assuming I can upgrade, and then uncomment the lines and re-run.

---

### Post by cmnorton on 2007-09-28
Thank you for all the help. The first system upgraded to 6.10, and is on its way to 7.04. I was able to avoid all the problems with my second system because of the help provided here. That is also on its way to 7.04 via 6.10.

---

