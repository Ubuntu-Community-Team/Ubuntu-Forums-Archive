---
title: "Software Sources in a big mess, can't update or upgrade, please help"
date: 2016-02-14
forum: Installation &amp; Upgrades
---

### Post by matthewpettyuk on 2016-02-14
My software sources are in a big mess. When I apt-get update, I get a bunch of error messages. When I try to upgrade, it says there are outstanding dependencies, and it won;t let me upgrade.

Can anyone point to a step-by-step method for cleaning up my sources, including any PPAs I may have added?

---

### Post by mörgæs on 2016-02-14
[https://repogen.simplylinux.ch/index.php](https://repogen.simplylinux.ch/index.php)

---

### Post by oldos2er on 2016-02-14
Please post output of both commands ```
cat /etc/apt/sources.list

ll /etc/apt/sources.list.d/
```

---

### Post by grahammechanical on 2016-02-14
PPAs are often a source of error messages. It does not necessarily mean that your software sources are a big mess. Go to System Settings>Software & Updates and disable those PPAs and that should remove some of the error messages.

There may be other messages related to dependency issues. We do not know that without seeing those error messages. You do not tell us what version of Ubuntu you are running. If we are using an end of life version then will we also be unable to update and get error messages.

When you say it won't let you upgrade, do you refer to the update/upgrade process or to upgrading to a newer version of Ubuntu? Before upgrading to a newer version we need to update/upgrade the existing version.

Regards.

---

### Post by matthewpettyuk on 2016-02-16
I tried to get it back to a clean slate, but I'm not really sure how it all hangs together.

```
matthew@matthew-Lemur-Ultra:/usr/bin$ cat /etc/apt/sources.list
#------------------------------------------------------------------------------#
#                            OFFICIAL UBUNTU REPOS                             #
#------------------------------------------------------------------------------#


###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ vivid main restricted universe multiverse

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ vivid-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ vivid-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ vivid-proposed main restricted universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu vivid partner

#------------------------------------------------------------------------------#
#                           UNOFFICIAL UBUNTU REPOS                            #
#------------------------------------------------------------------------------#


###### 3rd Party Binary Repos

#### Dropbox PPA - http://dropbox.com
## Run this command: sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
deb http://linux.dropbox.com/ubuntu/ vivid main

#### GetDeb - http://www.getdeb.net
## Run this command: wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
deb http://archive.getdeb.net/ubuntu vivid-getdeb apps

#### Gimp PPA - https://launchpad.net/~otto-kesselgulasch/+archive/gimp
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu vivid main

#### GNOME3 Extra Apps PPA - https://launchpad.net/~gnome3-team/+archive/gnome3
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu vivid main

#### Google Chrome Browser - http://www.google.com/linuxrepositories/
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/chrome/deb/ stable main

#### Highly Explosive PPA - https://launchpad.net/~dhor/+archive/myway
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93330B78
deb http://ppa.launchpad.net/dhor/myway/ubuntu vivid main

#### LibreOffice PPA - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu vivid main

#### Mozilla Daily Build Team PPA - http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu vivid main

#### muCommander - http://www.mucommander.com/
## Run this command: sudo wget -O - http://apt.mucommander.com/apt.key | sudo apt-key add - 
deb http://apt.mucommander.com stable main non-free contrib

#### Oracle Java (JDK) Installer PPA - http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
deb http://ppa.launchpad.net/webupd8team/java/ubuntu vivid main

#### Steam for Linux - http://store.steampowered.com/about/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F24AEA9FB05498B7
deb [arch=i386] http://repo.steampowered.com/steam/ precise steam



```

```
matthew@matthew-Lemur-Ultra:/usr/bin$ ll /etc/apt/sources.list.d/
total 456
drwxr-xr-x 2 root root 12288 Feb 16 07:35 ./
drwxr-xr-x 6 root root  4096 Feb  9 22:25 ../
-rw-r--r-- 1 root root    62 Feb 16 07:35 appgrid-stable-vivid.list
-rw-r--r-- 1 root root    62 Feb  8 12:22 appgrid-stable-vivid.list.distUpgrade
-rw-r--r-- 1 root root    62 Feb  9 23:12 appgrid-stable-vivid.list.save
-rw-r--r-- 1 root root   256 Feb  9 23:12 atareao-atareao-quantal.list
-rw-r--r-- 1 root root   256 Feb  8 12:22 atareao-atareao-quantal.list.distUpgrade
-rw-r--r-- 1 root root   256 Feb  9 23:12 atareao-atareao-quantal.list.save
-rw-r--r-- 1 root root   168 Feb  9 23:12 atareao-atareao-trusty.listmatthew@matthew-Lemur-Ultra:/usr/bin$ ll /etc/apt/sources.list.d/
total 456
drwxr-xr-x 2 root root 12288 Feb 16 07:35 ./
drwxr-xr-x 6 root root  4096 Feb  9 22:25 ../
-rw-r--r-- 1 root root    62 Feb 16 07:35 appgrid-stable-vivid.list
-rw-r--r-- 1 root root    62 Feb  8 12:22 appgrid-stable-vivid.list.distUpgrade
-rw-r--r-- 1 root root    62 Feb  9 23:12 appgrid-stable-vivid.list.save
-rw-r--r-- 1 root root   256 Feb  9 23:12 atareao-atareao-quantal.list
-rw-r--r-- 1 root root   256 Feb  8 12:22 atareao-atareao-quantal.list.distUpgrade
-rw-r--r-- 1 root root   256 Feb  9 23:12 atareao-atareao-quantal.list.save
-rw-r--r-- 1 root root   168 Feb  9 23:12 atareao-atareao-trusty.list
-rw-r--r-- 1 root root   168 Feb  8 12:22 atareao-atareao-trusty.list.distUpgrade
-rw-r--r-- 1 root root   168 Feb  9 23:12 atareao-atareao-trusty.list.save
-rw-r--r-- 1 root root   125 Feb  9 23:12 chms-ubuntu-jdotxt-vivid.list
-rw-r--r-- 1 root root   125 Feb  8 12:22 chms-ubuntu-jdotxt-vivid.list.distUpgrade
-rw-r--r-- 1 root root   125 Feb  9 23:12 chms-ubuntu-jdotxt-vivid.list.save
-rw-r--r-- 1 root root   254 Feb  9 23:12 diesch-testing-quantal.list
-rw-r--r-- 1 root root   254 Feb  9 23:12 diesch-testing-quantal.list.save
-rw-r--r-- 1 root root   138 Feb  9 23:12 diodon-team-ubuntu-stable-vivid.list
-rw-r--r-- 1 root root   138 Feb  9 23:12 diodon-team-ubuntu-stable-vivid.list.save
-rw-r--r-- 1 root root   148 Feb  9 23:12 doctormo-genetic-wall-trusty.list
-rw-r--r-- 1 root root   148 Feb  9 23:12 doctormo-genetic-wall-trusty.list.save
-rw-r--r-- 1 root root    65 Feb 11 07:40 dropbox.list
-rw-r--r-- 1 root root    80 Feb  8 12:22 dropbox.list.distUpgrade
-rw-r--r-- 1 root root    80 Feb  9 23:12 dropbox.list.save
-rw-r--r-- 1 root root   192 Feb  9 23:12 fantasyleague0629-wildguppy-trusty.list
-rw-r--r-- 1 root root   192 Feb  9 23:12 fantasyleague0629-wildguppy-trusty.list.save
-rw-r--r-- 1 root root   150 Feb  9 23:12 fossfreedom-ubuntu-packagefixes-vivid.list
-rw-r--r-- 1 root root   150 Feb  9 23:12 fossfreedom-ubuntu-packagefixes-vivid.list.save
-rw-r--r-- 1 root root    90 Feb  9 23:12 getdeb.list
-rw-r--r-- 1 root root    90 Feb  8 12:22 getdeb.list.distUpgrade
-rw-r--r-- 1 root root    90 Feb  9 23:12 getdeb.list.save
-rw-r--r-- 1 root root   280 Feb  9 23:12 gloobus-dev-gloobus-preview-quantal.list
-rw-r--r-- 1 root root   280 Feb  8 12:22 gloobus-dev-gloobus-preview-quantal.list.distUpgrade
-rw-r--r-- 1 root root   280 Feb  9 23:12 gloobus-dev-gloobus-preview-quantal.list.save
-rw-r--r-- 1 root root   180 Feb  9 23:12 google-talkplugin.list
-rw-r--r-- 1 root root   180 Feb  8 12:22 google-talkplugin.list.distUpgrade
-rw-r--r-- 1 root root   180 Feb  9 23:12 google-talkplugin.list.save
-rw-r--r-- 1 root root   176 Feb  9 23:12 ian-berke-ppa-drawers-raring.list
-rw-r--r-- 1 root root   176 Feb  9 23:12 ian-berke-ppa-drawers-raring.list.save
-rw-r--r-- 1 root root   180 Feb  9 23:12 ian-berke-ppa-drawers-trusty.list
-rw-r--r-- 1 root root   180 Feb  9 23:12 ian-berke-ppa-drawers-trusty.list.save
-rw-r--r-- 1 root root    85 Feb  9 23:12 intellinuxgraphics.list
-rw-r--r-- 1 root root    85 Feb  8 12:22 intellinuxgraphics.list.distUpgrade
-rw-r--r-- 1 root root    85 Feb  9 23:12 intellinuxgraphics.list.save
-rw-r--r-- 1 root root   160 Feb  9 23:12 kilian-f_lux-raring.list
-rw-r--r-- 1 root root   160 Feb  8 12:22 kilian-f_lux-raring.list.distUpgrade
-rw-r--r-- 1 root root   160 Feb  9 23:12 kilian-f_lux-raring.list.save
-rw-r--r-- 1 root root   164 Feb  9 23:12 linrunner-tlp-trusty.list
-rw-r--r-- 1 root root   164 Feb  9 23:12 linrunner-tlp-trusty.list.save
-rw-r--r-- 1 root root   124 Feb  9 23:12 moka-ubuntu-stable-vivid.list
-rw-r--r-- 1 root root   178 Feb  9 23:12 nilarimogard-webupd8-trusty.list
-rw-r--r-- 1 root root   178 Feb  8 12:22 nilarimogard-webupd8-trusty.list.distUpgrade
-rw-r--r-- 1 root root   178 Feb  9 23:12 nilarimogard-webupd8-trusty.list.save
-rw-r--r-- 1 root root   166 Feb  9 23:12 nodesource.list
-rw-r--r-- 1 root root   166 Feb  9 23:12 nodesource.list.save
-rw-r--r-- 1 root root   223 Feb  9 23:12 noobslab-icons-trusty.list
-rw-r--r-- 1 root root   223 Feb  8 12:22 noobslab-icons-trusty.list.distUpgrade
-rw-r--r-- 1 root root   223 Feb  9 23:12 noobslab-icons-trusty.list.save
-rw-r--r-- 1 root root   168 Feb  9 23:12 noobslab-themes-trusty.list
-rw-r--r-- 1 root root   168 Feb  8 12:22 noobslab-themes-trusty.list.distUpgrade
-rw-r--r-- 1 root root   168 Feb  9 23:12 noobslab-themes-trusty.list.save
-rw-r--r-- 1 root root   156 Feb  9 23:12 numix-ppa-trusty.list
-rw-r--r-- 1 root root   156 Feb  8 12:22 numix-ppa-trusty.list.distUpgrade
-rw-r--r-- 1 root root   156 Feb  9 23:12 numix-ppa-trusty.list.save
-rw-r--r-- 1 root root   268 Feb  9 23:12 osmoma-audio-recorder-quantal.list
-rw-r--r-- 1 root root   268 Feb  8 12:22 osmoma-audio-recorder-quantal.list.distUpgrade
-rw-r--r-- 1 root root   268 Feb  9 23:12 osmoma-audio-recorder-quantal.list.save
-rw-r--r-- 1 root root   162 Feb  9 23:12 peterlevi-ppa-trusty.list
-rw-r--r-- 1 root root   162 Feb  8 12:22 peterlevi-ppa-trusty.list.distUpgrade
-rw-r--r-- 1 root root   162 Feb  9 23:12 peterlevi-ppa-trusty.list.save
-rw-r--r-- 1 root root   170 Feb  9 23:12 pipelight-stable-trusty.list
-rw-r--r-- 1 root root   170 Feb  9 23:12 pipelight-stable-trusty.list.save
-rw-r--r-- 1 root root    78 Feb  9 23:12 playonlinux.list
-rw-r--r-- 1 root root    78 Feb  8 12:22 playonlinux.list.distUpgrade
-rw-r--r-- 1 root root    78 Feb  9 23:12 playonlinux.list.save
-rw-r--r-- 1 root root   102 Jun  5  2015 plexmediaserver.list.distUpgrade
-rw-r--r-- 1 root root   133 Dec 16 22:04 plexmediaserver.list.save
-rw-r--r-- 1 root root   248 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_capsized_ubuntu.list
-rw-r--r-- 1 root root   248 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_capsized_ubuntu.list.save
-rw-r--r-- 1 root root   221 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_dearesther_ubuntu.list
-rw-r--r-- 1 root root   221 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_dearesther_ubuntu.list.save
-rw-r--r-- 1 root root   224 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_hotline-miami_ubuntu.list
-rw-r--r-- 1 root root   224 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_hotline-miami_ubuntu.list.save
-rw-r--r-- 1 root root   254 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_little-inferno_ubuntu.list
-rw-r--r-- 1 root root   254 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_little-inferno_ubuntu.list.save
-rw-r--r-- 1 root root   216 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_proteus_ubuntu.list
-rw-r--r-- 1 root root   216 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_proteus_ubuntu.list.save
-rw-r--r-- 1 root root   206 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_spacepiratesandzombies_ubuntu.list
-rw-r--r-- 1 root root   206 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_spacepiratesandzombies_ubuntu.list.save
-rw-r--r-- 1 root root    75 Feb  9 23:12 qtodotxt.list
-rw-r--r-- 1 root root    75 Feb  8 12:22 qtodotxt.list.distUpgrade
-rw-r--r-- 1 root root    75 Feb  9 23:12 qtodotxt.list.save
-rw-r--r-- 1 root root   206 Feb  9 23:12 system76.list
-rw-r--r-- 1 root root   206 Feb  8 12:22 system76.list.distUpgrade
-rw-r--r-- 1 root root   206 Feb  9 23:12 system76.list.save
-rw-r--r-- 1 root root   210 Feb  9 23:12 thefanclub-grive-tools-trusty.list
-rw-r--r-- 1 root root   210 Feb  9 23:12 thefanclub-grive-tools-trusty.list.save
-rw-r--r-- 1 root root   136 Feb  9 23:12 thejambi-ubuntu-thejambi-vivid.list
-rw-r--r-- 1 root root   136 Feb  9 23:12 thejambi-ubuntu-thejambi-vivid.list.save
-rw-r--r-- 1 root root   218 Feb  9 23:12 tsbarnes-indicator-keylock-raring.list
-rw-r--r-- 1 root root   218 Feb  8 12:22 tsbarnes-indicator-keylock-raring.list.distUpgrade
-rw-r--r-- 1 root root   218 Feb  9 23:12 tsbarnes-indicator-keylock-raring.list.save
-rw-r--r-- 1 root root   150 Feb  9 23:12 ubuntuhandbook1-ubuntu-audacity-vivid.list
-rw-r--r-- 1 root root   150 Feb  8 12:22 ubuntuhandbook1-ubuntu-audacity-vivid.list.distUpgrade
-rw-r--r-- 1 root root   150 Feb  9 23:12 ubuntuhandbook1-ubuntu-audacity-vivid.list.save
-rw-r--r-- 1 root root   180 Feb  9 23:12 vegastrike-data.list
-rw-r--r-- 1 root root   180 Feb  9 23:12 vegastrike-data.list.save
-rw-r--r-- 1 root root   258 Feb  9 23:12 webupd8team-java-quantal.list
-rw-r--r-- 1 root root   258 Feb  8 12:22 webupd8team-java-quantal.list.distUpgrade
-rw-r--r-- 1 root root   258 Feb  9 23:12 webupd8team-java-quantal.list.save
-rw-r--r-- 1 root root   152 Feb  9 23:12 yorba-ppa-raring.list
-rw-r--r-- 1 root root   152 Feb  8 12:22 yorba-ppa-raring.list.distUpgrade
-rw-r--r-- 1 root root   152 Feb  9 23:12 yorba-ppa-raring.list.save

-rw-r--r-- 1 root root   168 Feb  8 12:22 atareao-atareao-trusty.list.distUpgrade
-rw-r--r-- 1 root root   168 Feb  9 23:12 atareao-atareao-trusty.list.save
-rw-r--r-- 1 root root   125 Feb  9 23:12 chms-ubuntu-jdotxt-vivid.list
-rw-r--r-- 1 root root   125 Feb  8 12:22 chms-ubuntu-jdotxt-vivid.list.distUpgrade
-rw-r--r-- 1 root root   125 Feb  9 23:12 chms-ubuntu-jdotxt-vivid.list.save
-rw-r--r-- 1 root root   254 Feb  9 23:12 diesch-testing-quantal.list
-rw-r--r-- 1 root root   254 Feb  9 23:12 diesch-testing-quantal.list.save
-rw-r--r-- 1 root root   138 Feb  9 23:12 diodon-team-ubuntu-stable-vivid.list
-rw-r--r-- 1 root root   138 Feb  9 23:12 diodon-team-ubuntu-stable-vivid.list.save
-rw-r--r-- 1 root root   148 Feb  9 23:12 doctormo-genetic-wall-trusty.list
-rw-r--r-- 1 root root   148 Feb  9 23:12 doctormo-genetic-wall-trusty.list.save
-rw-r--r-- 1 root root    65 Feb 11 07:40 dropbox.list
-rw-r--r-- 1 root root    80 Feb  8 12:22 dropbox.list.distUpgrade
-rw-r--r-- 1 root root    80 Feb  9 23:12 dropbox.list.save
-rw-r--r-- 1 root root   192 Feb  9 23:12 fantasyleague0629-wildguppy-trusty.list
-rw-r--r-- 1 root root   192 Feb  9 23:12 fantasyleague0629-wildguppy-trusty.list.save
-rw-r--r-- 1 root root   150 Feb  9 23:12 fossfreedom-ubuntu-packagefixes-vivid.list
-rw-r--r-- 1 root root   150 Feb  9 23:12 fossfreedom-ubuntu-packagefixes-vivid.list.save
-rw-r--r-- 1 root root    90 Feb  9 23:12 getdeb.list
-rw-r--r-- 1 root root    90 Feb  8 12:22 getdeb.list.distUpgrade
-rw-r--r-- 1 root root    90 Feb  9 23:12 getdeb.list.save
-rw-r--r-- 1 root root   280 Feb  9 23:12 gloobus-dev-gloobus-preview-quantal.list
-rw-r--r-- 1 root root   280 Feb  8 12:22 gloobus-dev-gloobus-preview-quantal.list.distUpgrade
-rw-r--r-- 1 root root   280 Feb  9 23:12 gloobus-dev-gloobus-preview-quantal.list.save
-rw-r--r-- 1 root root   180 Feb  9 23:12 google-talkplugin.list
-rw-r--r-- 1 root root   180 Feb  8 12:22 google-talkplugin.list.distUpgrade
-rw-r--r-- 1 root root   180 Feb  9 23:12 google-talkplugin.list.save
-rw-r--r-- 1 root root   176 Feb  9 23:12 ian-berke-ppa-drawers-raring.list
-rw-r--r-- 1 root root   176 Feb  9 23:12 ian-berke-ppa-drawers-raring.list.save
-rw-r--r-- 1 root root   180 Feb  9 23:12 ian-berke-ppa-drawers-trusty.list
-rw-r--r-- 1 root root   180 Feb  9 23:12 ian-berke-ppa-drawers-trusty.list.save
-rw-r--r-- 1 root root    85 Feb  9 23:12 intellinuxgraphics.list
-rw-r--r-- 1 root root    85 Feb  8 12:22 intellinuxgraphics.list.distUpgrade
-rw-r--r-- 1 root root    85 Feb  9 23:12 intellinuxgraphics.list.save
-rw-r--r-- 1 root root   160 Feb  9 23:12 kilian-f_lux-raring.list
-rw-r--r-- 1 root root   160 Feb  8 12:22 kilian-f_lux-raring.list.distUpgrade
-rw-r--r-- 1 root root   160 Feb  9 23:12 kilian-f_lux-raring.list.save
-rw-r--r-- 1 root root   164 Feb  9 23:12 linrunner-tlp-trusty.list
-rw-r--r-- 1 root root   164 Feb  9 23:12 linrunner-tlp-trusty.list.save
-rw-r--r-- 1 root root   124 Feb  9 23:12 moka-ubuntu-stable-vivid.listmatthew@matthew-Lemur-Ultra:/usr/bin$ ll /etc/apt/sources.list.d/
total 456
drwxr-xr-x 2 root root 12288 Feb 16 07:35 ./
drwxr-xr-x 6 root root  4096 Feb  9 22:25 ../
-rw-r--r-- 1 root root    62 Feb 16 07:35 appgrid-stable-vivid.list
-rw-r--r-- 1 root root    62 Feb  8 12:22 appgrid-stable-vivid.list.distUpgrade
-rw-r--r-- 1 root root    62 Feb  9 23:12 appgrid-stable-vivid.list.save
-rw-r--r-- 1 root root   256 Feb  9 23:12 atareao-atareao-quantal.list
-rw-r--r-- 1 root root   256 Feb  8 12:22 atareao-atareao-quantal.list.distUpgrade
-rw-r--r-- 1 root root   256 Feb  9 23:12 atareao-atareao-quantal.list.save
-rw-r--r-- 1 root root   168 Feb  9 23:12 atareao-atareao-trusty.list
-rw-r--r-- 1 root root   168 Feb  8 12:22 atareao-atareao-trusty.list.distUpgrade
-rw-r--r-- 1 root root   168 Feb  9 23:12 atareao-atareao-trusty.list.save
-rw-r--r-- 1 root root   125 Feb  9 23:12 chms-ubuntu-jdotxt-vivid.list
-rw-r--r-- 1 root root   125 Feb  8 12:22 chms-ubuntu-jdotxt-vivid.list.distUpgrade
-rw-r--r-- 1 root root   125 Feb  9 23:12 chms-ubuntu-jdotxt-vivid.list.save
-rw-r--r-- 1 root root   254 Feb  9 23:12 diesch-testing-quantal.list
-rw-r--r-- 1 root root   254 Feb  9 23:12 diesch-testing-quantal.list.save
-rw-r--r-- 1 root root   138 Feb  9 23:12 diodon-team-ubuntu-stable-vivid.list
-rw-r--r-- 1 root root   138 Feb  9 23:12 diodon-team-ubuntu-stable-vivid.list.save
-rw-r--r-- 1 root root   148 Feb  9 23:12 doctormo-genetic-wall-trusty.list
-rw-r--r-- 1 root root   148 Feb  9 23:12 doctormo-genetic-wall-trusty.list.save
-rw-r--r-- 1 root root    65 Feb 11 07:40 dropbox.list
-rw-r--r-- 1 root root    80 Feb  8 12:22 dropbox.list.distUpgrade
-rw-r--r-- 1 root root    80 Feb  9 23:12 dropbox.list.save
-rw-r--r-- 1 root root   192 Feb  9 23:12 fantasyleague0629-wildguppy-trusty.list
-rw-r--r-- 1 root root   192 Feb  9 23:12 fantasyleague0629-wildguppy-trusty.list.save
-rw-r--r-- 1 root root   150 Feb  9 23:12 fossfreedom-ubuntu-packagefixes-vivid.list
-rw-r--r-- 1 root root   150 Feb  9 23:12 fossfreedom-ubuntu-packagefixes-vivid.list.save
-rw-r--r-- 1 root root    90 Feb  9 23:12 getdeb.list
-rw-r--r-- 1 root root    90 Feb  8 12:22 getdeb.list.distUpgrade
-rw-r--r-- 1 root root    90 Feb  9 23:12 getdeb.list.save
-rw-r--r-- 1 root root   280 Feb  9 23:12 gloobus-dev-gloobus-preview-quantal.list
-rw-r--r-- 1 root root   280 Feb  8 12:22 gloobus-dev-gloobus-preview-quantal.list.distUpgrade
-rw-r--r-- 1 root root   280 Feb  9 23:12 gloobus-dev-gloobus-preview-quantal.list.save
-rw-r--r-- 1 root root   180 Feb  9 23:12 google-talkplugin.list
-rw-r--r-- 1 root root   180 Feb  8 12:22 google-talkplugin.list.distUpgrade
-rw-r--r-- 1 root root   180 Feb  9 23:12 google-talkplugin.list.save
-rw-r--r-- 1 root root   176 Feb  9 23:12 ian-berke-ppa-drawers-raring.list
-rw-r--r-- 1 root root   176 Feb  9 23:12 ian-berke-ppa-drawers-raring.list.save
-rw-r--r-- 1 root root   180 Feb  9 23:12 ian-berke-ppa-drawers-trusty.list
-rw-r--r-- 1 root root   180 Feb  9 23:12 ian-berke-ppa-drawers-trusty.list.save
-rw-r--r-- 1 root root    85 Feb  9 23:12 intellinuxgraphics.list
-rw-r--r-- 1 root root    85 Feb  8 12:22 intellinuxgraphics.list.distUpgrade
-rw-r--r-- 1 root root    85 Feb  9 23:12 intellinuxgraphics.list.save
-rw-r--r-- 1 root root   160 Feb  9 23:12 kilian-f_lux-raring.list
-rw-r--r-- 1 root root   160 Feb  8 12:22 kilian-f_lux-raring.list.distUpgrade
-rw-r--r-- 1 root root   160 Feb  9 23:12 kilian-f_lux-raring.list.save
-rw-r--r-- 1 root root   164 Feb  9 23:12 linrunner-tlp-trusty.list
-rw-r--r-- 1 root root   164 Feb  9 23:12 linrunner-tlp-trusty.list.save
-rw-r--r-- 1 root root   124 Feb  9 23:12 moka-ubuntu-stable-vivid.list
-rw-r--r-- 1 root root   178 Feb  9 23:12 nilarimogard-webupd8-trusty.list
-rw-r--r-- 1 root root   178 Feb  8 12:22 nilarimogard-webupd8-trusty.list.distUpgrade
-rw-r--r-- 1 root root   178 Feb  9 23:12 nilarimogard-webupd8-trusty.list.save
-rw-r--r-- 1 root root   166 Feb  9 23:12 nodesource.list
-rw-r--r-- 1 root root   166 Feb  9 23:12 nodesource.list.save
-rw-r--r-- 1 root root   223 Feb  9 23:12 noobslab-icons-trusty.list
-rw-r--r-- 1 root root   223 Feb  8 12:22 noobslab-icons-trusty.list.distUpgrade
-rw-r--r-- 1 root root   223 Feb  9 23:12 noobslab-icons-trusty.list.save
-rw-r--r-- 1 root root   168 Feb  9 23:12 noobslab-themes-trusty.list
-rw-r--r-- 1 root root   168 Feb  8 12:22 noobslab-themes-trusty.list.distUpgrade
-rw-r--r-- 1 root root   168 Feb  9 23:12 noobslab-themes-trusty.list.save
-rw-r--r-- 1 root root   156 Feb  9 23:12 numix-ppa-trusty.list
-rw-r--r-- 1 root root   156 Feb  8 12:22 numix-ppa-trusty.list.distUpgrade
-rw-r--r-- 1 root root   156 Feb  9 23:12 numix-ppa-trusty.list.save
-rw-r--r-- 1 root root   268 Feb  9 23:12 osmoma-audio-recorder-quantal.list
-rw-r--r-- 1 root root   268 Feb  8 12:22 osmoma-audio-recorder-quantal.list.distUpgrade
-rw-r--r-- 1 root root   268 Feb  9 23:12 osmoma-audio-recorder-quantal.list.save
-rw-r--r-- 1 root root   162 Feb  9 23:12 peterlevi-ppa-trusty.list
-rw-r--r-- 1 root root   162 Feb  8 12:22 peterlevi-ppa-trusty.list.distUpgrade
-rw-r--r-- 1 root root   162 Feb  9 23:12 peterlevi-ppa-trusty.list.save
-rw-r--r-- 1 root root   170 Feb  9 23:12 pipelight-stable-trusty.list
-rw-r--r-- 1 root root   170 Feb  9 23:12 pipelight-stable-trusty.list.save
-rw-r--r-- 1 root root    78 Feb  9 23:12 playonlinux.list
-rw-r--r-- 1 root root    78 Feb  8 12:22 playonlinux.list.distUpgrade
-rw-r--r-- 1 root root    78 Feb  9 23:12 playonlinux.list.save
-rw-r--r-- 1 root root   102 Jun  5  2015 plexmediaserver.list.distUpgrade
-rw-r--r-- 1 root root   133 Dec 16 22:04 plexmediaserver.list.save
-rw-r--r-- 1 root root   248 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_capsized_ubuntu.list
-rw-r--r-- 1 root root   248 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_capsized_ubuntu.list.save
-rw-r--r-- 1 root root   221 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_dearesther_ubuntu.list
-rw-r--r-- 1 root root   221 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_dearesther_ubuntu.list.save
-rw-r--r-- 1 root root   224 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_hotline-miami_ubuntu.list
-rw-r--r-- 1 root root   224 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_hotline-miami_ubuntu.list.save
-rw-r--r-- 1 root root   254 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_little-inferno_ubuntu.list
-rw-r--r-- 1 root root   254 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_little-inferno_ubuntu.list.save
-rw-r--r-- 1 root root   216 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_proteus_ubuntu.list
-rw-r--r-- 1 root root   216 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_proteus_ubuntu.list.save
-rw-r--r-- 1 root root   206 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_spacepiratesandzombies_ubuntu.list
-rw-r--r-- 1 root root   206 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_spacepiratesandzombies_ubuntu.list.save
-rw-r--r-- 1 root root    75 Feb  9 23:12 qtodotxt.list
-rw-r--r-- 1 root root    75 Feb  8 12:22 qtodotxt.list.distUpgrade
-rw-r--r-- 1 root root    75 Feb  9 23:12 qtodotxt.list.save
-rw-r--r-- 1 root root   206 Feb  9 23:12 system76.list
-rw-r--r-- 1 root root   206 Feb  8 12:22 system76.list.distUpgrade
-rw-r--r-- 1 root root   206 Feb  9 23:12 system76.list.save
-rw-r--r-- 1 root root   210 Feb  9 23:12 thefanclub-grive-tools-trusty.list
-rw-r--r-- 1 root root   210 Feb  9 23:12 thefanclub-grive-tools-trusty.list.save
-rw-r--r-- 1 root root   136 Feb  9 23:12 thejambi-ubuntu-thejambi-vivid.list
-rw-r--r-- 1 root root   136 Feb  9 23:12 thejambi-ubuntu-thejambi-vivid.list.save
-rw-r--r-- 1 root root   218 Feb  9 23:12 tsbarnes-indicator-keylock-raring.list
-rw-r--r-- 1 root root   218 Feb  8 12:22 tsbarnes-indicator-keylock-raring.list.distUpgrade
-rw-r--r-- 1 root root   218 Feb  9 23:12 tsbarnes-indicator-keylock-raring.list.save
-rw-r--r-- 1 root root   150 Feb  9 23:12 ubuntuhandbook1-ubuntu-audacity-vivid.list
-rw-r--r-- 1 root root   150 Feb  8 12:22 ubuntuhandbook1-ubuntu-audacity-vivid.list.distUpgrade
-rw-r--r-- 1 root root   150 Feb  9 23:12 ubuntuhandbook1-ubuntu-audacity-vivid.list.save
-rw-r--r-- 1 root root   180 Feb  9 23:12 vegastrike-data.list
-rw-r--r-- 1 root root   180 Feb  9 23:12 vegastrike-data.list.save
-rw-r--r-- 1 root root   258 Feb  9 23:12 webupd8team-java-quantal.list
-rw-r--r-- 1 root root   258 Feb  8 12:22 webupd8team-java-quantal.list.distUpgrade
-rw-r--r-- 1 root root   258 Feb  9 23:12 webupd8team-java-quantal.list.save
-rw-r--r-- 1 root root   152 Feb  9 23:12 yorba-ppa-raring.list
-rw-r--r-- 1 root root   152 Feb  8 12:22 yorba-ppa-raring.list.distUpgrade
-rw-r--r-- 1 root root   152 Feb  9 23:12 yorba-ppa-raring.list.save

-rw-r--r-- 1 root root   178 Feb  9 23:12 nilarimogard-webupd8-trusty.list
-rw-r--r-- 1 root root   178 Feb  8 12:22 nilarimogard-webupd8-trusty.list.distUpgrade
-rw-r--r-- 1 root root   178 Feb  9 23:12 nilarimogard-webupd8-trusty.list.save
-rw-r--r-- 1 root root   166 Feb  9 23:12 nodesource.list
-rw-r--r-- 1 root root   166 Feb  9 23:12 nodesource.list.save
-rw-r--r-- 1 root root   223 Feb  9 23:12 noobslab-icons-trusty.list
-rw-r--r-- 1 root root   223 Feb  8 12:22 noobslab-icons-trusty.list.distUpgrade
-rw-r--r-- 1 root root   223 Feb  9 23:12 noobslab-icons-trusty.list.save
-rw-r--r-- 1 root root   168 Feb  9 23:12 noobslab-themes-trusty.list
-rw-r--r-- 1 root root   168 Feb  8 12:22 noobslab-themes-trusty.list.distUpgrade
-rw-r--r-- 1 root root   168 Feb  9 23:12 noobslab-themes-trusty.list.save
-rw-r--r-- 1 root root   156 Feb  9 23:12 numix-ppa-trusty.list
-rw-r--r-- 1 root root   156 Feb  8 12:22 numix-ppa-trusty.list.distUpgrade
-rw-r--r-- 1 root root   156 Feb  9 23:12 numix-ppa-trusty.list.save
-rw-r--r-- 1 root root   268 Feb  9 23:12 osmoma-audio-recorder-quantal.list
-rw-r--r-- 1 root root   268 Feb  8 12:22 osmoma-audio-recorder-quantal.list.distUpgrade
-rw-r--r-- 1 root root   268 Feb  9 23:12 osmoma-audio-recorder-quantal.list.save
-rw-r--r-- 1 root root   162 Feb  9 23:12 peterlevi-ppa-trusty.list
-rw-r--r-- 1 root root   162 Feb  8 12:22 peterlevi-ppa-trusty.list.distUpgrade
-rw-r--r-- 1 root root   162 Feb  9 23:12 peterlevi-ppa-trusty.list.save
-rw-r--r-- 1 root root   170 Feb  9 23:12 pipelight-stable-trusty.list
-rw-r--r-- 1 root root   170 Feb  9 23:12 pipelight-stable-trusty.list.save
-rw-r--r-- 1 root root    78 Feb  9 23:12 playonlinux.list
-rw-r--r-- 1 root root    78 Feb  8 12:22 playonlinux.list.distUpgrade
-rw-r--r-- 1 root root    78 Feb  9 23:12 playonlinux.list.save
-rw-r--r-- 1 root root   102 Jun  5  2015 plexmediaserver.list.distUpgrade
-rw-r--r-- 1 root root   133 Dec 16 22:04 plexmediaserver.list.save
-rw-r--r-- 1 root root   248 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_capsized_ubuntu.list
-rw-r--r-- 1 root root   248 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_capsized_ubuntu.list.save
-rw-r--r-- 1 root root   221 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_dearesther_ubuntu.list
-rw-r--r-- 1 root root   221 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_dearesther_ubuntu.list.save
-rw-r--r-- 1 root root   224 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_hotline-miami_ubuntu.list
-rw-r--r-- 1 root root   224 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_hotline-miami_ubuntu.list.save
-rw-r--r-- 1 root root   254 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_little-inferno_ubuntu.list
-rw-r--r-- 1 root root   254 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_little-inferno_ubuntu.list.save
-rw-r--r-- 1 root root   216 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_proteus_ubuntu.list
-rw-r--r-- 1 root root   216 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_proteus_ubuntu.list.save
-rw-r--r-- 1 root root   206 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_spacepiratesandzombies_ubuntu.list
-rw-r--r-- 1 root root   206 Feb  9 23:12 private-ppa.launchpad.net_commercial-ppa-uploaders_spacepiratesandzombies_ubuntu.list.save
-rw-r--r-- 1 root root    75 Feb  9 23:12 qtodotxt.list
-rw-r--r-- 1 root root    75 Feb  8 12:22 qtodotxt.list.distUpgrade
-rw-r--r-- 1 root root    75 Feb  9 23:12 qtodotxt.list.save
-rw-r--r-- 1 root root   206 Feb  9 23:12 system76.list
-rw-r--r-- 1 root root   206 Feb  8 12:22 system76.list.distUpgrade
-rw-r--r-- 1 root root   206 Feb  9 23:12 system76.list.save
-rw-r--r-- 1 root root   210 Feb  9 23:12 thefanclub-grive-tools-trusty.list
-rw-r--r-- 1 root root   210 Feb  9 23:12 thefanclub-grive-tools-trusty.list.save
-rw-r--r-- 1 root root   136 Feb  9 23:12 thejambi-ubuntu-thejambi-vivid.list
-rw-r--r-- 1 root root   136 Feb  9 23:12 thejambi-ubuntu-thejambi-vivid.list.save
-rw-r--r-- 1 root root   218 Feb  9 23:12 tsbarnes-indicator-keylock-raring.list
-rw-r--r-- 1 root root   218 Feb  8 12:22 tsbarnes-indicator-keylock-raring.list.distUpgrade
-rw-r--r-- 1 root root   218 Feb  9 23:12 tsbarnes-indicator-keylock-raring.list.save
-rw-r--r-- 1 root root   150 Feb  9 23:12 ubuntuhandbook1-ubuntu-audacity-vivid.list
-rw-r--r-- 1 root root   150 Feb  8 12:22 ubuntuhandbook1-ubuntu-audacity-vivid.list.distUpgrade
-rw-r--r-- 1 root root   150 Feb  9 23:12 ubuntuhandbook1-ubuntu-audacity-vivid.list.save
-rw-r--r-- 1 root root   180 Feb  9 23:12 vegastrike-data.list
-rw-r--r-- 1 root root   180 Feb  9 23:12 vegastrike-data.list.save
-rw-r--r-- 1 root root   258 Feb  9 23:12 webupd8team-java-quantal.list
-rw-r--r-- 1 root root   258 Feb  8 12:22 webupd8team-java-quantal.list.distUpgrade
-rw-r--r-- 1 root root   258 Feb  9 23:12 webupd8team-java-quantal.list.save
-rw-r--r-- 1 root root   152 Feb  9 23:12 yorba-ppa-raring.list
-rw-r--r-- 1 root root   152 Feb  8 12:22 yorba-ppa-raring.list.distUpgrade
-rw-r--r-- 1 root root   152 Feb  9 23:12 yorba-ppa-raring.list.save


```

---

### Post by oldos2er on 2016-02-16
Vivid recently went end-of-life, which means it's no longer supported and its repositories have moved to old-releases (and will no longer be updated). You can either update to or perform a clean install of 15.10, if you wish.

---

