---
title: "Cannot install Wine on Ubuntu 12.04 (Precise) x64"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2012-09-17
I have Ubuntu 12.04 x64.  I have been trying to install Wine to no avail.  I entered a question on Launchpad and received some suggestions.  It seems that whoever was trying to help me assumed I had been successful.  I went back to Launchpad and said the issue was not resolved.  Here is the address of my thread:

[https://answers.launchpad.net/ubuntu/+source/apt/+question/208510]("https://answers.launchpad.net/ubuntu/+source/apt/+question/208510")

Can someone give me some more suggestions?  I've tried many of the solutions that some folks have said worked, but none worked for me.

---

### Post by sanderj on 2012-09-17
Does 
```
sudo apt-get dist-upgrade
```

help?

---

### Post by cscj01 on 2012-09-17
No. I get the following:```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  ia32-libs
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```I'm going nuts trying to figure this out.

---

### Post by sanderj on 2012-09-18
Can you post the output, including the "sudo apt-get dist-upgrade"? Just to make sure you typed that?

---

### Post by cscj01 on 2012-09-18
Here you are:```
butch@Car-Photo-Ubuntu:~$ sudo apt-get dist-upgrade
[sudo] password for butch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  ia32-libs
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
butch@Car-Photo-Ubuntu:~$
```Let me add that ia32-libs shows in Update Manager as a Recommended Update, but I cannot check its' install box.  If I use Synaptic to select it for upgrade, it wants to remove many packages (338 to be exact).  Among these are many apps such as Firefox, Thunderbird, Gimp, Audacity, Brasero, Darktable, and on and on and on.  Also many system packages are indicated to be removed.  I believe there is something dreadfully wrong here, but I cannot resolve it.

---

### Post by cscj01 on 2012-09-18
I removed ia32-libs because it could not be upgraded without removing much of my system and nothing depended on it.  I then tried to install wine again after doing an```
sudo apt-get update
```but kept getting getting unmet dependencies.  As I follow those dependencies, I end up with dependencies on one leg of libglib2.0-0:i386 that indicates a dependency on upstart-jobs and initscripts.  I get a message saying there is a substitution for upstart jobs to upstart and both upstart and initscripts are at their latest versions.

Maybe I should disable all my PPA's and try the wine install?

---

### Post by cscj01 on 2012-09-18
Thanks to this post [http://ubuntuforums.org/showpost.php?p=12246372&postcount=7]("http://ubuntuforums.org/showpost.php?p=12246372&postcount=7"), I now have Wine installed.

Thanks for your help.

---

