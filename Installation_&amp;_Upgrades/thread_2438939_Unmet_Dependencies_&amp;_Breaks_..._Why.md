---
title: "Unmet Dependencies &amp; Breaks ... Why?"
date: 2020-03-20
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2020-03-20
I thought I could find a previous post resolving this issue, but could not. One must ask ... Why is there UNMET Dependencies???

```

~$ sudo aptitude dist-upgrade
The following NEW packages will be installed:
  linux-headers-4.15.0-91{a} linux-headers-4.15.0-91-lowlatency{a} 
  linux-image-4.15.0-91-lowlatency{a} linux-modules-4.15.0-91-lowlatency{a} 
The following packages will be upgraded:
  gcc-8-base{b} grub-common grub-pc grub-pc-bin grub2-common libatomic1 
  libcc1-0 libgcc1{b} libgomp1 libitm1 liblsan0 libmpx2 libquadmath0 
  libstdc++6 libtsan0 linux-headers-lowlatency linux-image-lowlatency 
  linux-lowlatency 
18 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 70.5 MB of archives. After unpacking 332 MB will be used.
The following packages have unmet dependencies:
 gcc-8-base : Breaks: gcc-8-base:i386 (!= 8.3.0-26ubuntu1~18.04) but 8.3.0-6ubuntu1~18.04.1 is installed
 gcc-8-base:i386 : Breaks: gcc-8-base (!= 8.3.0-6ubuntu1~18.04.1) but 8.3.0-26ubuntu1~18.04 is to be installed
 libgcc1 : Breaks: libgcc1:i386 (!= 1:8.3.0-26ubuntu1~18.04) but 1:8.3.0-6ubuntu1~18.04.1 is installed
 libgcc1:i386 : Breaks: libgcc1 (!= 1:8.3.0-6ubuntu1~18.04.1) but 1:8.3.0-26ubuntu1~18.04 is to be installed
The following actions will resolve these dependencies:

      Keep the following packages at their current version:
1)      gcc-8-base [8.3.0-6ubuntu1~18.04.1 (now)]          
2)      libatomic1 [8.3.0-6ubuntu1~18.04.1 (now)]          
3)      libcc1-0 [8.3.0-6ubuntu1~18.04.1 (now)]            
4)      libgcc1 [1:8.3.0-6ubuntu1~18.04.1 (now)]           
5)      libgomp1 [8.3.0-6ubuntu1~18.04.1 (now)]            
6)      libitm1 [8.3.0-6ubuntu1~18.04.1 (now)]             
7)      liblsan0 [8.3.0-6ubuntu1~18.04.1 (now)]            
8)      libmpx2 [8.3.0-6ubuntu1~18.04.1 (now)]             
9)      libquadmath0 [8.3.0-6ubuntu1~18.04.1 (now)]        
10)     libstdc++6 [8.3.0-6ubuntu1~18.04.1 (now)]          
11)     libtsan0 [8.3.0-6ubuntu1~18.04.1 (now)]            

Accept this solution? [Y/n/q/?] 


```

Surely everyone who is not an expert or programmer, would be stumped at this point - including me! Yes? -Or- No? -Or- Quit? 
Why is this happening? How do "we the people" know which software version one should keep, and what to do with "Broken or Unmet Dependencies? 

When I brought up Synaptic Pkg. Mgr., nothing shows up when selecting "Broken Pkgs".  Still stumped ! ! !

Thanks.

---

### Post by TheFu on 2020-03-20
Usually, the issue is that 
```
sudo apt update
```
hasn't been run recently.

Normal people don't manually install .deb packages.  
Normal people limit their use of PPAs to only trusted sources.

Any package manually installed can include dependencies that conflict with other packages and updates.
The only fix that i know is to manually uninstall any manually installed .deb files, patch everything to be current, then find a new version of the problem package that doesn't have conflicts.

Aptitude should probably not be used all the time.  Use apt or apt-get unless there is a specific reason to use aptitude.

BTW, i would answer "NO" to that question until a solution that removes gcc-8-base is offered.

---

### Post by Rick St. George on 2020-03-22
As mentioned, running UbuntuStudio which has a lot of bundled software. The only softward I've installed via Deb Pkg. is VirutualBox, Opera & Pale Moon browsers (for variable security reasons), and CodeBlocks. Of course, I always run "update" first, and this time - ALL were checked (incl. multiverse & universe).

And the reason I use "aptitude" is due to 1Fallen's confirmation of my actions in this post (see last comment);
[https://ubuntuforums.org/showthread.php?t=2427235&page=2](https://ubuntuforums.org/showthread.php?t=2427235&page=2)
You'll notice, 64 programs were removed.

Moreover, the following is what now shows up for "apt sources";

```

~$ inxi -r
Repos:     Active apt sources in file: /etc/apt/sources.list
           deb [arch=amd64] http://us.archive.ubuntu.com/ubuntu/ bionic-security main restricted universe multiverse
           deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-security main restricted universe multiverse #Added by software-properties
           deb [arch=amd64] http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse
           deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted universe multiverse #Added by software-properties
           deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse
           deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted universe multiverse #Added by software-properties


```

So, looks like some doubling here - by "Software Properties".  Another problem?!?!?  I also notice the version currently running does not match with what shows above in the first post.

```

~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic


```

---

### Post by Rick St. George on 2020-03-22
Think this worked. Used Aptitude to "install" gcc-8-base. It upgraded it and resolved dependencies.
Upon running upgrade again ... nothing to upgrade and no unmet dependencies showed.

Sometimes I amaze myself.... sometimes! Its only Logic - Right?
Hope this helps someone.

:guitar:

---

