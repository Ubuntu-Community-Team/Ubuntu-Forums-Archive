---
title: "Assistance Updating Driver"
date: 2021-01-02
forum: Installation &amp; Upgrades
---

### Post by nbmota on 2021-01-02
I just ran the following command on the Linux terminal:
[LIST]
[*]**sudo apt update** 
[/LIST]
Then, I got a message that said:
[LIST]
[*] *1 package can be upgraded. Run 'apt list --upgradable' to see it.* 
[/LIST]
So, I ran the following command in the terminal also:
[LIST]
[*]**sudo apt list --upgradable** 
[/LIST]
Then, I got the following messages in the terminal:
[LIST]
[*][I]ubuntu-drivers-common/focal-updates 1:0.8.4~0.20.04.3 amd64 [upgradable from: 1:0.8.1]
[/I] 
[*]*N: There is 1 additional version. Please use the '-a' switch to see it* 
[/LIST]

Yet, I cannot figure out how to update the driver that the above message indicated in Ubuntu. Could anyone tell me how to update the following driver?
[LIST]
[*]*ubuntu-drivers-common/focal-updates 1:0.8.4~0.20.04.3 amd64 [upgradable from: 1:0.8.1]* 
[/LIST]
I appriciate any assistance.


Sincerely,

Nataly Mota

---

### Post by deadflowr on 2021-01-02
There is no driver to update.
The update is for the driver installer mechanism package.
The package desription reads as thus
```
Description: **Detect and install additional Ubuntu driver packages**
 This package aggregates and abstracts Ubuntu specific logic and knowledge
 about third-party driver packages. It provides:
 .
  - a Python API for detecting driver packages for a particular piece of
    hardware or the whole system.
 .
  - an "ubuntu-drivers" command line tool to list or install driver packages
    (mostly for integration in installers).
 .
  - some NVidia specific support code to find the most appropriate driver
    version, as well as setting up the alternatives symlinks that the
    proprietary NVidia and FGLRX packages use.
```
So you can just run
```
sudo apt upgrade
```
and  be done.

---

