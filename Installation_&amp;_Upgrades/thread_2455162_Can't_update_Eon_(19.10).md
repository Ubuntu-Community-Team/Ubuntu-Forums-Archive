---
title: "Can't update Eon (19.10) ??"
date: 2020-12-13
forum: Installation &amp; Upgrades
---

### Post by oygle on 2020-12-13
I went to add a new application called Planner from Synaptic and got a few error messages, files not found. In terminal, an update shows:

```
$ sudo apt update
[sudo] password for **********: 
Ign:1 http://au.archive.ubuntu.com/ubuntu eoan InRelease                                                                                      
Ign:2 http://au.archive.ubuntu.com/ubuntu eoan-updates InRelease                                                                              
Ign:3 http://security.ubuntu.com/ubuntu eoan-security InRelease                       
Ign:4 http://au.archive.ubuntu.com/ubuntu eoan-backports InRelease                    
Hit:5 http://ppa.launchpad.net/audio-recorder/ppa/ubuntu eoan InRelease               
Err:6 http://au.archive.ubuntu.com/ubuntu eoan Release                                
  404  Not Found [IP: 202.158.214.106 80]
Err:7 http://au.archive.ubuntu.com/ubuntu eoan-updates Release                                                                  
  404  Not Found [IP: 202.158.214.106 80]
Err:8 http://au.archive.ubuntu.com/ubuntu eoan-backports Release                                                                
  404  Not Found [IP: 202.158.214.106 80]
Err:9 http://security.ubuntu.com/ubuntu eoan-security Release                                                                   
  404  Not Found [IP: 91.189.88.142 80]
Ign:10 http://www.scootersoftware.com bcompare4 InRelease                                                                       
Hit:11 http://ppa.launchpad.net/mkusb/ppa/ubuntu eoan InRelease                                           
Hit:12 http://www.scootersoftware.com bcompare4 Release
Reading package lists... Done
E: The repository 'http://au.archive.ubuntu.com/ubuntu eoan Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://au.archive.ubuntu.com/ubuntu eoan-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://au.archive.ubuntu.com/ubuntu eoan-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu eoan-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

Am I to assume this is simply because Eon (vers 19.10 ) is no longer supported ?

---

### Post by TheFu on 2020-12-13
> **oygle said:**
> I went to add a new application called Planner from Synaptic and got a few error messages, files not found. In terminal, an update shows:



Am I to assume this is simply because Eon (vers 19.10 ) is no longer supported ?

Yes.  Move to a supported release. It is lkely that because you didn't move before support ended then a full reinstall will be needed.

Regardless, backup anything you don't want to lose before doing anything. Sometimes bad things happen during complex changes like OS upgrades.

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle) explains ubuntu release cycles.

---

### Post by Bashing-om on 2020-12-13
oygle - hey

Yup -
> 
Ubuntu 19.10 (Eoan Ermine) was the 31st release of Ubuntu, support ended July 2020.


[INDENT][INDENT]the short and the long of it all
[/INDENT][/INDENT]

---

### Post by DuckHook on 2020-12-13
> **oygle said:**
> …Am I to assume this is simply because Eon (vers 19.10 ) is no longer supported ?

> **TheFu said:**
> Yes.  Move to a supported release.

…[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle) explains ubuntu release cycles.
I would also highly recommend that you stick to LTS releases and stay away from standard releases.

---

### Post by oygle on 2020-12-13
> **TheFu said:**
> Yes.  Move to a supported release. It is lkely that because you didn't move before support ended then a full reinstall will be needed.

Regardless, backup anything you don't want to lose before doing anything. Sometimes bad things happen during complex changes like OS upgrades.

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle) explains ubuntu release cycles.

Okay thanks. Yes, I always do a fresh install ( after backups) of any release.

> **Bashing-om said:**
> oygle - hey

Yup -

[INDENT][INDENT]the short and the long of it all
[/INDENT][/INDENT]

Thanks  :)

---

### Post by oygle on 2020-12-13
> **DuckHook said:**
> I would also highly recommend that you stick to LTS releases and stay away from standard releases.

Okay thanks :)

---

