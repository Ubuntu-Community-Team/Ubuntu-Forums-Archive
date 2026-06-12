---
title: "Upgrade problem"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by minerbog on 2010-12-10
I received this error in my terminal today when running an upgarde.  Anyone knows what it means???

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  imagemagick libmagick++2 libmagickcore2 libmagickcore2-extra libmagickwand2
  perlmagick
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,653kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libmagickcore2 libmagickwand2 imagemagick libmagick++2 libmagickcore2-extra
  perlmagick
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated

```

---

### Post by sikander3786 on 2010-12-10
Post the output of this one.

```
sudo apt-get update
```

---

### Post by minerbog on 2010-12-12
Here is my output from 'apt-get update'

```

 
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB   
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_GB       
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/yogarine/eclipse/ubuntu/ lucid/main Translation-en_GB
Hit http://gb.archive.ubuntu.com lucid Release.gpg                             
Get: 1 http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB [62.9kB]
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://archive.canonical.com lucid Release                                 
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://deb.opera.com stable Release.gpg                                    
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_GB              
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources                     
Get: 2 http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB [2,332B]
Get: 3 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB [33.9kB]
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Hit http://security.ubuntu.com lucid-security/multiverse Sources               
Hit http://deb.opera.com stable Release                                        
Get: 4 http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB [37.7kB]
Hit http://linux.dropbox.com lucid Release.gpg                                 
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_GB              
Hit http://gb.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB  
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com lucid Release                                
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://gb.archive.ubuntu.com lucid-updates Release                         
Hit http://gb.archive.ubuntu.com lucid/main Packages                           
Ign http://deb.opera.com stable/non-free Packages                              
Hit http://gb.archive.ubuntu.com lucid/restricted Packages
Hit http://gb.archive.ubuntu.com lucid/main Sources
Hit http://gb.archive.ubuntu.com lucid/restricted Sources
Hit http://gb.archive.ubuntu.com lucid/universe Packages
Hit http://gb.archive.ubuntu.com lucid/universe Sources
Hit http://gb.archive.ubuntu.com lucid/multiverse Packages
Hit http://gb.archive.ubuntu.com lucid/multiverse Sources
Hit http://gb.archive.ubuntu.com lucid-updates/main Packages
Hit http://gb.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://gb.archive.ubuntu.com lucid-updates/main Sources
Hit http://gb.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://gb.archive.ubuntu.com lucid-updates/universe Packages
Hit http://gb.archive.ubuntu.com lucid-updates/universe Sources
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://deb.opera.com stable/non-free Packages
Hit http://linux.dropbox.com lucid Release
Hit http://linux.dropbox.com lucid/main Packages
Fetched 137kB in 0s (225kB/s)
Reading package lists... Done

```

---

### Post by sikander3786 on 2010-12-12
There are no authentication problems whatsoever in apt-get update.

Are you still getting that authentication error when you try to install something?

---

### Post by minerbog on 2010-12-14
1

---

### Post by minerbog on 2010-12-14
> **sikander3786 said:**
> There are no authentication problems whatsoever in apt-get update.

Are you still getting that authentication error when you try to install something?

No it's only when I try and update?

---

### Post by Colin@oxford on 2010-12-14
I am getting a similar problems today - but only if I use the Update Manager or Synaptic.  apt-get upgrade does not complain about unauthenticated packages, but Synaptic does.  The packages that both say need upgrading are:

gnome-settings-daemon libc-bin libc-dev-bin libc6 libc6-dbg libc6-dev
  libc6-i686

---

### Post by sikander3786 on 2010-12-14
> **Colin@oxford said:**
> I am getting a similar problems today - but only if I use the Update Manager or Synaptic.  apt-get upgrade does not complain about unauthenticated packages, but Synaptic does.  The packages that both say need upgrading are:

gnome-settings-daemon libc-bin libc-dev-bin libc6 libc6-dbg libc6-dev
  libc6-i686
Please post the complete output of *sudo apt-get update*.

@minorbog: That is unusual. apt-get is not complaining about anything. Can you post a screenshot when it happens?

---

### Post by Colin@oxford on 2010-12-14
Running apt-get update produces this output, and then the update manager was happy (no unauthenticated packages).

> Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB   
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg [189B]                   
Get: 3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB [62.9kB]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Get: 4 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]                   
Ign [http://archive.canonical.com/](http://archive.canonical.com/) lucid/partner Translation-en_GB              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Get: 5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB [2,332B]
Get: 6 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB [33.9kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Get: 7 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB [37.7kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release.gpg [198B]          
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release [44.7kB]            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources
Fetched 182kB in 1s (157kB/s)
Reading package lists... Done


---

