---
title: "Can't update/upgrade because of purged app"
date: 2020-06-11
forum: Installation &amp; Upgrades
---

### Post by porphyry52 on 2020-06-11
Here's what happens when I try to update/upgrade:
```
~ $ sudo apt update
[sudo] password for q: 
Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 https://repo.skype.com/deb stable InRelease                              
Hit:3 http://archive.canonical.com bionic InRelease                            
Hit:4 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Hit:5 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease           
Ign:6 http://ppa.launchpad.net/linphone/release/ubuntu bionic InRelease        
Hit:7 http://security.ubuntu.com/ubuntu bionic-security InRelease       
[B]Err:8 http://ppa.launchpad.net/linphone/release/ubuntu bionic Release         
  404  Not Found [IP: 91.189.95.83 80][/B]
Reading package lists... Done                      
E: The repository 'http://ppa.launchpad.net/linphone/release/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
~ $ ~ $ sudo apt-get clean
~ $ sudo add-apt-repository -r ppa:http://ppa.launchpad.net/linphone/release/ubuntu bionic Release
Error: need a single repository as argument
~ $ sudo add-apt-repository -r ppa:http://ppa.launchpad.net/linphone/release/ubuntu
Cannot add PPA: 'ppa:~http/ubuntu/ppa'.
The user named '~http' does not have any PPA
~ $ sudo add-apt-repository -r ppa:linphone/release/ubuntu
Cannot add PPA: 'ppa:~linphone/release/ubuntu'.
The team named '~linphone' has no PPA named 'release/ubuntu'
Please choose from the following available PPAs:
 * 'release':  Linphone (release)
~ $ sudo add-apt-repository -r ppa:linphone *
Error: need a single repository as argument
~ $ sudo add-apt-repository -r ppa:linphone*
Cannot add PPA: 'ppa:~linphone*/ubuntu/ppa'.
ERROR: '~linphone*' user or team does not exist.
~ $ sudo apt update -q
Hit:1 https://repo.skype.com/deb stable InRelease
Hit:2 http://security.ubuntu.com/ubuntu bionic-security InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Hit:4 http://archive.canonical.com bionic InRelease
Hit:5 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease
Ign:6 http://ppa.launchpad.net/linphone/release/ubuntu bionic InRelease
Hit:7 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease
[B]Err:8 http://ppa.launchpad.net/linphone/release/ubuntu bionic Release
  404  Not Found [IP: 91.189.95.83 80][/B]
Reading package lists...
E: The repository 'http://ppa.launchpad.net/linphone/release/ubuntu bionic Release' does not have a Release file.

```
I removed and purged linphone and replaced it with ekiga.  Since then I cannot update/upgrade because of this Err:8.  How do I get rid of it? Reinstalling linphone is not an option.

---

### Post by CelticWarrior on 2020-06-11
Just remove the Linphone's PPA.

---

### Post by deadflowr on 2020-06-11
Should be
```
sudo add-apt-repository -r ppa:linphone/release
```
That said, since the ppa has no bionic packages, and never did, you can try deleting the list file for it in /etc/apt/sources.list.d
This would, of course be a bit more nuclear but will do the job all the same.

FTR, linphone has packages in the regular Ubuntu archives so more likely you installed it from there as opposed to the ppa,
which as stated, has no bionic archives so nothing would have been installed from it.

---

### Post by ActionParsnip on 2020-06-12
[http://ppa.launchpad.net/linphone/release/ubuntu/dists/](http://ppa.launchpad.net/linphone/release/ubuntu/dists/)

The PPA doesn't support your release and should be removed.

---

### Post by ActionParsnip on 2020-06-12
Not all PPAs support all releases and they are under no obligation to do so either

---

### Post by porphyry52 on 2020-06-14
> **deadflowr said:**
> Should be
```
sudo add-apt-repository -r ppa:linphone/release
```
That said, since the ppa has no bionic packages, and never did, you can try deleting the list file for it in /etc/apt/sources.list.d
This would, of course be a bit more nuclear but will do the job all the same.


Many thanks. Didn't have to use the nuclear option.

---

