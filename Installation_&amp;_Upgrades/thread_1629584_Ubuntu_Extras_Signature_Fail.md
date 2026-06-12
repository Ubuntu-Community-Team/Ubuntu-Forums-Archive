---
title: "Ubuntu Extras Signature Fail"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by KatsumeBlisk on 2010-11-23
I have looked around and cannot find a fix for this error. Whenever I update my repos, I get an error about the public key of the extras repository. ```
Get:1 http://extras.ubuntu.com maverick Release.gpg [316B]
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Get:2 http://extras.ubuntu.com maverick Release [57.3kB]                       
Err http://extras.ubuntu.com maverick Release                                  
  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                    
Ign http://ppa.launchpad.net/raof/aubergine/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/raof/aubergine/ubuntu/ maverick/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release
Hit http://security.ubuntu.com maverick-security Release                       
Hit http://us.archive.ubuntu.com maverick-updates Release                      
Hit http://ppa.launchpad.net maverick Release                        
Hit http://security.ubuntu.com maverick-security/main Sources        
Hit http://us.archive.ubuntu.com maverick/main Sources
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources           
Hit http://us.archive.ubuntu.com maverick/multiverse Sources         
Hit http://us.archive.ubuntu.com maverick/main i386 Packages         
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages   
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages     
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages   
Hit http://us.archive.ubuntu.com maverick-updates/main Sources       
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources 
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Fetched 317B in 1s (215B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
zack@ubuntu:~$ sudo apt-get update
Get:1 http://extras.ubuntu.com maverick Release.gpg [316B]
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Get:2 http://extras.ubuntu.com maverick Release [57.3kB]                       
Err http://extras.ubuntu.com maverick Release                                  
  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release             
Hit http://ppa.launchpad.net maverick Release.gpg                    
Ign http://ppa.launchpad.net/raof/aubergine/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/raof/aubergine/ubuntu/ maverick/main Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Hit http://security.ubuntu.com maverick-security/main Sources
Hit http://ppa.launchpad.net maverick Release  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://security.ubuntu.com maverick-security/restricted Sources  
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates Release
Hit http://us.archive.ubuntu.com maverick/main Sources
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Fetched 317B in 1s (181B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```This is what I get when I "sudo apt-get update".

All help is appreciated.

---

### Post by cheetaux on 2010-11-23
Having the same problem.

---

### Post by dmcdow on 2010-11-23
I am having same problem as well.
ubuntu 10.10 
dell dimension e510

---

### Post by ajunsum on 2010-11-24
same here too

---

### Post by lambdalisp on 2010-11-24
This worked for me.

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv DB141E2302FDF932
sudo apt-get update

```

---

### Post by ajunsum on 2010-11-24
thanks lambdalisp!
worked for me too...

---

### Post by epari.siva on 2010-11-24
Works great for me too! Thanks

---

### Post by Chris on 2010-11-24
The real question is what happened and why did we have to pull a new key.  Why didn't it update automatically, etc.  Seems like a problem even if it's easily fixable because it doesn't seem like we did anything that should have broken in the first place.

---

### Post by DaleEMoore on 2010-11-24
I just do-release-upgrade -ed to 10.10 from 10.04. Then:```
apt-get update && apt-get -y dist-upgrade && if [ -e /var/run/reboot-required ]; then echo "REBOOT required"; else echo "Not required to reboot at `date`."; fi

```failed because of the missing key. But, thanks to you fine folks:```
apt-key adv --keyserver keyserver.ubuntu.com --recv DB141E2302FDF932
apt-get update

```fixed it.

Thanks!!

---

### Post by dmcdow on 2010-11-24
> **Chris said:**
> The real question is what happened and why did we have to pull a new key.  Why didn't it update automatically, etc.  Seems like a problem even if it's easily fixable because it doesn't seem like we did anything that should have broken in the first place.

It worked for me too.  Ditto on this question.

---

### Post by philosophers-stone on 2010-11-25
> **lambdalisp said:**
> This worked for me.

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv DB141E2302FDF932
sudo apt-get update

```
  Thanks!! That solve the problem for me...=D>

---

### Post by earthmeLon on 2010-11-26
Confirm this was required after installing 10.10 x64 from Alternative CD.  If trouble persists, try
```

sudo apt-get install --reinstall ubuntu-extras-keyring
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv DB141E2302FDF932
sudo apt-get update

```

---

### Post by efflandt on 2010-11-26
The two liner resolves it for natty development too, so it must have been a general issue.

---

### Post by hezuo on 2010-11-27
Thanks a lot, it did work!

---

