---
title: "unable to install software in Ubuntu"
date: 2012-04-21
forum: Installation &amp; Upgrades
---

### Post by Mallikarjuna1234 on 2012-04-21
hi folks,

i am new to ubuntu,

i have installed the ubunut 11.04

i loged in as root, while i am installing when i click on the getsoftware of ubuntu software center, loading symbol is coming and even though waiting for long time symbol exists. but no installation.

please help me

thanks in advance

---

### Post by Metul Burr on 2012-04-21
You can use the terminal to download the same repos from soft.center
```
sudo apt-cache search <your_program>
``` to search for repos
```
sudo apt-get install <your_program>
``` to install

---

### Post by Mallikarjuna1234 on 2012-04-21
i am unable to connect to repository what might be the problem.

---

### Post by mörgæs on 2012-04-21
Try to change mirror.

---

### Post by Mallikarjuna1234 on 2012-04-21
> **mörgæs said:**
> Try to change mirror.

hi morgaes the problem is i am not able to connect to repository, that's why when i click on getsoftware button loading symbol is comming. how to rectify this.

---

### Post by mörgæs on 2012-04-21
Yes, that's why you should try to change mirror / server to download from (using 'software sources').

---

### Post by raja.genupula on 2012-04-21
copy either information at details arrow or do as sudo apt-get update and post the output of it

---

### Post by raja.genupula on 2012-04-21
copy either information at details arrow or do as ```
sudo apt-get update
``` and post the output of it

---

### Post by Mallikarjuna1234 on 2012-04-22
> **raja.genupula said:**
> copy either information at details arrow or do as sudo apt-get update and post the output of it

it is giving the error for the command

sudo apt-get update

Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
  
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports InRelease                     
  
Err [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
  
Err [http://archive.cannonical.com](http://archive.cannonical.com) maverick InRelease                           
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
  Unable to connect to 192.168.0.52:3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg
  Unable to connect to 192.168.0.52:3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg
  Unable to connect to 192.168.0.52:3128:
Err [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg
  Unable to connect to 192.168.0.52:3128:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg
  Unable to connect to 192.168.0.52:3128:
Err [http://archive.cannonical.com](http://archive.cannonical.com) maverick Release.gpg
  Unable to connect to 192.168.0.52:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg
  Unable to connect to 192.168.0.52:3128:
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports Release.gpg
  Unable to connect to 192.168.0.52:3128:
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease](http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/InRelease](http://archive.canonical.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/InRelease](http://extras.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://archive.cannonical.com/ubuntu/dists/maverick/InRelease](http://archive.cannonical.com/ubuntu/dists/maverick/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Unable to connect to 192.168.0.52:3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 192.168.0.52:3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Unable to connect to 192.168.0.52:3128:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/natty-backports/Release.gpg)  Unable to connect to 192.168.0.52:3128:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/Release.gpg](http://archive.canonical.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 192.168.0.52:3128:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to 192.168.0.52:3128:

W: Failed to fetch [http://archive.cannonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.cannonical.com/ubuntu/dists/maverick/Release.gpg)  Unable to connect to 192.168.0.52:3128:

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/natty/Release.gpg)  Unable to connect to 192.168.0.52:3128:

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by mörgæs on 2012-04-22
The poor thing has been upgraded (at least) from 10.10 with not-so-good results. I believe you are better off with a fresh install.

---

