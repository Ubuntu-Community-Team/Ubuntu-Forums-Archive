---
title: "Some repositories fail to update: &quot;Is no longer signed&quot;"
date: 2018-05-15
forum: Installation &amp; Upgrades
---

### Post by christian79 on 2018-05-15
Hello,


I have a server in an internal network which uses a proxy to access some parts of the web. For now the updates worked just fine, but it stopped working for 3 repositories a few weeks ago. Since then I have not found a solution to this issue.


This is my command line:
```
$ sudo apt-get update
[sudo] password for ctwx: 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://de.archive.ubuntu.com/ubuntu xenial InRelease          
Get:3 http://dl.google.com/linux/chrome/deb stable Release [1,189 B]           
Get:4 http://de.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]    
Err:5 http://dl.google.com/linux/chrome/deb stable Release.gpg                 
  500  Internal Server Error
Hit:6 https://deb.nodesource.com/node_6.x xenial InRelease                     
Hit:7 https://download.docker.com/linux/ubuntu xenial InRelease                
Get:8 http://de.archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]  
Ign:9 http://pkg.jenkins.io/debian-stable binary/ InRelease                    
Get:10 http://de.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [775 kB]
Hit:11 http://pkg.jenkins.io/debian-stable binary/ Release                     
Ign:12 http://security.ubuntu.com/ubuntu xenial-security InRelease             
Ign:13 http://pkg.jenkins.io/debian-stable binary/ Release.gpg                
Get:14 http://de.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [713 kB]
Get:15 http://security.ubuntu.com/ubuntu xenial-security Release [106 kB]      
Err:16 http://security.ubuntu.com/ubuntu xenial-security Release.gpg
  500  Internal Server Error
Hit:17 https://packages.gitlab.com/runner/gitlab-runner/ubuntu xenial InRelease
Get:18 http://de.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [627 kB]                                            
Get:19 http://de.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [577 kB]
Reading package lists... Done                               
E: The repository 'http://dl.google.com/linux/chrome/deb stable Release' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://pkg.jenkins.io/debian-stable binary/ Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu xenial-security Release' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```


I already tried to add the keys manually but it does not work. Interestingly not only the third party repos fail but also the security repository from Ubuntu itself.
This machine is running Ubuntu 16.04.


Do you have any suggestions how to resolve this issue?

---

### Post by dino99 on 2018-05-15
Testing [http://dl.google.com/](http://dl.google.com/) is switching to [https://www.google.com/chrome/](https://www.google.com/chrome/) 
Trying the new url [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)  is working

So now https is used with a new path
[https://www.tecmint.com/install-google-chrome-in-debian-ubuntu-linux-mint/](https://www.tecmint.com/install-google-chrome-in-debian-ubuntu-linux-mint/)

---

### Post by christian79 on 2018-05-15
Thanks! That fixed at least the google repo. But the Ubuntu security repo is still failing.

The https was also the issue on the Jenkins repo. I did the steps as described here: [http://pkg.jenkins-ci.org/debian/](http://pkg.jenkins-ci.org/debian/)

---

### Post by dino99 on 2018-05-15
i does not get issue with:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe

---

### Post by christian79 on 2018-05-15
Strange... Maybe the internal IT department changed something on the firewall. I replaced it by 
> deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-security main restricted universe multiverse
#deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-security main restricted universe multiverse
This works fine. 

Thank you for your help!

---

