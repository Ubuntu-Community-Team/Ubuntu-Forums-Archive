---
title: "When checking for upgrades on Upgrade Manager my public key is not available."
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by wilwil0 on 2010-06-14
When I click "check" in Update Manager it tries to download 541 files, skiping each one and the giving me this message:

> W: GPG error: [http://linux.dropbox.com](http://linux.dropbox.com) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC918B335044912E
W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139

W: GPG error: [http://packages.deepin.org](http://packages.deepin.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1BFC74C9B79DB919
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DA360C64005E0276
W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release](http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release)  

W: Failed to fetch [http://linux.dropbox.com/dists/karmic/main/binary-i386/Packages.gz](http://linux.dropbox.com/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://download.virtualbox.org/dists/karmic/main/binary-i386/Packages.gz](http://download.virtualbox.org/dists/karmic/main/binary-i386/Packages.gz)  404  Not found

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release/dists/karmic/main/binary-i386/Packages.gz](http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release/dists/karmic/main/binary-i386/Packages.gz)  404  Not found

W: Failed to fetch [http://ppa.launchpad.net/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.


I'm guessing this has something to do with authentication keys or something on software sources but I'm clueless how to solve it.

---

### Post by mikewhatever on 2010-06-14
The errors you posted have nothing to do with *your* public key, whatever that is. You have quite a few third party repositories - dropbox, virtualbox, launchpad, the pulic keys for which are missing. You need to add them as per instructions on the respective repository web page.

---

### Post by wilwil0 on 2010-06-14
Hi and thanks for replying.

I'm not really sure what I am supposed to be adding and where, lets take one webpage there (it's made more difficult by the fact some of them 404 and evidently don't exist!?!).

[http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release](http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release)

I can see lots of things that look like they should be somewhere, I'm just not sure where I put anything. 

On Software Sources there is a tab called Authentication with things like that.

If I'm getting the complete wrong end of the stick could you please tell me how I would add the public keys, using the virtualbox thing I linked earlier in this post as an example.

---

### Post by wesleybishop on 2010-06-14
Are you still getting the public key errors? If so, you could try authenticating the repositories by manually importing the public keys, using:

Code:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys [KEY]
Where [KEY] in the above example is the ID of the public key you want to retrieve.
 
 
[http://ubuntuforums.org/showthread.php?t=1506426](http://ubuntuforums.org/showthread.php?t=1506426)

---

### Post by wilwil0 on 2010-06-14
That certainly appears to work as I've done what you have said in the terminal and it's now asking me for the password for my user, but whenever I type no characters appear, what's up with that?

---

### Post by mikewhatever on 2010-06-14
The instructions on adding the vbox pubkey is on the following page:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
> wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

Looks simple.

---

### Post by wilwil0 on 2010-06-14
Just to confirm if you were wondering, it has never done that before and i have always been able to type in my terminal.

---

### Post by mikewhatever on 2010-06-14
I think I am somewhat condescending today, sorry about that. In case you are still having a hard time figuring out the keys, let's try and tackle them one by one.

---

### Post by wilwil0 on 2010-06-14
Thank you very much, although if you were wondering about the last problem I posed, it turns out that you can type your password, the blinker simply doesn't move.

Anyway, about the keys, of the three links left one ( [http://linux.dropbox.com/](http://linux.dropbox.com/) ) simply 404's, so I don't know what to do about that one.

As for 

[http://ppa.launchpad.net/](http://ppa.launchpad.net/)
and
[http://packages.deepin.org/](http://packages.deepin.org/)

I don't know which directory to navigate to, I don't know what I am supposed to be looking for to find the correct file to link into the rest of command you posted. I have managed to do that one for Virtualbox though, and followed that link.

---

### Post by mikewhatever on 2010-06-14
> **wilwil0 said:**
> Thank you very much, although if you were wondering about the last problem I posed, it turns out that you can type your password, the blinker simply doesn't move.
It's not supposed to. Just enter your password and hit 'Enter'.

> 
Anyway, about the keys, of the three links left one ( [http://linux.dropbox.com/](http://linux.dropbox.com/) ) simply 404's, so I don't know what to do about that one.

As for 

[http://ppa.launchpad.net/](http://ppa.launchpad.net/)
and
[http://packages.deepin.org/](http://packages.deepin.org/)

I don't know which directory to navigate to, I don't know what I am supposed to be looking for to find the correct file to link into the rest of command you posted. I have managed to do that one for Virtualbox though, and followed that link.

The 404 error is unrelated to the pubkeys problem. It simply means that the package or the repository could not be accessed or no longer available.
Why don't you post the sources.list for review.
```
cat /etc/apt/sources.list
```

---

### Post by wilwil0 on 2010-06-14
Results:

> # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100318)]/ lucid main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports restricted main multiverse universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted universe multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-proposed restricted main multiverse universe

deb [http://packages.deepin.org](http://packages.deepin.org) karmic main
deb [http://linux.dropbox.com](http://linux.dropbox.com) karmic main
deb [http://download.virtualbox.org](http://download.virtualbox.org) karmic main
deb [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic main
deb [http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release](http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release) karmic main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free


---

### Post by mikewhatever on 2010-06-14
Let's tackle the launchpad key for now.
```
gpg --keyserver keyserver.ubuntu.com --recv 005E0276
gpg --export --armor 005E0276 | sudo apt-key add - && sudo apt-get update
```
When done, run **sudo apt-get update** and post the output.
Did the command for vbox work?

---

### Post by wilwil0 on 2010-06-14
Yes the command for virtualbox worked perfectly, all the updates downloaded.

I'll try these new commands...

---

### Post by wilwil0 on 2010-06-14
Erm, the output from "sudo apt-get update" is quite long

> Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_GB    
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_GB              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Get: 1 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Translation-en_GB                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Translation-en_GB             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Get: 2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB           
Get: 3 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]                    
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release.gpg                              
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_GB                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB     
Hit [http://deb.opera.com](http://deb.opera.com) lenny Release.gpg                                     
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Translation-en_GB                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Get: 4 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                            
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports Release.gpg                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/restricted Translation-en_GB 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/main Translation-en_GB       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://download.skype.com](http://download.skype.com) stable Release                                   
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Translation-en_GB                   
Hit [http://deb.opera.com](http://deb.opera.com) lenny Release                                         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/multiverse Translation-en_GB 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/universe Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed Release.gpg                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/restricted Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/main Translation-en_GB        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/multiverse Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/universe Translation-en_GB    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Get: 5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,061B]                      
Ign [http://linux.dropbox.com](http://linux.dropbox.com) karmic Release.gpg                                
Ign [http://linux.dropbox.com](http://linux.dropbox.com) karmic/main Translation-en_GB                     
Hit [http://linux.dropbox.com](http://linux.dropbox.com) karmic Release.gpg                                
Ign [http://linux.dropbox.com](http://linux.dropbox.com) karmic/main Translation-en_GB                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Get: 6 [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release [1,723B]                      
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages                         
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg                          
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/main Translation-en_GB               
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg                          
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/main Translation-en_GB               
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed Release                       
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Get: 7 [http://packages.deepin.org](http://packages.deepin.org) karmic Release.gpg [197B]                    
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release.gpg                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Ign [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources                     
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Translation-en_GB           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Ign [http://linux.dropbox.com](http://linux.dropbox.com) karmic Release                                    
Hit [http://linux.dropbox.com](http://linux.dropbox.com) karmic Release                                    
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://deb.opera.com](http://deb.opera.com) lenny/non-free Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/restricted Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/main Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/multiverse Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/universe Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/restricted Sources           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release                              
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/main Sources                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/multiverse Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-backports/universe Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/restricted Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/main Packages                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Translation-en_GB                 
Ign [http://linux.dropbox.com](http://linux.dropbox.com) karmic/main Packages                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/multiverse Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/universe Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/restricted Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/main Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/multiverse Sources            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-proposed/universe Sources              
Ign [http://packages.deepin.org](http://packages.deepin.org) karmic/main Translation-en_GB                   
Get: 8 [http://packages.deepin.org](http://packages.deepin.org) lucid Release.gpg [197B]                     
Ign [http://packages.deepin.org](http://packages.deepin.org) lucid/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://linux.dropbox.com](http://linux.dropbox.com) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/main Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Get: 9 [http://packages.deepin.org](http://packages.deepin.org) karmic Release [2,034B]                      
Ign [http://linux.dropbox.com](http://linux.dropbox.com) karmic/main Packages                              
Get: 10 [http://packages.deepin.org](http://packages.deepin.org) lucid Release [2,033B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Ign [http://packages.deepin.org](http://packages.deepin.org) karmic Release                                  
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages                          
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/main Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Err [http://linux.dropbox.com](http://linux.dropbox.com) karmic/main Packages                              
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Packages                    
Ign [http://packages.deepin.org](http://packages.deepin.org) lucid Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/main Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Hit [http://getswiftfox.com](http://getswiftfox.com) unstable/non-free Packages                          
Get: 11 [http://packages.deepin.org](http://packages.deepin.org) karmic/main Packages [91.0kB]               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/main Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Err [http://download.virtualbox.org](http://download.virtualbox.org) karmic/main Packages                        
  404  Not found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Err [http://download.virtualbox.org](http://download.virtualbox.org) karmic/main Packages                        
  404  Not found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Get: 12 [http://packages.deepin.org](http://packages.deepin.org) lucid/main Packages [92.0kB]                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
  404  Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Get: 13 [http://packages.deepin.org](http://packages.deepin.org) lucid/main Sources [33.8kB]                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Fetched 232kB in 5s (40.9kB/s)
W: GPG error: [http://packages.deepin.org](http://packages.deepin.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1BFC74C9B79DB919
W: GPG error: [http://packages.deepin.org](http://packages.deepin.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1BFC74C9B79DB919
W: Failed to fetch [http://linux.dropbox.com/dists/karmic/main/binary-i386/Packages.gz](http://linux.dropbox.com/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://download.virtualbox.org/dists/karmic/main/binary-i386/Packages.gz](http://download.virtualbox.org/dists/karmic/main/binary-i386/Packages.gz)  404  Not found

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release/dists/karmic/main/binary-i386/Packages.gz](http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release/dists/karmic/main/binary-i386/Packages.gz)  404  Not found

W: Failed to fetch [http://ppa.launchpad.net/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


---

### Post by mikewhatever on 2010-06-14
Right, as far as I can see, the only pubkey related errors are now the ones pointing to [http://packages.deepin.org/](http://packages.deepin.org/). What is [http://packages.deepin.org/?](http://packages.deepin.org/?) Is there a web page?

---

### Post by wilwil0 on 2010-06-14
If I'm honest I hadn't heard of that website until now :/

I've been googling in the meanwhile and do you think any of these ought to be useful?

[http://keyserver.ubuntu.com:11371/pks/lookup?search=deepin&op=vindex](http://keyserver.ubuntu.com:11371/pks/lookup?search=deepin&op=vindex)

[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6F45981DA6AC026D](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6F45981DA6AC026D)
[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x71669FF9D9D2D798](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x71669FF9D9D2D798)

I've tried using these in the "wget -q [link] -O- | sudo apt-key add -" command but it comes up with

  [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6F45981DA6AC026D](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6F45981DA6AC026D)
>  wget -q [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6F45981DA6AC026D](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6F45981DA6AC026D) -O- | sudo apt-key add -
[1] 14582
-O-: command not found
gpg: no valid OpenPGP data found.


[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x71669FF9D9D2D798](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x71669FF9D9D2D798)
>  wget -q [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x71669FF9D9D2D798](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x71669FF9D9D2D798) -O- | sudo apt-key add -
[2] 14589
-O-: command not found
[1]   Exit 1                  wget -q [http://keyserver.ubuntu.com:11371/pks/lookup?op=get](http://keyserver.ubuntu.com:11371/pks/lookup?op=get)
gpg: no valid OpenPGP data found.
[1]   Exit 1                  wget -q [http://keyserver.ubuntu.com:11371/pks/lookup?op=get](http://keyserver.ubuntu.com:11371/pks/lookup?op=get)
[2]+  Exit 1                  wget -q [http://keyserver.ubuntu.com:11371/pks/lookup?op=get](http://keyserver.ubuntu.com:11371/pks/lookup?op=get)



---

### Post by wilwil0 on 2010-06-15
What does it mean when an update has been hit, e.g:

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg

---

### Post by mikewhatever on 2010-06-15
> **wilwil0 said:**
> If I'm honest I hadn't heard of that website until now :/

I've been googling in the meanwhile and do you think any of these ought to be useful?

[http://keyserver.ubuntu.com:11371/pks/lookup?search=deepin&op=vindex](http://keyserver.ubuntu.com:11371/pks/lookup?search=deepin&op=vindex)

[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6F45981DA6AC026D](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x6F45981DA6AC026D)
[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x71669FF9D9D2D798](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x71669FF9D9D2D798)

No, I think not. May I ask why add that repository if you don't know what it is. I strongly advise against adding any untrusted third party repositories. If you do, it will, very likely, break your system.

---

