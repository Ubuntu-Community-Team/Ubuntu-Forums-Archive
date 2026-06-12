---
title: "Trouble getting g++ compiler"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by Bowjangles on 2007-12-02
So I'm trying to install the g++ complier and when I download the package it asks me to insert my Ubuntu 7.10 cd.  I do that and then I get hit with a bunch files not being found. Anyone know a sure fire way to get this compiler installed?

Thanks for your help,

---

### Post by yabbadabbadont on 2007-12-02
In a terminal window, run:
```
sudo apt-get install build-essential
```

---

### Post by Bowjangles on 2007-12-02
So I did that and I got the same error I was getting before it.  Here I'll post the what the errors look like.:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc
  manpages-dev libstdc++6-4.1-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev patch
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7934kB of archives.
After unpacking 31.9MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

----------------------------------------------------------------------------------------------------
After I insert the cd it gets to about 20% progress then I get the following error:


Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/g/glibc/libc6-dev_2.6.1-1ubuntu9_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-16ubuntu2_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/g/gcc-4.1/g++-4.1_4.1.2-16ubuntu2_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/p/patch/patch_2.5.9-4_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/d/dpkg/dpkg-dev_1.14.5ubuntu16_all.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by mellowd on 2007-12-02
Sounds like your CD is dodgy. Take the CD out of your sources file and retry.

---

### Post by LaRoza on 2007-12-02
System->Administration->Synaptic Package Manager

Settings->Repositories

Uncheck the CD.

---

### Post by Bowjangles on 2007-12-02
thanks guys! that did the trick. Now I can go about writing my program for class.  Hope this post helps for anyone who needs it.

---

### Post by LaRoza on 2007-12-02
> **Bowjangles said:**
> thanks guys! that did the trick. Now I can go about writing my program for class.  Hope this post helps for anyone who needs it.

Glad we could help.

Mark it as solved.

---

### Post by Zenith42 on 2007-12-14
Hiya. I had the exact same problem and it didn't help... I got:

E: Couldn't find package build-essential

whereas when I put the CD in it gave me the same as described above...
I know the CD's dodgy... I don't know if that has anything to do with the fact that I had to "overburn" it or what, but I don't want to have to do the whole thing over again. 

I'm a complete noob, so this site has been a godsend. Still, I'm stumped.

---

### Post by ifknot on 2008-05-09
Thank you!

Excellent post solves my exact same problem :)

---

