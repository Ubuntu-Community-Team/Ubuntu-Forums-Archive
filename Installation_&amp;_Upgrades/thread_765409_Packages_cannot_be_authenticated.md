---
title: "Packages cannot be authenticated"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by James- on 2008-04-24
Before HH was released I did a "sudo update-manager --devel-release" and now that HH is released, when ever I update it gives me an error :
Not all updates can be installed, Run a partial upgrade, to install as many updates as possible


i press of partial upgrade and it fails giving me :

Error authenticating some packages: libglib1.2ldbl libgtk1.2

Please help

---

### Post by Ub1476 on 2008-04-24
```
sudo apt-get -f install
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by James- on 2008-04-24
thank you seems to be working :D!!!

---

### Post by myonta on 2008-04-29
I'm having pretty much the same problem. However, when I use the code provided, I can only get so far.

After I enter ```
sudo apt-get -f install
``` I get the following:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxml-rss-perl libswt3.2-gtk-jni
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1342 not upgraded
```
I think that's all fine.
The next line, ```
sudo apt-get update && sudo apt-get upgrade
``` prints out the server and package lists and then this:
```
856 upgraded, 0 newly installed, 0 to remove and 486 not upgraded.
Need to get 1419MB/1422MB of archives.
After unpacking, 82.5MB disk space will be freed.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)'
in the drive '/cdrom/' and press enter
```
It so happens I have a copy of the 8.04 (AMD64) Desktop install disk but that's clearly not what it wants:
```
Get:1 http://ca.archive.ubuntu.com hardy/main libc6-i386 2.7-10ubuntu3 [3699kB]
Media change: please insert the disc labeled            
 'Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)'
in the drive '/cdrom/' and press enter
```
Ctrl-C and I'm back to the prompt. Thing is, I'd rather not have to download all the release media just to workaround this issue. Though I'll do whatever I have to do.

I haven't even gotten to ```
sudo apt-get dist-upgrade
``` yet.

Let me know what I should do. Thanks,
~Jon

---

### Post by myonta on 2008-04-29
Think I've got it:

I checked my third-party software list and noticed the cdrom listing. I just deleted it and now it's downloading as expected.

It'll still be a bit before it's done, but here's hoping it'll install without issues.
~Jon

---

