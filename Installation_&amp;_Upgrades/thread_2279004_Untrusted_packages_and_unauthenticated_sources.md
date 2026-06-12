---
title: "Untrusted packages and unauthenticated sources"
date: 2015-05-20
forum: Installation &amp; Upgrades
---

### Post by StephenG on 2015-05-20
I'm running out of patience and ideas.  For the past two weeks, I keep getting notices that Ubuntu wants to update some security issues, including the new kernel from Ubuntu.  However, I continually get the above error messages about sources and packages.  Tried updating the public keys, since that was the first error message.  Initially, I'm told that the keys haven't changed, then that the keyserver has timed out.  It's become an endless loop.  I'm including the responses to: apt-get update, apt-key adv --keyserver hkp://subkeys.pgp.net --recv-keys 40976EAF437D05B5, apt-get upgrade, and apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5.

None of the keys appear to have changed, and yet neither do they seem to work.  Help???


```
stephen@stephen-desktop:~$ sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                
Get:1 [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg [933 B]                 
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty Release 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                           
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources/DiffIndex     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                     
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security InRelease
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg [933 B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg [933 B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security Release.gpg [933 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources/DiffIndex                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources/DiffIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources/DiffIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources/DiffIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages/DiffIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages/DiffIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages/DiffIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages/DiffIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources/DiffIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources/DiffIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources/DiffIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources/DiffIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages/DiffIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Sources/DiffIndex        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Sources/DiffIndex  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Sources/DiffIndex  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Sources/DiffIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main i386 Packages/DiffIndex  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse i386 Packages      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security/universe Translation-en_US
Fetched 4,737 B in 1min 26s (54 B/s)
Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
```


```
stephen@stephen-desktop:~$ sudo apt-key adv --keyserver hkp://subkeys.pgp.net  --recv-keys 40976EAF437D05B5
[sudo] password for stephen: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.LD084MZ48p --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyserver hkp://subkeys.pgp.net --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```


```
stephen@stephen-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-generic-pae linux-headers-generic
  linux-headers-generic-pae linux-image-generic linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
```


```
stephen@stephen-desktop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.S2EAwyp4UV --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
```

---

### Post by dino99 on 2015-05-20
as i know extras.ubuntu.com is abandoned
[http://askubuntu.com/questions/127326/how-to-fix-missing-gpg-keys](http://askubuntu.com/questions/127326/how-to-fix-missing-gpg-keys)

---

### Post by StephenG on 2015-05-20
Followed the link and followed the Y-PPA Manager suggestion.  Same outcome.  Still getting that dern untrusted package error message.

And the results of apt-get update are the same as well.

---

### Post by dino99 on 2015-05-20
be sure that all the source entries are valid
and are you using a proxy ?

---

### Post by StephenG on 2015-05-20
Not sure how to verify source entries and, no, I'm not using a proxy.

---

### Post by v3.xx on 2015-05-20
Try this fix
[http://ubuntuforums.org/showthread.php?t=1869890&page=2&p=11396851#post11396851](http://ubuntuforums.org/showthread.php?t=1869890&page=2&p=11396851#post11396851)

Is this a possibility?
[http://ubuntuforums.org/showthread.php?t=2257304&p=13190302#post13190302](http://ubuntuforums.org/showthread.php?t=2257304&p=13190302#post13190302)

and this
[http://ubuntuforums.org/showthread.php?t=2257304&p=13190302#post13190302](http://ubuntuforums.org/showthread.php?t=2257304&p=13190302#post13190302)

To verify your sources list
```
cat /etc/apt/sources.list
```

To verify PPA source
```
ls /etc/apt/sources.list.d/*.list
```

---

### Post by StephenG on 2015-05-20
```
stephen@stephen-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main multiverse restricted universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main multiverse restricted universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse #Added by software-properties

deb http://us.archive.ubuntu.com/ubuntu/ trusty-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-security main multiverse restricted universe #Added by software-properties
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

##  This is the gscan2pdf application updater
```

```
stephen@stephen-desktop:~$ ls /etc/apt/sources.list.d/*.list/etc/apt/sources.list.d/ehoover-compholio-trusty.list
/etc/apt/sources.list.d/fuzebox.list
/etc/apt/sources.list.d/mqchael-pipelight-trusty.list
/etc/apt/sources.list.d/pipelight-stable-trusty.list
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list
```

So, now I see that in the ls feedback, there's a "precise" entry for the Wine PPA, and I'm not quite certain how to fix that.  Nor do I have any idea why the gscan2pdf updater is there at all since I uninstalled that program long ago.

---

### Post by v3.xx on 2015-05-20
Gscan2 has been commented (##) out, no problem with that.

You do need to remove that wine ppa.  Use software sources to remove.
```
software-properties-gtk
```
And while your there, uncheck 'Source Code'.  That is for package developers and such.  No need to update something you do not use.

Any progress on those gpg errors?

---

### Post by StephenG on 2015-05-20
Since I use Wine quite often, don't I need to have some PPA there to let it update?

No progress on the keys.  Still getting the same dern untrusted source or package error every time I try to update the system, even for the Ubuntu Base updates.  I  can't see how the key for hte kernel can be untrusted.

---

### Post by v3.xx on 2015-05-20
> **StephenG said:**
> Since I use Wine quite often, don't I need to have some PPA there to let it update?
What version of wine are you using?
```
apt-cache policy wine
```

---

### Post by StephenG on 2015-05-20
```
stephen@stephen-desktop:~$ apt-cache policy wine
wine:
  Installed: 1:1.6.2-0ubuntu4
  Candidate: 1:1.6.2-0ubuntu4
  Version table:
 *** 1:1.6.2-0ubuntu4 0
        500 http://mirror.cogentco.com/pub/linux/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status
```

---

### Post by v3.xx on 2015-05-20
It looks to me your running the ubuntu 14.04 package of wine, located in the software center.

[http://packages.ubuntu.com/trusty/wine1.6](http://packages.ubuntu.com/trusty/wine1.6)

You can also just uncheck it in software sources.  This will disable the ppa if you are unsure.

---

### Post by StephenG on 2015-05-22
Bump.  Is no one else having these issues with untrusted sources and the public keys for the updater?

Tried resetting but no go.
Also tried adding the public keys manually, per "OpenSourceForGeeks" (2nd approach).  All installed as predicted, but the results are the same: signature couldn't be verified because the public key is not available.

Tried editing the gpg.conf file to change keyserver from gnupg to ubuntu as follows:

keyserver [http://keyserver.ubuntu.com](http://keyserver.ubuntu.com)
# keyserver hkp://keys.gnupg.net

to no avail.  What is going on?

Where the heck am I supposed to find the public keys for 14.04 updater, if not at the Ubuntu keyserver?!?  I am flippin' lost here!!

---

### Post by Bashing-om on 2015-05-22
StephenG; Hello;

Allow me to jump in here . Yeah, authentication can get complex and deep.
Let's make sure we do not have 2 separate issues here . GPG keys and a broke wine install.

GPG keys:
Show us what is presently configured:
```

cat ~/.gnupg/gpg.conf
sudo apt-key list
ls -al /etc/apt/trusted.gpg ##just to verify permissions##
ls -al /etc/apt/trusted.gpg.d
ls -al /home/<user_name>/.gnupg/ ##where<user_name> is your's ##

```

Now for wine:
installed is the version that is available in the repo;
Let's revert the wine install to that of the repo:
show:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
In order to revert and remove the possible PPA.

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-05-22
The germane portion of the gpg.conf file (I presume) is:

keyserver hkp://keys.gnupg.net
#keyserver mailto:pgp-public-keys@keys.nl.pgp.net
#keyserver ldap://keyserver.pgp.com

```
stephen@stephen-desktop:~$ sudo apt-key list
[sudo] password for stephen: 
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024D/3E5C1192 2010-09-20
uid                  Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

pub   4096R/C0B21F32 2012-05-11
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

pub   1024R/5BC3E400 2009-01-20
uid                  Launchpad PPA for Jeffrey Ratcliffe

gpg: [don't know]: invalid packet (ctb=2d)
gpg: keydb_search_next failed: invalid packet
```

```
stephen@stephen-desktop:~$ ls -al /etc/apt/trusted.gpg ##just to verify permission##
-rw-r--r-- 1 root root 21457 May 20 17:31 /etc/apt/trusted.gpg

stephen@stephen-desktop:~$ ls -al /etc/apt/trusted.gpg.d
total 20
drwxr-xr-x 2 root root 4096 May 20 10:52 .
drwxr-xr-x 6 root root 4096 May 20 17:31 ..
-rw-r--r-- 1 root root  481 May  7 21:18 fuzebox.gpg
-rw-r--r-- 1 root root  371 Jan  2 17:20 pipelight-stable.gpg
-rw-r--r-- 1 root root    0 Jan  2 17:20 pipelight-stable.gpg~
-rw-r--r-- 1 root root  346 May 20 10:52 webupd8team-y-ppa-manager.gpg
-rw-r--r-- 1 root root    0 May 20 10:52 webupd8team-y-ppa-manager.gpg~
```

```
stephen@stephen-desktop:~$ ls -al /home/stephen-desktop/ .gnupg/
ls: cannot access /home/stephen-desktop/: No such file or directory
.gnupg/:
total 40
drwx------  2 stephen stephen 4096 May 22 09:39 .
drwxr-xr-x 54 stephen stephen 4096 May 22 09:22 ..
-rw-------  1 stephen stephen 9398 May 22 09:39 gpg.conf
-rw-------  1 stephen stephen 9437 May 22 09:32 gpg.conf~
-rw-------  1 stephen stephen  368 Jan 24  2013 pubring.gpg
-rw-------  1 stephen stephen    0 Jan 24  2013 pubring.gpg~
-rw-------  1 stephen stephen    0 Jan 24  2013 secring.gpg
-rw-------  1 stephen stephen 1200 Jan 24  2013 trustdb.gpg

```

```
stephen@stephen-desktop:~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://mirror.cogentco.com/pub/linux/ubuntu/ trusty main restricted
     6	
     7	## Major bug fix updates produced after the final release of the
     8	## distribution.
     9	deb http://mirror.cogentco.com/pub/linux/ubuntu/ trusty-updates main restricted
    10	
    11	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12	## team. Also, please note that software in universe WILL NOT receive any
    13	## review or updates from the Ubuntu security team.
    14	deb http://mirror.cogentco.com/pub/linux/ubuntu/ trusty universe
    15	deb http://mirror.cogentco.com/pub/linux/ubuntu/ trusty-updates universe
    16	
    17	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    18	## team, and may not be under a free licence. Please satisfy yourself as to 
    19	## your rights to use the software. Also, please note that software in 
    20	## multiverse WILL NOT receive any review or updates from the Ubuntu
    21	## security team.
    22	deb http://mirror.cogentco.com/pub/linux/ubuntu/ trusty multiverse
    23	deb http://mirror.cogentco.com/pub/linux/ubuntu/ trusty-updates multiverse
    24	
    25	## N.B. software from this repository may not have been tested as
    26	## extensively as that contained in the main release, although it includes
    27	## newer versions of some applications which may provide useful features.
    28	## Also, please note that software in backports WILL NOT receive any review
    29	## or updates from the Ubuntu security team.
    30	deb http://mirror.cogentco.com/pub/linux/ubuntu/ trusty-backports main restricted universe multiverse
    31	
    32	deb http://mirror.cogentco.com/pub/linux/ubuntu/ trusty-security main restricted
    33	deb http://mirror.cogentco.com/pub/linux/ubuntu/ trusty-security universe
    34	deb http://mirror.cogentco.com/pub/linux/ubuntu/ trusty-security multiverse
    35	
    36	## Uncomment the following two lines to add software from Canonical's
    37	## 'partner' repository.
    38	## This software is not part of Ubuntu, but is offered by Canonical and the
    39	## respective vendors as a service to Ubuntu users.
    40	deb http://archive.canonical.com/ubuntu trusty partner
    41	# deb-src http://archive.canonical.com/ubuntu trusty partner
    42	
    43	## This software is not part of Ubuntu, but is offered by third-party
    44	## developers who want to ship their latest software.
    45	deb http://extras.ubuntu.com/ubuntu trusty main
    46	# deb-src http://extras.ubuntu.com/ubuntu trusty main
    47	
    48	##  This is the gscan2pdf application updater
```

```
stephen@stephen-desktop:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/ehoover-compholio-trusty.list <==

==> /etc/apt/sources.list.d/ehoover-compholio-trusty.list.save <==

==> /etc/apt/sources.list.d/fuzebox.list <==

==> /etc/apt/sources.list.d/fuzebox.list.save <==

==> /etc/apt/sources.list.d/mqchael-pipelight-trusty.list <==

==> /etc/apt/sources.list.d/mqchael-pipelight-trusty.list.save <==

==> /etc/apt/sources.list.d/pipelight-stable-trusty.list <==

==> /etc/apt/sources.list.d/pipelight-stable-trusty.list.save <==

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list <==

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.distUpgrade <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save <==

==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list.save <==
deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu trusty main

```

```
stephen@stephen-desktop:~$ ls -al /home/stephen/ .gnupg/
.gnupg/:
total 40
drwx------  2 stephen stephen 4096 May 22 09:39 .
drwxr-xr-x 54 stephen stephen 4096 May 22 09:22 ..
-rw-------  1 stephen stephen 9398 May 22 09:39 gpg.conf
-rw-------  1 stephen stephen 9437 May 22 09:32 gpg.conf~
-rw-------  1 stephen stephen  368 Jan 24  2013 pubring.gpg
-rw-------  1 stephen stephen    0 Jan 24  2013 pubring.gpg~
-rw-------  1 stephen stephen    0 Jan 24  2013 secring.gpg
-rw-------  1 stephen stephen 1200 Jan 24  2013 trustdb.gpg

/home/stephen/:
ls: cannot access /home/stephen/.gvfs: Permission denied
total 620
drwxr-xr-x 54 stephen stephen   4096 May 22 09:22 .
drwxr-xr-x  3 root    root      4096 Oct 17  2012 ..
-rw-rw-r--  1 stephen stephen  85209 Nov 24 21:26 2014 JV Basketball.ods
drwx------  3 stephen stephen   4096 Oct 17  2012 .adobe
-rw-------  1 stephen stephen   6814 May 21 15:35 .bash_history
-rw-r--r--  1 stephen stephen    220 Oct 17  2012 .bash_logout
-rw-r--r--  1 stephen stephen   3486 Oct 17  2012 .bashrc
drwxrwxr-x  5 stephen stephen   4096 Apr 14  2014 .bitpim-files
drwx------  2 stephen stephen   4096 Jan 24  2014 .bogofilter
drwx------ 39 stephen stephen   4096 May 20 14:26 .cache
drwxrwxr-x  6 stephen stephen   4096 Nov 30  2012 .clamtk
drwx------  3 stephen stephen   4096 Aug 15  2014 .compiz
drwxrwxr-x  3 stephen stephen   4096 Oct 17  2012 .compiz-1
drwx------ 36 stephen stephen   4096 Apr 28 08:48 .config
drwx------  3 stephen stephen   4096 Oct 17  2012 .dbus
drwxr-xr-x  2 stephen stephen   4096 May 22 09:21 Desktop
-rw-r--r--  1 stephen stephen     26 Aug 12  2014 .dmrc
drwxr-xr-x 32 stephen stephen   4096 May 19 15:16 Documents
drwxr-xr-x  8 stephen stephen   4096 May 22 09:12 Downloads
-rw-r--r--  1 stephen stephen   8445 Oct 17  2012 examples.desktop
drwxr-xr-x  2 stephen stephen   4096 Aug 13  2014 fontconfig
drwxr-xr-x  2 stephen stephen   4096 Aug 13  2014 .fontconfig
drwx------  6 stephen stephen   4096 May 19 17:35 .gconf
drwx------  4 stephen stephen   4096 Oct 28  2012 .gegl-0.0
drwxr-xr-x 22 stephen stephen   4096 Jul  8  2014 .gimp-2.6
drwxr-xr-x 24 stephen stephen   4096 May 20 14:46 .gimp-2.8
-rw-r-----  1 stephen stephen      0 Aug 12  2014 .gksu.lock
drwx------  3 stephen stephen   4096 May 15 16:18 .gnome
drwx------  4 stephen stephen   4096 Aug 13  2014 .gnome2
drwx------  2 stephen stephen   4096 May 22 09:39 .gnupg
-rw-rw-r--  1 stephen stephen 127696 Nov  1  2012 GOES appointment.pdf
-rw-------  1 stephen stephen      0 Feb 22  2013 .goutputstream-0M0TSW
-rw-------  1 stephen stephen      0 Sep 23  2013 .goutputstream-12843W
-rw-------  1 stephen stephen      0 Mar 19  2013 .goutputstream-1HF2TW
-rw-------  1 stephen stephen      0 Oct 30  2012 .goutputstream-1M9GMW
-rw-------  1 stephen stephen      0 Oct 26  2013 .goutputstream-330M5W
-rw-------  1 stephen stephen      0 Sep 27  2013 .goutputstream-38WX3W
-rw-------  1 stephen stephen      0 Apr 25  2013 .goutputstream-3L42VW
-rw-------  1 stephen stephen      0 Oct 18  2012 .goutputstream-3Q7KMW
-rw-------  1 stephen stephen      0 Jul  2  2013 .goutputstream-3VCKZW
-rw-------  1 stephen stephen      0 Jan 10  2013 .goutputstream-51IGQW
-rw-------  1 stephen stephen      0 Oct 18  2012 .goutputstream-5HTKMW
-rw-------  1 stephen stephen      0 Jul  7  2014 .goutputstream-5W5LIX
-rw-------  1 stephen stephen      0 Jun  8  2013 .goutputstream-7GLDYW
-rw-------  1 stephen stephen      0 Sep 23  2013 .goutputstream-7SCG4W
-rw-------  1 stephen stephen      0 Oct 18  2012 .goutputstream-828JMW
-rw-------  1 stephen stephen      0 May 13  2014 .goutputstream-9054FX
-rw-------  1 stephen stephen      0 Jan  4  2014 .goutputstream-A9T18W
-rw-------  1 stephen stephen      0 Dec 22  2012 .goutputstream-C5MRPW
-rw-------  1 stephen stephen      0 Dec 17  2013 .goutputstream-CIWE8W
-rw-------  1 stephen stephen      0 Dec 23  2013 .goutputstream-GDIG8W
-rw-------  1 stephen stephen      0 Jul  5  2013 .goutputstream-GZAPZW
-rw-------  1 stephen stephen      0 Apr 30  2013 .goutputstream-H2ZLWW
-rw-------  1 stephen stephen      0 Aug 14  2013 .goutputstream-HZ3V1W
-rw-------  1 stephen stephen      0 Aug 11  2013 .goutputstream-IJKT1W
-rw-------  1 stephen stephen      0 Apr  9  2013 .goutputstream-J05MVW
-rw-------  1 stephen stephen      0 Feb 18  2013 .goutputstream-LAIZSW
-rw-------  1 stephen stephen      0 Oct 25  2012 .goutputstream-M7UNMW
-rw-------  1 stephen stephen      0 Apr 16  2014 .goutputstream-MR0XDX
-rw-------  1 stephen stephen      0 Mar 24  2014 .goutputstream-NWQMDX
-rw-------  1 stephen stephen      0 Nov 23  2012 .goutputstream-OHEWNW
-rw-------  1 stephen stephen      0 Nov 30  2012 .goutputstream-P94OOW
-rw-------  1 stephen stephen      0 May 15  2014 .goutputstream-PX1VFX
-rw-------  1 stephen stephen      0 Mar  9  2014 .goutputstream-Q5L8BX
-rw-------  1 stephen stephen      0 Oct 18  2012 .goutputstream-T50VMW
-rw-------  1 stephen stephen      0 Aug  2  2013 .goutputstream-TMV70W
-rw-------  1 stephen stephen      0 Apr 12  2014 .goutputstream-TU74DX
-rw-------  1 stephen stephen      0 Nov 11  2013 .goutputstream-U0XL6W
-rw-------  1 stephen stephen      0 Oct 19  2013 .goutputstream-UFD64W
-rw-------  1 stephen stephen      0 Sep  7  2013 .goutputstream-UUG32W
-rw-------  1 stephen stephen      0 Oct 18  2012 .goutputstream-UYOAMW
-rw-------  1 stephen stephen      0 Aug 27  2013 .goutputstream-WXYK2W
-rw-------  1 stephen stephen      0 Jul 21  2013 .goutputstream-XEU8ZW
-rw-------  1 stephen stephen      0 Nov 14  2012 .goutputstream-YQ14NW
-rw-------  1 stephen stephen      0 Jul  3  2013 .goutputstream-Z1V1ZW
-rw-------  1 stephen stephen      0 Nov  1  2012 .goutputstream-ZB93MW
-rw-------  1 stephen stephen      0 Dec  3  2013 .goutputstream-ZEWJ7W
-rw-------  1 stephen stephen      0 Oct 18  2012 .goutputstream-ZTDWMW
drwx------  2 stephen stephen   4096 Dec  3  2013 .gphoto
-rw-rw-r--  1 stephen stephen   2108 Mar 30  2013 .gscan2pdf
drwxrwxr-x  3 stephen stephen   4096 May  2  2014 .gstreamer-0.10
-rw-rw-r--  1 stephen stephen    147 Aug 13  2014 .gtk-bookmarks
d?????????  ? ?       ?            ?            ? .gvfs
drwxr-----  2 stephen stephen   4096 Oct 17  2012 .hplip
-rw-------  1 stephen stephen  67682 May 19 17:35 .ICEauthority
drwx------  4 stephen stephen   4096 Jan  6 22:30 .kde
drwxr-xr-x  7 stephen stephen   4096 Mar 11 23:18 kdenlive
-rw-rw-r--  1 stephen stephen  12686 May 22 09:12 key1
-rw-rw-r--  1 stephen stephen   5776 May 22 09:15 key2
-rw-rw-r--  1 stephen stephen   2012 May 22 09:17 key3
-rw-r--r--  1 root    root      1199 May  7 21:15 keyring.gpg
-rw-r--r--  1 root    root      1199 May  7 21:18 keyring.gpg.1
drwx------  3 stephen stephen   4096 Jan 14  2013 .launchpadlib
drwxr-xr-x  3 stephen stephen   4096 Oct 17  2012 .local
drwx------  3 stephen stephen   4096 Oct 17  2012 .macromedia
drwx------  3 stephen stephen   4096 Oct 17  2012 .mission-control
drwx------  4 stephen stephen   4096 Oct 17  2012 .mozilla
drwxr-xr-x  2 stephen stephen   4096 Oct 17  2012 Music
drwx------  3 stephen stephen   4096 Mar 18 09:08 .nv
drwxrwxr-x  2 stephen stephen   4096 Oct 29  2013 .nvidia
-rw-rw-r--  1 stephen stephen      0 May 15  2013 .odbc.ini
drwxr-xr-x 10 stephen stephen   4096 Mar 24 22:25 Pictures
drwx------  3 stephen stephen   4096 Nov 30  2012 .pki
drwxrwxr-x 12 stephen stephen   4096 Dec 16  2013 .PlayOnLinux
-rw-r--r--  1 stephen stephen    675 Oct 17  2012 .profile
drwxr-xr-x  2 stephen stephen   4096 Oct 17  2012 Public
drwx------  2 stephen stephen   4096 May 11 12:08 .pulse
-rw-------  1 stephen stephen    256 Oct 17  2012 .pulse-cookie
-rw-r--r--  1 stephen root       430 May 20 10:58 repositories.backup-2015-05-20-1058.tar.gz
drwx------  3 stephen stephen   4096 May  6  2013 .sane
drwxrwxr-x  6 stephen stephen   4096 Mar 23  2014 simple-scan-3.12.0
drwx------  7 stephen stephen   4096 May 22 22:51 .Skype
drwx------  2 stephen stephen   4096 Jan 24  2014 .spamassassin
drwxr-xr-x  2 stephen stephen   4096 Oct 17  2012 Templates
drwx------  4 stephen stephen   4096 Oct 19  2012 .thumbnails
drwx------  4 stephen stephen   4096 Oct 17  2012 .thunderbird
drwxrwxr-x  2 stephen stephen   4096 Dec 26  2012 Ubuntu One
drwxr-xr-x  2 stephen stephen   4096 Jan 19 13:55 Videos
-rw-rw-r--  1 stephen stephen  17404 May 20 12:11 William Recap for Senior Day.odt
-rw-rw-r--  1 stephen stephen      2 Oct 18  2012 .windows-serial
drwxrwxr-x  4 stephen stephen   4096 May 20 14:47 .wine
drwxrwxr-x  4 stephen stephen   4096 May 19 00:26 .wine-pipelight
-rw-------  1 stephen stephen     60 May 19 17:35 .Xauthority
drwxrwxr-x  2 stephen stephen   4096 Oct 18  2012 .xinput.d
-rw-------  1 stephen stephen    108 May 19 17:35 .xsession-errors
-rw-------  1 stephen stephen    802 May 19 17:27 .xsession-errors.old
```

Some of these entries mean nothing to me since they refer to programs that I have deleted -- or believed I had, though obviously portions of them remain, clogging things up.  What also makes no sense is why the updater would *all of a sudden* decide it no longer had valid keys, though I had done nothing that I know of to change any of the settings, etc.  I do not try to tweak what I know nothing about, so there's no reason for settings to change themselves.  The error messages started popping up only in response to me telling the auto-updater to go ahead and install the latest Ubuntu security updates.  Weird.

---

### Post by Bashing-om on 2015-05-23
StephenG; Well ..

We have a problem, as I do not know how to fix:

I think:
> 
d?????????  ? ?       ?            ?            ? .gvfs
 in your /home is the root of the problem. 
Where it should be as:
```

ls -al /home/sysop/
drwx------  2 sysop sysop    4096 May 19  2013 .gvfs

```
That most likely leads also to :
> 
gpg: [don't know]: invalid packet (ctb=2d)
gpg: keydb_search_next failed: invalid packet

Indicates to me that the .gvfs directory is corrupt, and perhaps files also within the directory. I have no idea of how to rebuild that directory !
Others please jump in here and advise.
v3.xx, what thinkist thou ?

From the state of wine I can accept that there occurred an improper reversion from PPA to the version in the software repository, and that too may have led to this condition.
StephenG what steps did you do to revert wine ?
Depending, perhaps we need to re-instate the PPA and then revert back to the repo ???

And lastly, not related to the issues at hand, is the old 12.04 install files '.goutputstream' that can be safely removed.

[INDENT][INDENT]if I knew better
[INDENT][INDENT][INDENT]I would say else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-05-26
I am happy to uninstall Wine and reinstall it if that would be the easiest fix, at least for that PPA issue.  I have no particular attachment to the current version.  Nor do I have any recollection of reverting from one version to an earlier one.  I generally try to keep things as up-to-date as possible, but have never gone to an earlier version of any software, preferring to find and fix (with lots of help from this forum!) any bugs on new releases -- and I much prefer to wait for the LTS releases, shying away from beta anything.

---

### Post by v3.xx on 2015-05-26
> **Bashing-om said:**
> v3.xx, what thinkist thou ?
Thou thinkist in a while.  I need to reread this thread and knock a few things off the 'honey do' list at home.  Be back later when I can focus on this :)

---

### Post by v3.xx on 2015-05-26
> I am happy to uninstall Wine and reinstall it if that would be the easiest fix
I still think this is a good idea.  You have y-ppa-manager, put it to work.  Is should revert to the default of wine for 14o4.  If it doesn't, we take it from there.

---

### Post by Bashing-om on 2015-05-26
v3.xx - StephenG; Hello;

While I may agree that (re-)installing Wine is needed. I bet no can do until the signing keys on the system are fixed.
Unfortunately I have no idea how to repair the directory:
> 
ls -al /home ->> d?????????  ? ?       ?            ?            ? .gvfs


[INDENT]we want the horse
[INDENT][INDENT][INDENT]before the cart
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by v3.xx on 2015-05-26
Could happen.  If thats the case, just have to remove it for now.

As for ~/.gvfs; mine is empty and thats all I know about it.

---

### Post by Bashing-om on 2015-05-27
StephenG; v3.xx; Morning ;

Another thought in mind is that we are not exceeding the maximum number of keyrings.
What returns:
```

ls /etc/apt/trusted.gpg.d | wc -l

```

[INDENT][INDENT]as I continue in my consideration of this issue
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-06-16
What returns in response to that command, Bashing-om, is the number "5"

---

### Post by von Corax on 2015-06-20
As of a week or so ago, I'm having a similar problem. I had been updating from ussg.iu.edu; two days ago I got a warning notification that my package info was out of date. Update Manager told me that my package info had not been updated for 9 days. (That would put it at June 11.) I changed to "Main Server" and got a list of 19 updates, but Update Manager claims none of them can be trusted.

I tried a few of the suggestions above with no success. When I reload in Synaptic, or run apt-update, I get the following:
```
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://www.openprinting.org lsb3.2 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 24CBF5474CFD1E2F
W: GPG error: http://archive.ubuntu.com precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.canonical.com precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E354FBD902A9EC29
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 30C0868B8020F06A
W: GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 517590D9A8492E35
W: GPG error: http://archive.canonical.com lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C2518248EEA14886
W: GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 517590D9A8492E35
W: GPG error: http://archive.ubuntu.com precise-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com precise-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com precise-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

```

Also, as of a few minutes ago, I get an "internal system error" from update-apt-xapian-index.

I'm running 12.04 LTS with Kernel Linux 3.2.0-85-generic, if that helps. (One of the pending updates is 3.2.0-86.)

---

### Post by Bashing-om on 2015-06-20
von Corax; Hello;

Mind you, there is more I do not know than what I do know. I am more than willing to explore this situation and see what we can learn.
One commonality is the control files in your /home directory.
For starters, let's make sure that 'you' own these files and not "root" .
Post back the results of terminal command:
```

ls -al /home/<your_user_name>/.gnupg

```
example: ls -al /home/von-Corax/.gnupg

One instance of a GPG key error is one thing, a bunch of them, we look for that common factor.

[INDENT][INDENT][INDENT]seek and ye shall find
[/INDENT][/INDENT][/INDENT]

---

### Post by von Corax on 2015-06-20
> **Bashing-om said:**
> von Corax; Hello;
One commonality is the control files in your /home directory.
For starters, let's make sure that 'you' own these files and not "root" .


```
dave@proteus:~$ ls -al /home/dave/.gnupg
total 152
drwx------   2 dave dave  4096 Jan  8 13:48 .
drwxr-xr-x 103 dave dave 12288 Jun 18 00:13 ..
-rw-------   1 dave dave  9398 Jan  8 13:48 gpg.conf
-rw-------   1 dave dave 58186 Jan  8 13:48 pubring.gpg
-rw-------   1 dave dave 58186 Jan  8 13:48 pubring.gpg~
-rw-------   1 dave dave     0 Jan  8 13:48 secring.gpg
-rw-------   1 dave dave  1200 Jan  8 13:48 trustdb.gpg
dave@proteus:~$ 


```

FWIW, I just checked my logs, and my last successful update was on 11 June 2015, and included kernel 3.2.0-85.

---

### Post by Bashing-om on 2015-06-20
von Corax; Well well ;

That looks good; Moving on a long and testing !
what returns :
```

for r in /var/lib/apt/lists/*Release; do if ! gpgv --keyring /etc/apt/trusted.gpg $r.gpg $r; then echo "error: $? Problem with $r"; fi; done

```
That will check the gpg signatures of the Release files.... any errors it's say "error: X Problem with ...."

Maybe we get a hint on where to look further for that common situation.

[INDENT][INDENT]Oh where oh where can my little file be 
[/INDENT][/INDENT]

---

### Post by von Corax on 2015-06-20
```
dave@proteus:~$ for r in /var/lib/apt/lists/*Release; do if ! gpgv --keyring /etc/apt/trusted.gpg $r.gpg $r; then echo "error: $? Problem with $r"; fi; done
gpgv: can't open `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_Release
gpgv: can't open `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_Release
gpgv: can't open `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-backports_Release
gpgv: can't open `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_Release
gpgv: can't open `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-security_Release
gpgv: can't open `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise-updates_Release
gpgv: can't open `/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release
gpgv: can't open `/var/lib/apt/lists/deb.opera.com_opera-stable_dists_stable_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/deb.opera.com_opera-stable_dists_stable_Release
gpgv: can't open `/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_Release
gpgv: can't open `/var/lib/apt/lists/ppa.launchpad.net_arand_redeclipse_ubuntu_dists_precise_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/ppa.launchpad.net_arand_redeclipse_ubuntu_dists_precise_Release
gpgv: can't open `/var/lib/apt/lists/ppa.launchpad.net_groovy-dev_grails_ubuntu_dists_precise_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/ppa.launchpad.net_groovy-dev_grails_ubuntu_dists_precise_Release
gpgv: can't open `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_Release
gpgv: can't open `/var/lib/apt/lists/www.openprinting.org_download_printdriver_debian_dists_lsb3.2_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/www.openprinting.org_download_printdriver_debian_dists_lsb3.2_Release
dave@proteus:~$ 


```

All files in this directory are owned by root.

---

### Post by Bashing-om on 2015-06-20
von Corax; Yes !

We have a solid hint .

Let's try:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```
To remove the suspected corrupted control files, and 'update' to rebuild them.

[INDENT][INDENT]how now brown cow 
[/INDENT][/INDENT]

---

### Post by von Corax on 2015-06-20
[FONT=courier new]apt-get update [/FONT]produced reams of output, ending with
```
Fetched 29.0 MB in 1min 37s (296 kB/s)                                                                                             
Reading package lists... Done
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://www.openprinting.org lsb3.2 Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 24CBF5474CFD1E2F
W: GPG error: http://archive.ubuntu.com precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.canonical.com precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E354FBD902A9EC29
W: GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 517590D9A8492E35
W: GPG error: http://archive.canonical.com lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 30C0868B8020F06A
W: GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 517590D9A8492E35
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C2518248EEA14886
W: GPG error: http://archive.ubuntu.com precise-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com precise-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com precise-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
dave@proteus:/var/lib/apt$ 

```

I haven't tried [FONT=courier new]apt-get upgrade [/FONT]yet.

---

### Post by Bashing-om on 2015-06-20
von Corax; Yuk ;

Unpleasant surprise that last, and nope If 'update' does not run clean no need to 'upgrade' as it would be in-effective,

OK, let's poke at it and see what bites back:
```

sudo apt-key adv --recv-keys --keyserver 40976EAF437D05B5

```

Maybe we get a hint why the /list files are not recognized.

[INDENT][INDENT]if at 1st you do not succeed
[INDENT][INDENT][INDENT]do something else ( sky diving is excepted)
[/INDENT][/INDENT][/INDENT] [/INDENT][/INDENT]

---

### Post by von Corax on 2015-06-20
What will this do (before I try it?)

---

### Post by Bashing-om on 2015-06-20
von Corax; Hey;

Regret the delay, Internet connectivity issues - not in my house .. 
Any way, while I am able to connect:
That command will install one GPG Key.
From this test, win  or loose, maybe we can determine where the fault lies that so many of the keys are lost.

Anyone else with a better procedure, I am sure open to learn better.

[INDENT][INDENT]right, wrong or otherwise
[INDENT][INDENT][INDENT]do something
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by von Corax on 2015-06-20
Okay. Done; no error messages.

---

### Post by Bashing-om on 2015-06-20
von Corax; Hey !

I continue with internet connectivity issues, bear with that:
```

sysop@1404mini:~$ ping -c3 suddenlink.com
PING suddenlink.com (107.22.178.157) 56(84) bytes of data.
64 bytes from 107.22.178.157: icmp_seq=2 ttl=35 time=90.3 ms

--- suddenlink.com ping statistics ---
3 packets transmitted, 1 received, 66% packet loss, time 11101ms
rtt min/avg/max/mdev = 90.314/90.314/90.314/0.000 ms
sysop@1404mini:~$ ping -c3 suddenlink.com
PING suddenlink.com (107.22.178.157) 56(84) bytes of data.

--- suddenlink.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

```

As to your issue. Well, What we can do is to (RE-)install the GPG keys. As much as I would like to know what the root of the issue is:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A040830F7FAC5991
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 24CBF5474CFD1E2F
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E354FBD902A9EC29
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 517590D9A8492E35
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 30C0868B8020F06A
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 517590D9A8492E35
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys C2518248EEA14886

```

Now let's see if you can :
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]maybe YES
[INDENT][INDENT][INDENT]could be, not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by von Corax on 2015-06-20
Aha. Your first "apt-key" command didn't actually install anything - you didn't specify a keyserver.

Anyway, that was easy enough to figure out, and apt-get update exited normally, but
```
dave@proteus:~$ sudo apt-get upgrade
[sudo] password for dave: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dave@proteus:~$ 

```

EDIT: Something's happened, though - Update Manager shows nothing pending, and the System menu shows a reboot required. Is it safe to ignore the message about the locking error?

---

### Post by Bashing-om on 2015-06-21
von Corax; Hey hey ...

All is good now ? 
I do expect that by this time - 14 hours later - that you have found that :
> 
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

one can only have one instance of  package management active at the given time. If Software Center or other is active, can not also run an apt command.


Yeah I did mess up that --keyserver command ! Haste makes waste is the only explanation I can offer in that I failed to double check my directive. Sheesshh, sorry.
[INDENT][INDENT]any who

[INDENT][INDENT][INDENT]setting pretty now ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by von Corax on 2015-06-21
It took me a while to notice that every time I ran apt-get update it  would launch Update Manager in the background. I tried apt-get upgrade  again an hour or so later and got "0 updates available; 0 updates  installed."

It seems my problem has been solved (if, perhaps, not completely identified) and so I proffer my thanks and appreciation.

---

### Post by Bashing-om on 2015-06-21
von Corax; Great !


I too regret we did not determine that underlying causation, But OH well - I will poke at it in another time and place.
I do wish happy trails to you ;

[INDENT][INDENT]we go on about our merry way
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-26
Bashing-Om, please excuse my absence from the thread I started here.  Four months of remodeling at my farm left me without this computer -- using only my iPhone.  Since getting use of it back, I've followed all through this thread and tried everything, step-by-step.  I was finally able to get the zillion megs of updates to go through, for no apparent reason.  That left me with just the latest Ubuntu Base update of about 21 megs.  However, the unauthenticated public key issue has again raised its ugly head and the OS again won't update.  Going back through the thread, I started from scratch and eventually came to this info, in response to the command regarding "for r in /var/lib/apt/lists/*Release"  Woudl you mind looking at it and giving me some ideas?
> stephen@stephen-desktop:~$ for r in /var/lib/apt/lists/*Release; do if ! gpgv --keyring /etc/apt/trusted.gpg $r; then echo "error: $? Problem with $r"; fi; done
gpgv: no valid OpenPGP data found.
gpgv: the signature could not be verified.
Please remember that the signature file (.sig or .asc)
should be the first file given on the command line.
error: 0 Problem with /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_Release
gpgv: Signature made Thu 22 Oct 2015 03:18:53 AM EDT using DSA key ID 437D05B5
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpgv: Signature made Thu 22 Oct 2015 03:18:53 AM EDT using RSA key ID C0B21F32
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
gpgv: no valid OpenPGP data found.
gpgv: the signature could not be verified.
Please remember that the signature file (.sig or .asc)
should be the first file given on the command line.
error: 0 Problem with /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty_Release
gpgv: Signature made Mon 26 Oct 2015 11:08:09 AM EDT using DSA key ID 437D05B5
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpgv: Signature made Mon 26 Oct 2015 11:08:09 AM EDT using RSA key ID C0B21F32
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
gpgv: Signature made Mon 26 Oct 2015 02:12:13 PM EDT using DSA key ID 437D05B5
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpgv: Signature made Mon 26 Oct 2015 02:12:13 PM EDT using RSA key ID C0B21F32
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
gpgv: no valid OpenPGP data found.
gpgv: the signature could not be verified.
Please remember that the signature file (.sig or .asc)
should be the first file given on the command line.
error: 0 Problem with /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_Release
gpgv: Signature made Fri 23 Oct 2015 09:50:07 AM EDT using RSA key ID EEA14886
gpgv: Can't check signature: public key not found
error: 0 Problem with /var/lib/apt/lists/ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_trusty_InRelease


---

### Post by StephenG on 2015-10-26
Although there are several lines that begin with "error" they seem to indicate zero errors, with the notable exception of the lane near the end that there is no public key found for the signature of key EEA14886.  I don't find that key anywhere in any other query.  Sign me "Stumped.  Really."

---

### Post by Bashing-om on 2015-10-26
StephenG; Hey ...

still here, after all this time .
That for loop does not work out for me either:
```

sysop@1404mini:~$ for r in /var/lib/apt/lists/*Release; do if ! gpgv --keyring /etc/apt/trusted.gpg $r; then echo "error: $? Problem with $r"; fi; done
gpgv: no valid OpenPGP data found.
gpgv: the signature could not be verified.
Please remember that the signature file (.sig or .asc)
should be the first file given on the command line.
error: 0 Problem with /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_Release
gpgv: no valid OpenPGP data found.
gpgv: the signature could not be verified.
Please remember that the signature file (.sig or .asc)
should be the first file given on the command line.
error: 0 Problem with /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_Release
gpgv: no valid OpenPGP data found.
gpgv: the signature could not be verified.
Please remember that the signature file (.sig or .asc)
should be the first file given on the command line.
error: 0 Problem with /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_Release
gpgv: no valid OpenPGP data found.
gpgv: the signature could not be verified.
Please remember that the signature file (.sig or .asc)
should be the first file given on the command line.
error: 0 Problem with /var/lib/apt/lists/ftp.utexas.edu_ubuntu_dists_trusty_Release
gpgv: Signature made Fri 16 Oct 2015 07:10:11 PM CDT using DSA key ID 437D05B5
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpgv: Signature made Fri 16 Oct 2015 07:10:11 PM CDT using RSA key ID C0B21F32
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
gpgv: Signature made Mon 26 Oct 2015 10:08:09 AM CDT using DSA key ID 437D05B5
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpgv: Signature made Mon 26 Oct 2015 10:08:09 AM CDT using RSA key ID C0B21F32
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
sysop@1404mini:~$

```

I am about done for this session . let me have the time to look back over the thread . I will return to this later (AM ?)GMT-5 .See then what I can propose.

[INDENT][INDENT]security
[INDENT][INDENT][INDENT]a thing indeed
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-26
Am happy to rerun any and all commands and post the results, if need be.  Really am stumped as to why I was able suddenly to get all those past updates to take, but then get left with the same old problem.

---

### Post by Bashing-om on 2015-10-26
StephenG; Hey ..

Let's have a fresh look at what the package manager thinks.
Post back:
```

sudo apt update
sudo apt upgrade

```

we work our way back from that .

[INDENT][INDENT]all in some process
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-26
Part 1
```
stephen@stephen-desktop:~$ sudo apt update
[sudo] password for stephen: 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease [64.4 kB]             
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports InRelease [64.5 kB]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease                         
Get:3 [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg [933 B]                  
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages/DiffIndex        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages/DiffIndex               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports InRelease                       
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease [64.4 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease                        
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg [933 B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages/DiffIndex
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en [309 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_US              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                      
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en [6,148 B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en [3,569 B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en [171 kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse i386 Packages/DiffIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse i386 Packages/DiffIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release     
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [617 kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.1 kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages [325 kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages [12.1 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse i386 Packages        
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main i386 Packages [338 kB]   
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted i386 Packages [12.2 kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe i386 Packages [117 kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse i386 Packages [3,846 B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages/DiffIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages/DiffIndex        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages/DiffIndex          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages/DiffIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_US                
Fetched 2,124 kB in 12s (168 kB/s)                                             
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
```

Since I'm not running any RAID on this machine, I don't understand the two error messages regarding it.

Part 2
```
stephen@stephen-desktop:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  wine-gecko2.21 wine-mono0.0.8
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-headers-3.13.0-66 linux-headers-3.13.0-66-generic
  linux-image-3.13.0-66-generic linux-image-extra-3.13.0-66-generic
The following packages will be upgraded:
  linux-generic linux-generic-pae linux-headers-generic
  linux-headers-generic-pae linux-image-generic linux-image-generic-pae
6 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 61.4 MB of archives.
After this operation, 223 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  linux-image-3.13.0-66-generic linux-generic-pae linux-image-generic-pae
  linux-image-extra-3.13.0-66-generic linux-generic linux-image-generic
  linux-headers-generic-pae linux-headers-3.13.0-66
  linux-headers-3.13.0-66-generic linux-headers-generic
Install these packages without verification? [y/N] y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main linux-image-3.13.0-66-generic i386 3.13.0-66.108 [14.7 MB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main linux-generic-pae i386 3.13.0.66.72 [1,746 B]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main linux-image-generic-pae i386 3.13.0.66.72 [1,746 B]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main linux-image-extra-3.13.0-66-generic i386 3.13.0-66.108 [37.1 MB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main linux-generic i386 3.13.0.66.72 [1,782 B]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main linux-image-generic i386 3.13.0.66.72 [2,384 B]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-generic-pae i386 3.13.0.66.72 [1,750 B]
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-3.13.0-66 all 3.13.0-66.108 [8,872 kB]
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-3.13.0-66-generic i386 3.13.0-66.108 [698 kB]
Get:10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main linux-headers-generic i386 3.13.0.66.72 [2,374 B]
Fetched 61.4 MB in 3min 8s (326 kB/s)                                          
Selecting previously unselected package linux-image-3.13.0-66-generic.
(Reading database ... 630861 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-66-generic_3.13.0-66.108_i386.deb ...
Done.
Unpacking linux-image-3.13.0-66-generic (3.13.0-66.108) ...
Preparing to unpack .../linux-generic-pae_3.13.0.66.72_i386.deb ...
Unpacking linux-generic-pae (3.13.0.66.72) over (3.13.0.52.59) ...
Preparing to unpack .../linux-image-generic-pae_3.13.0.66.72_i386.deb ...
Unpacking linux-image-generic-pae (3.13.0.66.72) over (3.13.0.52.59) ...
Selecting previously unselected package linux-image-extra-3.13.0-66-generic.
Preparing to unpack .../linux-image-extra-3.13.0-66-generic_3.13.0-66.108_i386.deb ...
Unpacking linux-image-extra-3.13.0-66-generic (3.13.0-66.108) ...
Preparing to unpack .../linux-generic_3.13.0.66.72_i386.deb ...
Unpacking linux-generic (3.13.0.66.72) over (3.13.0.52.59) ...
Preparing to unpack .../linux-image-generic_3.13.0.66.72_i386.deb ...
Unpacking linux-image-generic (3.13.0.66.72) over (3.13.0.52.59) ...
Preparing to unpack .../linux-headers-generic-pae_3.13.0.66.72_i386.deb ...
Unpacking linux-headers-generic-pae (3.13.0.66.72) over (3.13.0.52.59) ...
Selecting previously unselected package linux-headers-3.13.0-66.
Preparing to unpack .../linux-headers-3.13.0-66_3.13.0-66.108_all.deb ...
Unpacking linux-headers-3.13.0-66 (3.13.0-66.108) ...
Selecting previously unselected package linux-headers-3.13.0-66-generic.
Preparing to unpack .../linux-headers-3.13.0-66-generic_3.13.0-66.108_i386.deb ...
Unpacking linux-headers-3.13.0-66-generic (3.13.0-66.108) ...
Preparing to unpack .../linux-headers-generic_3.13.0.66.72_i386.deb ...
Unpacking linux-headers-generic (3.13.0.66.72) over (3.13.0.52.59) ...
Setting up linux-image-3.13.0-66-generic (3.13.0-66.108) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-51-generic
Found initrd image: /boot/initrd.img-3.13.0-51-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
ERROR: sil: wrong # of devices in RAID set "sil_aeaibgcecefb" [1/2] on /dev/sdb
done
Setting up linux-image-extra-3.13.0-66-generic (3.13.0-66.108) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-51-generic
Found initrd image: /boot/initrd.img-3.13.0-51-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
ERROR: sil: wrong # of devices in RAID set "sil_aeaibgcecefb" [1/2] on /dev/sdb
done
Setting up linux-image-generic (3.13.0.66.72) ...
Setting up linux-headers-3.13.0-66 (3.13.0-66.108) ...
Setting up linux-headers-3.13.0-66-generic (3.13.0-66.108) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
Setting up linux-headers-generic (3.13.0.66.72) ...
Setting up linux-generic (3.13.0.66.72) ...
Setting up linux-generic-pae (3.13.0.66.72) ...
Setting up linux-image-generic-pae (3.13.0.66.72) ...
Setting up linux-headers-generic-pae (3.13.0.66.72) ...

```

After running the two commands (above), the latest update "took" for no apparent reason and now when I run the updater, it says the computer is up-to-date.  I guess I'll not know whether whatever it was is cured until the next update comes out.  Then, if it runs without all the system gyrations I've been through for the past four months, I'll think it's fixed (itself?!?).  Meantime, if you spot something suspicious, please let me know.

Thanks for your time and efforts throughout the thread.

Stephen

I forgot the proper protocol and thought I'd done it right.  I'll make more sure in the future.  Thank you for the reminder.

---

### Post by QIII on 2015-10-26
@StephenG:

Please use code tags to include commands issued in the terminal and their results:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by Bashing-om on 2015-10-26
StephenG; Maybe;

We are out of the woods ..
I am tired and have had it for this session. Got a bit of research and think'n to do on this yet.
We then check that certain directories and files exists and run another check.

I will return.

[INDENT][INDENT]it is a process
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-10-27
StephenG; Morning;

Did refreshing the data-base fix ?
What now returns:
```

sudo apt-key update

```

[INDENT][INDENT]we see then
[INDENT][INDENT][INDENT]what tale gets told
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-27
I forgot the proper protocol and thought I'd done it right.  I'll make more sure in the future.  Thank you for the reminder.

```
stephen@stephen-desktop:~$ sudo apt-key update
[sudo] password for stephen: 
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4

```

However, when I run apt-get update, following the million lines of info, I get this same result as before, and I am still very baffled:

```
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32

```

Have I got the server address wrong somewhere somehow?  Set to access the wrong server -- maybe one that's been abandoned again?

---

### Post by Bashing-om on 2015-10-27
StephenG; Yeah ;

Tis a puzzle ... " apt-key update" says there is no problem .Let's say, as one reason, apt's control files are corrupted;
What results when they are removed and rebuilt ?
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```

else, well
[INDENT][INDENT][INDENT]we can get the more aggressive
[/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-27
First two worked fine.  AS soon as I entered the update command, I got the SOSO:

```
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
```

And for the upgrade command, I get, in part, this warning, just as I did when it finally decided to do the major update earlier.:

```
WARNING: The following packages cannot be authenticated!
  ntpdate python3-problem-report python3-apport apport apport-gtk
  python-problem-report python-apport
Install these packages without verification? [y/N] y
```

By simply telling it to override the objections, it seems to do the update/upgrade.  I'm guessing I have something amiss in the Update Manager code, though I've carefully checked and rechecked the settings and they all seem fine to me.

---

### Post by Bashing-om on 2015-10-27
StephenG; Ummphhh ..

Apparently the problem is deeper, presently I do not know how to isolate.
Maybe we can poke at it .. as I do not presently know a better thing to do .
```

gpg --keyserver keyserver.ubuntu.com --recv 16126D3A3E5C1192
gpg --export --armor 16126D3A3E5C1192 | sudo apt-key add -

```
to add it to your local keyring .

See if this procedure is permanent for this one key . If it is repeat for the other 2 keys ?

[INDENT][INDENT]for lack of a better course
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-27
It looks like the key gets imported fine:

```
stephen@stephen-desktop:~$ gpg --keyserver keyserver.ubuntu.com --recv 16126D3A3E5C1192
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: public key "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
stephen@stephen-desktop:~$ gpg --export --armor 16126D3A3E5C1192 | sudo apt-key add -
[sudo] password for stephen: 
OK
```

But when I then run update again, I get the same error message as earlier (along with similar error messages for all the other keys):

```
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
```

How can I be sure I've got the right server listed as the one to access for these keys?  I keep running across posts mentioning older server addresses that are no longer active?

It also seems as though someone from the Ubuntu team could let me know if I'm using, somehow, an outdated public key or of there's a different public key available.  After all, as I said when I started my portion of this discussion, this issue only reared its ugly head when I tried to do the update in May.  Prior to that, as in within days earlier, everything worked fine and all updates were non-problematic.  Almost as though there was a bad line of code in that update that miscued the public key-ring.

---

### Post by Bashing-om on 2015-10-27
StephenG; Hey !

You may have something here ! 
What is in your sources.list ?
```

cat /etc/apt/sources.list

```

Now that is a ->
[INDENT][INDENT][INDENT]thought
[/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-27
Return to Sources query, and I have absolutely no idea why there would be any references left behind to Precise nor to gscan2pdf, even though they've been commented out:

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu trusty universe
deb http://archive.ubuntu.com/ubuntu trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu trusty multiverse
deb http://archive.ubuntu.com/ubuntu trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu trusty-security main restricted
deb http://archive.ubuntu.com/ubuntu trusty-security universe
deb http://archive.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu trusty main

##  This is the gscan2pdf application updater
```

Another response, slightly different query, in case it helps.  Again, I have no idea why there are any references to fuzebox (which I uninstalled years ago), nor to Wine of the Precise version rather than of the Trusty version:


```
stephen@stephen-desktop:~$ ls /etc/apt/sources.list.d/*.list/etc/apt/sources.list.d/ehoover-compholio-trusty.list
/etc/apt/sources.list.d/fuzebox.list
/etc/apt/sources.list.d/mqchael-pipelight-trusty.list
/etc/apt/sources.list.d/pipelight-stable-trusty.list
/etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list
```

---

### Post by Bashing-om on 2015-10-27
StephenG; Well ..

so much for that thought, you are are on a current and supported release.

As to the source fetches in /etc/apt/sources.list.d/ ;
so long as they are active, they are active.

fuzebox maybe a serious problem .. no longer supported ? Maybe yes ! as one source of the GPG errors . I can not get the URL to resolve for me.
As to how we are going to get it off the system, now that is a horse of another color . We may have a problem.

and concur " /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list " needs to be reverted and this PPA removed. Another possibe soutse of errors. As Wine is now supported in our repo, I bet this PPA has also been discontinued .

while at it may as well check all these PPAs and make sure they are supported;
```

cat /etc/apt/sources.list.d/*.list

``` whose outputs will have the URLs to check from.


But, yeah, let us fix these PPAs and see then what the GPG situation is .

[INDENT][INDENT][INDENT]you do good work
[/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-27
Well, I used to be VERY comfortable with DOS command line stuff -- probably because I had a great DOS manual with instructions and examples of all the commands and all their switches.  I have yet to find such a thing for Linux and feel very lost most of the time.  That said, if you are expecting me to know how to "revert the PPA" or otherwise rid myself of the fuzebox trash, you're probably mistaken.  I will, no doubt, need some step-by-steps on those items.  Meanwhile ...

```
stephen@stephen-desktop:~$ cat /etc/apt/sources.list.d/*.list
deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu trusty main
```

---

### Post by Bashing-om on 2015-10-27
StephenG; Yeah ... 

I do feel your frustration for lack of a nice concise one-size-fits manual .  Takes a bit to put the pieces together for sure.
There is no substitute for the on-system manual of commands and installed applications.
```

man <command>

```
can help a bunch.

As to our present sloppyation . We may have our work cut out for us as there maybe no means to utilize package management tools to get us out of this,

We start by looking at what is installed and get the URL as a place to start.
oopps .. Ya remove the PPAs from /etc/apt/sources.list.d/ ?
```

tail -v -n +1 /etc/apt/sources.list.d/*

```

[INDENT][INDENT]Houston
[INDENT][INDENT][INDENT]is there a problem
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-27
OK, so I'm not exactly sure what you just had me do, not what I'm looking at, but ...

```
stephen@stephen-desktop:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/ehoover-compholio-trusty.list <==

==> /etc/apt/sources.list.d/ehoover-compholio-trusty.list.save <==

==> /etc/apt/sources.list.d/fuzebox.list <==

==> /etc/apt/sources.list.d/fuzebox.list.save <==

==> /etc/apt/sources.list.d/mqchael-pipelight-trusty.list <==

==> /etc/apt/sources.list.d/mqchael-pipelight-trusty.list.save <==

==> /etc/apt/sources.list.d/pipelight-stable-trusty.list <==

==> /etc/apt/sources.list.d/pipelight-stable-trusty.list.save <==

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list <==

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.distUpgrade <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save <==

==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list.save <==
deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu trusty main

```

Actually, a good substitute would be a hard-copy of the manual, you know about 7 or 8 hundred pages long, that I could thumb through as I lie in bed in the evening, highlighting and studying the various commands that I thought I might be able to use tomorrow when I'm experimenting with the OS.

Interestingly, I ran the Y-PPA Manager and when I asked it to deal with duplicate PPAs, I got this message (here's a screen shot) so I've not done anything until you see it and advise.

[IMG]/home/stephen/Pictures/Screenshot from 2015-10-27 23:35:29.png[/IMG]

well, that didn't work. Let me try something else to get the screen shot to you

---

### Post by QIII on 2015-10-27
Hello!

To attach an image in line, use the "paper clip" icon in the tool bar above the text input box.

Cheers.

---

### Post by StephenG on 2015-10-27
Can't seem to get the screen shot to download to the message.  Anyway, I told Y-PPA to go ahead and discard the duplicate PPAs.

Thank you.

Jeez.  Just got the same old dern untrusted sources error message when I tried to do the suggested updates through the regular updater icon.  WTH is going on???

I just found this thread and wonder if you think this set of commands might do the trick.  I don't like to run unknown commands without some second opinion.

[http://askubuntu.com/questions/677939/w-gpg-error-and-warning-the-following-packages-cannot-be-authenticated?lq=1](http://askubuntu.com/questions/677939/w-gpg-error-and-warning-the-following-packages-cannot-be-authenticated?lq=1)

I also ran across this file and wonder if it's what's causing the trouble.  What concerns me are all the references to Precise.  It's at /etc/apt/sources.list.d and is named: sources.list.distUpgrade

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

##  This is the gscan2pdf application updater
deb http://ppa.launchpad.net/jeffreyratcliffe/ubuntu precise main
deb-src http://ppa.launchpad.net/jeffreyratcliffe/ubuntu precise main
```

---

### Post by Bashing-om on 2015-10-28
StephenG; Well ...

At this point we have to get rid of those old PPA's that no longer have support. Get them off the system. Now that is much easier said than done.
Particularly so is the original URL is no longer available. I am loosing sleep trying to figure out a way around it and keep the system in a consistent state.

As to removing and repopulating the .gpg directory; Nope not going to advocate that action.

@QIII ; Sure glad you continue to look over our shoulders .

We now have to remove anything not needed that could interfere with proper authentication of received software. My present concern is " ehoover-compholio-trusty.list . I will do the homework, see if there is a possibility to re-install the PPA and then maybe ppa-purge ? - to revert installed softwares back to what is in our repository.

Be advised I think in small steps .. A, B, C, to arrive at point D .

Learning; there are lots and lots of resources on-line:
[http://ubuntuhandbook.org/](http://ubuntuhandbook.org/)
[http://ubuntuguide.org/wiki/Ubuntu_Trusty](http://ubuntuguide.org/wiki/Ubuntu_Trusty) <-The ubuntu_guide
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)
[http://ubuntu-manual.org/downloads](http://ubuntu-manual.org/downloads)
[http://www.itworld.com/operating-systems/347533/ubuntu-guide-displaced-windows-users](http://www.itworld.com/operating-systems/347533/ubuntu-guide-displaced-windows-users)
To name but a few I found useful .
[INDENT]books:
[INDENT][http://search.oreilly.com/?q=linux](http://search.oreilly.com/?q=linux) <-Books, anything linux ![/INDENT][/INDENT]


Anyway, this is my thought - get rid of the old PPAs -
[INDENT][INDENT][INDENT]and I am sticking to it
[/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-28
I have explored the .gpg folder and there are only three files there -- one named fuzebox.gpg (which I am happy to delete since I deleted the program long ago) and two other files (I can't open either of them) -- pipelight-stable.gpg and webupd8team-y-ppa-manager.gpg.  All the info I've found on the issue indicates that one of the problems is if there are more than 40 keys in the gpg file.  It looks like that is certainly not the case here, unless they are stored elsewhere than this directory.  Thoughts?

Bashing-Om, I understand your reluctance to delete the trusted.gpg file , but ... when I opened it just to see what I might see, the first thing that caught my eye was the warning at the top of the window, that the file couldn't be properly opened since it contained some "invalid characters."  Not sure what that's telling me.  I'm attaching a screen shot.

---

### Post by Bashing-om on 2015-10-28
StephenG; Hello;

I do not think you can be anywhere near that 40 key limit for the number of keyrings.
You can check with:
```

ls /etc/apt/trusted.gpg.d | wc -l

```

As to  "trusted.gpg file" : That file contains sensitive information and is encrypted. Only the system resources can read and manipulate that file.

Just one of the reasons
[INDENT][INDENT]linux is so secure
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-28
returned the number 5

returned the number 5

Do you mean a copy from prior to the May update when it all went haywire?  If so, I wouldn't know where to find it.

Is this any help?  Should we be deleting some of these 0-byte files?

---

### Post by Bashing-om on 2015-10-28
StephenG; Yep ...

Good there . So,

We are back to those old PPA's . Still researching what and in what order we can do ... 
Ya got a backup copy on your system of the old /etc/apt/sources.list.d/ directory ? Would make things a lot easier if we had those URL's .

Messy enough
[INDENT][INDENT][INDENT]as it is
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-10-28
StephenG; Welp ...

If you do not know that you have a backup of that directory ..then it is a safe bet it does not exist.
But will only take a sec to check and hope ->
```

ls -al /etc/apt/sources.list.d/

```
and refresh the mind on what we might have to work with.

[INDENT][INDENT]not looking forward to this
[INDENT][INDENT][INDENT]with any pleasure in mind
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-28
```
stephen@stephen-desktop:~$ ls /etc/apt/sources.list.d/*.list/etc/apt/sources.list.d/pipelight-stable-trusty.list
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list
stephen@stephen-desktop:~$ ls -al /etc/apt/sources.list.d/
total 20
drwxr-xr-x 2 root root 4096 Oct 27 23:41 .
drwxr-xr-x 6 root root 4096 Oct 26 19:18 ..
-rw-r--r-- 1 root root    0 Jan  2  2015 ehoover-compholio-trusty.list.save
-rw-r--r-- 1 root root    0 May 19 16:49 fuzebox.list.save
-rw-r--r-- 1 root root    0 Jan  2  2015 mqchael-pipelight-trusty.list.save
-rw-r--r-- 1 root root    0 May 19 16:47 pipelight-stable-trusty.list
-rw-r--r-- 1 root root    0 May 19 16:47 pipelight-stable-trusty.list.save
-rw-r--r-- 1 root root  134 Aug 12  2014 ubuntu-wine-ppa-precise.list.distUpgrade
-rw-r--r-- 1 root root    0 May 11 12:08 ubuntu-wine-ppa-precise.list.save
-rw-r--r-- 1 root root   74 Oct 28 10:31 webupd8team-y-ppa-manager-trusty.list
-rw-r--r-- 1 root root   76 Oct 28 10:31 webupd8team-y-ppa-manager-trusty.list.save

```

I did just find a directory named "repositories.backup-2015-05-20-1058.tar.gz"

Is that any help?  The files within it contain URLs for various PPAs, it seems.  Well, at least the non-zero size ones do.  There are about a half-dozen or more 0-size files.

---

### Post by Bashing-om on 2015-10-28
StephenG; Yeah,

As we go we will clean up that directory behind us .. 0 bytes == no info .

I am still at ehoover-compholio. I do have a semi so plan, still working it out.

And a couple of thoughts on the others .. I am not in despair, yet .

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-28
Just kind of wondering if there's an instruction somewhere telling the updater to go find those files for the PPA source information and it's getting stuck since the files are empty.  As I've said, Linux is still somewhat a mystery to me.

Trusty old Google, just let me know that ehoover-compholio is for a Netflix app.  Which I do not use.  I suppose we could stop thinking about it and simply delete it, for starters.

---

### Post by Bashing-om on 2015-10-28
StephenG; Hey;

I wish :
> 
I suppose we could stop thinking about it and simply delete it, for starters.

it were just that simple. We have to remove the files that the PPA installed and/or revert these to what is in the repo to remain compatible with the versions installed on the operating system. We also must keep the package manager happy.

I do consider what we have here is the system is attempting to fetch files requiring the be authenticated .. and as the PPA's are non-existent .. the authentication fails and we get GPG errors . ( the keys we know are on the system )

In my thought process this probability must be eliminated. And besides .. we need to clean the system up anyway !
And I be a work'n on it .

[INDENT][INDENT]oh Boy 
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-28
Does Ubuntu have an install file(s) somewhere that registers all the changes a particular install performs?  Or is there a command to scrub the file system of all mentions of a particular abandoned or uninstalled program?  Like an orphan finder?  If I thought it was possible to dump and reinstall a clean version of 14.04 without losing any data or other files, I'm happy to do that.  As it is, I leave in the early morning for 6 days in Texas to visit family and I'll be off this machine for that time period.  So, please don't kill yourself on my account ... at least not until next Wednesday ;-))

---

### Post by Bashing-om on 2015-10-28
StephenGl Hey ...

I am flexible .. we work this at your pace .. ( I have plenty to keep me occupied 'till ya return) .
Presently I know we are going to RE-install ehoover/compholio and then purge it .. Now I have some "hints" that when we purge this PPA it will also take care of both netflix and pipelight - with the exception of a few desktop files - ... but I am not "SURE" ... Still doing the homework here to find out what is going to happen before we encounter it as a shock.

It has already been this long, a few days longer will be alright too . 

> 
Does Ubuntu have an install file(s) somewhere that registers all the changes a particular install performs?

Nope not exactly ... but there are means. When you know what you are looking for .

> 
Or is there a command to scrub the file system of all mentions of a particular abandoned or uninstalled program? Like an orphan finder?

yep, and we will when we get to that point .

I keep plugging away at this.

[INDENT][INDENT]progress made slowly
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-10-28
I certainly wish I knew enough more that I could actually ask questions, or make suggestions, that moved the ball forward rather than just sounding stoopid.  Since I've been using Ubuntu since version 6 or 7, I should oughta know some of this stuff, but it seems the only time I ever learn anything is when I get stuck and come here for help.  I suppose that's the difference between a 25 year old (when I began messing with and understanding DOS) and a 65 year old (when I'm retired to my farm and can't stay up half the night messing with OSs).

---

### Post by Bashing-om on 2015-10-28
StephenG; Hey !

That is not fair ! 
I am a retired 65 year old - living on the farm that has supported us for 30 years .. and here is where i do spend my time ... I rest at night when my eyes cross and my mind ceases to function reliably .
I have been - and continue to do so - messing with computers since the late '60's . Hope to continue for 60 or so more years .

[INDENT][INDENT]12 tabs open on ehoover/compholio
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-29
Bashing-Om, are you still there?  I'm still unable to figure this out, despite hours and hours of following threads and leads on this forum.

---

### Post by Bashing-om on 2015-11-29
StephenG; Hey, Yeah ...

Still here and hang'n on .

Let us get a fresh look at the situation:
Post back .
```

sudo apt-get update
sudo apt-get upgrade

```
and a new look at what the system is fetching:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

[INDENT][INDENT]and here we go again
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-29
I just did the upgrade and it manages to upgrade everything but the linux headers (and associated 6 or 7 files).  Will post other results momentarily.

```
stephen@stephen-desktop:~$ sudo apt-get update
Hit http://ppa.launchpad.net trusty InRelease
Ign http://archive.ubuntu.com trusty InRelease
Ign http://archive.canonical.com trusty InRelease                       
Get:1 http://archive.ubuntu.com trusty-updates InRelease [64.4 kB]      
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:2 http://archive.canonical.com trusty Release.gpg [933 B]                  
Hit http://archive.canonical.com trusty Release                                
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://archive.canonical.com trusty Release                                
Ign http://archive.canonical.com trusty/partner i386 Packages/DiffIndex
Ign http://archive.ubuntu.com trusty-updates InRelease                     
Get:3 http://archive.ubuntu.com trusty-security InRelease [64.4 kB]        
Hit http://archive.canonical.com trusty/partner Translation-en
Hit http://archive.canonical.com trusty/partner i386 Packages
Ign http://archive.ubuntu.com trusty-security InRelease                       
Get:4 http://archive.ubuntu.com trusty Release.gpg [933 B]
Ign http://archive.ubuntu.com trusty-updates/main i386 Packages/DiffIndex
Ign http://archive.canonical.com trusty/partner Translation-en_US
Hit http://archive.ubuntu.com trusty-updates/main Translation-en
Ign http://archive.ubuntu.com trusty-security/main i386 Packages/DiffIndex
Hit http://archive.ubuntu.com trusty-security/main Translation-en
Hit http://archive.ubuntu.com trusty Release        
Ign http://archive.ubuntu.com trusty Release         
Hit http://archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://archive.ubuntu.com trusty-security/main i386 Packages
Ign http://archive.ubuntu.com trusty/main i386 Packages/DiffIndex
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/main i386 Packages
Ign http://archive.ubuntu.com trusty-updates/main Translation-en_US
Ign http://archive.ubuntu.com trusty-security/main Translation-en_US
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Fetched 131 kB in 3s (36.8 kB/s)
Reading package lists... Done
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
```

```
stephen@stephen-desktop:~$ sudo apt-get upgrade
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libnspr4 linux-generic linux-generic-pae linux-headers-generic
  linux-headers-generic-pae linux-image-generic linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```

```
stephen@stephen-desktop:~$ cat -n /etc/apt/sources.list
     1	
     2	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     3	# newer versions of the distribution.
     4	deb http://archive.ubuntu.com/ubuntu trusty main
     5	
     6	## Major bug fix updates produced after the final release of the
     7	## distribution.
     8	deb http://archive.ubuntu.com/ubuntu trusty-updates main
     9	
    10	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    11	## team. Also, please note that software in universe WILL NOT receive any
    12	## review or updates from the Ubuntu security team.
    13	
    14	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    15	## team, and may not be under a free licence. Please satisfy yourself as to 
    16	## your rights to use the software. Also, please note that software in 
    17	## multiverse WILL NOT receive any review or updates from the Ubuntu
    18	## security team.
    19	
    20	## N.B. software from this repository may not have been tested as
    21	## extensively as that contained in the main release, although it includes
    22	## newer versions of some applications which may provide useful features.
    23	## Also, please note that software in backports WILL NOT receive any review
    24	## or updates from the Ubuntu security team.
    25	
    26	deb http://archive.ubuntu.com/ubuntu trusty-security main
    27	
    28	## Uncomment the following two lines to add software from Canonical's
    29	## 'partner' repository.
    30	## This software is not part of Ubuntu, but is offered by Canonical and the
    31	## respective vendors as a service to Ubuntu users.
    32	deb http://archive.canonical.com/ubuntu trusty partner
    33	# deb-src http://archive.canonical.com/ubuntu trusty partner
    34	
    35	## This software is not part of Ubuntu, but is offered by third-party
    36	## developers who want to ship their latest software.
    37	# deb http://extras.ubuntu.com/ubuntu trusty main
    38	# deb-src http://extras.ubuntu.com/ubuntu trusty main
    39	
    40	##  This is the gscan2pdf application updater
```

```
stephen@stephen-desktop:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/ehoover-compholio-trusty.list.save <==

==> /etc/apt/sources.list.d/fuzebox.list.save <==

==> /etc/apt/sources.list.d/mqchael-pipelight-trusty.list.save <==

==> /etc/apt/sources.list.d/pipelight-stable-trusty.list <==

==> /etc/apt/sources.list.d/pipelight-stable-trusty.list.save <==

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.distUpgrade <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save <==

==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list.save <==
# deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu trusty main
```

Still faced with getting rid of the fuzebox all together, and either updating the WINE source or getting rid of it and reinstalling proper version.

---

### Post by Bashing-om on 2015-11-29
StephenG; Hey;

Think'n and alook'n ...

Yeah, for sure we have to address:
> 
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) [color=blue]precise[/color] main

get off that 12.04 release and up on trusty.

I be back .. seeking a best way forward.

[INDENT][INDENT][INDENT]all in knowing how
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-11-29
StephenG; Ho Kay ...

I am making little headway on fuze ... seems it is no longer in existence (??).

A focus on Wine then .. Let's us see IF we can revert the PPA to the package from our repo:
what returns:
```

apt-cache policy wine

```
so we jave an idea of what we are wotking with.

And now see if we can get to the repo package version:
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-wine/ppa

```

Once we have wine and fuze taken care of such that the GPG keys are in order, then we get those "0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded."  new kernel installed.

[INDENT][INDENT]one issue at a time
[INDENT][INDENT][INDENT]what my little mind can cope with
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-29
```
stephen@stephen-desktop:~$ apt-cache policy wine
wine:
  Installed: (none)
  Candidate: (none)
  Version table:

```

```
stephen@stephen-desktop:~$ sudo apt-get install ppa-purge
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ppa-purge is already the newest version.
ppa-purge set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded


stephen@stephen-desktop:~$ sudo ppa-purge ppa:ubuntu-wine/ppa
Updating packages lists
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
PPA to be removed: ubuntu-wine ppa
Warning:  Could not find package list for PPA: ubuntu-wine ppa

```

I do find this file when I search for fuzebox:

```
--2015-05-07 21:18:40--  http://apt.fuzebox.com/apt/keyring.gpg
Resolving apt.fuzebox.com (apt.fuzebox.com)... 206.81.183.53
Connecting to apt.fuzebox.com (apt.fuzebox.com)|206.81.183.53|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1199 (1.2K) [application/octet-stream]
Saving to: ‘keyring.gpg.1’

     0K .                                                     100% 65.6M=0s

2015-05-07 21:18:40 (65.6 MB/s) - ‘keyring.gpg.1’ saved [1199/1199]

```

---

### Post by Bashing-om on 2015-11-29
StephenG; Welp;

System does not think Wine is installed; let's see what files remain on the system:
```

sudo find / -name "wine*"

```
Then decide what we are going to do .

Still do not know what to do about fuzebox . Recon we will get to that directly.


[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-29
/usr/bin/wine

---

### Post by Bashing-om on 2015-11-29
StephenG; Well !

Not much installed huh ?

Still want to see what the package manager can/will do.
Can we get a real file name for wine ? What returns:
```

ls -al /usr/bin/wine
ls -al /var/lib/dpkg/info/wine*.list

```

as it is never nice to fool mother package manager

---

### Post by StephenG on 2015-11-29
stephen@stephen-desktop:~$ ls -al /usr/bin/wine
-rwxr-xr-x 1 root root 9748 Apr  4  2014 /usr/bin/wine


stephen@stephen-desktop:~$ ls -al /var/lib/dpkg/info/wine*.list
-rw-r--r-- 1 root root 58622 Oct 26 22:45 /var/lib/dpkg/info/wine1.6-i386.list
-rw-r--r-- 1 root root  7410 Oct 26 22:45 /var/lib/dpkg/info/wine1.6.list
-rw-r--r-- 1 root root     0 Oct 26 22:38 /var/lib/dpkg/info/wine-browser-installer.list
-rw-r--r-- 1 root root   275 Oct 26 22:45 /var/lib/dpkg/info/wine-gecko2.21:i386.list
-rw-r--r-- 1 root root   307 Oct 26 22:45 /var/lib/dpkg/info/wine-mono0.0.8.list
-rw-r--r-- 1 root root     0 Oct 26 22:38 /var/lib/dpkg/info/wine-silverlight5.1-installer.list
-rw-r--r-- 1 root root   764 Oct 26 22:45 /var/lib/dpkg/info/winetricks.list

Hold the phone, sir.  I forgot the * in the find wine command.  I will send the real return after it completes.  ;-)) Sorry ...

```
stephen@stephen-desktop:~$ sudo find / -name "wine*"
[sudo] password for stephen: 
/usr/bin/winetricks
/usr/bin/winefile
/usr/bin/wineg++
/usr/bin/wineconsole
/usr/bin/winecpp
/usr/bin/winepath
/usr/bin/wine
/usr/bin/wine-preloader
/usr/bin/winegcc
/usr/bin/winecfg
/usr/bin/winebuild
/usr/bin/wineboot
/usr/bin/wine-auto
/usr/bin/winedbg
/usr/bin/winemine
/usr/bin/winemaker
/usr/bin/wineserver
/usr/bin/winedump
/usr/share/winetricks
/usr/share/winetricks/icons/hicolor/scalable/apps/winetricks.svg
/usr/share/applications/wine-browsedrive.desktop
/usr/share/applications/wine-notepad.desktop
/usr/share/applications/winetricks.desktop
/usr/share/applications/wine.desktop
/usr/share/applications/wine-uninstaller.desktop
/usr/share/applications/wine-winecfg.desktop
/usr/share/icons/hicolor/22x22/apps/wine.png
/usr/share/icons/hicolor/22x22/apps/wine-uninstaller.png
/usr/share/icons/hicolor/22x22/apps/wine-winecfg.png
/usr/share/icons/hicolor/22x22/apps/wine-notepad.png
/usr/share/icons/hicolor/32x32/apps/wine.png
/usr/share/icons/hicolor/32x32/apps/wine-uninstaller.png
/usr/share/icons/hicolor/32x32/apps/wine-winecfg.png
/usr/share/icons/hicolor/32x32/apps/wine-notepad.png
/usr/share/icons/hicolor/24x24/apps/wine.png
/usr/share/icons/hicolor/24x24/apps/wine-uninstaller.png
/usr/share/icons/hicolor/24x24/apps/wine-winecfg.png
/usr/share/icons/hicolor/24x24/apps/wine-notepad.png
/usr/share/icons/hicolor/16x16/apps/wine.png
/usr/share/icons/hicolor/16x16/apps/wine-uninstaller.png
/usr/share/icons/hicolor/16x16/apps/wine-winecfg.png
/usr/share/icons/hicolor/16x16/apps/wine-notepad.png
/usr/share/icons/hicolor/48x48/apps/wine.png
/usr/share/icons/hicolor/48x48/apps/wine-uninstaller.png
/usr/share/icons/hicolor/48x48/apps/wine-winecfg.png
/usr/share/icons/hicolor/48x48/apps/wine-notepad.png
/usr/share/icons/hicolor/scalable/apps/wine.svg
/usr/share/icons/hicolor/scalable/apps/wine-uninstaller.svg
/usr/share/icons/hicolor/scalable/apps/winetricks.svg
/usr/share/icons/hicolor/scalable/apps/wine-winecfg.svg
/usr/share/icons/oxygen/64x64/apps/wine.png
/usr/share/icons/oxygen/22x22/apps/wine.png
/usr/share/icons/oxygen/32x32/apps/wine.png
/usr/share/icons/oxygen/128x128/apps/wine.png
/usr/share/icons/oxygen/16x16/apps/wine.png
/usr/share/icons/oxygen/48x48/apps/wine.png
/usr/share/wine
/usr/share/wine/mono/wine-mono-0.0.8.msi
/usr/share/wine/wine.inf
/usr/share/wine/gecko/wine_gecko-2.21-x86.msi
/usr/share/wine/wineserver-restart-required.update-notifier
/usr/share/app-install/icons/wine.svg
/usr/share/app-install/desktop/wine1.6:wine.desktop
/usr/share/app-install/desktop/winefish:winefish.desktop
/usr/share/man/fr.UTF-8/man1/wineserver.1.gz
/usr/share/man/fr.UTF-8/man1/wine.1.gz
/usr/share/man/fr.UTF-8/man1/winemaker.1.gz
/usr/share/man/man1/winemine.1.gz
/usr/share/man/man1/winedbg.1.gz
/usr/share/man/man1/winegcc.1.gz
/usr/share/man/man1/winecpp.1.gz
/usr/share/man/man1/winecfg.1.gz
/usr/share/man/man1/wineserver.1.gz
/usr/share/man/man1/winedump.1.gz
/usr/share/man/man1/wineboot.1.gz
/usr/share/man/man1/winefile.1.gz
/usr/share/man/man1/winebuild.1.gz
/usr/share/man/man1/winetricks.1.gz
/usr/share/man/man1/wine.1.gz
/usr/share/man/man1/wineconsole.1.gz
/usr/share/man/man1/winemaker.1.gz
/usr/share/man/man1/winepath.1.gz
/usr/share/man/man1/wineg++.1.gz
/usr/share/man/pl.UTF-8/man1/wine.1.gz
/usr/share/man/de.UTF-8/man1/wineserver.1.gz
/usr/share/man/de.UTF-8/man1/wine.1.gz
/usr/share/man/de.UTF-8/man1/winemaker.1.gz
/usr/share/bash-completion/completions/wine
/usr/share/binfmts/wine
/usr/share/kde4/apps/katepart/syntax/winehq.xml
/usr/share/lintian/overrides/wine1.6
/usr/share/desktop-directories/wine-wine.directory
/usr/share/desktop-directories/wine-Programs-Accessories.directory
/usr/share/desktop-directories/wine-Programs.directory
/usr/share/doc/winetricks
/usr/share/doc/texlive-doc/support/arara/figures/winedt
/usr/share/doc/texlive-doc/support/arara/figures/winedt/winedt-optionsinterface.png
/usr/share/doc/texlive-doc/support/arara/figures/winedt/winedt-menu.png
/usr/share/doc/texlive-doc/support/arara/figures/winedt/winedt-ararabutton.png
/usr/share/doc/texlive-doc/latex/newlfm/wine.pdf
/usr/share/doc/texlive-doc/latex/newlfm/wine.eps.gz
/usr/share/doc/wine1.6
/usr/share/doc/wine-gecko2.21
/usr/share/doc/wine-mono0.0.8
/usr/share/doc/wine1.6-i386
/usr/lib/mime/packages/wine1.6
/usr/lib/i386-linux-gnu/wine
/usr/lib/i386-linux-gnu/wine/winebrowser.exe.so
/usr/lib/i386-linux-gnu/wine/winealsa.drv.so
/usr/lib/i386-linux-gnu/wine/wined3d.dll.so
/usr/lib/i386-linux-gnu/wine/winefile.exe.so
/usr/lib/i386-linux-gnu/wine/winex11.drv.so
/usr/lib/i386-linux-gnu/wine/winemenubuilder.exe.so
/usr/lib/i386-linux-gnu/wine/winedbg.exe.so
/usr/lib/i386-linux-gnu/wine/winepath.exe.so
/usr/lib/i386-linux-gnu/wine/winemsibuilder.exe.so
/usr/lib/i386-linux-gnu/wine/wineoss.drv.so
/usr/lib/i386-linux-gnu/wine/winemapi.dll.so
/usr/lib/i386-linux-gnu/wine/winepulse.drv.so
/usr/lib/i386-linux-gnu/wine/winejoystick.drv.so
/usr/lib/i386-linux-gnu/wine/wineps16.drv16.so
/usr/lib/i386-linux-gnu/wine/winegstreamer.dll.so
/usr/lib/i386-linux-gnu/wine/wineboot.exe.so
/usr/lib/i386-linux-gnu/wine/wineps.drv.so
/usr/lib/i386-linux-gnu/wine/fakedlls/winefile.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/wined3d.dll
/usr/lib/i386-linux-gnu/wine/fakedlls/wineps.drv
/usr/lib/i386-linux-gnu/wine/fakedlls/winepulse.drv
/usr/lib/i386-linux-gnu/wine/fakedlls/winemine.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/winex11.drv
/usr/lib/i386-linux-gnu/wine/fakedlls/winealsa.drv
/usr/lib/i386-linux-gnu/wine/fakedlls/winecfg.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/wineps16.drv16
/usr/lib/i386-linux-gnu/wine/fakedlls/winemp3.acm
/usr/lib/i386-linux-gnu/wine/fakedlls/winevdm.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/wineconsole.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/wineboot.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/winemapi.dll
/usr/lib/i386-linux-gnu/wine/fakedlls/winemsibuilder.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/winebrowser.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/wineoss.drv
/usr/lib/i386-linux-gnu/wine/fakedlls/winejoystick.drv
/usr/lib/i386-linux-gnu/wine/fakedlls/winedbg.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/winedevice.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/winegstreamer.dll
/usr/lib/i386-linux-gnu/wine/fakedlls/winemenubuilder.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/winepath.exe
/usr/lib/i386-linux-gnu/wine/wineconsole.exe.so
/usr/lib/i386-linux-gnu/wine/winecfg.exe.so
/usr/lib/i386-linux-gnu/wine/winedevice.exe.so
/usr/lib/i386-linux-gnu/wine/winevdm.exe.so
/usr/lib/i386-linux-gnu/wine/winemine.exe.so
/usr/lib/i386-linux-gnu/wine/winemp3.acm.so
/proc/sys/fs/binfmt_misc/wine
/home/stephen/.wine-pipelight/wine-wininet-installer.installed
/home/stephen/.wine-pipelight/wine-silverlight5.1-installer.installed
/home/stephen/.wine-pipelight/wine-mpg2splt-installer.installed
/home/stephen/.wine-pipelight/drive_c/windows/system32/winefile.exe
/home/stephen/.wine-pipelight/drive_c/windows/system32/wined3d-csmt.dll
/home/stephen/.wine-pipelight/drive_c/windows/system32/wined3d.dll
/home/stephen/.wine-pipelight/drive_c/windows/system32/wineps.drv
/home/stephen/.wine-pipelight/drive_c/windows/system32/winepulse.drv
/home/stephen/.wine-pipelight/drive_c/windows/system32/winemine.exe
/home/stephen/.wine-pipelight/drive_c/windows/system32/winex11.drv
/home/stephen/.wine-pipelight/drive_c/windows/system32/winealsa.drv
/home/stephen/.wine-pipelight/drive_c/windows/system32/winecfg.exe
/home/stephen/.wine-pipelight/drive_c/windows/system32/winemp3.acm
/home/stephen/.wine-pipelight/drive_c/windows/system32/winevdm.exe
/home/stephen/.wine-pipelight/drive_c/windows/system32/wineconsole.exe
/home/stephen/.wine-pipelight/drive_c/windows/system32/wineps16.drv
/home/stephen/.wine-pipelight/drive_c/windows/system32/wineboot.exe
/home/stephen/.wine-pipelight/drive_c/windows/system32/winemapi.dll
/home/stephen/.wine-pipelight/drive_c/windows/system32/winemsibuilder.exe
/home/stephen/.wine-pipelight/drive_c/windows/system32/winebrowser.exe
/home/stephen/.wine-pipelight/drive_c/windows/system32/winejoystick.drv
/home/stephen/.wine-pipelight/drive_c/windows/system32/winedbg.exe
/home/stephen/.wine-pipelight/drive_c/windows/system32/winedevice.exe
/home/stephen/.wine-pipelight/drive_c/windows/system32/winemenubuilder.exe
/home/stephen/.wine-pipelight/drive_c/windows/system32/winepath.exe
/home/stephen/.cache/winetricks
/home/stephen/.config/wine-wininet-installer.accept-license
/home/stephen/.config/menus/applications-merged/wine-Programs-PDF-XChange PDF Viewer-PDF-Viewer.menu
/home/stephen/.config/menus/applications-merged/wine-Programs-PDF-XChange PDF Viewer-PDF-Viewer Users Manual.menu
/home/stephen/.config/menus/applications-merged/wine-Programs-PDF-XChange PDF Viewer-Tracker Updater.menu
/home/stephen/.config/menus/applications-merged/wine-Programs-PDF-XChange PDF Viewer-Uninstall.menu
/home/stephen/.config/menus/applications-merged/wine-Programs-PDF-XChange PDF Viewer-PDF-Viewer License.menu
/home/stephen/.local/share/applications/wine-extension-rtf.desktop
/home/stephen/.local/share/applications/wine-extension-wri.desktop
/home/stephen/.local/share/applications/wine-extension-htm.desktop
/home/stephen/.local/share/applications/wine
/home/stephen/.local/share/applications/wine-extension-jpe.desktop
/home/stephen/.local/share/applications/wine-extension-txt.desktop
/home/stephen/.local/share/applications/wine-extension-msp.desktop
/home/stephen/.local/share/applications/wine-extension-ini.desktop
/home/stephen/.local/share/applications/wine-extension-vbs.desktop
/home/stephen/.local/share/applications/wine-extension-chm.desktop
/home/stephen/.local/share/applications/wine-extension-png.desktop
/home/stephen/.local/share/applications/wine-extension-xml.desktop
/home/stephen/.local/share/applications/wine-extension-url.desktop
/home/stephen/.local/share/applications/wine-extension-hlp.desktop
/home/stephen/.local/share/applications/wine-extension-jfif.desktop
/home/stephen/.local/share/applications/wine-extension-xcvault.desktop
/home/stephen/.local/share/applications/wine-extension-gif.desktop
/home/stephen/.local/share/applications/wine-extension-pdf.desktop
/home/stephen/.local/share/desktop-directories/wine-wine.directory
/home/stephen/.local/share/desktop-directories/wine-Programs-PDF-XChange PDF Viewer.directory
/home/stephen/.local/share/desktop-directories/wine-Programs-Celtx.directory
/home/stephen/.local/share/desktop-directories/wine-Programs-Fitbit Connect.directory
/home/stephen/.local/share/desktop-directories/wine-Programs.directory
/home/stephen/.PlayOnLinux/wine
/home/stephen/.PlayOnLinux/wineprefix
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winefile.exe
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/wined3d.dll
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/wineps.drv
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winemine.exe
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winex11.drv
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winealsa.drv
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winecfg.exe
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winemp3.acm
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winevdm.exe
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/wineconsole.exe
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/wineps16.drv
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/wineboot.exe
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winemapi.dll
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winemsibuilder.exe
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winebrowser.exe
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/wineoss.drv
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winejoystick.drv
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winedbg.exe
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/gecko/1.4/wine_gecko
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winedevice.exe
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winegstreamer.dll
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winemenubuilder.exe
/home/stephen/.PlayOnLinux/wineprefix/default/drive_c/windows/system32/winepath.exe
/home/stephen/.PlayOnLinux/plugins/Capture/software/usr/bin/wine-pthread
/home/stephen/.PlayOnLinux/plugins/Capture/software/usr/bin64/wine-pthread
/home/stephen/.PlayOnLinux/plugins/Wine Look/scripts/wine_colors_from_gnome.py
/home/stephen/Downloads/Wine/wine-1.6.1
/home/stephen/Downloads/Wine/wine-1.6.1/server/wineserver.fr.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/server/wineserver.de.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/server/wineserver.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/tools/wineapploader.in
/home/stephen/Downloads/Wine/wine-1.6.1/tools/winegcc
/home/stephen/Downloads/Wine/wine-1.6.1/tools/winegcc/winegcc.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/tools/winegcc/winegcc.c
/home/stephen/Downloads/Wine/wine-1.6.1/tools/winebuild
/home/stephen/Downloads/Wine/wine-1.6.1/tools/winebuild/winebuild.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/tools/wineinstall
/home/stephen/Downloads/Wine/wine-1.6.1/tools/wine.inf.in
/home/stephen/Downloads/Wine/wine-1.6.1/tools/winewrapper
/home/stephen/Downloads/Wine/wine-1.6.1/tools/wine.desktop
/home/stephen/Downloads/Wine/wine-1.6.1/tools/winemaker
/home/stephen/Downloads/Wine/wine-1.6.1/tools/winemaker.de.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/tools/winemaker.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/tools/winemaker.fr.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/tools/winedump
/home/stephen/Downloads/Wine/wine-1.6.1/tools/winedump/winedump.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/tools/winedump/winedump.h
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wineps.drv
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wineps.drv/wineps.rc
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wineps.drv/wineps.drv.spec
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winex11.drv
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winex11.drv/winex11.drv.spec
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winealsa.drv
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winealsa.drv/winealsa.drv.spec
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wineqtdecoder
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wineqtdecoder/wineqtdecoder.rgs
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wineqtdecoder/wineqtdecoder.spec
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/msacm.dll16/wineacm16.h
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wined3d
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wined3d/wined3d_private.h
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wined3d/wined3d_gl.h
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wined3d/wined3d_main.c
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wined3d/wined3d.spec
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winemapi
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winemapi/winemapi.spec
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wineps16.drv16
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wineps16.drv16/wineps16.drv16.spec
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winecoreaudio.drv
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winecoreaudio.drv/winecoreaudio.drv.spec
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winemp3.acm
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winemp3.acm/winemp3.acm.spec
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/kernel32/winerror.mc
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winemac.drv
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winemac.drv/winemac.drv.spec
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/gdi32/tests/wine_test.ttf
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/gdi32/tests/wine_test.sfd
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wineoss.drv
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wineoss.drv/wineoss.drv.spec
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winejoystick.drv
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winejoystick.drv/winejoystick.drv.spec
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winmm/winemm.h
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winegstreamer
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winegstreamer/winegstreamer.inf
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winegstreamer/winegstreamer.spec
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/wnaspi32/winescsi.h
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/msacm32/wineacm.h
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/winecrt0
/home/stephen/Downloads/Wine/wine-1.6.1/dlls/mmsystem.dll16/winemm16.h
/home/stephen/Downloads/Wine/wine-1.6.1/loader/wine.de.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/loader/wine.fr.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/loader/wine.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/loader/wine_info.plist.in
/home/stephen/Downloads/Wine/wine-1.6.1/loader/wine.pl.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winefile
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winefile/winefile.svg
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winefile/winefile.rc
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winefile/winefile.ico
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winefile/winefile.c
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winefile/winefile.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winefile/winefile.h
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winevdm
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winevdm/winevdm.c
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winemenubuilder
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winemenubuilder/winemenubuilder.c
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winedevice
/home/stephen/Downloads/Wine/wine-1.6.1/programs/wineconsole
/home/stephen/Downloads/Wine/wine-1.6.1/programs/wineconsole/winecon_private.h
/home/stephen/Downloads/Wine/wine-1.6.1/programs/wineconsole/wineconsole.c
/home/stephen/Downloads/Wine/wine-1.6.1/programs/wineconsole/winecon_user.h
/home/stephen/Downloads/Wine/wine-1.6.1/programs/wineconsole/wineconsole.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/programs/wineconsole/wineconsole_res.h
/home/stephen/Downloads/Wine/wine-1.6.1/programs/wineconsole/wineconsole.rc
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winepath
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winepath/winepath.c
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winepath/winepath.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winemsibuilder
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winecfg
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winecfg/winecfg.ico
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winecfg/winecfg.h
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winecfg/winecfg.svg
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winecfg/winecfg.c
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winecfg/winecfg.rc
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winecfg/winecfg.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/programs/wineboot
/home/stephen/Downloads/Wine/wine-1.6.1/programs/wineboot/wineboot.rc
/home/stephen/Downloads/Wine/wine-1.6.1/programs/wineboot/wineboot.c
/home/stephen/Downloads/Wine/wine-1.6.1/programs/wineboot/wineboot.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winebrowser
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winetest
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winetest/winetest.ico
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winetest/winetest.svg
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winetest/winetest.h
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winetest/winetest.rc
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winedbg
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winedbg/winedbg.c
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winedbg/winedbg.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winedbg/winedbg.rc
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winemine
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winemine/winemine.ico
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winemine/winemine.svg
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winemine/winemine.man.in
/home/stephen/Downloads/Wine/wine-1.6.1/programs/winemine/winemine.rc
/home/stephen/Downloads/Wine/wine-1.6.1/po/wine.pot
/home/stephen/Downloads/Wine/wine-1.6.1/include/winevt.h
/home/stephen/Downloads/Wine/wine-1.6.1/include/wine
/home/stephen/Downloads/Wine/wine-1.6.1/include/wine/wined3d.h
/home/stephen/Downloads/Wine/wine-1.6.1/include/wine/wine_common_ver.rc
/home/stephen/Downloads/Wine/wine-1.6.1/include/wine/winedxgi.idl
/home/stephen/Downloads/Wine/wine-1.6.1/include/winerror.h
/home/stephen/Downloads/Wine/wine-1.6.1/libs/wine
/home/stephen/Downloads/Wine/wine-1.6.1/libs/wine/wine.def
/home/stephen/Downloads/Wine/wine-1.6.1/libs/wine/wine.map
/home/stephen/Downloads/Wine/wine-1.6.1.tar.bz2
/home/stephen/.wine/drive_c/users/stephen/Application Data/wine_gecko
/home/stephen/.wine/drive_c/users/stephen/Temp/wine_ppds
/home/stephen/.wine/drive_c/users/stephen/Local Settings/Temporary Internet Files/Content.IE5/06Y14VTA/winehq_logo_text[0]
/home/stephen/.wine/drive_c/users/stephen/Local Settings/Temporary Internet Files/Content.IE5/8MPRBYKH/winehq_logo_glass[0]
/home/stephen/.wine/drive_c/users/stephen/Local Settings/Temporary Internet Files/Content.IE5/CU34EHG2/winehq_logo_text[1]
/home/stephen/.wine/drive_c/users/stephen/Local Settings/Temporary Internet Files/Content.IE5/CU34EHG2/winehq_logo_glass[0]
/home/stephen/.wine/drive_c/windows/system32/winefile.exe
/home/stephen/.wine/drive_c/windows/system32/wined3d.dll
/home/stephen/.wine/drive_c/windows/system32/wineps.drv
/home/stephen/.wine/drive_c/windows/system32/winepulse.drv
/home/stephen/.wine/drive_c/windows/system32/winemine.exe
/home/stephen/.wine/drive_c/windows/system32/winex11.drv
/home/stephen/.wine/drive_c/windows/system32/winealsa.drv
/home/stephen/.wine/drive_c/windows/system32/winecfg.exe
/home/stephen/.wine/drive_c/windows/system32/winemp3.acm
/home/stephen/.wine/drive_c/windows/system32/winevdm.exe
/home/stephen/.wine/drive_c/windows/system32/wineconsole.exe
/home/stephen/.wine/drive_c/windows/system32/wineps16.drv
/home/stephen/.wine/drive_c/windows/system32/wineboot.exe
/home/stephen/.wine/drive_c/windows/system32/winemapi.dll
/home/stephen/.wine/drive_c/windows/system32/winemsibuilder.exe
/home/stephen/.wine/drive_c/windows/system32/winebrowser.exe
/home/stephen/.wine/drive_c/windows/system32/wineoss.drv
/home/stephen/.wine/drive_c/windows/system32/winejoystick.drv
/home/stephen/.wine/drive_c/windows/system32/winedbg.exe
/home/stephen/.wine/drive_c/windows/system32/gecko/2.21/wine_gecko
/home/stephen/.wine/drive_c/windows/system32/gecko/1.4/wine_gecko
/home/stephen/.wine/drive_c/windows/system32/winedevice.exe
/home/stephen/.wine/drive_c/windows/system32/winegstreamer.dll
/home/stephen/.wine/drive_c/windows/system32/winemenubuilder.exe
/home/stephen/.wine/drive_c/windows/system32/winepath.exe
/etc/xdg/menus/applications-merged/wine.menu
/var/lib/binfmts/wine
/var/lib/dpkg/info/wine1.6.postrm
/var/lib/dpkg/info/wine-silverlight5.1-installer.postrm
/var/lib/dpkg/info/wine1.6-i386.postrm
/var/lib/dpkg/info/wine-gecko2.21:i386.md5sums
/var/lib/dpkg/info/wine1.6.postinst
/var/lib/dpkg/info/winetricks.list
/var/lib/dpkg/info/wine-silverlight5.1-installer.list
/var/lib/dpkg/info/wine1.6-i386.shlibs
/var/lib/dpkg/info/wine1.6.conffiles
/var/lib/dpkg/info/wine1.6.md5sums
/var/lib/dpkg/info/winetricks.md5sums
/var/lib/dpkg/info/wine-mono0.0.8.md5sums
/var/lib/dpkg/info/wine-browser-installer.list
/var/lib/dpkg/info/wine1.6-i386.postinst
/var/lib/dpkg/info/wine-gecko2.21:i386.list
/var/lib/dpkg/info/wine1.6.config
/var/lib/dpkg/info/wine1.6.prerm
/var/lib/dpkg/info/wine1.6-i386.list
/var/lib/dpkg/info/wine-browser-installer.postrm
/var/lib/dpkg/info/wine1.6-i386.md5sums
/var/lib/dpkg/info/wine1.6.preinst
/var/lib/dpkg/info/wine-mono0.0.8.list
/var/lib/dpkg/info/wine1.6.list

```

Better?  Make more sense?

---

### Post by Bashing-om on 2015-11-29
StephenG; Yeah !

We have the files and the file names !

Let's run:
```

sudo apt-get --purge remove wine1.6 winetricks wine-gecko* netflix-desktop
rm -rf $HOME/.wine
rm -rf .wine-browser/
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
sudo apt-get autoremove wine
sudo apt-get autoremove

sudo apt-add-repository --remove ppa:ubuntu-wine/ppa ## which I expect to say it does not exist ## 

```
It is over kill, and I do expect many of these - not to exist - proceed anyway to the next command in line on the aboves .
Does" apt-add-repository --remove " deal with  /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.distUpgrade for us, or do we manually remove these references . I bet manually !
Anything else left ?
```

ls -al .local/share/applications/wine/Programs/

```

I do expect Wine now to be flushed from the system ... and we can move onto what to do about fluxbox,
then is the GPG errors
then is to update to the latest kernel .

[INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-29
Everything seems to go according to (your) plan, except the second-to-last command that you thought might produce nothing, actually gave me this response.  Hopefully, it's not a complication.

```
stephen@stephen-desktop:~$ sudo apt-add-repository --remove ppa:ubuntu-wine/ppa
 Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie and Maarten Lankhorst.
 More info: [https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa](https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa)
Press [ENTER] to continue or ctrl-c to cancel removing it

stephen@stephen-desktop:~$ ls -al .local/share/applications/wine/Programs/
total 20
drwxrwxr-x 5 stephen stephen 4096 Jun 10  2013 .
drwxrwxr-x 3 stephen stephen 4096 Oct 18  2012 ..
drwxrwxr-x 2 stephen stephen 4096 Apr 21  2015 Celtx
drwxrwxr-x 2 stephen stephen 4096 Mar 30  2013 Fitbit Connect
drwxrwxr-x 2 stephen stephen 4096 May 18  2015 PDF-XChange PDF Viewer
```

Should I again try update, to see what we get? or wait until more is done? and I'm sorry I forgot to enclose the code above.

Also, since the FitBit application is not linux-friendly, we can remove it as well.  Ditto for the Celtx program.  I love the PDF Xchange so want to keep it, though it only works with WINE.

---

### Post by Bashing-om on 2015-11-29
StephenG; Hummm ..

Yeah, go ahead and " sudo apt-add-repository --remove ppa:ubuntu-wine/ppa " >> " Press [ENTER] to continue or ctrl-c to cancel removing it "
Press enter to remove ( what ever it might find).

I am afraid to mess with " .local/share/applications/wine/Programs/ " as I do not recognize the files. Best leave well enough alone as chances are they belong with other applications also .

And YES code tags help a bunch .. maintains the formatting and does a lot to promote readability .

And before seeing about update/GPG errors .. lets deal with fuzebox.


Meanwhile, see what I can find out about fuzebox removal ... not seeing a lot yet to help us .

[INDENT][INDENT]I hate when this happens
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-29
I did press <enter> both when I did it earlier and again when I did it just now, with the same result:

```
stephen@stephen-desktop:~$ sudo apt-add-repository --remove ppa:ubuntu-wine/ppa
[sudo] password for stephen: 
 Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie and Maarten Lankhorst.
 More info: https://launchpad.net/~ubuntu-wine/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel removing it

stephen@stephen-desktop:~$ 

```

Or should it be apt-get-repository?

---

### Post by Bashing-om on 2015-11-29
StephenG; Nawww ..
> 
Or should it be apt-get-repository?

I did double check and the command as given is correct, think just that there is nothing for the command to operate with as we have removed all the files.

Let's move on to fuzebox . Yuk:
[https://support.fuze.com/hc/en-us/articles/201527877-Does-Fuze-Support-Linux-](https://support.fuze.com/hc/en-us/articles/201527877-Does-Fuze-Support-Linux-)
Seems that the web has been scrubbed of all references to this application .. I get either a blank page, non-loading page, or a miss-direction on the majority of my attempts to find any information !
Let's again prepare do this the hard way .
what returns:
```

dpkg -l fuzelinuxclient
sudo find / -name fuzelinuxclient
ls -al /var/lib/dpkg/info/fuzelinuxclient.list
grep -B3 -A10 fuzelinuxclient /var/lib/dpkg/status

```

----------------------------
And:
Do we still have that corrupted .gvfs directory ?
what now :
```

ls -al /home/stephen/.gvfs

```


As I just do not know
[INDENT][INDENT][INDENT]but willing to find out[/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-29
I just sent Fuze (the new Fuzebox) a tech support query asking for instructions on completely deleting their app.  Will let you know what I hear.  Meanwhile ... carrying on with your instructions.

```
stephen@stephen-desktop:~$ dpkg -l fuzelinuxclient
dpkg-query: no packages found matching fuzelinuxclient
stephen@stephen-desktop:~$ sudo find / -name fuzelinuxclient
[sudo] password for stephen: 
stephen@stephen-desktop:~$ ls -al /var/lib/dpkg/info/fuzelinuxclient.list
ls: cannot access /var/lib/dpkg/info/fuzelinuxclient.list: No such file or directory
stephen@stephen-desktop:~$ grep -B3 -A10 fuzelinuxclient /var/lib/dpkg/status

```

```
stephen@stephen-desktop:~$ ls -al /home/stephen/.gvfs
total 8
drwx------  2 stephen stephen 4096 Oct 17  2012 .
drwxr-xr-x 54 stephen stephen 4096 Nov 29 17:34 ..

```

---

### Post by Bashing-om on 2015-11-29
StephenG; sheessshh ;

All that says that fuzebox is not installed - or at least not under the name I expected .
I await to see what the app admins have to say .

And the good news in respect to .gvfs, looks good to me now !

Come the morrow, maybe we can focus on the GPG errors .

[INDENT][INDENT]clearing the deck for action
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-29
Trying a find command for fuze* to see what I might find .  Will let you know if anytning pops up.  And shouldn't your tag-line read "happy ubuntu'n" rather than "ubutu'n?

Here's the return.  Anything meaningful to you?

```
stephen@stephen-desktop:~$ sudo find / -name fuze*
[sudo] password for stephen: 
/etc/apt/trusted.gpg.d/fuzebox.gpg
/etc/apt/sources.list.d/fuzebox.list.save

```

File named "fuzebox.gpg" contains this info.  Helpful?

```
--2015-05-07 21:18:40--  http://apt.fuzebox.com/apt/keyring.gpg
Resolving apt.fuzebox.com (apt.fuzebox.com)... 206.81.183.53
Connecting to apt.fuzebox.com (apt.fuzebox.com)|206.81.183.53|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1199 (1.2K) [application/octet-stream]
Saving to: ‘keyring.gpg.1’

     0K .                                                     100% 65.6M=0s

2015-05-07 21:18:40 (65.6 MB/s) - ‘keyring.gpg.1’ saved [1199/1199]

```

---

### Post by Bashing-om on 2015-11-29
StephenG; Hey !

Well find in fuzebox tells us nothing new . 
I can accept that perhaps one source of the GPG errors ...but will know more when we know that application is no longer in the system.

And YES my tag line should be corrected ... Bet I do that next ... humm all this time and I have not noticed that little typo !

[INDENT][INDENT][progress made
[INDENT][INDENT][INDENT][INDENT]slowly
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-29
The folder "fuzebox.list.save" is a zero byte file.  The folder it's in -- "/etc/apt/sources.list.d/" looks like this, with many zero-byte files in it.

---

### Post by Bashing-om on 2015-11-29
StephenG; Yeah ...

While we are waiting.
This is the only 3rd party PPA we are interested in keeping.
> 
==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list <==
deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) trusty main

==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list.save <==
# deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) trusty main


all others can be safely removed.
```

sudo rm /etc/apt/sources.list.d/ehoover-compholio-trusty.list.save
sudo rm /etc/apt/sources.list.d/fuzebox.list.save
sudo rm /etc/apt/sources.list.d/mqchael-pipelight-trusty.list.save
sudo rm /etc/apt/sources.list.d/pipelight-stable-trusty.list
sudo rm /etc/apt/sources.list.d/pipelight-stable-trusty.list.save
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.distUpgrade
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save

```

And and and ... while we are on the subject; we want to add the universe, mutliverse, extra and partners repos back into the /etc/apt/sources.list file. These repos are safe and do come in handy . Also maybe a source of the errors as something requiring an update and no access to do so .

We will look at that too in the morrow. Presently I am tired and there is a good chance of an error on my part in seeing what/where/how to add back in the repos we want ... and not make a duplicate entry ... that too - a duplicate- is a no no .

As a reference my working sources.list file:
[http://paste.ubuntu.com/13570127/](http://paste.ubuntu.com/13570127/)

to compare to and rebuild yours . Always, always make a backup of any file that is the be edited ... never can tell what might happen ... power outages can do real mean things at such a time ...

[INDENT][INDENT]progress made
[INDENT][INDENT][INDENT]slowly
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-30
Followed all above commands and got no error messages.  Simply back to the command line, which I presume means that the command "took" and nothing was typed wrong.

Here's the response from FUZE.  You'd think that even though they don't support Linux any more, they could still know how to delete their own program.  Pretty worthless.  I just now finished my farm chores and followed all your commands above, so I'll start to look at the links he sent.


Scott Q., Nov 30, 07:13:

Hello Stephen,

Thank you for contacting Fuze Technical Support concerning your request, I am sorry to hear of the issue you are experiencing.

Unfortunately we do not support Linux nor do we offer support for Fuze installed on Linux based machines for either installation or un-installation. Once we abandoned support in for Fuze with Linux (February 11, 2015) we notified our community and users via our knowledge base article Does Fuze Support Linux? which you can read about. You will need to perform a web search or speak with other Linux users to determine the best method for removing programs from your Linux based operating system.

During my search I have found many references concerning this task, one of which is How to uninstall programs in Ubuntu if they are not in Software Center? 12.04 that may already have a topic that covers your situation and needs, or will allow you to seek advice and instructions to resolve this matter for you.

We do apologize for the inconveniences this has caused and we would be more than happy to assist you if there were support for Fuze for Linux, and resources/support options available for us to provide to you.

Sincerely,

Scott Q.
Fuze Technical Support
Email: [email]techsupport@fuze.com[/email]

You can always find the latest Fuze Information on our Support Page here: 
[http://support.fuze.com/](http://support.fuze.com/)

---

### Post by Bashing-om on 2015-11-30
StephenG; Sheesshhh ...

So much for customer support .. I go back and see what I can find ,, but not to hopeful.
I do not think fuzebox exists on the system ... but sure would be nice to confirm .
Gimme a bit of time to go a look'n .

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-30
I've sent a follow-up to "Scott Q." asking what the <Program Name> might be that we're looking for.

Do you think, then, that the only reference to the program is in the GPG file and those two files that I told you of last night?

Scott Q's very (really?) helpful response, which I will follow right now with the "find" command and let you know if anything rears its ugly head:

Scott Q., Nov 30, 12:33:

Hi Stephen,

You may want to look for "fuze, fuzebox, fuze meeting" or any other variation of a package with the name "Fuze" listed.

Sincerely,

---

### Post by Bashing-om on 2015-11-30
StephenG; YUk;

My results are same as last night .. no info, and what was has been scrubbed from the web.
The only hint I have is " fuzelinuxclient '.
So yeah .. we are looking with 'find' to see what we can find .

[INDENT][INDENT]dancing in the dark
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-30
The find found nothing.  I even tried capitalizing the F, thinking that might make a difference.  (It took me more than a month when I first started messing with Linux, to realize that capitalization makes a difference. Duh!)  Found nothing.  So, I guess you're surmise that we've gotten rid of the dastardly program may probably be correct.  Onward, through the fog!

---

### Post by Bashing-om on 2015-11-30
StephenG; Ho Kay ..

Onward, next up is to get the /etc/apt/sources.list file up to snuff.
You got that under control, or require guidance in making that happen ?

Once the sources.list file is updated ... see what now results with update/upgrade .

[INDENT][INDENT]there are pleasant surprises
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-30
The find found nothing.  I even tried capitalizing the F, thinking that might make a difference.  (It took me more than a month when I first started messing with Linux, to realize that capitalization makes a difference. Duh!)  Found nothing.  So, I guess you're surmise that we've gotten rid of the dastardly program may probably be correct.  Onward, through the fog!

I will need your guidance.  Please?  Pretty please?

---

### Post by Bashing-om on 2015-11-30
StephenG; Sure !

Give me a bit to work it up .. as seems to me the easies is for me to work it up and pass it back to you .

be back in a bit ,

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-30
I'm guessing that the first thing to do is to now reboot, to settle all the recent changes.  Yes?

---

### Post by Bashing-om on 2015-11-30
StephenG; OK;

Here is my take on the new sources.list file:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ trusty main restricted
	
## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ trusty universe
deb http://archive.ubuntu.com/ubuntu/ trusty-updates universe
	
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://archive.ubuntu.com/ubuntu/ trusty-updates multiverse
	
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
	
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse

	
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner

deb-src http://archive.canonical.com/ubuntu trusty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
	

	
##  This is the gscan2pdf application updater

```
I can make errors and mistakes though I have looked it over twice, I do recommend that you also look it over and compare all of the files to see that what I present makes sense and is correct.

Back up what is current on your system:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-30nov2015

```

copy the new file into place.

Now with the new sources.list file in place, update the system:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

We still have any GPG errors - will not be surprised IF all is now fixed .

Now reboot and we see the total effect.

[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-30
The main difference between yours and mine seems to be the / between "ubuntu" and "trusty" in several entries; and the fact that I have universe, multiverse and main all in one command.  What difference will those make?  See below:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu trusty main universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu trusty-updates main universe multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu trusty-security main universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu trusty main

##  This is the gscan2pdf application updater
```

And I don't see the notation "restricted" anywhere in my file.  I have unselected the source code options in the updating settings.  Is that what the restricted is for?

And may I safely delete lines like th last one referencing the gscan2pdf application updater?  Or should it be left for some reason, even though it's commented out?

---

### Post by Bashing-om on 2015-11-30
StephenGl Yeah;

Will work as you have edited/amended.
see: [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)
for the repo breakdown and what 'restricted' is .
As to " ##  This is the gscan2pdf application updater" up to you . I left it as a possible reminder of what you may want to do at a later time.

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

``` and we see where we stand now.

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by mc4man on 2015-11-30
Just to clarify (not pertinent to issue
~/.gvfs is not used in 14.04 or newer  & if there can safely be deleted.
Why would it be there?
1. Left over from an upgrade from a previous release of Ubuntu that did use it.
2. Improper use of sudo with certain gui apps

---

### Post by Bashing-om on 2015-11-30
@mc4man :)

Good to know info .. yeah this is an upgrade from precise.
But I still have it on my 14.04 install on an upgrade from raring .

[INDENT][INDENT]never cam know
[INDENT][INDENT][INDENT]enough
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-30
Well, damn.  For the first time since May, when I run the regular upgrade icon, I get an "all things up-to-date" without the horrible "some files can't be verified" error message.  When I did the "dist-upgrade" there was one troubling (to me, at least) section with an error message.  I've included it below.  Any thoughts on the error portions of the message?  since I have no RAID set up on this machine, I can't figure out the error message referencing an ncorrect number of RAID arrays.


```
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-70-generic
Found initrd image: /boot/initrd.img-3.13.0-70-generic
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-51-generic
Found initrd image: /boot/initrd.img-3.13.0-51-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
ERROR: sil: wrong # of devices in RAID set "sil_aeaibgcecefb" [1/2] on /dev/sdb
done
Setting up linux-image-extra-3.13.0-70-generic (3.13.0-70.113) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-70-generic /boot/vmlinuz-3.13.0-70-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-70-generic /boot/vmlinuz-3.13.0-70-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-70-generic /boot/vmlinuz-3.13.0-70-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-70-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-70-generic /boot/vmlinuz-3.13.0-70-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-70-generic /boot/vmlinuz-3.13.0-70-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-70-generic /boot/vmlinuz-3.13.0-70-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-70-generic
Found initrd image: /boot/initrd.img-3.13.0-70-generic
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-51-generic
Found initrd image: /boot/initrd.img-3.13.0-51-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-67-generic-pae
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
ERROR: sil: wrong # of devices in RAID set "sil_aeaibgcecefb" [1/2] on /dev/sdb
done
Setting up linux-image-generic (3.13.0.70.76) ...
Setting up linux-headers-3.13.0-70 (3.13.0-70.113) ...
Setting up linux-headers-3.13.0-70-generic (3.13.0-70.113) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-70-generic /boot/vmlinuz-3.13.0-70-generic
Setting up linux-headers-generic (3.13.0.70.76) ...
Setting up linux-generic (3.13.0.70.76) ...
Setting up linux-generic-pae (3.13.0.70.76) ...
Setting up linux-image-generic-pae (3.13.0.70.76) ...
Setting up linux-headers-generic-pae (3.13.0.70.76) ...
```

But for crying out loud when I run update from terminal, I still am getting the GPG errors.  I'm really not understanding this -- AT ALL.

```
Reading package lists... Done
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.ubuntu.com trusty-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32

```

---

### Post by Bashing-om on 2015-11-30
StephenG: Well

1st things 1st. no idea:
> 
ERROR: sil: wrong # of devices in RAID set "sil_aeaibgcecefb" [1/2] on /dev/sdb

that will put me in a deep learning mode also .

As to our continued fight with the GPG errors ;
What results:
```

sudo apt-key update

```

see where we go from there.

[INDENT][INDENT]if it were easy
cave men would have done this
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-30
```
stephen@stephen-desktop:~$ sudo apt-key update
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
```

Just ran Y-PPA manager and it told me it had repaired all broken PPAs and had updated all others.  Still getting the GPG key error on apt-get update.

---

### Post by Bashing-om on 2015-11-30
StephenG; Humm .. 

Now that is unexpected ! As the system is aware of the keys, WHY is it screaming and hollering "  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 " .

Will sleep on this, see what comes to mind when rested .

[INDENT]Now
[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-11-30
I need some sleep.  See y'all tomorrow, if you can still stand dealing with this craziness.

Why would there be two different signing keys for each entry -- the CD Image and the archive?  And why are there two different keys dated 2012, that seem to duplicate the other two keys in terms of use?  B-O, didn't you tell me earlier that duplication is a bad thing, a no-no?

---

### Post by Bashing-om on 2015-12-01
StephenG; Morning;


And back to this GPG thing ... I would realy like to learn the why and where of .
let's take this approach:
```

for r in /var/lib/apt/lists/*Release; do if ! gpgv --keyring /etc/apt/trusted.gpg $r.gpg $r; then echo "error: $? Problem with $r"; fi; done

```
That will check the gpg signatures of the Release files.... any errors it's say "error: X Problem with ...."

As a reference, my resilt:
```

sysop@1404mini:~$ for r in /var/lib/apt/lists/*Release; do if ! gpgv --keyring /etc/apt/trusted.gpg $r.gpg $r; then echo "error: $? Problem with $r"; fi; done
gpgv: Signature made Fri 13 Nov 2015 01:50:55 PM CST using DSA key ID 437D05B5
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpgv: Signature made Fri 13 Nov 2015 01:50:55 PM CST using RSA key ID C0B21F32
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
gpgv: Signature made Tue 24 Nov 2015 01:15:40 PM CST using DSA key ID 7FAC5991
gpgv: Good signature from "Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>"
gpgv: Signature made Sun 17 May 2015 11:01:03 AM CDT using DSA key ID 3E5C1192
gpgv: Good signature from "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpgv: Signature made Thu 08 May 2014 09:20:33 AM CDT using DSA key ID 437D05B5
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>"
gpgv: Signature made Thu 08 May 2014 09:20:33 AM CDT using RSA key ID C0B21F32
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
gpgv: can't open `/var/lib/apt/lists/ftp.utexas.edu_ubuntu_dists_trusty-updates_InRelease.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/ftp.utexas.edu_ubuntu_dists_trusty-updates_InRelease
gpgv: can't open `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_InRelease.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_InRelease
sysop@1404mini:~$

```
Where it indicates I have a problem that even I was not aware of ! Think my resolution will be to re-create the " /var/lib/apt/lists/*" files .
The same solution "might" apply in your case .

[INDENT][INDENT]I still want to know
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-12-01
Now this doesn't look very good to me.  But what do I know ...

```
stephen@stephen-desktop:~$ for r in /var/lib/apt/lists/*Release; do if ! gpgv --keyring /etc/apt/trusted.gpg $r.gpg $r; then echo "error: $? Problem with $r"; fi; done
gpgv: can't open `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_Release
gpgv: can't open `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty_Release
gpgv: can't open `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-security_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-security_Release
gpgv: can't open `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_Release
gpgv: can't open `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_Release.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_Release
gpgv: can't open `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_trusty_InRelease.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/ppa.launchpad.net_webupd8team_y-ppa-manager_ubuntu_dists_trusty_InRelease
```

---

### Post by Bashing-om on 2015-12-01
StephenG; Hey ...

I do believe we have corrupted control files.
Let's try this to remove and rebuild them:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```
MergeLists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon.
When corrupted, they can be safely deleted. Apt will recreate them during the next apt-get update.

Now is the system still in a bother over the GPG keys ?

[INDENT][INDENT]maybe now, YES
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-12-01
Arrggh ...

```
stephen@stephen-desktop:~$ sudo rm -fr /var/lib/apt/lists
[sudo] password for stephen: 
stephen@stephen-desktop:~$ sudo mkdir -pv /var/lib/apt/lists/partial
mkdir: created directory ‘/var/lib/apt/lists’
mkdir: created directory ‘/var/lib/apt/lists/partial’
stephen@stephen-desktop:~$ sudo apt-get update
Ign http://archive.ubuntu.com trusty InRelease
Get:1 http://archive.ubuntu.com trusty-updates InRelease [64.4 kB]             
Get:2 http://ppa.launchpad.net trusty InRelease [15.5 kB]                      
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:3 http://archive.ubuntu.com trusty-security InRelease [64.4 kB]            
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Get:4 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Get:5 http://archive.canonical.com trusty Release.gpg [933 B]                  
Ign http://archive.ubuntu.com trusty-security InRelease                        
Get:6 http://archive.ubuntu.com trusty Release.gpg [933 B]                     
Get:7 http://archive.ubuntu.com trusty-updates/main i386 Packages [641 kB]     
Get:8 http://ppa.launchpad.net trusty/main i386 Packages [1,077 B]             
Get:9 http://extras.ubuntu.com trusty Release [11.9 kB]                        
Ign http://extras.ubuntu.com trusty Release                                    
Get:10 http://archive.canonical.com trusty Release [9,359 B]                   
Ign http://archive.canonical.com trusty Release                                
Get:11 http://ppa.launchpad.net trusty/main Translation-en [868 B]             
Get:12 http://extras.ubuntu.com trusty/main i386 Packages [14 B]               
Get:13 http://archive.canonical.com trusty/partner i386 Packages [6,308 B]     
Get:14 http://archive.canonical.com trusty/partner Translation-en [4,588 B]    
Ign http://archive.canonical.com trusty/partner Translation-en_US              
Get:15 http://archive.ubuntu.com trusty-updates/universe i386 Packages [329 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en_US                  
Ign http://extras.ubuntu.com trusty/main Translation-en                     
Get:16 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.1 kB]
Get:17 http://archive.ubuntu.com trusty-updates/main Translation-en [327 kB]
Get:18 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [6,832 B]
Get:19 http://archive.ubuntu.com trusty-updates/universe Translation-en [173 kB]
Get:20 http://archive.ubuntu.com trusty-security/main i386 Packages [358 kB]
Get:21 http://archive.ubuntu.com trusty-security/universe i386 Packages [120 kB]
Get:22 http://archive.ubuntu.com trusty-security/multiverse i386 Packages [4,967 B]
Get:23 http://archive.ubuntu.com trusty-security/main Translation-en [206 kB]  
Get:24 http://archive.ubuntu.com trusty-security/multiverse Translation-en [2,437 B]
Get:25 http://archive.ubuntu.com trusty-security/universe Translation-en [69.9 kB]
Get:26 http://archive.ubuntu.com trusty Release [58.5 kB]                      
Ign http://archive.ubuntu.com trusty Release                                   
Get:27 http://archive.ubuntu.com trusty/main i386 Packages [1,348 kB]          
Get:28 http://archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]      
Get:29 http://archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]      
Get:30 http://archive.ubuntu.com trusty/main Translation-en [762 kB]           
Get:31 http://archive.ubuntu.com trusty/multiverse Translation-en [102 kB]     
Get:32 http://archive.ubuntu.com trusty/universe Translation-en [4,089 kB]     
Ign http://archive.ubuntu.com trusty-updates/main Translation-en_US            
Ign http://archive.ubuntu.com trusty-updates/multiverse Translation-en_US      
Ign http://archive.ubuntu.com trusty-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com trusty-security/main Translation-en_US           
Ign http://archive.ubuntu.com trusty-security/multiverse Translation-en_US     
Ign http://archive.ubuntu.com trusty-security/universe Translation-en_US       
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 14.8 MB in 45s (328 kB/s)                                              
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com trusty-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
stephen@stephen-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-generic-pae linux-headers-generic
  linux-headers-generic-pae linux-image-generic linux-image-generic-pae
The following packages will be upgraded:
  linux-libc-dev thunderbird thunderbird-globalmenu thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-us
6 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 33.9 MB of archives.
After this operation, 18.4 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  linux-libc-dev thunderbird-locale-en thunderbird thunderbird-gnome-support
  thunderbird-globalmenu thunderbird-locale-en-us
Install these packages without verification? [y/N] y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty-updates/main linux-libc-dev i386 3.13.0-71.114 [770 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty-updates/main thunderbird-locale-en i386 1:38.4.0+build3-0ubuntu0.14.04.1 [349 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ trusty-updates/main thunderbird i386 1:38.4.0+build3-0ubuntu0.14.04.1 [32.8 MB]
Get:4 http://archive.ubuntu.com/ubuntu/ trusty-updates/main thunderbird-gnome-support i386 1:38.4.0+build3-0ubuntu0.14.04.1 [8,532 B]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty-updates/main thunderbird-globalmenu i386 1:38.4.0+build3-0ubuntu0.14.04.1 [8,218 B]
Get:6 http://archive.ubuntu.com/ubuntu/ trusty-updates/main thunderbird-locale-en-us all 1:38.4.0+build3-0ubuntu0.14.04.1 [9,986 B]
Fetched 33.9 MB in 1min 35s (357 kB/s)                                         
(Reading database ... 688932 files and directories currently installed.)
Preparing to unpack .../linux-libc-dev_3.13.0-71.114_i386.deb ...
Unpacking linux-libc-dev:i386 (3.13.0-71.114) over (3.13.0-70.113) ...
Preparing to unpack .../thunderbird-locale-en_1%3a38.4.0+build3-0ubuntu0.14.04.1_i386.deb ...
Unpacking thunderbird-locale-en (1:38.4.0+build3-0ubuntu0.14.04.1) over (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird_1%3a38.4.0+build3-0ubuntu0.14.04.1_i386.deb ...
Unpacking thunderbird (1:38.4.0+build3-0ubuntu0.14.04.1) over (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird-gnome-support_1%3a38.4.0+build3-0ubuntu0.14.04.1_i386.deb ...
Unpacking thunderbird-gnome-support (1:38.4.0+build3-0ubuntu0.14.04.1) over (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird-globalmenu_1%3a38.4.0+build3-0ubuntu0.14.04.1_i386.deb ...
Unpacking thunderbird-globalmenu (1:38.4.0+build3-0ubuntu0.14.04.1) over (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird-locale-en-us_1%3a38.4.0+build3-0ubuntu0.14.04.1_all.deb ...
Unpacking thunderbird-locale-en-us (1:38.4.0+build3-0ubuntu0.14.04.1) over (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Setting up linux-libc-dev:i386 (3.13.0-71.114) ...
Setting up thunderbird (1:38.4.0+build3-0ubuntu0.14.04.1) ...
Setting up thunderbird-locale-en (1:38.4.0+build3-0ubuntu0.14.04.1) ...
Setting up thunderbird-gnome-support (1:38.4.0+build3-0ubuntu0.14.04.1) ...
Setting up thunderbird-globalmenu (1:38.4.0+build3-0ubuntu0.14.04.1) ...
Setting up thunderbird-locale-en-us (1:38.4.0+build3-0ubuntu0.14.04.1) ...

```

Can you explain to me why it seems to be searching for the GPG keys and apparently locating them but then not being able to authenticate them?  I guess I do not understand the authentication process.  I thought it matched what was on this system with some checksum on the server to see if they were legitimate.

---

### Post by Bashing-om on 2015-12-01
StephenG; Nope;

I am as lost as you are in trying to understand where the failure is . The keys are on the system, the system knows about them but apt does not .
I really thought removing the /list directory and rebuilding would be effective. Disappointed to say the least .

I ask myself, what gives ?

one more time, let's see what happens when ->
Add the keys:
```

sudo apt-key adv --recv-keys --keyserver   keyserver.ubuntu.com 40976EAF437D05B5
sudo apt-key adv --recv-keys --keyserver   keyserver.ubuntu.com 3B4FE6ACC0B21F32
sudo apt-key adv --recv-keys --keyserver   keyserver.ubuntu.com 16126D3A3E5C1192

```

Consider, if this again fails, to delete the keys and re-add them . Maybe then the paths will be established .  
 
Lemme see what I can learn . Will be back

[INDENT][INDENT]we have the documentation
[INDENT][INDENT]put the pieces together[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-12-01
How do I delete them in order to re-add, since this didn't work?

```
stephen@stephen-desktop:~$ sudo apt-key adv --recv-keys --keyserver  keyserver.ubuntu.com 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.1W4tV3M4sM --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
stephen@stephen-desktop:~$ sudo apt-key adv --recv-keys --keyserver  keyserver.ubuntu.com 3B4FE6ACC0B21F32
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.GWpJsAxm48 --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg --recv-keys --keyserver keyserver.ubuntu.com 3B4FE6ACC0B21F32
gpg: requesting key C0B21F32 from hkp server keyserver.ubuntu.com
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
stephen@stephen-desktop:~$ sudo apt-key adv --recv-keys --keyserver  keyserver.ubuntu.com 16126D3A3E5C1192
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.e8gZiTZGnK --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
stephen@stephen-desktop:~$ sudo apt-get update
Hit http://ppa.launchpad.net trusty InRelease
Ign http://archive.ubuntu.com trusty InRelease                      
Ign http://archive.canonical.com trusty InRelease                   
Ign http://extras.ubuntu.com trusty InRelease                       
Get:1 http://archive.ubuntu.com trusty-updates InRelease [64.4 kB]             
Get:2 http://archive.canonical.com trusty Release.gpg [933 B]                  
Get:3 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty Release                                
Ign http://extras.ubuntu.com trusty Release                                    
Ign http://archive.canonical.com trusty Release                                
Ign http://extras.ubuntu.com trusty/main i386 Packages/DiffIndex               
Ign http://archive.canonical.com trusty/partner i386 Packages/DiffIndex        
Ign http://archive.ubuntu.com trusty-updates InRelease                     
Get:4 http://archive.ubuntu.com trusty-security InRelease [64.4 kB]        
Ign http://archive.ubuntu.com trusty-security InRelease                        
Hit http://archive.canonical.com trusty/partner Translation-en                 
Get:5 http://archive.ubuntu.com trusty Release.gpg [933 B]                     
Hit http://archive.canonical.com trusty/partner i386 Packages         
Hit http://extras.ubuntu.com trusty/main i386 Packages                
Ign http://archive.ubuntu.com trusty-updates/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com trusty-updates/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com trusty-updates/multiverse i386 Packages/DiffIndex
Ign http://archive.canonical.com trusty/partner Translation-en_US
Get:6 http://archive.ubuntu.com trusty-updates/main Translation-en [327 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en_US    
Ign http://extras.ubuntu.com trusty/main Translation-en       
Get:7 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [6,832 B]
Get:8 http://archive.ubuntu.com trusty-updates/universe Translation-en [173 kB]
Ign http://archive.ubuntu.com trusty-security/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com trusty-security/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com trusty-security/multiverse i386 Packages/DiffIndex
Hit http://archive.ubuntu.com trusty-security/main Translation-en
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-security/universe Translation-en
Hit http://archive.ubuntu.com trusty Release      
Ign http://archive.ubuntu.com trusty Release     
Get:9 http://archive.ubuntu.com trusty-updates/main i386 Packages [641 kB]
Get:10 http://archive.ubuntu.com trusty-updates/universe i386 Packages [329 kB]
Get:11 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.1 kB]
Get:12 http://archive.ubuntu.com trusty-security/main i386 Packages [358 kB]   
Get:13 http://archive.ubuntu.com trusty-security/universe i386 Packages [120 kB]
Get:14 http://archive.ubuntu.com trusty-security/multiverse i386 Packages [4,967 B]
Ign http://archive.ubuntu.com trusty/main i386 Packages/DiffIndex              
Ign http://archive.ubuntu.com trusty/universe i386 Packages/DiffIndex          
Ign http://archive.ubuntu.com trusty/multiverse i386 Packages/DiffIndex        
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                 
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Hit http://archive.ubuntu.com trusty/main i386 Packages                        
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages                  
Ign http://archive.ubuntu.com trusty-updates/main Translation-en_US            
Ign http://archive.ubuntu.com trusty-updates/multiverse Translation-en_US      
Ign http://archive.ubuntu.com trusty-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com trusty-security/main Translation-en_US           
Ign http://archive.ubuntu.com trusty-security/multiverse Translation-en_US     
Ign http://archive.ubuntu.com trusty-security/universe Translation-en_US       
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 2,104 kB in 13s (153 kB/s)                                             
Reading package lists... Done
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
```

According to launchpad, this bug.error has been occurring now for about 2 years.  Really?!?  And I thought it was unique to my system ...

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540)

---

### Post by mc4man on 2015-12-01
I'd probably create a new admin user, log in to it & try there to see if same results for apt-get update or ok.

---

### Post by StephenG on 2015-12-01
Wandering about with the find command, looking for zero-length .gpg files, this is what came up.  Is the info of any use to us?

```
stephen@stephen-desktop:~$ find -name '*.gpg' -size 0
./.gnupg/secring.gpg

```

Also, in the folder /etc/apt I still find files (not zero byte!) named fuzebox.gpg and pipelight-stable.gpg  I thought we had deleted all things concerned with both those programs.

New admin account.  Results the same.  Same unverifiable keys.

---

### Post by Bashing-om on 2015-12-02
StephenG; mc4man; Hey !

We have a hint as to what is not going on.
My results:
```

sysop@1404mini:~$ ls -al ./.gnupg/secring.gpg
-rw------- 1 sysop sysop 2592 Dec  9  2013 ./.gnupg/secring.gpg
sysop@1404mini:~$ file ./.gnupg/secring.gpg
./.gnupg/secring.gpg: data
sysop@1404mini:~$

```

As StephenG will be out of town for a few days, we pick this back up at a later time ( advised in a PM ).

[INDENT][INDENT]we have a target
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-12-06
I&#8217;m back in town and here's the result of your commands:

```
stephen@stephen-desktop:~$ ls -al ./.gnupg/secring.gpg
-rw------- 1 stephen stephen 0 Jan 24  2013 ./.gnupg/secring.gpg
stephen@stephen-desktop:~$ file ./.gnupg/secring.gpg
./.gnupg/secring.gpg: empty 

```

Not much but maybe the fact that it's empty is, in fact, a world of information

Now, every time I reboot, I get an internal error message and after I tell it to send the report, it fires up "fine."  I'm sure there must be a log somewhere in the system, telling us what the heck's going on.   When I search for the term "log" I get lots and lots of files but some can't be opened and I'm not sure which ones I'm looking for.  Any ideas?

---

### Post by Bashing-om on 2015-12-07
StephenG; Hey;

Hang'n with you . All i have managed to do is gain a deeper appreciation of the complexity of the security system.
I still do not understand where or why this failure is occurring .
Seeking to find system errors one looks at:
```

cat /var/log/syslog
cat /var/log/kern.log
cat /var/log/dmesg

```

In furtherance of our troubleshooting:
```

ls -al .gnupg
ls -al .gnupg/pubring.gpg
ls -al .gnupg/secring.gpg

```
The outputs should show you the owner.

If that is the case let's try and reinstall the keyrings:
```

sudo apt-get --reinstall install ubuntu-keyring
sudo apt-get install --reinstall ubuntu-keyring ubuntu-extras-keyring

```

Depending on what results, we can still keep in mind to delete the keys and fetch them again, see if that re-establishes the path.

[INDENT][INDENT]if I know better
[INDENT][INDENT][INDENT]I would do better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-12-07
Whew ....

```
stephen@stephen-desktop:~$ cat /var/log/syslog
Dec  7 07:52:59 stephen-desktop anacron[6805]: Job `cron.daily' terminated
Dec  7 07:52:59 stephen-desktop anacron[6805]: Normal exit (1 job run)
Dec  7 08:17:01 stephen-desktop CRON[7810]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  7 08:52:05 stephen-desktop dhclient: DHCPREQUEST of 10.0.0.14 on eth0 to 10.0.0.1 port 67 (xid=0x93a3f09)
Dec  7 08:52:05 stephen-desktop dhclient: DHCPACK of 10.0.0.14 from 10.0.0.1
Dec  7 08:52:05 stephen-desktop dhclient: bound to 10.0.0.14 -- renewal in 39544 seconds.
Dec  6 23:58:47 stephen-desktop NetworkManager[1020]: <info> kernel firmware directory '/lib/firmware' changed
Dec  7 08:52:05 stephen-desktop NetworkManager[1020]: <info> (eth0): DHCPv4 state changed reboot -> renew
Dec  7 08:52:05 stephen-desktop NetworkManager[1020]: <info>   address 10.0.0.14
Dec  7 08:52:05 stephen-desktop NetworkManager[1020]: <info>   prefix 24 (255.255.255.0)
Dec  7 08:52:05 stephen-desktop NetworkManager[1020]: <info>   gateway 10.0.0.1
Dec  7 08:52:05 stephen-desktop NetworkManager[1020]: <info>   hostname 'stephen-desktop'
Dec  7 08:52:05 stephen-desktop NetworkManager[1020]: <info>   nameserver '10.0.0.1'
Dec  7 08:52:05 stephen-desktop NetworkManager[1020]: <info>   domain name 'home'
Dec  7 08:52:05 stephen-desktop dbus[730]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Dec  7 08:52:05 stephen-desktop dbus[730]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec  7 09:17:01 stephen-desktop CRON[8083]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  7 10:03:11 stephen-desktop kernel: [39679.960037] usb 1-3: new high-speed USB device number 5 using ehci-pci
Dec  7 10:03:11 stephen-desktop kernel: [39680.092440] usb 1-3: New USB device found, idVendor=0424, idProduct=2514
Dec  7 10:03:11 stephen-desktop kernel: [39680.092452] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Dec  7 10:03:11 stephen-desktop kernel: [39680.092875] hub 1-3:1.0: USB hub found
Dec  7 10:03:11 stephen-desktop kernel: [39680.093053] hub 1-3:1.0: 4 ports detected
Dec  7 10:03:11 stephen-desktop kernel: [39680.364034] usb 1-3.3: new high-speed USB device number 6 using ehci-pci
Dec  7 10:03:11 stephen-desktop kernel: [39680.688928] usb 1-3.3: New USB device found, idVendor=046d, idProduct=081a
Dec  7 10:03:11 stephen-desktop kernel: [39680.688942] usb 1-3.3: New USB device strings: Mfr=0, Product=0, SerialNumber=2
Dec  7 10:03:11 stephen-desktop kernel: [39680.688949] usb 1-3.3: SerialNumber: C18D2690
Dec  7 10:03:11 stephen-desktop kernel: [39680.689421] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081a)
Dec  7 10:03:11 stephen-desktop kernel: [39680.786285] input: UVC Camera (046d:081a) as /devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.3/1-3.3:1.0/input/input19
Dec  7 10:03:13 stephen-desktop kernel: [39681.948671] usb_audio: Warning! Unlikely big volume range (=6144), cval->res is probably wrong.
Dec  7 10:03:13 stephen-desktop mtp-probe: checking bus 1, device 6: "/sys/devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.3"
Dec  7 10:03:13 stephen-desktop mtp-probe: bus: 1, device: 6 was not an MTP device
Dec  7 10:03:13 stephen-desktop rtkit-daemon[1828]: Successfully made thread 8309 of process 2750 (n/a) owned by '1000' RT at priority 5.
Dec  7 10:03:13 stephen-desktop rtkit-daemon[1828]: Supervising 5 threads of 1 processes of 1 users.
Dec  7 10:17:01 stephen-desktop CRON[8670]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  7 11:17:01 stephen-desktop CRON[8973]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  7 11:22:16 stephen-desktop dbus[730]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Dec  7 11:22:16 stephen-desktop kernel: [39681.948682] usb_audio: [5] FU [Mic Capture Volume] ch = 1, val = 1536/7680/1systemd-hostnamed[9005]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Dec  7 11:22:16 stephen-desktop dbus[730]: [system] Successfully activated service 'org.freedesktop.hostname1'
Dec  7 11:56:21 stephen-desktop kernel: [46470.227521] perf samples too long (2505 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Dec  7 11:56:31 stephen-desktop dbus[730]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Dec  7 11:56:31 stephen-desktop kernel: [46480.702506] systemd-hostnamed[9326]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Dec  7 11:56:31 stephen-desktop dbus[730]: [system] Successfully activated service 'org.freedesktop.hostname1'
Dec  7 12:17:01 stephen-desktop CRON[9928]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  7 13:17:01 stephen-desktop CRON[10300]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  7 13:50:36 stephen-desktop dbus[730]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Dec  7 13:50:37 stephen-desktop kernel: [53326.713906] systemd-hostnamed[10564]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Dec  7 13:50:37 stephen-desktop dbus[730]: [system] Successfully activated service 'org.freedesktop.hostname1'
Dec  7 14:10:06 stephen-desktop dbus[730]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Dec  7 14:10:06 stephen-desktop dbus[730]: [system] Successfully activated service 'org.freedesktop.hostname1'
Dec  7 14:10:06 stephen-desktop kernel: [54495.068140] systemd-hostnamed[10741]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Dec  7 14:17:01 stephen-desktop CRON[10806]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  7 15:17:01 stephen-desktop CRON[11119]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec  7 16:17:01 stephen-desktop CRON[11410]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```


```
stephen@stephen-desktop:~$ cat /var/log/kern.log
Dec  7 10:03:11 stephen-desktop kernel: [39679.960037] usb 1-3: new high-speed USB device number 5 using ehci-pci
Dec  7 10:03:11 stephen-desktop kernel: [39680.092440] usb 1-3: New USB device found, idVendor=0424, idProduct=2514
Dec  7 10:03:11 stephen-desktop kernel: [39680.092452] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Dec  7 10:03:11 stephen-desktop kernel: [39680.092875] hub 1-3:1.0: USB hub found
Dec  7 10:03:11 stephen-desktop kernel: [39680.093053] hub 1-3:1.0: 4 ports detected
Dec  7 10:03:11 stephen-desktop kernel: [39680.364034] usb 1-3.3: new high-speed USB device number 6 using ehci-pci
Dec  7 10:03:11 stephen-desktop kernel: [39680.688928] usb 1-3.3: New USB device found, idVendor=046d, idProduct=081a
Dec  7 10:03:11 stephen-desktop kernel: [39680.688942] usb 1-3.3: New USB device strings: Mfr=0, Product=0, SerialNumber=2
Dec  7 10:03:11 stephen-desktop kernel: [39680.688949] usb 1-3.3: SerialNumber: C18D2690
Dec  7 10:03:11 stephen-desktop kernel: [39680.689421] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081a)
Dec  7 10:03:11 stephen-desktop kernel: [39680.786285] input: UVC Camera (046d:081a) as /devices/pci0000:00/0000:00:02.1/usb1/1-3/1-3.3/1-3.3:1.0/input/input19
Dec  7 10:03:13 stephen-desktop kernel: [39681.948671] usb_audio: Warning! Unlikely big volume range (=6144), cval->res is probably wrong.
Dec  7 11:22:16 stephen-desktop kernel: [39681.948682] usb_audio: [5] FU [Mic Capture Volume] ch = 1, val = 1536/7680/1systemd-hostnamed[9005]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Dec  7 11:56:21 stephen-desktop kernel: [46470.227521] perf samples too long (2505 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
```


The dmesg command is so large, I can't even get all of it on the screen at one time to scroll up to let me copy it, but here's what I could copy.  And since I haven't added any new USB devices in at least 2 years, I have no idea what that reference is.

```
[    0.186756] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.186832] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.186907] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.186983] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.187059] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.187134] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0
[    0.187308] ACPI: Enabled 1 GPEs in block 20 to 5F
[    0.187315] ACPI: \_SB_.PCI0: notify handler is installed
[    0.187371] Found 1 acpi root devices
[    0.187459] vgaarb: setting as boot device: PCI:0000:03:00.0
[    0.187459] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.187459] vgaarb: loaded
[    0.187459] vgaarb: bridge control possible 0000:03:00.0
[    0.187459] SCSI subsystem initialized
[    0.187459] libata version 3.00 loaded.
[    0.187459] ACPI: bus type USB registered
[    0.187459] usbcore: registered new interface driver usbfs
[    0.187459] usbcore: registered new interface driver hub
[    0.187459] usbcore: registered new device driver usb
[    0.188082] PCI: Using ACPI for IRQ routing
[    0.189164] PCI: pci_cache_line_size set to 64 bytes
[    0.189202] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.189205] e820: reserve RAM buffer [mem 0xbfee0000-0xbfffffff]
[    0.189310] NetLabel: Initializing
[    0.189311] NetLabel:  domain hash size = 128
[    0.189312] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.189325] NetLabel:  unlabeled traffic allowed by default
[    0.189340] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.189340] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[    0.189340] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.190089] Switched to clocksource hpet
[    0.194315] AppArmor: AppArmor Filesystem Enabled
[    0.194348] pnp: PnP ACPI init
[    0.194363] ACPI: bus type PNP registered
[    0.194500] system 00:00: [io  0x1000-0x107f] has been reserved
[    0.194503] system 00:00: [io  0x1080-0x10ff] has been reserved
[    0.194506] system 00:00: [io  0x1400-0x147f] has been reserved
[    0.194509] system 00:00: [io  0x1480-0x14ff] has been reserved
[    0.194514] system 00:00: [io  0x1800-0x187f] has been reserved
[    0.194516] system 00:00: [io  0x1880-0x18ff] has been reserved
[    0.194521] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.194620] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.194622] system 00:01: [io  0x0800-0x0801] has been reserved
[    0.194625] system 00:01: [io  0x0290-0x0297] has been reserved
[    0.194628] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.194639] pnp 00:02: [dma 4]
[    0.194657] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.194736] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.194775] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.194799] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.194831] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.194970] pnp 00:07: [dma 2]
[    0.195000] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.195226] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.195536] pnp 00:09: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.196253] system 00:0a: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.196256] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.196393] system 00:0b: [mem 0x000cda00-0x000cffff] has been reserved
[    0.196396] system 00:0b: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.196398] system 00:0b: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.196401] system 00:0b: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.196403] system 00:0b: [mem 0xfefff000-0xfefff0ff] has been reserved
[    0.196406] system 00:0b: [mem 0xbfee0000-0xbfefffff] could not be reserved
[    0.196409] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
[    0.196411] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.196414] system 00:0b: [mem 0x00100000-0xbfedffff] could not be reserved
[    0.196417] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.196420] system 00:0b: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.196422] system 00:0b: [mem 0xfefff000-0xfeffffff] could not be reserved
[    0.196425] system 00:0b: [mem 0xfff80000-0xfff80fff] has been reserved
[    0.196428] system 00:0b: [mem 0xfff90000-0xfffbffff] has been reserved
[    0.196431] system 00:0b: [mem 0xfffed000-0xfffeffff] has been reserved
[    0.196434] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.196441] pnp: PnP ACPI: found 12 devices
[    0.196442] ACPI: bus type PNP unregistered
[    0.196445] PnPBIOS: Disabled by ACPI PNP
[    0.233312] pci 0000:00:06.0: PCI bridge to [bus 01]
[    0.233316] pci 0000:00:06.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.233320] pci 0000:00:0e.0: PCI bridge to [bus 02]
[    0.233323] pci 0000:00:0e.0:   bridge window [io  0x9000-0xafff]
[    0.233325] pci 0000:00:0e.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    0.233329] pci 0000:00:0f.0: PCI bridge to [bus 03]
[    0.233331] pci 0000:00:0f.0:   bridge window [io  0x8000-0x8fff]
[    0.233334] pci 0000:00:0f.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.233337] pci 0000:00:0f.0:   bridge window [mem 0xd8000000-0xe7ffffff 64bit pref]
[    0.233341] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.233343] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.233345] pci_bus 0000:00: resource 6 [mem 0xc0000000-0xf3ffffff]
[    0.233348] pci_bus 0000:00: resource 7 [mem 0xf4000000-0xfcffffffff]
[    0.233350] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.233353] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.233355] pci_bus 0000:01: resource 5 [mem 0x000a0000-0x000bffff]
[    0.233358] pci_bus 0000:01: resource 6 [mem 0xc0000000-0xf3ffffff]
[    0.233360] pci_bus 0000:01: resource 7 [mem 0xf4000000-0xfcffffffff]
[    0.233363] pci_bus 0000:02: resource 0 [io  0x9000-0xafff]
[    0.233365] pci_bus 0000:02: resource 1 [mem 0xfdd00000-0xfddfffff]
[    0.233368] pci_bus 0000:03: resource 0 [io  0x8000-0x8fff]
[    0.233370] pci_bus 0000:03: resource 1 [mem 0xfb000000-0xfcffffff]
[    0.233372] pci_bus 0000:03: resource 2 [mem 0xd8000000-0xe7ffffff 64bit pref]
[    0.233406] NET: Registered protocol family 2
[    0.233599] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.233622] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.233663] TCP: Hash tables configured (established 8192 bind 8192)
[    0.233697] TCP: reno registered
[    0.233699] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.233710] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.233767] NET: Registered protocol family 1
[    0.234017] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[    0.304339] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.304488] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.304530] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.304572] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.304615] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.304659] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.304709] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.304762] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.304817] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.304835] pci 0000:03:00.0: Video device with shadowed ROM
[    0.304843] PCI: CLS 32 bytes, default 64
[    0.304901] Trying to unpack rootfs image as initramfs...
[    0.642191] Freeing initrd memory: 18492K (f5bd2000 - f6de1000)
[    0.642369] microcode: AMD CPU family 0xf not supported
[    0.642371] Scanning for low memory corruption every 60 seconds
[    0.642632] Initialise system trusted keyring
[    0.642675] audit: initializing netlink socket (disabled)
[    0.642687] type=2000 audit(1449460924.640:1): initialized
[    0.663181] bounce pool size: 64 pages
[    0.663192] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.664532] zbud: loaded
[    0.664624] VFS: Disk quotas dquot_6.5.2
[    0.664665] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.665141] fuse init (API version 7.22)
[    0.665232] msgmni has been set to 1697
[    0.665302] Key type big_key registered
[    0.665929] Key type asymmetric registered
[    0.665931] Asymmetric key parser 'x509' registered
[    0.665964] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.666005] io scheduler noop registered
[    0.666007] io scheduler deadline registered (default)
[    0.666032] io scheduler cfq registered
[    0.666146] pcieport 0000:00:0e.0: irq 40 for MSI/MSI-X
[    0.666189] pcieport 0000:00:0f.0: irq 41 for MSI/MSI-X
[    0.666239] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.666257] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.666316] ipmi message handler version 39.2
[    0.666393] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.666397] ACPI: Power Button [PWRB]
[    0.666445] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.666447] ACPI: Power Button [PWRF]
[    0.666495] ACPI: Fan [FAN] (on)
[    0.666732] ACPI: [Package] has zero elements (f733d500)
[    0.666734] ACPI: Invalid passive threshold
[    0.666922] thermal LNXTHERM:00: registered as thermal_zone0
[    0.666924] ACPI: Thermal Zone [THRM] (40 C)
[    0.666949] GHES: HEST is not enabled!
[    0.667013] isapnp: Scanning for PnP cards...
[    0.672054] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.692421] 00:08: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.693505] Linux agpgart interface v0.103
[    0.694811] brd: module loaded
[    0.695406] loop: module loaded
[    0.695868] libphy: Fixed MDIO Bus: probed
[    0.695980] tun: Universal TUN/TAP device driver, 1.6
[    0.695982] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.696048] PPP generic driver version 2.4.2
[    0.696082] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.696085] ehci-pci: EHCI PCI platform driver
[    0.696214] ehci-pci 0000:00:02.1: EHCI Host Controller
[    0.696222] ehci-pci 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.696230] ehci-pci 0000:00:02.1: debug port 1
[    0.696258] ehci-pci 0000:00:02.1: cache line size of 32 is not supported
[    0.696279] ehci-pci 0000:00:02.1: irq 22, io mem 0xfe02e000
[    0.708019] ehci-pci 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.708067] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.708069] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.708071] usb usb1: Product: EHCI Host Controller
[    0.708073] usb usb1: Manufacturer: Linux 3.13.0-71-generic ehci_hcd
[    0.708075] usb usb1: SerialNumber: 0000:00:02.1
[    0.708161] hub 1-0:1.0: USB hub found
[    0.708168] hub 1-0:1.0: 10 ports detected
[    0.708333] ehci-platform: EHCI generic platform driver
[    0.708341] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.708342] ohci-pci: OHCI PCI platform driver
[    0.708438] ohci-pci 0000:00:02.0: OHCI PCI host controller
[    0.708442] ohci-pci 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.708466] ohci-pci 0000:00:02.0: irq 23, io mem 0xfe02f000
[    0.766044] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.766047] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.766049] usb usb2: Product: OHCI PCI host controller
[    0.766051] usb usb2: Manufacturer: Linux 3.13.0-71-generic ohci_hcd
[    0.766053] usb usb2: SerialNumber: 0000:00:02.0
[    0.766154] hub 2-0:1.0: USB hub found
[    0.766162] hub 2-0:1.0: 10 ports detected
[    0.766346] ohci-platform: OHCI generic platform driver
[    0.766358] uhci_hcd: USB Universal Host Controller Interface driver
[    0.766433] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.766839] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.766844] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.766941] mousedev: PS/2 mouse device common for all mice
[    0.767049] rtc_cmos 00:04: RTC can wake from S4
[    0.767177] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.767211] rtc_cmos 00:04: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.767275] device-mapper: uevent: version 1.0.3
[    0.767330] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.767347] platform eisa.0: Probing EISA bus 0
[    0.767350] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.767352] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.767355] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.767357] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.767359] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.767362] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.767364] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.767366] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.767368] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.767370] platform eisa.0: EISA: Detected 0 cards
[    0.767376] cpufreq-nforce2: No nForce2 chipset.
[    0.767380] ledtrig-cpu: registered to indicate activity on CPUs
[    0.767502] TCP: cubic registered
[    0.767602] NET: Registered protocol family 10
[    0.767775] NET: Registered protocol family 17
[    0.767787] Key type dns_resolver registered
[    0.767908] Using IPI No-Shortcut mode
[    0.767968] Loading compiled-in X.509 certificates
[    0.771007] Loaded X.509 cert 'Magrathea: Glacier signing key: 655fbfbc18c819b0f746ac96ca2739056cce87c5'
[    0.771018] registered taskstats version 1
[    0.784819] Key type trusted registered
[    0.808821] Key type encrypted registered
[    0.808826] AppArmor: AppArmor sha1 policy hashing enabled
[    0.808828] IMA: No TPM chip found, activating TPM-bypass!
[    0.809027] regulator-dummy: disabling
[    0.809061]   Magic number: 11:943:8
[    0.809169] rtc_cmos 00:04: setting system clock to 2015-12-07 04:02:05 UTC (1449460925)
[    0.809299] powernow-k8: fid 0x14 (2800 MHz), vid 0x8
[    0.809301] powernow-k8: fid 0x12 (2600 MHz), vid 0xa
[    0.809302] powernow-k8: fid 0x10 (2400 MHz), vid 0xc
[    0.809304] powernow-k8: fid 0xe (2200 MHz), vid 0xe
[    0.809305] powernow-k8: fid 0xc (2000 MHz), vid 0x10
[    0.809306] powernow-k8: fid 0xa (1800 MHz), vid 0x10
[    0.809308] powernow-k8: fid 0x2 (1000 MHz), vid 0x12
[    0.809331] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (2 cpu cores) (version 2.20.00)
[    0.809336] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.809337] EDD information not available.
[    0.809370] PM: Hibernation image not present or could not be loaded.
[    1.020517] isapnp: No Plug & Play device found
[    1.020929] Freeing unused kernel memory: 880K (c19c1000 - c1a9d000)
[    1.020967] Write protecting the kernel text: 6564k
[    1.021031] Write protecting the kernel read-only data: 2780k
[    1.021033] NX-protecting the kernel data: 5724k
[    1.033065] systemd-udevd[95]: starting version 204
[    1.060928] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.061183] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[    1.080904] Floppy drive(s): fd0 is 1.44M
[    1.101358] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    1.102327] FDC 0 is a post-1991 82077
[    1.156114] firewire_ohci 0000:01:0b.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x2
[    1.540016] usb 2-4: new full-speed USB device number 2 using ohci-pci
[    1.584518] forcedeth 0000:00:08.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1e:8c:6d:0a:d2
[    1.584521] forcedeth 0000:00:08.0: highdma csum vlan pwrctl mgmt gbit lnktim msi desc-v3
[    1.584692] sata_nv 0000:00:05.0: version 3.5
[    1.584940] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    1.584959] sata_nv 0000:00:05.0: Using SWNCQ mode
[    1.585653] scsi0 : sata_nv
[    1.585730] scsi1 : sata_nv
[    1.585763] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xdc00 irq 20
[    1.585766] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xdc08 irq 20
[    1.586007] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[    1.586014] sata_nv 0000:00:05.1: Using SWNCQ mode
[    1.586716] scsi2 : sata_nv
[    1.586780] scsi3 : sata_nv
[    1.586813] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc800 irq 23
[    1.586815] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc808 irq 23
[    1.587031] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 22
[    1.587039] sata_nv 0000:00:05.2: Using SWNCQ mode
[    1.587687] scsi4 : sata_nv
[    1.587756] scsi5 : sata_nv
[    1.587790] ata5: SATA max UDMA/133 cmd 0xc400 ctl 0xc000 bmdma 0xb400 irq 22
[    1.587793] ata6: SATA max UDMA/133 cmd 0xbc00 ctl 0xb800 bmdma 0xb408 irq 22
[    1.587811] pata_amd 0000:00:04.0: version 0.4.1
[    1.588396] scsi6 : pata_amd
[    1.588457] scsi7 : pata_amd
[    1.588491] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.588493] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.656087] firewire_core 0000:01:0b.0: created device fw0: GUID 001e8c000018fdaa, S400
[    1.752436] ata7.00: HPA detected: current 240119615, native 240121728
[    1.752442] ata7.00: ATA-7: Maxtor 4R120L0, RAMB1TU0, max UDMA/133
[    1.752445] ata7.00: 240119615 sectors, multi 1: LBA48 
[    1.752452] ata7: nv_mode_filter: 0x7f39f&0x7f39f->0x7f39f, BIOS=0x7f000 (0xc7000000) ACPI=0x7f01f (15:600:0x13)
[    1.764027] usb 2-4: New USB device found, idVendor=045e, idProduct=0745
[    1.764030] usb 2-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.764032] usb 2-4: Product: Microsoft\xffffffc2\xffffffae 2.4GHz Transceiver v6.0
[    1.764034] usb 2-4: Manufacturer: Microsoft
[    1.774495] hidraw: raw HID events driver (C) Jiri Kosina
[    1.775051] ata7.00: configured for UDMA/133
[    1.813223] usbcore: registered new interface driver usbhid
[    1.813226] usbhid: USB HID core driver
[    1.817209] input: Microsoft Microsoft\xffffffc2\xffffffae 2.4GHz Transceiver v6.0 as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.0/input/input5
[    1.817285] hid-generic 0003:045E:0745.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft\xffffffc2\xffffffae 2.4GHz Transceiver v6.0] on usb-0000:00:02.0-4/input0
[    1.818533] input: Microsoft Microsoft\xffffffc2\xffffffae 2.4GHz Transceiver v6.0 as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.1/input/input6
[    1.818608] hid-generic 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft\xffffffc2\xffffffae 2.4GHz Transceiver v6.0] on usb-0000:00:02.0-4/input1
[    1.838163] input: Microsoft Microsoft\xffffffc2\xffffffae 2.4GHz Transceiver v6.0 as /devices/pci0000:00/0000:00:02.0/usb2/2-4/2-4:1.2/input/input7
[    1.838261] hid-generic 0003:045E:0745.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Microsoft Microsoft\xffffffc2\xffffffae 2.4GHz Transceiver v6.0] on usb-0000:00:02.0-4/input2
[    1.900017] ata5: SATA link down (SStatus 0 SControl 300)
[    2.052029] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.052031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.060269] ata1.00: ATA-7: Maxtor 6Y080M0, YAR51EW0, max UDMA/133
[    2.060272] ata1.00: 160086528 sectors, multi 1: LBA 
[    2.076205] ata3.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L08, max UDMA/100
[    2.076281] ata1.00: configured for UDMA/133
[    2.076421] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y080M0   YAR5 PQ: 0 ANSI: 5
[    2.076558] sd 0:0:0:0: [sda] 160086528 512-byte logical blocks: (81.9 GB/76.3 GiB)
[    2.076602] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.076609] sd 0:0:0:0: [sda] Write Protect is off
[    2.076612] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.076636] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.080513]  sda: sda1
[    2.080703] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.108121] ata3.00: configured for UDMA/100
[    2.388021] ata2: SATA link down (SStatus 0 SControl 300)
[    2.389247] scsi 2:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L08 PQ: 0 ANSI: 5
[    2.392201] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.392203] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.392312] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.392417] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.704020] ata4: SATA link down (SStatus 0 SControl 300)
[    3.016019] ata6: SATA link down (SStatus 0 SControl 300)
[    3.016168] scsi 6:0:0:0: Direct-Access     ATA      Maxtor 4R120L0   RAMB PQ: 0 ANSI: 5
[    3.016343] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    3.016357] sd 6:0:0:0: [sdb] 240119615 512-byte logical blocks: (122 GB/114 GiB)
[    3.016401] ata8: port disabled--ignoring
[    3.016496] sd 6:0:0:0: [sdb] Write Protect is off
[    3.016500] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.016545] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.049708]  sdb: sdb1 sdb2 < sdb5 >
[    3.050055] sd 6:0:0:0: [sdb] Attached SCSI disk
[    4.089507] random: nonblocking pool is initialized
[    4.217790] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   38.065804] Adding 3141628k swap on /dev/sdb5.  Priority:-1 extents:1 across:3141628k FS
[   39.556717] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   39.809925] systemd-udevd[357]: starting version 204
[   40.786681] parport_pc 00:09: reported by Plug and Play ACPI
[   40.786710] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   40.961248] lp0: using parport0 (interrupt-driven).
[   41.006579] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   41.101022] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   41.101028] ACPI Warning: 0x00001c40-0x00001c7f SystemIO conflicts with Region \_SB_.PCI0.SM01 1 (20131115/utaddress-251)
[   41.101034] ACPI Warning: 0x00001c40-0x00001c7f SystemIO conflicts with Region \_SB_.PCI0.SM00 2 (20131115/utaddress-251)
[   41.101038] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   41.139009] ppdev: user-space parallel port driver
[   41.183280] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.300570] type=1400 audit(1449460965.989:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=412 comm="apparmor_parser"
[   41.300579] type=1400 audit(1449460965.989:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=412 comm="apparmor_parser"
[   41.300583] type=1400 audit(1449460965.989:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=412 comm="apparmor_parser"
[   41.301064] type=1400 audit(1449460965.989:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=412 comm="apparmor_parser"
[   41.301071] type=1400 audit(1449460965.989:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=412 comm="apparmor_parser"
[   41.301317] type=1400 audit(1449460965.989:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=412 comm="apparmor_parser"
[   41.755764] device-mapper: multipath: version 1.6.0 loaded
[   41.884222] [drm] Initialized drm 1.1.0 20060810
[   42.127306] kvm: disabled by bios
[   42.145172] kvm: disabled by bios
[   42.575936] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   42.575949] hda_intel: msi for device 1043:81f6 set to 0
[   42.575987] hda-intel 0000:00:06.1: Disabling 64bit DMA
[   42.580337] hda-intel 0000:00:06.1: Enable delay in RIRB handling
[   43.332479] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[   43.528031] autoconfig: line_outs=4 (0x12/0x16/0x24/0x25/0x0) type:line
[   43.528036]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   43.528038]    hp_outs=1 (0x11/0x0/0x0/0x0/0x0)
[   43.528039]    mono: mono_out=0x0
[   43.528041]    dig-out=0x1b/0x0
[   43.528042]    inputs:
[   43.528044]      Front Mic=0x14
[   43.528045]      Rear Mic=0x17
[   43.528047]      Line=0x15
[   43.528048]      CD=0x18
[   43.895024] nvidia: module license 'NVIDIA' taints kernel.
[   43.895029] Disabling lock debugging due to kernel taint
[   43.911840] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   43.918895] ACPI: PCI Interrupt Link [APC6] enabled at IRQ 16
[   43.918922] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=none
[   43.919267] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:03:00.0 on minor 0
[   43.919275] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.128  Wed Aug 26 10:41:50 PDT 2015
[   44.553794] init: failsafe main process (697) killed by TERM signal
[   45.060245] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:06.1/sound/card0/input13
[   45.060390] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:06.1/sound/card0/input12
[   45.060511] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:06.1/sound/card0/input11
[   45.060627] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:06.1/sound/card0/input10
[   45.060744] input: HDA NVidia Line as /devices/pci0000:00/0000:00:06.1/sound/card0/input9
[   45.060862] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:06.1/sound/card0/input8
[   45.061629] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   45.061638] hda_intel: Disabling MSI
[   45.061647] hda-intel 0000:03:00.1: Handle VGA-switcheroo audio client
[   45.061689] hda-intel 0000:03:00.1: Disabling 64bit DMA
[   45.064996] hda-intel 0000:03:00.1: Enable delay in RIRB handling
[   45.078156] type=1400 audit(1449460969.765:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=804 comm="apparmor_parser"
[   45.078166] type=1400 audit(1449460969.765:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=804 comm="apparmor_parser"
[   45.078630] type=1400 audit(1449460969.765:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=804 comm="apparmor_parser"
[   45.165379] type=1400 audit(1449460969.853:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=814 comm="apparmor_parser"
[   45.794031] Bluetooth: Core ver 2.17
[   45.794062] NET: Registered protocol family 31
[   45.794063] Bluetooth: HCI device and connection manager initialized
[   45.794072] Bluetooth: HCI socket layer initialized
[   45.794075] Bluetooth: L2CAP socket layer initialized
[   45.794080] Bluetooth: SCO socket layer initialized
[   45.999641] init: cups main process (805) killed by HUP signal
[   45.999655] init: cups main process ended, respawning
[   46.012108] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:0f.0/0000:03:00.1/sound/card1/input17
[   46.012207] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:0f.0/0000:03:00.1/sound/card1/input16
[   46.012272] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:0f.0/0000:03:00.1/sound/card1/input15
[   46.012325] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:0f.0/0000:03:00.1/sound/card1/input14
[   46.070606] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   46.070610] Bluetooth: BNEP filters: protocol multicast
[   46.070620] Bluetooth: BNEP socket layer initialized
[   46.163108] Bluetooth: RFCOMM TTY layer initialized
[   46.163120] Bluetooth: RFCOMM socket layer initialized
[   46.163126] Bluetooth: RFCOMM ver 1.11
[   46.931733] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
```


```
stephen@stephen-desktop:~$ ls -al .gnupg
total 68
drwx------  2 stephen stephen  4096 Dec  2 00:09 .
drwxr-xr-x 54 stephen stephen  4096 Dec  7 11:24 ..
-rw-------  1 stephen stephen  9398 May 22  2015 gpg.conf
-rw-------  1 stephen stephen  9437 May 22  2015 gpg.conf~
-rw-------  1 stephen stephen 15436 Oct 28 12:12 pubring.gpg
-rw-------  1 stephen stephen 15436 Oct 28 12:12 pubring.gpg~
-rw-------  1 stephen stephen     0 Jan 24  2013 secring.gpg
-rw-------  1 stephen stephen  1200 Oct 28 12:12 trustdb.gpg
stephen@stephen-desktop:~$ ls -al .gnupg/pubring.gpg
-rw------- 1 stephen stephen 15436 Oct 28 12:12 .gnupg/pubring.gpg
stephen@stephen-desktop:~$ ls -al .gnupg/secring.gpg
-rw------- 1 stephen stephen 0 Jan 24  2013 .gnupg/secring.gpg

```


```
stephen@stephen-desktop:~$ sudo apt-get --reinstall install ubuntu-keyring
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-66 linux-headers-3.13.0-66-generic
  linux-image-3.13.0-66-generic linux-image-extra-3.13.0-66-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 16.7 kB of archives.
After this operation, 0 B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  ubuntu-keyring
Install these packages without verification? [y/N] y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main ubuntu-keyring all 2012.05.19 [16.7 kB]
Fetched 16.7 kB in 0s (47.7 kB/s)         
(Reading database ... 718815 files and directories currently installed.)
Preparing to unpack .../ubuntu-keyring_2012.05.19_all.deb ...
Unpacking ubuntu-keyring (2012.05.19) over (2012.05.19) ...
Setting up ubuntu-keyring (2012.05.19) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
```



```
stephen@stephen-desktop:~$ sudo apt-get install --reinstall ubuntu-keyring ubuntu-extras-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-66 linux-headers-3.13.0-66-generic
  linux-image-3.13.0-66-generic linux-image-extra-3.13.0-66-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 3,424 B/20.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  ubuntu-keyring ubuntu-extras-keyring
Install these packages without verification? [y/N] y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main ubuntu-extras-keyring all 2010.09.27 [3,424 B]
Fetched 3,424 B in 0s (15.1 kB/s)                
(Reading database ... 718815 files and directories currently installed.)
Preparing to unpack .../ubuntu-keyring_2012.05.19_all.deb ...
Unpacking ubuntu-keyring (2012.05.19) over (2012.05.19) ...
Setting up ubuntu-keyring (2012.05.19) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
(Reading database ... 718815 files and directories currently installed.)
Preparing to unpack .../ubuntu-extras-keyring_2010.09.27_all.deb ...
Unpacking ubuntu-extras-keyring (2010.09.27) over (2010.09.27) ...
Setting up ubuntu-extras-keyring (2010.09.27) ...
Importing extras.ubuntu.com keyring
OK
Processing extras.ubuntu.com removal keyring
gpg: /etc/apt/trustdb.gpg: trustdb created
OK

```

---

### Post by Bashing-om on 2015-12-07
All looks fairly descent .
There is this :
> 
nvidia: module verification failed: signature and/or  required key missing - tainting kernel

we might want to look at in a different thread as the display driver has nothing to do with this thread.

And this do look promising :
```

Processing extras.ubuntu.com removal keyring
gpg: /etc/apt/trustdb.gpg: [color=green]trustdb created[/color]
OK

```

Reboot, is the GPG errors now gone ?

[INDENT][INDENT][INDENT]maybe YES
[/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-12-07
The "internal error" message I was getting on reboot did not show up this time, but apt-get update still shows all the missing gpg keys.  I have to run to school to watch my son play basketball for a while but will be back in a couple of hours.  I should have remembered my lessons from when I used to deal with Windows:  when things start going wrong and you've been diligent about keeping your anti-virus up-to-date and run regularly, then it's probably either a memory stick or the video driver.  I don't think I'm using an nVidea driver, I think I'm using the ubuntu driver that came with 14.04.

---

### Post by Bashing-om on 2015-12-07
StephenG; Shucks,

We could hope, no ?

OK .. I am in favor now of deleting these keys !
```

sudo apt-key del 16126D3A3E5C1192

```
then updating the repository
```

sudo apt-get update

```
You should get a NO_PUBKEY error instead of a BADSIG error and
```

sudo apt-key finger

```
should not find the key (called "Ubuntu Extras Archive Automatic Signing Key")

Now add the key back into the system:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192

```
The result of apt-key finger -now- should have
> 
pub   1024D/3E5C1192 2010-09-20
      Key fingerprint = C474 15DF F48C 0964 5B78  6094 1612 6D3A 3E5C 1192
uid                  Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

If this is so for this one key, repeat for the other two that are giving us the fits .

[INDENT][INDENT][INDENT]maybe now ?
[/INDENT][/INDENT][/INDENT]

---

### Post by StephenG on 2015-12-07
I did each key separately and got the same response for each -- seems to be the same as before.  I never did get BADSIG errors earlier, just that there was no pub-key.  To shorten the response, I redid them all together and here's the response:

```
stephen@stephen-desktop:~$ sudo apt-key del 3B4F6ACC0B21F32 40976EAF437D05B5 16126D3A3E5C1192
[sudo] password for stephen: 
OK
stephen@stephen-desktop:~$ sudo apt-get update
Ign http://archive.ubuntu.com trusty InRelease
Get:1 http://archive.ubuntu.com trusty-updates InRelease [64.4 kB]             
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:2 http://archive.canonical.com trusty Release.gpg [933 B]                  
Get:3 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Get:4 http://archive.ubuntu.com trusty-security InRelease [64.4 kB]            
Hit http://archive.canonical.com trusty Release                                
Ign http://archive.canonical.com trusty Release                                
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://extras.ubuntu.com trusty Release                                    
Ign http://archive.ubuntu.com trusty-security InRelease                        
Get:5 http://archive.ubuntu.com trusty Release.gpg [933 B]                     
Ign http://archive.canonical.com trusty/partner i386 Packages/DiffIndex        
Ign http://archive.ubuntu.com trusty-updates/main i386 Packages/DiffIndex      
Ign http://extras.ubuntu.com trusty/main i386 Packages/DiffIndex               
Ign http://archive.ubuntu.com trusty-updates/universe i386 Packages/DiffIndex  
Ign http://archive.ubuntu.com trusty-updates/multiverse i386 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Ign http://archive.ubuntu.com trusty-security/main i386 Packages/DiffIndex     
Ign http://archive.ubuntu.com trusty-security/universe i386 Packages/DiffIndex 
Ign http://archive.ubuntu.com trusty-security/multiverse i386 Packages/DiffIndex
Hit http://archive.ubuntu.com trusty-security/main Translation-en     
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en        
Hit http://archive.ubuntu.com trusty-security/universe Translation-en          
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://archive.ubuntu.com trusty Release                                   
Ign http://archive.ubuntu.com trusty Release                                   
Hit http://archive.ubuntu.com trusty-updates/main i386 Packages                
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://archive.ubuntu.com trusty-updates/universe i386 Packages            
Hit http://archive.ubuntu.com trusty-updates/multiverse i386 Packages          
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://archive.ubuntu.com trusty-security/main i386 Packages               
Hit http://archive.ubuntu.com trusty-security/universe i386 Packages
Hit http://archive.ubuntu.com trusty-security/multiverse i386 Packages
Ign http://archive.canonical.com trusty/partner Translation-en_US 
Ign http://archive.canonical.com trusty/partner Translation-en     
Ign http://archive.ubuntu.com trusty/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com trusty/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com trusty/multiverse i386 Packages/DiffIndex
Hit http://archive.ubuntu.com trusty/main Translation-en
Hit http://archive.ubuntu.com trusty/multiverse Translation-en
Hit http://archive.ubuntu.com trusty/universe Translation-en
Hit http://archive.ubuntu.com trusty/main i386 Packages
Hit http://archive.ubuntu.com trusty/universe i386 Packages
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages
Ign http://archive.ubuntu.com trusty-updates/main Translation-en_US
Ign http://archive.ubuntu.com trusty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com trusty-security/main Translation-en_US
Ign http://archive.ubuntu.com trusty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty-security/universe Translation-en_US
Ign http://archive.ubuntu.com trusty/main Translation-en_US
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
Fetched 131 kB in 7s (16.4 kB/s)                                               
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com trusty-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.ubuntu.com trusty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
```


The "finger" command seems to have still found the keys, as here:

```
stephen@stephen-desktop:~$ sudo apt-key finger
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
      Key fingerprint = 6302 39CC 130E 1A7F D81A  27B1 4097 6EAF 437D 05B5
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
      Key fingerprint = C598 6B4F 1257 FFA8 6632  CBA7 4618 1433 FBB7 5451
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024D/3E5C1192 2010-09-20
      Key fingerprint = C474 15DF F48C 0964 5B78  6094 1612 6D3A 3E5C 1192
uid                  Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

pub   4096R/C0B21F32 2012-05-11
      Key fingerprint = 790B C727 7767 219C 42C8  6F93 3B4F E6AC C0B2 1F32
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
      Key fingerprint = 8439 38DF 228D 22F7 B374  2BC0 D94A A3F0 EFE2 1092
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

pub   1024R/5BC3E400 2009-01-20
      Key fingerprint = A13A F8A1 602A A450 FDE7  3BCC 4A13 8206 5BC3 E400
uid                  Launchpad PPA for Jeffrey Ratcliffe

pub   1024R/EEA14886 2010-05-04
      Key fingerprint = 7B2C 3B08 89BF 5709 A105  D03A C251 8248 EEA1 4886
uid                  Launchpad VLC

gpg: [don't know]: invalid packet (ctb=2d)
gpg: keydb_search_next failed: invalid packet
```

The fact that the keys do not seem to have been deleted is borne out in the re-install command, wherein they were found and unchanged, as here:

```
stephen@stephen-desktop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192 3B4FE6ACC0B21F32 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.NmRemYtwqn --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192 3B4FE6ACC0B21F32 40976EAF437D05B5
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: requesting key C0B21F32 from hkp server keyserver.ubuntu.com
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 3
gpg:              unchanged: 3
```

Some of the threads about this issue seem to have had some luck completely deleting the trusted.gpg file and re-establishing it.  Any thoughts on that?

---

### Post by matt_symes on 2015-12-07
Hi

It may be worth checking that apt is actually using the correct keyring.

Can you post the output of this command.

```
apt-config dump | grep -i etc
```

Kind regards

---

### Post by StephenG on 2015-12-07
```
stephen@stephen-desktop:~$ apt-config dump | grep -i etc
Dir::Etc "etc/apt/";
Dir::Etc::sourcelist "sources.list";
Dir::Etc::sourceparts "sources.list.d";
Dir::Etc::vendorlist "vendors.list";
Dir::Etc::vendorparts "vendors.list.d";
Dir::Etc::main "apt.conf";
Dir::Etc::netrc "auth.conf";
Dir::Etc::parts "apt.conf.d";
Dir::Etc::preferences "preferences";
Dir::Etc::preferencesparts "preferences.d";
Dir::Etc::trusted "trusted.gpg";
Dir::Etc::trustedparts "trusted.gpg.d";

```

---

### Post by matt_symes on 2015-12-07
Hi

> **StephenG said:**
> ```
stephen@stephen-desktop:~$ apt-config dump | grep -i etc
Dir::Etc "etc/apt/";
Dir::Etc::sourcelist "sources.list";
Dir::Etc::sourceparts "sources.list.d";
Dir::Etc::vendorlist "vendors.list";
Dir::Etc::vendorparts "vendors.list.d";
Dir::Etc::main "apt.conf";
Dir::Etc::netrc "auth.conf";
Dir::Etc::parts "apt.conf.d";
Dir::Etc::preferences "preferences";
Dir::Etc::preferencesparts "preferences.d";
Dir::Etc::trusted "trusted.gpg";
Dir::Etc::trustedparts "trusted.gpg.d";

```

That looks fine.

Can you post the output of

```
ls -lh /usr/lib/apt/methods/gpgv
file /usr/lib/apt/methods/gpgv
```

Kind regards

---

### Post by StephenG on 2015-12-07
```
stephen@stephen-desktop:~$ ls -lh /usr/lib/apt/methods/gpgv
-rwxr-xr-x 1 root root 26K Aug  1 15:22 /usr/lib/apt/methods/gpgv
stephen@stephen-desktop:~$ file /usr/lib/apt/methods/gpgv
/usr/lib/apt/methods/gpgv: ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=45ce3e05118b1c8600aee30c535a803f81a2ce48, stripped

```

---

### Post by matt_symes on 2015-12-07
Hi

> **StephenG said:**
> ```
stephen@stephen-desktop:~$ ls -lh /usr/lib/apt/methods/gpgv
-rwxr-xr-x 1 root root 26K Aug  1 15:22 /usr/lib/apt/methods/gpgv
stephen@stephen-desktop:~$ file /usr/lib/apt/methods/gpgv
/usr/lib/apt/methods/gpgv: ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=45ce3e05118b1c8600aee30c535a803f81a2ce48, stripped

```

That also looks good. (You're on a 32 bit installation ?)

Open a terminal and copy and past this into it as case is important so the capital letters are required.

```
sudo apt-get -o Debug::Acquire::gpgv="true" update
```

Post back the full output into you next post. I'm just about to go to sleep though so I won't look at it until tomorrow.

Kind regards

---

### Post by StephenG on 2015-12-07
```
stephen@stephen-desktop:~$ sudo apt-get -o Debug::Acquire::gpgv="true" update
[sudo] password for stephen: 
Ign http://archive.ubuntu.com trusty InRelease
Get:1 http://archive.ubuntu.com trusty-updates InRelease [64.4 kB]             
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
inside VerifyGetSigners
89% [InRelease gpgv 15.5 kB] [1 InRelease 57.6 kB/64.4 kB 89%] [Connecting to egpgv path: /usr/bin/gpgv
Keyring file: /etc/apt/trusted.gpg
Keyring path: /etc/apt/trusted.gpg.d/
Preparing to exec: /usr/bin/gpgv /usr/bin/gpgv --ignore-time-conflict --status-fd 3 --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg /tmp/apt.sig.j3Bmvd /tmp/apt.data.MKu8CD
Read: [GNUPG:] SIG_ID O4zcJ18qcP09FfZkRVg/9DMsYHE 2015-11-25 1448452760
Read: [GNUPG:] GOODSIG C2518248EEA14886 Launchpad VLC
Got GOODSIG, key ID:GOODSIG C2518248EEA14886
Read: [GNUPG:] VALIDSIG 7B2C3B0889BF5709A105D03AC2518248EEA14886 2015-11-25 1448452760 0 4 0 1 2 01 7B2C3B0889BF5709A105D03AC2518248EEA14886
gpgv exited
gpgv succeeded
100% [Waiting for headers] [Waiting for headers] [Connecting to extras.ubuntu.cinside VerifyGetSigners
100% [1 InRelease gpgv 64.4 kB] [Waiting for headers] [Waiting for headers] [Cogpgv path: /usr/bin/gpgv
Keyring file: /etc/apt/trusted.gpg
Keyring path: /etc/apt/trusted.gpg.d/
Preparing to exec: /usr/bin/gpgv /usr/bin/gpgv --ignore-time-conflict --status-fd 3 --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg /tmp/apt.sig.7ALrMc /tmp/apt.data.dOvKVC
Read: [GNUPG:] ERRSIG 40976EAF437D05B5 17 10 01 1449515305 9
Read: [GNUPG:] NO_PUBKEY 40976EAF437D05B5
Got NO_PUBKEY 
Read: [GNUPG:] ERRSIG 3B4FE6ACC0B21F32 1 10 01 1449515305 9
Read: [GNUPG:] NO_PUBKEY 3B4FE6ACC0B21F32
Got NO_PUBKEY 
gpgv exited
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Get:2 http://archive.ubuntu.com trusty-security InRelease [64.4 kB]            
Get:3 http://archive.canonical.com trusty Release.gpg [933 B]                  
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
100% [Waiting for headers] [Connecting to extras.ubuntu.com (91.189.92.152)] [Winside VerifyGetSigners
100% [2 InRelease gpgv 64.4 kB] [Waiting for headers] [Waiting for headers] [Cogpgv path: /usr/bin/gpgv
Keyring file: /etc/apt/trusted.gpg
Keyring path: /etc/apt/trusted.gpg.d/
Preparing to exec: /usr/bin/gpgv /usr/bin/gpgv --ignore-time-conflict --status-fd 3 --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg /tmp/apt.sig.0qprdt /tmp/apt.data.dXYSIT
Read: [GNUPG:] ERRSIG 40976EAF437D05B5 17 10 01 1449511553 9
Read: [GNUPG:] NO_PUBKEY 40976EAF437D05B5
Got NO_PUBKEY 
Read: [GNUPG:] ERRSIG 3B4FE6ACC0B21F32 1 10 01 1449511553 9
Read: [GNUPG:] NO_PUBKEY 3B4FE6ACC0B21F32
Got NO_PUBKEY 
gpgv exited
Ign http://archive.ubuntu.com trusty-security InRelease                        
Hit http://archive.canonical.com trusty Release                                
100% [Waiting for headers] [Connecting to extras.ubuntu.com (91.189.92.152)] [Winside VerifyGetSigners
Get:4 http://archive.ubuntu.com trusty Release.gpg [933 B]                     
100% [Release gpgv 9,359 B] [Waiting for headers] [Connecting to extras.ubuntu.gpgv path: /usr/bin/gpgv
Keyring file: /etc/apt/trusted.gpg
Keyring path: /etc/apt/trusted.gpg.d/
Preparing to exec: /usr/bin/gpgv /usr/bin/gpgv --ignore-time-conflict --status-fd 3 --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_trusty_Release.gpg /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_trusty_Release
Read: [GNUPG:] ERRSIG 40976EAF437D05B5 17 10 00 1447444255 9
Read: [GNUPG:] NO_PUBKEY 40976EAF437D05B5
Got NO_PUBKEY 
Read: [GNUPG:] ERRSIG 3B4FE6ACC0B21F32 1 10 00 1447444255 9
Read: [GNUPG:] NO_PUBKEY 3B4FE6ACC0B21F32
Got NO_PUBKEY 
gpgv exited
Ign http://archive.canonical.com trusty Release                                
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://archive.ubuntu.com trusty-updates/main i386 Packages/DiffIndex      
Ign http://archive.ubuntu.com trusty-updates/universe i386 Packages/DiffIndex  
Ign http://archive.ubuntu.com trusty-updates/multiverse i386 Packages/DiffIndex
Ign http://archive.canonical.com trusty/partner i386 Packages/DiffIndex        
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Ign http://archive.ubuntu.com trusty-security/main i386 Packages/DiffIndex     
Ign http://archive.ubuntu.com trusty-security/universe i386 Packages/DiffIndex 
Ign http://archive.ubuntu.com trusty-security/multiverse i386 Packages/DiffIndex
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://archive.ubuntu.com trusty-security/main Translation-en              
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en        
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://archive.ubuntu.com trusty-security/universe Translation-en          
Hit http://archive.ubuntu.com trusty Release                                   
100% [Translation-en 2,769 kB] [Waiting for headers] [Waiting for headers] [Waiinside VerifyGetSigners
100% [Translation-en 2,769 kB] [Release gpgv 58.5 kB] [Waiting for headers] [Wagpgv path: /usr/bin/gpgv
Keyring file: /etc/apt/trusted.gpg
Keyring path: /etc/apt/trusted.gpg.d/
Preparing to exec: /usr/bin/gpgv /usr/bin/gpgv --ignore-time-conflict --status-fd 3 --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_trusty_Release.gpg /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty_Release
Read: [GNUPG:] ERRSIG 40976EAF437D05B5 17 10 00 1399558833 9
Read: [GNUPG:] NO_PUBKEY 40976EAF437D05B5
Got NO_PUBKEY 
Read: [GNUPG:] ERRSIG 3B4FE6ACC0B21F32 1 10 00 1399558833 9
Read: [GNUPG:] NO_PUBKEY 3B4FE6ACC0B21F32
Got NO_PUBKEY 
gpgv exited
Ign http://archive.ubuntu.com trusty Release                                   
Get:5 http://archive.ubuntu.com trusty-updates/main i386 Packages [643 kB]     
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:6 http://extras.ubuntu.com trusty Release.gpg [72 B]                      
Ign http://archive.canonical.com trusty/partner Translation-en_US              
Hit http://extras.ubuntu.com trusty Release             
94% [5 Packages 129 kB/643 kB 20%]inside VerifyGetSigners
94% [Release gpgv 11.9 kB] [5 Packages 129 kB/643 kB 20%]gpgv path: /usr/bin/gpgv
Keyring file: /etc/apt/trusted.gpg
Keyring path: /etc/apt/trusted.gpg.d/
Preparing to exec: /usr/bin/gpgv /usr/bin/gpgv --ignore-time-conflict --status-fd 3 --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg /var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_trusty_Release.gpg /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_trusty_Release
Read: [GNUPG:] ERRSIG 16126D3A3E5C1192 17 2 00 1431878463 9
Read: [GNUPG:] NO_PUBKEY 16126D3A3E5C1192
Got NO_PUBKEY 
gpgv exited
Ign http://extras.ubuntu.com trusty Release              
Ign http://extras.ubuntu.com trusty/main i386 Packages/DiffIndex
Hit http://extras.ubuntu.com trusty/main i386 Packages  
Get:7 http://archive.ubuntu.com trusty-updates/universe i386 Packages [330 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:8 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.1 kB]
Get:9 http://archive.ubuntu.com trusty-security/main i386 Packages [360 kB]
Get:10 http://archive.ubuntu.com trusty-security/universe i386 Packages [120 kB]
Get:11 http://archive.ubuntu.com trusty-security/multiverse i386 Packages [4,967 B]
Ign http://archive.ubuntu.com trusty/main i386 Packages/DiffIndex              
Ign http://archive.ubuntu.com trusty/universe i386 Packages/DiffIndex          
Ign http://archive.ubuntu.com trusty/multiverse i386 Packages/DiffIndex        
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                 
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Hit http://archive.ubuntu.com trusty/main i386 Packages                        
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages                  
Ign http://archive.ubuntu.com trusty-updates/main Translation-en_US            
Ign http://archive.ubuntu.com trusty-updates/multiverse Translation-en_US      
Ign http://archive.ubuntu.com trusty-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com trusty-security/main Translation-en_US           
Ign http://archive.ubuntu.com trusty-security/multiverse Translation-en_US     
Ign http://archive.ubuntu.com trusty-security/universe Translation-en_US       
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 1,603 kB in 11s (139 kB/s)                                             
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com trusty-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

```

---

### Post by matt_symes on 2015-12-08
Hi

```

Read: [GNUPG:] ERRSIG 40976EAF437D05B5 17 10 01 1449515305 9
Read: [GNUPG:] NO_PUBKEY 40976EAF437D05B5
Got NO_PUBKEY 
Read: [GNUPG:] ERRSIG 3B4FE6ACC0B21F32 1 10 01 1449515305 9
Read: [GNUPG:] NO_PUBKEY 3B4FE6ACC0B21F32
Got NO_PUBKEY 
```

apt calls gpgv to verify the signatures of the files it gets. The work is done in the file apt-pkg/contri/gpgv.cc. apt creates two temporary files, one containing the signature and the other containing the text to check the signature, that is passes into gpgv.

gpgv is saying that the signature is invalid. I'm still looking into this but there are a couple of things i want to verify just to check your system.

Please post the output of 

```
cat /etc/lsb-release; uname -a; getconf LONG_BIT
```

The above i think i know but i just want to tripple check.

```
apt-get --version 
```

```
/usr/bin/gpgv --version
```

```
ldd $(which apt-get)
```

```
sudo updatedb && locate libapt-pkg.so
```

```
/usr/bin/gpg --no-default-keyring --keyring /etc/apt/trusted.gpg --armor --export ftpmaster@ubuntu.com | wc -c
```

Have you tried another mirror after deleting all the files in /var/lib/apt/lists ?

You have an odd problem here :)

Kind regards

---

### Post by StephenG on 2015-12-08
```
stephen@stephen-desktop:~$ cat /etc/lsb-release; uname -a; getconf LONG_BIT
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
Linux stephen-desktop 3.13.0-71-generic #114-Ubuntu SMP Tue Dec 1 02:35:20 UTC 2015 i686 athlon i686 GNU/Linux
32
```


```
stephen@stephen-desktop:~$ apt-get --version
apt 1.0.1ubuntu2 for i386 compiled on Aug  1 2015 19:21:31
Supported modules:
*Ver: Standard .deb
*Pkg:  Debian dpkg interface (Priority 30)
 Pkg:  Debian APT solver interface (Priority -1000)
 S.L: 'deb' Standard Debian binary tree
 S.L: 'deb-src' Standard Debian source tree
 Idx: Debian Source Index
 Idx: Debian Package Index
 Idx: Debian Translation Index
 Idx: Debian dpkg status file
 Idx: EDSP scenario file
```


```
stephen@stephen-desktop:~$ /usr/bin/gpgv --version
gpgv (GnuPG) 1.4.16
Copyright (C) 2013 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

```

```
stephen@stephen-desktop:~$ ldd $(which apt-get)
	linux-gate.so.1 =>  (0xb7781000)
	libapt-pkg.so.4.12 => /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12 (0xb761d000)
	libapt-private.so.0.0 => /usr/lib/i386-linux-gnu/libapt-private.so.0.0 (0xb75e6000)
	libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xb74fd000)
	libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xb74e0000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb7332000)
	libutil.so.1 => /lib/i386-linux-gnu/libutil.so.1 (0xb732e000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xb7329000)
	libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xb730e000)
	libbz2.so.1.0 => /lib/i386-linux-gnu/libbz2.so.1.0 (0xb72fc000)
	liblzma.so.5 => /lib/i386-linux-gnu/liblzma.so.5 (0xb72d6000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xb7290000)
	/lib/ld-linux.so.2 (0xb7782000)
```


```
stephen@stephen-desktop:~$ sudo updatedb && locate libapt-pkg.so
[sudo] password for stephen: 
/usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
/usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0
```

```
stephen@stephen-desktop:~$ /usr/bin/gpg --no-default-keyring --keyring /etc/apt/trusted.gpg --armor --export ftpmaster@ubuntu.com | wc -c
20191
```

At this point, after so many queries and commands and suggestions by Bashing-Om, I can't really remember whether we even deleted all the files in /var/lib/apt/lists, but I do not remember switching mirrors at any time.  I have, in the past switched several times, thinking that there were faulty connections leading to corrupted downloads, but nothing improved with those "fixes."  From your explanation (and I appreciated that very much, as linux is still a great deal of mystery to me), it sounds as though either the gpgv info is corrupted thus it's not able to verify the integrity of the signature, or there is no info to verify, resulting in the same conclusion by the file.  Hence, maybe we need to delete and rebuild the gpgv file -- if that's possible.  I even don't mind re-installing the OS, but I hate to have to reconstruct my entire file system if there is any other fix.

---

### Post by Buntu Bunny on 2015-12-08
> **v3.xx said:**
> Try this fix
[http://ubuntuforums.org/showthread.php?t=1869890&page=2&p=11396851#post11396851](http://ubuntuforums.org/showthread.php?t=1869890&page=2&p=11396851#post11396851)

I encountered the same problem this morning, came to the forum to see if I could find an answer, and this one worked for me. Thanks v3.xx!

---

### Post by Bashing-om on 2015-12-08
@matt_symes; Hello !

Sure glad that we have your expertise on this one . I am at my wit's end and for sure in a learning mode also .

[INDENT][INDENT]who ya gonna call
[/INDENT][/INDENT]

---

### Post by matt_symes on 2015-12-08
Hi

Hey bashing-om. I hope you're well.

@StephenG

Have you tried UbuntuBunny's suggestion in post #140 recently. I assumed you had but is my assumption incorrect ? I kind of alluded to it here

> Have you tried another mirror after deleting all the files in /var/lib/apt/lists ?

Kind regards

---

### Post by StephenG on 2015-12-08
I only came here with my questions (and very lengthy thread now) after trying several of the suggestions in the similar threads.  All the easy ones, that I felt comfortable doing without jeopardizing my entire system, did not work.  Hence, here I am with folks like you and Bashing-Om, apparently much more linux-literate than me, trying all the complex ones.

---

### Post by matt_symes on 2015-12-08
Hi

> **StephenG said:**
> I only came here with my questions (and very lengthy thread now) after trying several of the suggestions in the similar threads.  All the easy ones, that I felt comfortable doing without jeopardizing my entire system, did not work.  Hence, here I am with folks like you and Bashing-Om, apparently much more linux-literate than me, trying all the complex ones.

No worries.

Can we try to run the gpgv command that apt is running directly.

Firstly, can you post the output of this command. This is in case the next two commands don't work, we'll be able to verify paths.

```
ls -l /var/lib/apt/lists/*archive.ubuntu.com_ubuntu_dists_*Release
```

After that, can you run these two commands and post the output back here.

```
/usr/bin/gpgv -vv --ignore-time-conflict --keyring /etc/apt/trusted.gpg /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease
```

```
/usr/bin/gpgv -vv --ignore-time-conflict --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease
```

The last command should be exactly what apt is running assuming i have got the file name correct, but without the --output-fd switch which is not relevant. 

Kind regards

---

### Post by StephenG on 2015-12-08
```
stephen@stephen-desktop:~$ ls -l /var/lib/apt/lists/*archive.ubuntu.com_ubuntu_dists_*Release
-rw-r--r-- 1 root root 58512 May  8  2014 /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty_Release
-rw-r--r-- 1 root root 64441 Dec  8 07:43 /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-security_Release
-rw-r--r-- 1 root root 64439 Dec  8 07:43 /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_Release

```

```
stephen@stephen-desktop:~$ /usr/bin/gpgv -vv --ignore-time-conflict --keyring /etc/apt/trusted.gpg /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease
gpgv: can't open `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease'
gpgv: verify signatures failed: file open error

```

```
stephen@stephen-desktop:~$ /usr/bin/gpgv -vv --ignore-time-conflict --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease
gpgv: can't open `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease'
gpgv: verify signatures failed: file open error
```

So, the plot thickens.  This is the first time I remember getting a response that the gpg file can't be opened.  Basking-Om, do you remember seeing this error before?

---

### Post by Bashing-om on 2015-12-08
StephenG; matt_symes -- Welp ....

The only error condition that I am aware of:
> 
stephen@stephen-desktop:~$ ls -al ./.gnupg/secring.gpg
-rw------- 1 stephen stephen 0 Jan 24  2013 ./.gnupg/secring.gpg
stephen@stephen-desktop:~$ file ./.gnupg/secring.gpg
./.gnupg/secring.gpg: empty

And I still do not know how that files gets built.

Nor do I know presently what to make of:
> 
gpgv: verify signatures failed: file open error

As I also report this condition:
```

sysop@1404mini:~$ /usr/bin/gpgv -vv --ignore-time-conflict --keyring /etc/apt/trusted.gpg /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease
gpgv: can't open `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease'
gpgv: verify signatures failed: file open error
sysop@1404mini:~$

```
Keep in mind that I "may" have a system problem:
> 
sysop@1404mini:~$ for r in /var/lib/apt/lists/*Release; do if ! gpgv --keyring /etc/apt/trusted.gpg $r.gpg $r; then echo "error: $? Problem with $r"; fi; done
<snip>
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
gpgv: can't open `/var/lib/apt/lists/ubuntu.osuosl.org_ubuntu_dists_trusty-updates_InRelease.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/ubuntu.osuosl.org_ubuntu_dists_trusty-updates_InRelease

This condition persists even after I have changed my mirror site.

[INDENT][INDENT]yeah
[INDENT][INDENT][INDENT]I am stuck too
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by matt_symes on 2015-12-08
Hi

> **StephenG said:**
> ```
stephen@stephen-desktop:~$ ls -l /var/lib/apt/lists/*archive.ubuntu.com_ubuntu_dists_*Release
-rw-r--r-- 1 root root 58512 May  8  2014 /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty_Release
-rw-r--r-- 1 root root 64441 Dec  8 07:43 /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-security_Release
-rw-r--r-- 1 root root 64439 Dec  8 07:43 /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_Release

```

```
stephen@stephen-desktop:~$ /usr/bin/gpgv -vv --ignore-time-conflict --keyring /etc/apt/trusted.gpg /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease
gpgv: can't open `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease'
gpgv: verify signatures failed: file open error

```

```
stephen@stephen-desktop:~$ /usr/bin/gpgv -vv --ignore-time-conflict --keyring /etc/apt/trusted.gpg.d/pipelight-stable.gpg --keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg --keyring /etc/apt/trusted.gpg.d/fuzebox.gpg --keyring /etc/apt/trusted.gpg /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease
gpgv: can't open `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_InRelease'
gpgv: verify signatures failed: file open error
```

So, the plot thickens.  This is the first time I remember getting a response that the gpg file can't be opened.  Basking-Om, do you remember seeing this error before?

The reason why the last two commands failed is because the *InRelease files don't exist. That's the reason why i wanted the output from the first command.

Something struck me though. The number of characters in you public key for ftpmaster.

```
stephen@stephen-desktop:~$ /usr/bin/gpg --no-default-keyring --keyring /etc/apt/trusted.gpg --armor --export ftpmaster@ubuntu.com | wc -c
**20191**
```

It's much larger than the public key on my 16.04 dev install....
```

matthew-xu-16-04:/home/matthew:1 % /usr/bin/gpg --no-default-keyring --keyring /etc/apt/trusted.gpg --armor --export ftpmaster@ubuntu.com | wc -c
**8519**
matthew-xu-16-04:/home/matthew:1 
```

and also much larger than my 14.04 64bit install.
```

matthew-xu-16-04:/mnt/old_root:1 % /usr/bin/gpg --no-default-keyring --keyring etc/apt/trusted.gpg --armor --export ftpmaster@ubuntu.com | wc -c 
**9315**
matthew-xu-16-04:/mnt/old_root:1 %
```

Can you post the output of these commands please.

```
/usr/bin/gpg --list-public-keys --no-default-keyring --keyring /etc/apt/trusted.gpg
```

```
sha256sum /etc/apt/trusted.gpg
```

```
/usr/bin/gpg --list-public-keys --no-default-keyring --keyring /usr/share/keyrings/ubuntu-archive-keyring.gpg
```

```
sha256sum /usr/share/keyrings/ubuntu-archive-keyring.gpg
```

**EDIT:**

@Bashing-om. This may help you. 

> The only error condition that I am aware of:
```
stephen@stephen-desktop:~$ ls -al ./.gnupg/secring.gpg
-rw------- 1 stephen stephen 0 Jan 24 2013 ./.gnupg/secring.gpg
stephen@stephen-desktop:~$ file ./.gnupg/secring.gpg
./.gnupg/secring.gpg: empty
```
And I still do not know how that files gets built.

~/.gnupg/secring.gpg contains your own private gpg keys. If you have never created your own then it will be empty.

I've created some though.

```
matthew-xu-16-04:/mnt/old_root:1 % ls -lh ~/.gnupg/secring.gpg 
-rw------- 1 matthew matthew **5.1K** Aug  2  2014 /home/matthew/.gnupg/secring.gpg
matthew-xu-16-04:/mnt/old_root:1 
```

> Keep in mind that I "may" have a system problem:
```
sysop@1404mini:~$ for r in /var/lib/apt/lists/*Release; do if ! gpgv --keyring /etc/apt/trusted.gpg $r.gpg $r; then echo "error: $? Problem with $r"; fi; done
<snip>
gpgv: Good signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"
gpgv: can't open `/var/lib/apt/lists/ubuntu.osuosl.org_ubuntu_dists_trusty-updates_InRelease.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/ubuntu.osuosl.org_ubuntu_dists_trusty-updates_InRelease
```
This condition persists even after I have changed my mirror site.

To explain the above error messages try this command.

```
ls /var/lib/apt/lists/*Release.gpg
```

Kind regards

---

### Post by StephenG on 2015-12-08
```
stephen@stephen-desktop:~$ /usr/bin/gpg --list-public-keys --no-default-keyring --keyring /etc/apt/trusted.gpg
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024D/3E5C1192 2010-09-20
uid                  Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

pub   4096R/C0B21F32 2012-05-11
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

pub   1024R/5BC3E400 2009-01-20
uid                  Launchpad PPA for Jeffrey Ratcliffe

pub   1024R/EEA14886 2010-05-04
uid                  Launchpad VLC
```

```

stephen@stephen-desktop:~$ sha256sum /etc/apt/trusted.gpg
3b816ef14b50c2d3b19f727b04fde94e193eda7bae7b5e16d827ee13155f59c7  /etc/apt/trusted.gpg

```


```
stephen@stephen-desktop:~$ /usr/bin/gpg --list-public-keys --no-default-keyring --keyring /usr/share/keyrings/ubuntu-archive-keyring.gpg
/usr/share/keyrings/ubuntu-archive-keyring.gpg
----------------------------------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   4096R/C0B21F32 2012-05-11
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>
```


```
stephen@stephen-desktop:~$ sha256sum /usr/share/keyrings/ubuntu-archive-keyring.gpg
46988ea36b75c9653a41ce3ef717c8511478142ab80ec0cba012f5251a1cd4ff  /usr/share/keyrings/ubuntu-archive-keyring.gpg

```


One question I have is why there seem to be two different keys for the same use, to wit the two with the (2012) denoted seem to be exactly the same server address as the first two.  With the obvious exception of the 2012 designation.  Is that perhaps causing duplicated efforts and a conflict?

---

### Post by matt_symes on 2015-12-09
Hi

> **StephenG said:**
> One question I have is why there seem to be two different keys for the same use, to wit the two with the (2012) denoted seem to be exactly the same server address as the first two.  With the obvious exception of the 2012 designation.  Is that perhaps causing duplicated efforts and a conflict?

You have keys in that keyring that i would not expect. Can you post the output of (to get an up to date look)

```
ls -l /etc/apt/trusted.gpg.d
```

Kind regards

---

### Post by StephenG on 2015-12-09
```
stephen@stephen-desktop:~$ ls -l /etc/apt/trusted.gpg.d
total 12
-rw-r--r-- 1 root root 481 May  7  2015 fuzebox.gpg
-rw-r--r-- 1 root root 371 Jan  2  2015 pipelight-stable.gpg
-rw-r--r-- 1 root root   0 Jan  2  2015 pipelight-stable.gpg~
-rw-r--r-- 1 root root 346 May 20  2015 webupd8team-y-ppa-manager.gpg
-rw-r--r-- 1 root root   0 May 20  2015 webupd8team-y-ppa-manager.gpg~

```


During this operation, I had tried, with Bashing-Om's assistance, to completely delete all traces of both Fuzebox and Pipelight and yet they both show back up here. Weird.

---

### Post by matt_symes on 2015-12-09
Hi

There's something i want to try.

Delete the old list files.

```
sudo rm -r /var/lib/apt/lists/*
```

Backup your existing trusted keys database.

```
sudo mv /etc/apt/trusted.gpg{,.bk}
```

Copy the ubuntu archive key ring.

```
sudo cp /usr/share/keyrings/ubuntu-archive-keyring.gpg /etc/apt/trusted.gpg
```

Then update your system.

```
sudo apt-get update
```

You will get an error message about missing VLC keys but i am specifically looking to see if the key errors for the Ubuntu archive repository disappear. If they do then we can add the other keys manually.

If they don't then i think you should seriously consider backing up your files and reinstalling the OS and stop flogging this dead horse :)

Kind regards

---

### Post by StephenG on 2015-12-09
I suppose it's not odd at this point that I did not get the expected VLC missing key notice, but I did get all the usual suspects -- the missing keys errors.  What I wonder about is if it's "normal" to get all the below types of entries, where it looks like it's telling the updater to ignore a command but then immediately finding that same command somewhere else (the nugisphere, maybe, where e-mails go to heaven) and accepting it, or vice-versa.  This is just one screen's worth.  There are many, many like them, if you'd like to examine them all.  And what is the difference between and "In-Release" key and a "Release" key?

I am currently using Duplicity for my back-up software and I hope that's sufficient, but obviously I can't re-install 14.04 and then tell the backup to do it's thing or we'll end up back here.  Suggestions?

```
Get:26 http://archive.ubuntu.com trusty Release [58.5 kB]                      
Ign http://archive.ubuntu.com trusty Release                                   
Get:27 http://archive.ubuntu.com trusty/main i386 Packages [1,348 kB]          
Get:28 http://archive.ubuntu.com trusty/universe i386 Packages [5,866 kB]      
Get:29 http://archive.ubuntu.com trusty/multiverse i386 Packages [134 kB]      
Get:30 http://archive.ubuntu.com trusty/main Translation-en [762 kB]           
Get:31 http://archive.ubuntu.com trusty/multiverse Translation-en [102 kB]     
Get:32 http://archive.ubuntu.com trusty/universe Translation-en [4,089 kB]     
Ign http://archive.ubuntu.com trusty-updates/main Translation-en_US            
Ign http://archive.ubuntu.com trusty-updates/multiverse Translation-en_US      
Ign http://archive.ubuntu.com trusty-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com trusty-security/main Translation-en_US           
Ign http://archive.ubuntu.com trusty-security/multiverse Translation-en_US     
Ign http://archive.ubuntu.com trusty-security/universe Translation-en_US       
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US
W: GPG error: http://archive.ubuntu.com trusty-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32

```

---

### Post by matt_symes on 2015-12-09
Hi

> I suppose it's not odd at this point that I did not get the expected VLC missing key notice

That's really odd ! Can we check every thing worked as expected.

What's the output of this command please.

```
for f in /etc/apt/trusted.gpg{,.d/*}; do /usr/bin/gpg --list-public-keys --no-default-keyring --keyring "$f"; done
```

and this one.

```
ls -l /etc/apt/
```

> 
I am currently using Duplicity for my back-up software and I hope that's sufficient, but obviously I can't re-install 14.04 and then tell the backup to do it's thing or we'll end up back here. Suggestions?

I've not used duplicity so i may not be the most useful person. What exactly do you back up ? Everything ?

Kind regards

---

### Post by StephenG on 2015-12-09
```
stephen@stephen-desktop:~$ for f in /etc/apt/trusted.gpg{,.d/*}; do /usr/bin/gpg --list-public-keys --no-default-keyring --keyring "$f"; done
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   4096R/C0B21F32 2012-05-11
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

gpg: [don't know]: invalid packet (ctb=2d)
gpg: keydb_search_first failed: invalid packet
/etc/apt/trusted.gpg.d/pipelight-stable.gpg
-------------------------------------------
pub   1024R/25396B8E 2013-11-24
uid                  Launchpad PPA for Pipelight Dev Team

/etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg
----------------------------------------------------
pub   1024R/EEA14886 2010-05-04
uid                  Launchpad VLC

stephen@stephen-desktop:~$ 
```


```
stephen@stephen-desktop:~$ ls -l /etc/apt
total 104
drwxr-xr-x 2 root root  4096 Dec  7 22:06 apt.conf.d
drwxr-xr-x 2 root root  4096 Apr 20  2012 preferences.d
-rw-r--r-- 1 root root  1889 Nov 30 17:17 sources.list
-rw-r--r-- 1 root root  3131 Oct 17  2012 sources.list~
-rw-r--r-- 1 root root  1889 Nov 30 22:05 sources.list-30nov2015
drwxr-xr-x 2 root root  4096 Nov 30 14:13 sources.list.d
-rw-r--r-- 1 root root  3314 Aug 12  2014 sources.list.distUpgrade
-rw-r--r-- 1 root root  1887 Nov 30 17:17 sources.list.save
-rw------- 1 root root    40 Dec  7 16:48 trustdb.gpg
-rw-r--r-- 1 root root 12335 Dec  9 09:18 trusted.gpg
-rw-r--r-- 1 root root 21457 May 20  2015 trusted.gpg~
-rw-r--r-- 1 root root 21803 Oct 26 19:18 trusted.gpg.bk
drwxr-xr-x 2 root root  4096 Oct 26 19:18 trusted.gpg.d
stephen@stephen-desktop:~$ 
```

My mistake, the backup software is Deja Dup,  I have it set to auto backup once a week and to back up "Home (Stephen)" and to only ignore "Downloads."  Currently, there are about 350+ backup files from which to choose (Yeah!  More options!!).  FYI, in the second response, after the "104," the 1st, 2nd, 6th, and last entries have the ending notation, e.g., "apt.conf.d," highlighted in blue.

---

### Post by matt_symes on 2015-12-09
Hi

That's explains the VLC gpg keys then. 

They are in the keyring /etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg so that's  no longer a mystery.

This though is odd.

```
gpg: [don't know]: invalid packet (ctb=2d)
gpg: keydb_search_first failed: invalid packet
```

From here:
```

stephen@stephen-desktop:~$ ls -l /etc/apt/trusted.gpg.d
total 12
-rw-r--r-- 1 root root 481 May  7  2015 fuzebox.gpg
-rw-r--r-- 1 root root 371 Jan  2  2015 pipelight-stable.gpg
-rw-r--r-- 1 root root   0 Jan  2  2015 pipelight-stable.gpg~
-rw-r--r-- 1 root root 346 May 20  2015 webupd8team-y-ppa-manager.gpg
-rw-r--r-- 1 root root   0 May 20  2015 webupd8team-y-ppa-manager.gpg~
```

...and here...

```

stephen@stephen-desktop:~$ for f in /etc/apt/trusted.gpg{,.d/*}; do /usr/bin/gpg --list-public-keys --no-default-keyring --keyring "$f"; done
/etc/apt/trusted.gpg
...

gpg: [don't know]: invalid packet (ctb=2d)
gpg: keydb_search_first failed: invalid packet

...

/etc/apt/trusted.gpg.d/pipelight-stable.gpg
...

/etc/apt/trusted.gpg.d/webupd8team-y-ppa-manager.gpg
....

stephen@stephen-desktop:~$
```

... there is no entry (returned keys) for ```
/etc/apt/trusted.gpg.d/fuzebox.gpg
```

Hmm. I wonder if that's causing gpgv to bail out when called from apt-get and hence is not finding the archive GPG keys as the archive gpg keyring is the last keyring passed to gpgv from apt-get. 

Open a terminal and type

```
sudo rm /etc/apt/trusted.gpg.d/fuzebox.gpg
``` 

```
sudo apt-get update
```

Do the gpg errors disappear ?

If they do then we'll clean up your system for you.

Kind regards

---

### Post by StephenG on 2015-12-09
WOW !!!  We are down to this error:

```
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
stephen@stephen-desktop:~$ 

```

Holy mackerel, what just happened?  And the "IGN" comments are down to 7, from the previous update command, in which there were, I estimate, at least 25 or more.  Good work, pal.  Where to from here?

---

### Post by matt_symes on 2015-12-09
Hi

I'm just about to eat. We can clean up your system after that :)

Kind regards

---

### Post by matt_symes on 2015-12-09
Hi

We know the current state of your apt keyrings.

Can you now get the current state of your sources.

Please post the output of 

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

That should give us enough information to clean your system.

Kind regards

---

### Post by StephenG on 2015-12-09
Some portions of every line are in different colors, in case that makes any diference.

```
stephen@stephen-desktop:~$ grep "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty main universe multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty-updates main universe multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty-security main universe multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu trusty partner
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list:deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu trusty main
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list.save:deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu trusty main

```

---

### Post by matt_symes on 2015-12-09
Hi

> **StephenG said:**
> Some portions of every line are in different colors, in case that makes any diference.

```
stephen@stephen-desktop:~$ grep "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty main universe multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty-updates main universe multiverse
/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu trusty-security main universe multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu trusty partner
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list:deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu trusty main
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list.save:deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu trusty main

```

The red colour make no difference. That's just highlighting lines containing the regular expression that was passed into the grep command. The purple colour are the files grep has found matches for the regular expression.

Open a terminal. Copy and paste these commands into it.

First let's remove the unneeded keyring for pipelight.

```
sudo rm /etc/apt/trusted.gpg.d/pipelight-stable.gpg*
```

Next let's add the missing GPG keys for extras.ubuntu.com.

```
sudo apt-key adv --recv-keys --keyserver  keyserver.ubuntu.com 16126D3A3E5C1192
```

Then update your system

```
sudo apt-get update
```

If that throws back no errors then install htop. It's a tiny process information utility that will not use much hard drive space, but will allow us to verify that you can install packages.

```
sudo apt-get install htop
```

We'll keep the backup keyring we make on your system just in case there are issues (trusted.gpg.bk) as it contains some keys that are not in your new default keyring.

We're almost done (hopefully :))

Can you post the output of these commands

```
dpkg -l | egrep "fuze|pipe"
```

They will show if fuze and pipelight are still installed on your system.

To answer some of your previous questions:

> Holy mackerel, what just happened? 

You had a corrupted gpg keyring (fuzebox.gpg) on your system that was stopping apt getting all the GPG keys in all the apt keyrings on your system.

When gpgv (called by apt) tried to open the corrupted keyring it was failing and bailing out. 

Any keyrings that had GPG keys in, after that corrupted keyring was checked, were not being checked because of the bail out. 

It just so happens that the Ubuntu archive was the last keyring to be checked and it was never being checked.

It contains the missing GPG keys that it could not get from that keyring and hence the missing GPG key error messages when you tried to update.

I only skimmed the first five pages of this thread so I'm not 100% sure what the problem was previously.
> 
FYI, in the second response, after the "104," the 1st, 2nd, 6th, and last entries have the ending notation, e.g., "apt.conf.d," highlighted in blue. 

They are directories and not files.

> And what is the difference between and "In-Release" key and a "Release" key?

They are not keys, rather they are files.

On the repository server, the top level sources files are signed with GPG keys to verify the files come from the people/repositories they are supposed to come from.

There are two ways these files are signed. 

1. You can have a sources file (with the associated md5 hashes) and a separate file that contains the gpg signature of that file.

2. The other method is to have a single file that contains both the sources (with the associated md5 hashes) but also contains the GPG signature.

What apt does is, if there are two files (as in 1. above) then apt passes the two files into gpgv to verify the source file.

If there is a single file (as in 2. above) then apt splits out the sources and the signature into two separate files and passes them both into gpgv as above.

The InRelease files are examples of files that contain both the sources and gpg signature in one file.

The Release files contain only the sources. The associated gpg file for that sources file is deleted by apt when it has checked the signature is valid.

Some repositories use method 1, some use method 2 and some have both.

> 
One question I have is why there seem to be two different keys for the same use, to wit the two with the (2012) denoted seem to be exactly the same server address as the first two. With the obvious exception of the 2012 designation. Is that perhaps causing duplicated efforts and a conflict? 

You can have multiple keys. This is not a problem.

Kind regards

---

### Post by StephenG on 2015-12-09
Very, very good news, my friend.  There were zero errors generated.  Here's the response you requested:

```
stephen@stephen-desktop:~$ dpkg -l | egrep "fuze|pipe"
ii  libpipeline1:i386                                     1.3.0-1                                             i386         pipeline manipulation library
rc  pipelight                                             0.2.8.1~ubuntu14.04.1                               i386         allows usage of Silverlight through Wine
rc  pipelight-multi                                       0.2.8.1~ubuntu14.04.1                               i386         allows usage of Windows NPAPI plugins through Wine

```

One of the things Bashing-Om and I deleted early on was a very old version of WINE.  I'd love to get WINE back since I use PDFXchange a lot and it only works through WINE, as far as I can find (no linux version that I've found).  When we're done with getting rid of the errors (as in, now) should I be able to just use the Ubuntu software app installer to get a new updated version of that, as far as you can tell?  Or is that what htop is for -- to give us that answer?

---

### Post by matt_symes on 2015-12-09
Hi

> **StephenG said:**
> Very, very good news, my friend.  There were zero errors generated.  Here's the response you requested:

```
stephen@stephen-desktop:~$ dpkg -l | egrep "fuze|pipe"
ii  libpipeline1:i386                                     1.3.0-1                                             i386         pipeline manipulation library
rc  pipelight                                             0.2.8.1~ubuntu14.04.1                               i386         allows usage of Silverlight through Wine
rc  pipelight-multi                                       0.2.8.1~ubuntu14.04.1                               i386         allows usage of Windows NPAPI plugins through Wine

```


I would start afresh so

```
sudo apt-get purge pipelight pipelight-multi
```

Post back any errors.

> One of the things Bashing-Om and I deleted early on was a very old version of WINE.  I'd love to get WINE back since I use PDFXchange a lot and it only works through WINE, as far as I can find (no linux version that I've found).  When we're done with getting rid of the errors (as in, now) should I be able to just use the Ubuntu software app installer to get a new updated version of that, as far as you can tell?  Or is that what htop is for -- to give us that answer?

If htop installed correctly then you should be able to install any package using apt or the Ubuntu software centre.

Try to install wine and, if there are any errors, start a new thread in the Wine subforum and PM me the link.

I have to be honest and say that i have not used Wine for a very long time so i have no idea how up to date the version in the repositories is or whether it will run PDFXchange.

If you're happy and can install Wine or any package then please mark this thread as [solved] using the thread tools at the top of the page.

...but you should be good to roll now :D

Kind regards

---

### Post by StephenG on 2015-12-09
No errors generated with the above command.  Thank you ever so much.  I will be certain to mark it solved and point anyone else with the issue this way.  So I have a better handle on things, if I had started out by deleting the non-ubuntu keys, is it your opinion that we'd have resolved this earlier, or was the entire process a necessary evil to get to the final realization that it was that pipelight gpg file corrupting the system's attempts to verify the signatures?  Do I need to do anything actively with htop or does it just run in the background and let me know if things are going amok?
Oh, and I can never thank you enough for all the explanations you've given.  Though some of them seem to be over my head, I will research those I wasn't sure of and learn.

And for the first time since May, I am able to update using the regular updater that pops up every now and again to let me know there's stuff to update, without getting the missing keys error.  Fingers crossed.

---

### Post by Bashing-om on 2015-12-09
StephenG; matt_symes.

I have been following,
:)
[INDENT][INDENT]well done
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2015-12-09
> **Bashing-om said:**
> StephenG; matt_symes.

I have been following,
:)[INDENT][INDENT]well done
[/INDENT]
[/INDENT]

Me Too.. Nicely Done Matt =d>

---

### Post by matt_symes on 2015-12-09
Hi

> **StephenG said:**
> No errors generated with the above command.  Thank you ever so much.  I will be certain to mark it solved and point anyone else with the issue this way.

Thank you. That'll help others.

>  So I have a better handle on things, if I had started out by deleting the non-ubuntu keys, is it your opinion that we'd have resolved this earlier, or was the entire process a necessary evil to get to the final realization that it was that pipelight gpg file corrupting the system's attempts to verify the signatures?  

You had an unusual problem on your system. It's the first time i have come across a corrupt keyring.

It's not something the standard fixes would have found. 

To investigate problems like that, it helps to able to read apt's source code and to see what apt is trying to do and run tools like strace and gdb. Knowing you had tried other fixes helped to rule them out too.

That pointed the way towards the gpg keyrings themselves which we started looking at in detail in the last couple of posts.

The lucky break was that you had multiple VLC keys in different keyrings.

That type of problem is not an easy problem to find unless you're sitting at the keyboard and, 
for an issue like that, there's not much more you can do than investigate and poke at the problem.

I'm not surprised it took some time.

I think most people would have reinstalled long ago :)

> Do I need to do anything actively with htop or does it just run in the background and let me know if things are going amok?

htop doesn't run in the background. It'll run if you start it from a terminal.

If your interested in what it looks like then open a terminal and type

```
htop
``` 

Press q to exit. 

I only asked you to install it just to see if apt would return errors.

You can remove it with

```
sudo apt-get remove htop
```

> Oh, and I can never thank you enough for all the explanations you've given.  Though some of them seem to be over my head, I will research those I wasn't sure of and learn.

No worries. Glad i could help.

Kind regards

---

### Post by StephenG on 2015-12-09
Is there any reason to remove the program or better to keep it there in case it's needed later on?

Bashing-Om, in no way am I minimizing your assistance.  At the very least, it was your help that got us far enough along to attract Matt's attention.  I kept waiting for you to jump back in and hope you didn't get the idea I was tossing you under the bus; or overboard, either.  As a retired 29-year police sergeant, I hate to give up on a case that has so many clues available just when it looks like a conviction is possible.  ;-))  There was no way I was taking the easy way out and wiping the drive to re-install.  Ha.  That's for wussies.

---

### Post by matt_symes on 2015-12-09
Hi

> **runrickus said:**
> Me Too.. Nicely Done Matt =d>

Thanks runrickus.

bashing-om did the heavy lifting though, i just finished it off.

Kind regards

---

### Post by matt_symes on 2015-12-09
Hi

> **StephenG said:**
> Is there any reason to remove the program or better to keep it there in case it's needed later on?

The main htop binary is 134K on my 16.04 install. It's tiny.

Keep it because, even if you never use it, it's so small that it'll never cause you any disk storage problems. 

> There was no way I was taking the easy way out and wiping the drive to re-install.  Ha.  That's for wussies.

That's the spirit ;)

Kind regards

---

### Post by Bashing-om on 2015-12-09
StephenG; Hey ..

All good now .. Believe me I was stuck. Mat to the rescue .
The protocol on a thread is that if you have nothing productive to say, say nothing !
I am glad to know that we can purge the keyrings and rebuild them.

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

### Post by StephenG on 2015-12-09
Thanks.  My main regret of having moved to linux is that I miss my old DOS manual that explained and gave examples for all the commands/switches and their uses.  I wish there was such a thing for linux.  I really wish I had some idea what all the commands and switches Matt was telling me to use meant and did.  Day by day ...

---

### Post by Bashing-om on 2015-12-09
StephenG; Well !

You do have a installed manual !
in terminal do:
```

man man 

```
'man' can be a bit cryptic at times, but you will quickly get the hang of it as you use it .
There is a manual page for every command and for many applications as well .

[INDENT][INDENT]linux has been around
[INDENT][INDENT][INDENT]not much new under that sun
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

