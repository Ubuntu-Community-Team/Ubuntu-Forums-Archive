---
title: "recovery onto new pc"
date: 2016-08-28
forum: Installation &amp; Upgrades
---

### Post by Richard_Burton on 2016-08-28
I fresh installed 14.04 on a new pc then copied home from HDD rescued from old PC.  Movies no longer play with following:

```
The following packages have unmet dependencies:

gstreamer0.10-plugins-bad: Depends: libc6 (>= 2.15) but 2.19-0ubuntu6.9 is to be installed
                           Depends: libcairo2 (>= 1.2.4) but 1.13.0~20140204-0ubuntu1.1 is to be installed
                           Depends: libcdaudio1 (>= 0.99.12p2) but 0.99.12p2-13 is to be installed
                           Depends: libcurl3-gnutls (>= 7.16.2) but 7.35.0-1ubuntu2.8 is to be installed
                           Depends: libdvdnav4 (>= 4.1.3) but 4.2.1-3 is to be installed
                           Depends: libdvdread4 (>= 4.1.3) but 4.2.1-2ubuntu1 is to be installed
                           Depends: libfaad2 (>= 2.7) but 2.7-8 is to be installed
                           Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.3-0ubuntu4 is to be installed
                           Depends: libglib2.0-0 (>= 2.37.3) but 2.40.2-0ubuntu1 is to be installed
                           Depends: libgsm1 (>= 1.0.13) but 1.0.13-4 is to be installed
                           Depends: libgstreamer-plugins-bad0.10-0 (= 0.10.23-7.2ubuntu1.1) but 0.10.23-7.2ubuntu1.1 is to be installed
                           Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.36) but 0.10.36-1.1ubuntu2 is to be installed
                           Depends: libgstreamer0.10-0 (>= 0.10.36) but 0.10.36-1.2ubuntu3 is to be installed
                           Depends: libmpcdec6 (>= 1:0.1~r435) but 2:0.1~r459-1ubuntu3 is to be installed
                           Depends: libopenal1 (>= 1:1.13) but 1:1.14-4ubuntu1 is to be installed
                           Depends: libopus0 (>= 1.0.3) but 1.1-0ubuntu1 is to be installed
                           Depends: liborc-0.4-0 (>= 1:0.4.18) but 1:0.4.18-1ubuntu1 is to be installed
                           Depends: libpng12-0 (>= 1.2.13-4) but 1.2.50-1ubuntu2.14.04.2 is to be installed
                           Depends: librsvg2-2 (>= 2.14.4) but 2.40.2-1 is to be installed
                           Depends: librtmp0 (>= 2.3) but 2.4+20121230.gitdf6c518-1 is to be installed
                           Depends: libschroedinger-1.0-0 (>= 1.0.9) but 1.0.11-2ubuntu1 is to be installed
                           Depends: libsndfile1 (>= 1.0.20) but 1.0.25-7ubuntu2.1 is to be installed
                           Depends: libsoundtouch0 (>= 1.7.1-3~) but 1.7.1-5 is to be installed
                           Depends: libssl1.0.0 (>= 1.0.0) but 1.0.1f-1ubuntu2.19 is to be installed
                           Depends: libstdc++6 (>= 4.1.1) but 4.8.4-2ubuntu1~14.04.3 is to be installed
                           Depends: libvpx1 (>= 1.0.0) but 1.3.0-2 is to be installed
                           Depends: libxvidcore4 (>= 1.2.2) but 2:1.3.2-9ubuntu1 is to be installed
```
How to recover?

---

### Post by Bucky Ball on 2016-08-28
Welcome. I have added code tags to your post. Please see the green link in my signature at the bottom of my post for how to use them. 

You fresh installed 14.04 Ubuntu or a flavour of it (Lubuntu or Xubuntu for instance)? Have you installed ubuntu-restriced-extras and have Canonical Partners repositories enabled? 

Firstly, I would try doing this:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Reboot and try again before doing anything else. Let us know.

Just a slightly off-topic note which might be informative: If you have copied the whole contents of a /home partition or directory you are going to have the settings for the username and machine in the data. You probably don't want that. Perhaps better to just copy the data you want from the relevant folders in the old /home and plop them in the relevant /home folder/partition on the new install. A have a few installs. They all link to one universal /data partition from their /home directories on the install partition so they all access the same data, no confusion.

---

### Post by Richard_Burton on 2016-08-28
I'm just a little fearful about doing the upgrade to 16.04 as I have had quite a few problems with that release on an HP Pavillion dv6000 Laptop. I will consider doing the dist-upgrade
after I have made a back-up of the system. Unfortunately the HDD of my old PC has now packed up so I cannot access the original PC's system in any way.

---

### Post by Richard_Burton on 2016-08-28
There is probably only one application with history I wish to preserve and that is thunderbird e-mail. I would not like to lose it. With mysql I find that mysqldump to produce an sql output is fine for re-creating a mysql database even though it does not store data in my home folder.

---

### Post by Bucky Ball on 2016-08-28
The dist-upgrade command has nothing to do with upgrading to 16.04. It has to do with upgrading your currently installed release. No need to be fearful. See 'man apt' in a terminal for a description of what that command does.

---

### Post by Richard_Burton on 2016-08-28
I tried the commands suggested and results are just the same. On firing up the movie, I get message - 'looking  for ...plugins...'  and it goes off searching and recommending install gstreamer etc. Opting to install, it ends uo with unresolved dependencies as above.  
I realise, copying home folder included stuff which might cause problems so I might just go for the 16 upgrade and hope that this will clean up the system.  What do you think?

---

### Post by Bucky Ball on 2016-08-28
Is the system itself actually working fine, just these files that are playing up? If the system is unstable, upgrading it via the net to 16.04 won't change that and could make things worse.

If the system is stable, prior to upgrading do a full update and upgrade (this does not upgrade you to 16.04)

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Disable any PPAs you've installed manually (and any third-party graphics drivers to be safe).

For clarity, you have moved your /home partition to another partition? Or something else? Into the /home _*directory*_ inside the / partition, perhaps? What was moved from where to where, please?

---

### Post by Richard_Burton on 2016-08-29
I have now detected more extensive conflicts.  No movie player apps will install and removal of totem would not re-install, opera download froze during install with deb package installer.  deb package installer, nor ubuntu software centre can get through the thicket of conflicts.  Must be related to copying home folder from hp Pavillion to ASUS . Typical msg from installer:
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
Guess I'd better do a fresh install and copy my data over piecemeal.

---

### Post by Richard_Burton on 2016-08-29
Just one point in all this, everything seems to work from my old system except movie playing - i.e. email, mysql, firefox and internet real time updates- eg stock market quotes in real time etc. And of course documents.

---

