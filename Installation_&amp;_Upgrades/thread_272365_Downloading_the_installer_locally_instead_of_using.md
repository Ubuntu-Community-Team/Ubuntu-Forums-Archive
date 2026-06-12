---
title: "Downloading the installer locally instead of using repositories"
date: 2006-10-06
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-10-06
I am planning to deploy multiple xubuntu pcs. I am thinking that it is much better to download the updates only once and point other pcs to get the update on the first pc that downloads the update. Is there any options that can do like this?

---

### Post by Kateikyoushi on 2006-10-06
You can make local repository, [for example.]("http://www.omenix.org/?cat=3")

---

### Post by TheWizzard on 2006-10-06
very easy:

if you do a fresh install on one pc you should execute these commands:
```
sudo apt-get -y update
sudo apt-get -y upgrade
```

apt-get puts the .deb files in /var/cache/apt/archives 
if you are on a network, you can make a local repo using the .deb files. 
alternatively, you can just copy all .deb files to the /var/cache/apt/archives directories of the other PC's and execute apt-get update & upgrade on the other PC's.

apt does not download the .deb files if they are already in the cache directory.

cheers

---

### Post by tagra123 on 2006-10-06
Also you can look at debmirror and apt-proxy.

---

### Post by textguru on 2006-10-09
> **Kateikyoushi said:**
> You can make local repository, [for example.]("http://www.omenix.org/?cat=3")

Does repos means the host that has a copy of the patches? What other services that I need to enable on the local repository other than Apache?

---

### Post by textguru on 2006-10-18
> **TheWizzard said:**
> very easy:

if you do a fresh install on one pc you should execute these commands:
```
sudo apt-get -y update
sudo apt-get -y upgrade
```

apt-get puts the .deb files in /var/cache/apt/archives 
if you are on a network, you can make a local repo using the .deb files. 
alternatively, you can just copy all .deb files to the /var/cache/apt/archives directories of the other PC's and execute apt-get update & upgrade on the other PC's.

apt does not download the .deb files if they are already in the cache directory.

cheers

Have you tried this before? I have tried copying files on /var/cache/apt/archives to new machine and still it is still looking for internet repositories. Do I need to change repositories?

---

### Post by TheWizzard on 2006-10-20
> **textguru said:**
> Have you tried this before? I have tried copying files on /var/cache/apt/archives to new machine and still it is still looking for internet repositories. Do I need to change repositories?

mmm, apt-get upgrade should check /var/cache/apt/archives before downloading. strange... 

another option (less elegant) is to copy all deb files from /var/cache/apt/archives to the new computer and then:
```
sudo dpkg -i *.deb 
```

if you want to make a local repo, just search the forums. there's plenty of information.

---

### Post by textguru on 2006-10-20
I have followed what it is written on [http://ubuntuforums.org/printthread.php?t=42862](http://ubuntuforums.org/printthread.php?t=42862)

But I cant make this working on my setup. 

What I did on Local PC (that will be the repository server that already have apache installed): 
1. I've copied all the contents of /var/cache/apt/archives to /var/www/archives 
```
sudo cp -R /var/cache/apt/archives/ /var/www/
```
2. create autorepo file on /bin with this lines:
```
#!/bin/bash
sudo dpkg-scanpackages . /dev/null | gzip -9c > Packages.gz
sudo dpkg-scansources . /dev/null | gzip -9c > Sources.gz
```
3. I've make it executable sudo chmod +x autorepo
4. create repo Packages & Sources :
```
cd /var/www/archives
sudo autorepo
```

On remote PC:
1. Update apt sources of remote pcs with this line ONLY:
```
##Local Repository
deb http://ip/ archives/
```
2. run  apt-get update:
```
ubuntu@mypc:~$ sudo apt-get update
Ign http://<ip> archives/ Release.gpg
Ign http://<ip> archives/ Release
Ign http://<ip> archives/ Packages
Hit http://<ip> archives/ Packages
Reading package lists... Done

```
3. I got this error:
```
admin@remotepc:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  bind9-host cpio dnsutils firefox gzip libbind9-0 libdns21 libgnutls12
  libisc11 libisccc0 libisccfg1 libkrb53 liblwres9 libnspr4 libnss3
  libssl0.9.8 libtag1c2a libtagc0 libtheora0 libwmf0.2-7 libxfont1
  libxine-main1 linux-386 linux-image-2.6.15-26-386
  linux-restricted-modules-2.6.15-26-386 linux-restricted-modules-common
  mozilla-thunderbird openssh-client openssh-server python2.4
  python2.4-minimal readahead ssh xinit xserver-xorg-core
35 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 65.0MB of archives.
After unpacking 242kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  gzip libssl0.9.8 python2.4 python2.4-minimal cpio libgnutls12 libisc11
  libdns21 libisccc0 libisccfg1 libbind9-0 liblwres9 bind9-host dnsutils
  libkrb53 openssh-server openssh-client libnspr4 libnss3 firefox libtag1c2a
  libtagc0 libtheora0 libwmf0.2-7 libxfont1 libxine-main1 linux-386
  linux-image-2.6.15-26-386 linux-restricted-modules-common
  linux-restricted-modules-2.6.15-26-386 mozilla-thunderbird readahead xinit
  xserver-xorg-core ssh
Install these packages without verification [y/N]? Y
Err http://<ip> archives/ gzip 1.3.5-12ubuntu0.1
  404 Not Found
Err http://<ip> archives/ libssl0.9.8 0.9.8a-7ubuntu0.3
  404 Not Found
Err http://<ip> archives/ python2.4 2.4.3-0ubuntu6
  404 Not Found
Err http://<ip> archives/ python2.4-minimal 2.4.3-0ubuntu6
  404 Not Found
Err http://<ip> archives/ cpio 2.6-10ubuntu0.2
  404 Not Found
Err http://<ip> archives/ libgnutls12 1.2.9-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libisc11 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libdns21 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libisccc0 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libisccfg1 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libbind9-0 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ liblwres9 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ bind9-host 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ dnsutils 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libkrb53 1.4.3-5ubuntu0.1
  404 Not Found
Err http://<ip> archives/ openssh-server 1:4.2p1-7ubuntu3.1
  404 Not Found
Err http://<ip> archives/ openssh-client 1:4.2p1-7ubuntu3.1
  404 Not Found
Err http://<ip> archives/ libnspr4 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
  404 Not Found
Err http://<ip> archives/ libnss3 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
  404 Not Found
Err http://<ip> archives/ firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
  404 Not Found
Err http://<ip> archives/ libtag1c2a 1.4-4~dapper1
  404 Not Found
Err http://<ip> archives/ libtagc0 1.4-4~dapper1
  404 Not Found
Err http://<ip> archives/ libtheora0 0.0.0.alpha7-1ubuntu1~dapper1
  404 Not Found
Err http://<ip> archives/ libwmf0.2-7 0.2.8.3-3.1ubuntu0.1
  404 Not Found
Err http://<ip> archives/ libxfont1 1:1.0.0-0ubuntu3.2
  404 Not Found
Err http://<ip> archives/ libxine-main1 1.1.1+ubuntu2-7.3
  404 Not Found
Err http://<ip> archives/ linux-386 2.6.15.25
  404 Not Found
Err http://<ip> archives/ linux-image-2.6.15-26-386 2.6.15-26.47
  404 Not Found
Err http://<ip> archives/ linux-restricted-modules-common 2.6.15.11-5
  404 Not Found
Err http://<ip> archives/ linux-restricted-modules-2.6.15-26-386 2.6.15.11-4
  404 Not Found
Err http://<ip> archives/ mozilla-thunderbird 1.5.0.7-0ubuntu0.6.06
  404 Not Found
Err http://<ip> archives/ readahead 1:0.20050517.0220-0ubuntu5~dapper1
  404 Not Found
Err http://<ip> archives/ xinit 1.0.1-0ubuntu3.1
  404 Not Found
Err http://<ip> archives/ xserver-xorg-core 1:1.0.2-0ubuntu10.4
  404 Not Found
Err http://<ip> archives/ ssh 1:4.2p1-7ubuntu3.1
  404 Not Found
Failed to fetch http://<ip>/./gzip_1.3.5-12ubuntu0.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libssl0.9.8_0.9.8a-7ubuntu0.3_i386.deb  404 Not Found
Failed to fetch http://<ip>/./python2.4_2.4.3-0ubuntu6_i386.deb  404 Not Found
Failed to fetch http://<ip>/./python2.4-minimal_2.4.3-0ubuntu6_i386.deb  404 Not Found
Failed to fetch http://<ip>/./cpio_2.6-10ubuntu0.2_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libgnutls12_1.2.9-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libisc11_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libdns21_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libisccc0_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libisccfg1_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libbind9-0_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./liblwres9_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./bind9-host_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./dnsutils_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libkrb53_1.4.3-5ubuntu0.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./openssh-server_1%3a4.2p1-7ubuntu3.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./openssh-client_1%3a4.2p1-7ubuntu3.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libnspr4_2%3a1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libnss3_2%3a1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb  404 Not Found
Failed to fetch http://<ip>/./firefox_1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libtag1c2a_1.4-4~dapper1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libtagc0_1.4-4~dapper1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libtheora0_0.0.0.alpha7-1ubuntu1~dapper1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libwmf0.2-7_0.2.8.3-3.1ubuntu0.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libxfont1_1%3a1.0.0-0ubuntu3.2_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libxine-main1_1.1.1+ubuntu2-7.3_i386.deb  404 Not Found
Failed to fetch http://<ip>/./linux-386_2.6.15.25_i386.deb  404 Not Found
Failed to fetch http://<ip>/./linux-image-2.6.15-26-386_2.6.15-26.47_i386.deb  404 Not Found
Failed to fetch http://<ip>/./linux-restricted-modules-common_2.6.15.11-5_all.deb  404 Not Found
Failed to fetch http://<ip>/./linux-restricted-modules-2.6.15-26-386_2.6.15.11-4_i386.deb  404 Not Found
Failed to fetch http://<ip>/./mozilla-thunderbird_1.5.0.7-0ubuntu0.6.06_i386.deb  404 Not Found
Failed to fetch http://<ip>/./readahead_1%3a0.20050517.0220-0ubuntu5~dapper1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./xinit_1.0.1-0ubuntu3.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./xserver-xorg-core_1%3a1.0.2-0ubuntu10.4_i386.deb  404 Not Found
Failed to fetch http://<ip>/./ssh_1%3a4.2p1-7ubuntu3.1_all.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
admin@remotepc:~$

```

What's wrong on this?

---

### Post by aysiu on 2006-10-20
If they're all using the same hardware, you might actually save time by using PartImage to clone the drive:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by textguru on 2006-10-20
> **aysiu said:**
> If they're all using the same hardware, you might actually save time by using PartImage to clone the drive:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

thanks for the tip but I have different hardware specifications. Probaby I can use this when I have one. But I need to know the reason whats behind the problem.

---

### Post by aysiu on 2006-10-20
Well, it was worth a mention.

I think your best bet is the ```
sudo dpkg -i *.deb
``` of all the files from /var/cache/apt/archives - the option TheWizzard mentioned in post #7.

---

### Post by getglenn on 2006-10-24
i too have been looking for a solution to this problem with sharing downloaded .deb files... for MORE then 12 months!!!

i just cant believe that there isnt an elegant solution by now...

i have tried most of the suggestions in these forums with no success!!!

why is it so hard???

and for those people who suggest "just look in the forum, there is plenty of information",.. yes there is but most of it just DOES NOT WORK... otherwise we wouldnt have to continually post our help requests!

---

### Post by TheWizzard on 2006-10-25
> **getglenn said:**
> i too have been looking for a solution to this problem with sharing downloaded .deb files... for MORE then 12 months!!!

i just cant believe that there isnt an elegant solution by now...

i have tried most of the suggestions in these forums with no success!!!

why is it so hard???

and for those people who suggest "just look in the forum, there is plenty of information",.. yes there is but most of it just DOES NOT WORK... otherwise we wouldnt have to continually post our help requests!

what's the hard part in "sudo dpkg -i *.deb" ???

---

### Post by textguru on 2006-10-25
The only problem with 

```
what's the hard part in "sudo dpkg -i *.deb" ???
```

Is for example, I need to install macromedia flash player, it needs to be still connected to the internet to download some stuff which I do not know. I have tried it and found that it needs to download something from the internet. Hope you might help.

---

### Post by TheWizzard on 2006-10-26
> **textguru said:**
> The only problem with 

```
what's the hard part in "sudo dpkg -i *.deb" ???
```

Is for example, I need to install macromedia flash player, it needs to be still connected to the internet to download some stuff which I do not know. I have tried it and found that it needs to download something from the internet. Hope you might help.

did you install flash on the first box with: 
```
sudo aptitude install flashplugin-nonfree
```
in this case you'll need to answer a few questions. like if you agree with the licence. i don't remember that flash needed to connect to the internet, but i was online anyways. 
don't forget to run 
```
sudo update-flashplugin
```
after you install flash. 

hope this helps

---

### Post by h.mehdi on 2006-12-31
> **textguru said:**
> 
I got this error:
```
admin@remotepc:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  bind9-host cpio dnsutils firefox gzip libbind9-0 libdns21 libgnutls12
  libisc11 libisccc0 libisccfg1 libkrb53 liblwres9 libnspr4 libnss3
  libssl0.9.8 libtag1c2a libtagc0 libtheora0 libwmf0.2-7 libxfont1
  libxine-main1 linux-386 linux-image-2.6.15-26-386
  linux-restricted-modules-2.6.15-26-386 linux-restricted-modules-common
  mozilla-thunderbird openssh-client openssh-server python2.4
  python2.4-minimal readahead ssh xinit xserver-xorg-core
35 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 65.0MB of archives.
After unpacking 242kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  gzip libssl0.9.8 python2.4 python2.4-minimal cpio libgnutls12 libisc11
  libdns21 libisccc0 libisccfg1 libbind9-0 liblwres9 bind9-host dnsutils
  libkrb53 openssh-server openssh-client libnspr4 libnss3 firefox libtag1c2a
  libtagc0 libtheora0 libwmf0.2-7 libxfont1 libxine-main1 linux-386
  linux-image-2.6.15-26-386 linux-restricted-modules-common
  linux-restricted-modules-2.6.15-26-386 mozilla-thunderbird readahead xinit
  xserver-xorg-core ssh
Install these packages without verification [y/N]? Y
Err http://<ip> archives/ gzip 1.3.5-12ubuntu0.1
  404 Not Found
Err http://<ip> archives/ libssl0.9.8 0.9.8a-7ubuntu0.3
  404 Not Found
Err http://<ip> archives/ python2.4 2.4.3-0ubuntu6
  404 Not Found
Err http://<ip> archives/ python2.4-minimal 2.4.3-0ubuntu6
  404 Not Found
Err http://<ip> archives/ cpio 2.6-10ubuntu0.2
  404 Not Found
Err http://<ip> archives/ libgnutls12 1.2.9-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libisc11 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libdns21 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libisccc0 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libisccfg1 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libbind9-0 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ liblwres9 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ bind9-host 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ dnsutils 1:9.3.2-2ubuntu1.1
  404 Not Found
Err http://<ip> archives/ libkrb53 1.4.3-5ubuntu0.1
  404 Not Found
Err http://<ip> archives/ openssh-server 1:4.2p1-7ubuntu3.1
  404 Not Found
Err http://<ip> archives/ openssh-client 1:4.2p1-7ubuntu3.1
  404 Not Found
Err http://<ip> archives/ libnspr4 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
  404 Not Found
Err http://<ip> archives/ libnss3 2:1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06
  404 Not Found
Err http://<ip> archives/ firefox 1.5.dfsg+1.5.0.7-ubuntu0.6.06
  404 Not Found
Err http://<ip> archives/ libtag1c2a 1.4-4~dapper1
  404 Not Found
Err http://<ip> archives/ libtagc0 1.4-4~dapper1
  404 Not Found
Err http://<ip> archives/ libtheora0 0.0.0.alpha7-1ubuntu1~dapper1
  404 Not Found
Err http://<ip> archives/ libwmf0.2-7 0.2.8.3-3.1ubuntu0.1
  404 Not Found
Err http://<ip> archives/ libxfont1 1:1.0.0-0ubuntu3.2
  404 Not Found
Err http://<ip> archives/ libxine-main1 1.1.1+ubuntu2-7.3
  404 Not Found
Err http://<ip> archives/ linux-386 2.6.15.25
  404 Not Found
Err http://<ip> archives/ linux-image-2.6.15-26-386 2.6.15-26.47
  404 Not Found
Err http://<ip> archives/ linux-restricted-modules-common 2.6.15.11-5
  404 Not Found
Err http://<ip> archives/ linux-restricted-modules-2.6.15-26-386 2.6.15.11-4
  404 Not Found
Err http://<ip> archives/ mozilla-thunderbird 1.5.0.7-0ubuntu0.6.06
  404 Not Found
Err http://<ip> archives/ readahead 1:0.20050517.0220-0ubuntu5~dapper1
  404 Not Found
Err http://<ip> archives/ xinit 1.0.1-0ubuntu3.1
  404 Not Found
Err http://<ip> archives/ xserver-xorg-core 1:1.0.2-0ubuntu10.4
  404 Not Found
Err http://<ip> archives/ ssh 1:4.2p1-7ubuntu3.1
  404 Not Found
Failed to fetch http://<ip>/./gzip_1.3.5-12ubuntu0.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libssl0.9.8_0.9.8a-7ubuntu0.3_i386.deb  404 Not Found
Failed to fetch http://<ip>/./python2.4_2.4.3-0ubuntu6_i386.deb  404 Not Found
Failed to fetch http://<ip>/./python2.4-minimal_2.4.3-0ubuntu6_i386.deb  404 Not Found
Failed to fetch http://<ip>/./cpio_2.6-10ubuntu0.2_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libgnutls12_1.2.9-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libisc11_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libdns21_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libisccc0_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libisccfg1_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libbind9-0_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./liblwres9_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./bind9-host_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./dnsutils_1%3a9.3.2-2ubuntu1.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libkrb53_1.4.3-5ubuntu0.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./openssh-server_1%3a4.2p1-7ubuntu3.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./openssh-client_1%3a4.2p1-7ubuntu3.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libnspr4_2%3a1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libnss3_2%3a1.firefox1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb  404 Not Found
Failed to fetch http://<ip>/./firefox_1.5.dfsg+1.5.0.7-ubuntu0.6.06_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libtag1c2a_1.4-4~dapper1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libtagc0_1.4-4~dapper1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libtheora0_0.0.0.alpha7-1ubuntu1~dapper1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libwmf0.2-7_0.2.8.3-3.1ubuntu0.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libxfont1_1%3a1.0.0-0ubuntu3.2_i386.deb  404 Not Found
Failed to fetch http://<ip>/./libxine-main1_1.1.1+ubuntu2-7.3_i386.deb  404 Not Found
Failed to fetch http://<ip>/./linux-386_2.6.15.25_i386.deb  404 Not Found
Failed to fetch http://<ip>/./linux-image-2.6.15-26-386_2.6.15-26.47_i386.deb  404 Not Found
Failed to fetch http://<ip>/./linux-restricted-modules-common_2.6.15.11-5_all.deb  404 Not Found
Failed to fetch http://<ip>/./linux-restricted-modules-2.6.15-26-386_2.6.15.11-4_i386.deb  404 Not Found
Failed to fetch http://<ip>/./mozilla-thunderbird_1.5.0.7-0ubuntu0.6.06_i386.deb  404 Not Found
Failed to fetch http://<ip>/./readahead_1%3a0.20050517.0220-0ubuntu5~dapper1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./xinit_1.0.1-0ubuntu3.1_i386.deb  404 Not Found
Failed to fetch http://<ip>/./xserver-xorg-core_1%3a1.0.2-0ubuntu10.4_i386.deb  404 Not Found
Failed to fetch http://<ip>/./ssh_1%3a4.2p1-7ubuntu3.1_all.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
admin@remotepc:~$

```

What's wrong on this?

Hi, 

I have the same issue :(  could you find any solution ? apt can fetch some packages and some can't be fetched... I have to download and paste them in my /var/cache/apt/archives

Hope some one can help...

Thanks

---

### Post by az on 2006-12-31
Apt-move will manage a local repo.  Just remove all the remote sources in the networked machines' sources.list and keep the one local source.  Push stuff into that repo and make the client machines update regularly.

Any package you push into the local repo will get installed onto all the other machines.  That's how large deployments of Ubuntu/Debian are managed.



emma@ubuntu:~$ apt-cache show apt-move
Package: apt-move
Priority: optional
Section: universe/admin
Installed-Size: 212
Maintainer: Chuan-kai Lin <cklin@debian.org>
Architecture: i386
Version: 4.2.24-1.1ubuntu1
Depends: bc, dash, libapt-pkg-libc6.3-6-3.11, libc6 (>= 2.3.4-1), libgcc1 (>= 1:4.0.2), libstdc++6 (>= 4.0.2-4)
Recommends: apt
Filename: pool/universe/a/apt-move/apt-move_4.2.24-1.1ubuntu1_i386.deb
Size: 49302
MD5sum: dbea676e10e254dfaa6cec2378c8433b
Description: Maintain Debian packages in a package pool
 apt-move is used to move a collection of Debian package files into a proper
 archive hierarchy as is used in the official Debian archive. It is intended as
 a tool to help manage the apt-get(8) file cache, but could be configured to
 work with any collection of Debian packages.
 .
 Running apt-move periodically will assist in managing the resulting partial
 mirror by optionally removing obsolete packages, and creating valid local
 Packages.gz files.  It can also build a partial or complete local mirror of a
 Debian binary distribution (including an ``installed-packages only'' mirror).
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by tagra123 on 2006-12-31
> **getglenn said:**
> i too have been looking for a solution to this problem with sharing downloaded .deb files... for MORE then 12 months!!!

i just cant believe that there isnt an elegant solution by now...

i have tried most of the suggestions in these forums with no success!!!

why is it so hard???

and for those people who suggest "just look in the forum, there is plenty of information",.. yes there is but most of it just DOES NOT WORK... otherwise we wouldnt have to continually post our help requests!

Google has tons of info.

This is the how to I used to set up apt-proxy.  

[http://www.subvs.co.uk/apt-proxy_on_ubuntu](http://www.subvs.co.uk/apt-proxy_on_ubuntu)

Also using reconstructor you can create your own custom install cd/dvd.

[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

And there's always AptOnCd  

This is really a very nice utility. It creates a cd which can then be added to the repositories (sources.list) and you do not need to have an internet connection because the files are on cd.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Apt on Cd is by far the easiest of these is you dont want a server set up for apt-proxy. I placed apt-proxy on my mythtv box to make the mythtv box have a purpose other than just a tv recorder. I also use the mythtv box as a server. . Just follow the instrucions and it will work.

---

### Post by xtknight on 2006-12-31
> **TheWizzard said:**
> what's the hard part in "sudo dpkg -i *.deb" ???

It'll be a mess with all the dependencies.  You'd have to use --force-all to do them all with one command.

---

### Post by TheWizzard on 2007-01-04
> **xtknight said:**
> It'll be a mess with all the dependencies.  You'd have to use --force-all to do them all with one command.

??? if your set of .deb files is complete, there won't be a dependcy mess. 
using --force-all seems ridiculous to me. this is the ideal way to break your system.

---

