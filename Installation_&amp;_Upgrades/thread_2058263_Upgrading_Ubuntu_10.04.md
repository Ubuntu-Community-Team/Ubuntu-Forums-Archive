---
title: "Upgrading Ubuntu 10.04"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by cyb0rgb0rg on 2012-09-15
This is my first post, so go easy on the newbies. :-D

Background (Skip for non-blabla content):
I love the classic gnome and refuse to give it up as it is imo the best desktop around. Furthermore is classic gnome and the new kde the only enviroments I can make my Alienware work with compiz. So i was running Ubuntu 10.x for a while. Then I decided to do the brilliant move of accepting the system update to 12.04. I ended up tweaking myself crazy making compiz and the graphics drivers work on the new kernel and unity. And not to mention that compared to the productivity level Gnome 2 offers, unity is imo not very successful. Bearing in mind I'm a Windows Server sysadmin and need exactly that mixture of system level accessibility and adaptability that Linux with Gnome offers. For other needs unity, kde and mate is probably perfect, but my love has fell on the classic gnome. Anyway it was a mess and I reinstalled Ubuntu 10.04 and did my usual upgrading of the kernel and tweaking compiz in place, firing up awn and good to go. Like last time. Problem is, I don't quite remember if I was running 10.04 or 10.10 or what, the last time I had it working. I have an identical working solution now, but it brings me over to the question at hand.

The question:
I upgraded the kernel on the Ubuntu 10.04 LTS to 2.6.38-15 because it kinda makes my ethernet card and hd graphics come alive. Problem is, and I didn't get this the last time I configured Ubuntu 10.x, that when I try to install stuff that has dependencies to i.e. kernel-matching libraries, it won't allow it. Because it is "to new". If you know what I mean. How would I go about installing these dependencies when it suggests a lower version number.

Specific problem:
Skype. (For this example, I executed **sudo apt-get install skype**) Throws this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: ia32-libs (>= 2.4) but it is not going to be installed
         Depends: lib32asound2 (> 1.0.22) but it is not going to be installed
         Depends: lib32gcc1 (>= 1:4.1.1) but it is not going to be installed
         Depends: lib32stdc++6 (>= 4.4.0) but it is not going to be installed
         Depends: libc6-i386 (>= 2.7) but it is not going to be installed
         Recommends: sni-qt but it is not installable
E: Broken packages

```

And executing **sudo apt-get install libc6-i386** throws this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-i386: Depends: libc6 (= 2.13-0ubuntu13) but 2.11.1-0ubuntu7.10 is to be installed
E: Broken packages

```

System is 64 bit.

Grateful for any 2 cents.

---

### Post by wojox on 2012-09-15
How about:
```
sudo apt-get install ia32-libs
```

---

### Post by oldfred on 2012-09-15
You can have classic gnome in 12.04. It is almost the same, a few things have been moved to different menus and adding some settings helps.

gnome3 classic
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 
12.04 LTS / Precise Classic (No effects) Tweaks and tricks
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)

---

### Post by cyb0rgb0rg on 2012-09-16
Thanks peeps.

Executing **sudo apt-get install ia32-libs** gives me this output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ia32-libs: Depends: lib32gcc1 but it is not going to be installed
             Depends: libc6-i386 (>= 2.3.6-2) but it is not going to be installed
             Depends: lib32z1 but it is not going to be installed
             Depends: lib32stdc++6 but it is not going to be installed
             Depends: lib32asound2 but it is not going to be installed
             Depends: lib32bz2-1.0 but it is not going to be installed
             Depends: lib32ncurses5 but it is not going to be installed
             Depends: lib32v4l-0 but it is not going to be installed
E: Broken packages

```

Thanks oldfred, I'll give it another go as I can see broader experience on the subject is coming along nicely now. I don't really need any fancy schmancy working bumblebee setup or anything as the intel chipset on my m14x gives about 300fps in a rotating compiz cube with hires deskscape, translucency and reflection on. And I don't play any games on Linux.. (yet). ;-)

---

### Post by snowpine on 2012-09-16
Can you post the output of:

```
cat /etc/apt/sources.list
```

My suspicion is that you have a conflict in your software sources.

---

### Post by cyb0rgb0rg on 2012-09-18
```
# deb cdrom:[Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted
deb http://no.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://no.archive.ubuntu.com/ubuntu/ lucid universe
deb http://no.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://no.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://no.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://no.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://no.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

---

### Post by snowpine on 2012-09-18
> **cyb0rgb0rg said:**
> ```
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted
deb http://no.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://no.archive.ubuntu.com/ubuntu/ lucid main restricted

```

Do you see the problem right here? You have mixed up 11.04 Natty Narwhal and 10.04 Lucid Lynx software sources; they are not compatible!

Edit the file with

```
gksu gedit /etc/apt/sources.list
```

Delete this line

```
deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted
```

save the file and quit

refresh your software sources and upgrade

```
sudo apt-get update
sudo apt-get dist-upgrade
```

post back the output :)

---

### Post by cyb0rgb0rg on 2012-09-18
**sudo apt-get update**
```
Ign cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2) lucid Release.gpg
Ign cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2)/ lucid/restricted Translation-en_US
Ign cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2) lucid Release
Ign cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2) lucid/main Packages
Ign cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2) lucid/restricted Packages
Ign cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2) lucid/main Packages
Ign cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2) lucid/restricted Packages
Err cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2) lucid/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2) lucid/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://no.archive.ubuntu.com lucid Release.gpg                             
Ign http://no.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://no.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://no.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://no.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://no.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://ppa.launchpad.net/glasen/intel-driver/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://no.archive.ubuntu.com lucid-backports Release.gpg                   
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://no.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://no.archive.ubuntu.com lucid Release                                 
Hit http://no.archive.ubuntu.com lucid-updates Release                         
Hit http://no.archive.ubuntu.com lucid-backports Release                       
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://no.archive.ubuntu.com lucid/main Packages                           
Hit http://no.archive.ubuntu.com lucid/restricted Packages                     
Hit http://no.archive.ubuntu.com lucid/main Sources                            
Hit http://no.archive.ubuntu.com lucid/restricted Sources                      
Hit http://no.archive.ubuntu.com lucid/universe Packages                       
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://no.archive.ubuntu.com lucid/universe Sources                        
Hit http://no.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://no.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://no.archive.ubuntu.com lucid-updates/main Packages                   
Hit http://no.archive.ubuntu.com lucid-updates/restricted Packages             
Hit http://no.archive.ubuntu.com lucid-updates/main Sources                    
Hit http://no.archive.ubuntu.com lucid-updates/restricted Sources              
Hit http://no.archive.ubuntu.com lucid-updates/universe Packages               
Hit http://no.archive.ubuntu.com lucid-updates/universe Sources                
Hit http://no.archive.ubuntu.com lucid-updates/multiverse Packages             
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://no.archive.ubuntu.com lucid-updates/multiverse Sources              
Hit http://no.archive.ubuntu.com lucid-backports/main Packages                 
Hit http://no.archive.ubuntu.com lucid-backports/restricted Packages           
Hit http://no.archive.ubuntu.com lucid-backports/universe Packages             
Hit http://no.archive.ubuntu.com lucid-backports/multiverse Packages           
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://archive.canonical.com lucid Release
Hit http://archive.canonical.com lucid/partner Packages      
Hit http://archive.canonical.com lucid/partner Sources
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
W: Failed to fetch cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2)/dists/lucid/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04.4 LTS _Lucid Lynx_ - Release amd64 (20120214.2)/dists/lucid/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

```
**sudo apt-get dist-upgrade**
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-2.6.32-43 linux-headers-2.6.32-43-generic
  linux-headers-lbm-2.6.32-43-generic
The following packages will be upgraded:
  dhcp3-client dhcp3-common gnupg gnupg-curl gpgv
  linux-backports-modules-headers-lucid-generic linux-headers-generic
  linux-libc-dev
8 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.1MB of archives.
After this operation, 86.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://no.archive.ubuntu.com/ubuntu/ lucid-updates/main dhcp3-client 3.1.3-2ubuntu3.4 [275kB]
Get:2 http://no.archive.ubuntu.com/ubuntu/ lucid-updates/main dhcp3-common 3.1.3-2ubuntu3.4 [336kB]
Get:3 http://no.archive.ubuntu.com/ubuntu/ lucid-updates/main gpgv 1.4.10-2ubuntu1.1 [225kB]
Get:4 http://no.archive.ubuntu.com/ubuntu/ lucid-updates/main gnupg 1.4.10-2ubuntu1.1 [1,126kB]
Get:5 http://no.archive.ubuntu.com/ubuntu/ lucid-updates/main gnupg-curl 1.4.10-2ubuntu1.1 [77.9kB]
Get:6 http://no.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-2.6.32-43 2.6.32-43.97 [10.2MB]
Get:7 http://no.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-2.6.32-43-generic 2.6.32-43.97 [831kB]
Get:8 http://no.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-lbm-2.6.32-43-generic 2.6.32-43.45 [229kB]
Get:9 http://no.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-backports-modules-headers-lucid-generic 2.6.32.43.50 [5,078B]
Get:10 http://no.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-generic 2.6.32.43.50 [5,000B]
Get:11 http://no.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-libc-dev 2.6.32-43.97 [859kB]
Fetched 14.1MB in 5s (2,364kB/s)       
Preconfiguring packages ...
(Reading database ... 154711 files and directories currently installed.)
Preparing to replace dhcp3-client 3.1.3-2ubuntu3.3 (using .../dhcp3-client_3.1.3-2ubuntu3.4_amd64.deb) ...
Unpacking replacement dhcp3-client ...
Preparing to replace dhcp3-common 3.1.3-2ubuntu3.3 (using .../dhcp3-common_3.1.3-2ubuntu3.4_amd64.deb) ...
Unpacking replacement dhcp3-common ...
Preparing to replace gpgv 1.4.10-2ubuntu1 (using .../gpgv_1.4.10-2ubuntu1.1_amd64.deb) ...
Unpacking replacement gpgv ...
Preparing to replace gnupg 1.4.10-2ubuntu1 (using .../gnupg_1.4.10-2ubuntu1.1_amd64.deb) ...
Unpacking replacement gnupg ...
Preparing to replace gnupg-curl 1.4.10-2ubuntu1 (using .../gnupg-curl_1.4.10-2ubuntu1.1_amd64.deb) ...
Leaving `diversion of /usr/lib/gnupg/gpgkeys_curl to /usr/lib/gnupg/gpgkeys_curl.non_curl by gnupg-curl'
Leaving `diversion of /usr/lib/gnupg/gpgkeys_hkp to /usr/lib/gnupg/gpgkeys_hkp.non_curl by gnupg-curl'
Unpacking replacement gnupg-curl ...
Selecting previously deselected package linux-headers-2.6.32-43.
Unpacking linux-headers-2.6.32-43 (from .../linux-headers-2.6.32-43_2.6.32-43.97_all.deb) ...
Selecting previously deselected package linux-headers-2.6.32-43-generic.
Unpacking linux-headers-2.6.32-43-generic (from .../linux-headers-2.6.32-43-generic_2.6.32-43.97_amd64.deb) ...
Selecting previously deselected package linux-headers-lbm-2.6.32-43-generic.
Unpacking linux-headers-lbm-2.6.32-43-generic (from .../linux-headers-lbm-2.6.32-43-generic_2.6.32-43.45_amd64.deb) ...
Preparing to replace linux-backports-modules-headers-lucid-generic 2.6.32.42.49 (using .../linux-backports-modules-headers-lucid-generic_2.6.32.43.50_amd64.deb) ...
Unpacking replacement linux-backports-modules-headers-lucid-generic ...
Preparing to replace linux-headers-generic 2.6.32.42.49 (using .../linux-headers-generic_2.6.32.43.50_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Preparing to replace linux-libc-dev 2.6.32-42.96 (using .../linux-libc-dev_2.6.32-43.97_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Setting up dhcp3-common (3.1.3-2ubuntu3.4) ...
Setting up dhcp3-client (3.1.3-2ubuntu3.4) ...

Setting up gpgv (1.4.10-2ubuntu1.1) ...
Setting up gnupg (1.4.10-2ubuntu1.1) ...

Setting up gnupg-curl (1.4.10-2ubuntu1.1) ...
Setting up linux-headers-2.6.32-43 (2.6.32-43.97) ...
Setting up linux-headers-2.6.32-43-generic (2.6.32-43.97) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-43-generic /boot/vmlinuz-2.6.32-43-generic

Setting up linux-headers-lbm-2.6.32-43-generic (2.6.32-43.45) ...
Setting up linux-backports-modules-headers-lucid-generic (2.6.32.43.50) ...
Setting up linux-headers-generic (2.6.32.43.50) ...
Setting up linux-libc-dev (2.6.32-43.97) ...

```

---

### Post by cyb0rgb0rg on 2012-09-18
Thank you snowpine. By doing that the problem is solved.

---

### Post by snowpine on 2012-09-18
Glad it worked. :)

---

