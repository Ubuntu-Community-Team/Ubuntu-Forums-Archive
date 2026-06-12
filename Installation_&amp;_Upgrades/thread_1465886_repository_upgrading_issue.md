---
title: "repository upgrading issue"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by valke on 2010-04-29
Hi, when I run Update Manager, I get this error.

```
Failed to fetch http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

When I run sudo apt-get update, I get this error.

```
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US              
Get:2 http://dl.google.com stable Release [2,540B]                             
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://ppa.launchpad.net lucid Release.gpg                       
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://ppa.launchpad.net/do-core/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                
Ign http://ppa.launchpad.net lucid Release                                     
Get:3 http://dl.google.com stable/main Packages [916B]                         
Ign http://ppa.launchpad.net lucid/main Packages                               
Hit http://security.ubuntu.com lucid-security/main Packages                    
Ign http://ppa.launchpad.net lucid/main Packages                               
Hit http://security.ubuntu.com lucid-security/restricted Packages    
Hit http://security.ubuntu.com lucid-security/main Sources           
Hit http://security.ubuntu.com lucid-security/restricted Sources     
Hit http://security.ubuntu.com lucid-security/universe Packages      
Hit http://security.ubuntu.com lucid-security/universe Sources       
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Err http://ppa.launchpad.net lucid/main Packages                     
  404  Not Found
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Fetched 3,645B in 3s (1,091B/s)
W: Failed to fetch http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

How do I fix this?

---

### Post by Super McMac on 2010-04-29
I'm having the same problem. :confused:

---

### Post by valke on 2010-04-30
bump

---

### Post by smielke on 2010-05-09
Any solution to this yet?  I am having the same problem - very strange.

---

### Post by Danbo19 on 2010-05-28
Same error here. Seems like an error with the gnome-do ppa. I added it with sudo add-apt-repository ppa:do-core/ppa. I was just going to remove the ppa but there is apparently no way to do that built in to Ubuntu? I tried [ppa-purge]("https://launchpad.net/ppa-purge") but It didn't work. Any one else know how to fix this error or how to remove a ppa that was added with add-apt-repository?

---

### Post by Soul-Sing on 2010-05-28
404's are server errors, please try later connecting, prob. not a problem within your system at all.

---

### Post by gavdari on 2010-08-29
I found the solution somewhere else and thought maybe you're still having the same problem.
For me it was do-core team ppa, and I noticed they don't have any Lucid version. Changing the version to Karmic in software sources solved the problem, though I do not know whether it works or not. If not, then I guess there is nothing we can do since there is nothing for Lucid yet.

---

