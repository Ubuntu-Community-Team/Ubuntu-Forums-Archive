---
title: "Upgrade ubuntu from already upgraded system on network"
date: 2016-04-20
forum: Installation &amp; Upgrades
---

### Post by isthakur on 2016-04-20
Dear all
I have been searching for method to automatically upgrade a ubuntu system from already upgraded system. I have a network of about 10 computer and there are frequent updates available. It is very time consuming and takes lot of bandwidth to upgrade all the system. I want to upgrade one computer(system) from internet and want to set all computers to upgrade their softwares from already upgraded system. The installations of packages would be almost similar in all the systems.

Thanking you in advance

Regards
Inder Singh Thakur

---

### Post by TheFu on 2016-04-20
apt-cacher-ng is one option.  Been using it here for about 5 yrs.

---

### Post by Tadaen_Sylvermane on 2016-04-20
Definitely apt-cacher-ng. I put it on my server and never looked back... only for server and 2 laptops. Saves lots of bandwidth

---

### Post by isthakur on 2016-05-04
Thank you Dear [ ]("http://ubuntuforums.org/member.php?u=1037685")[**[COLOR=#000000]TheFu[/COLOR]**]("http://ubuntuforums.org/member.php?u=1037685") and [**[COLOR=#000000]Tadaen_Sylvermane[/COLOR]**]("http://ubuntuforums.org/member.php?u=1914514"). I am in the process of setting up lab with apt-cacher-ng and successfully configured the server. Just interested to know if this solution work with ubuntu derivatives like Linuxmint also?

---

### Post by TheFu on 2016-05-05
Don't know anything about Mint, but debian works.  I suspect it will work with any debian derivative distro - basically, any distro that uses APT.

---

### Post by isthakur on 2016-05-27
I had successfully setup the apt-cacher and was working as expected until yesterday when I found that I was not able to install virtualbox and geany
[FONT=courier new][/FONT][SIZE=2][FONT=courier new]sudo apt-get install virtualbox geany
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python3-pexpect python3-pil python3-ptyprocess python3-renderpm
  python3-reportlab python3-reportlab-accel
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  dkms geany-common libgsoap8 libvncserver1 virtualbox-dkms virtualbox-qt
Suggested packages:
  libvte9 vde2 virtualbox-guest-additions-iso
The following NEW packages will be installed:
  dkms geany geany-common libgsoap8 libvncserver1 virtualbox virtualbox-dkms
  virtualbox-qt
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 25.1 MB of archives.
After this operation, 105 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 dkms all 2.2.0.3-2ubuntu9 [67.3 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 geany-common all 1.26+dfsg-1 [1,833 kB]
Ign:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe i386 geany-common all 1.26+dfsg-1
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 geany amd64 1.26+dfsg-1 [988 kB]
Err:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 geany amd64 1.26+dfsg-1
  Hash Sum mismatch
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 libgsoap8 amd64 2.8.28-1 [216 kB]
Err:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 libgsoap8 amd64 2.8.28-1
  Hash Sum mismatch
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libvncserver1 amd64 0.9.10+dfsg-3build1 [121 kB]
Err:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 libvncserver1 amd64 0.9.10+dfsg-3build1
  Hash Sum mismatch
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse amd64 virtualbox-dkms all 5.0.16-dfsg-2 [616 kB]
Ign:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse i386 virtualbox-dkms all 5.0.16-dfsg-2
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse amd64 virtualbox amd64 5.0.16-dfsg-2 [14.1 MB]
Err:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse amd64 virtualbox amd64 5.0.16-dfsg-2
  Hash Sum mismatch
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse amd64 virtualbox-qt amd64 5.0.16-dfsg-2 [7,170 kB]
Err:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse amd64 virtualbox-qt amd64 5.0.16-dfsg-2
  Hash Sum mismatch
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe i386 geany-common all 1.26+dfsg-1 [1,833 kB]
Err:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe i386 geany-common all 1.26+dfsg-1
  Hash Sum mismatch
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse i386 virtualbox-dkms all 5.0.16-dfsg-2 [616 kB]
Err:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse i386 virtualbox-dkms all 5.0.16-dfsg-2
  Hash Sum mismatch
Fetched 68.1 kB in 0s (93.7 kB/s)
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/geany/geany-common_1.26+dfsg-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/geany/geany-common_1.26+dfsg-1_all.deb)  Hash Sum mismatch

E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/geany/geany_1.26+dfsg-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/geany/geany_1.26+dfsg-1_amd64.deb)  Hash Sum mismatch

E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/gsoap/libgsoap8_2.8.28-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/gsoap/libgsoap8_2.8.28-1_amd64.deb)  Hash Sum mismatch

E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libv/libvncserver/libvncserver1_0.9.10+dfsg-3build1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libv/libvncserver/libvncserver1_0.9.10+dfsg-3build1_amd64.deb)  Hash Sum mismatch

E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/v/virtualbox/virtualbox-dkms_5.0.16-dfsg-2_all.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/v/virtualbox/virtualbox-dkms_5.0.16-dfsg-2_all.deb)  Hash Sum mismatch

E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/v/virtualbox/virtualbox_5.0.16-dfsg-2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/v/virtualbox/virtualbox_5.0.16-dfsg-2_amd64.deb)  Hash Sum mismatch

E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/v/virtualbox/virtualbox-qt_5.0.16-dfsg-2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/v/virtualbox/virtualbox-qt_5.0.16-dfsg-2_amd64.deb)  Hash Sum mismatch

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


one post on askubuntu suggested that it is due to proxy.
please guide.

Regards
[/FONT][/SIZE]

---

