---
title: "Unable to install boot-repair on 19.10"
date: 2020-02-12
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2020-02-12
I cannot install boot-repair

sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: [https://sourceforge.net/p/boot-repair/home](https://sourceforge.net/p/boot-repair/home)
 More info: [https://launchpad.net/~yannubuntu/+a...tu/boot-repair]("https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair")
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Ign:1 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan InRelease
Hit:2 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan Release
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease [97.5 kB]      
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan InRelease [255 kB]                 
Get:6 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan InRelease [15.4 kB]
Get:7 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan/main amd64 Packages [1,704 B]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/main amd64 Packages [137 kB]
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates InRelease [97.5 kB]        
Get:10 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan/main Translation-en [1,576 B]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/main amd64 Packages [969 kB]      
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/main Translation-en [51.5 kB]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/main amd64 DEP-11 Metadata [204 B]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/main DEP-11 48x48 Icons [29 B]
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/main DEP-11 64x64 Icons [29 B]
Get:16 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/main amd64 c-n-f Metadata [1,940 B]
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/restricted amd64 Packages [8,904 B]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/restricted Translation-en [1,516 B]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/main amd64 DEP-11 Metadata [510 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/main DEP-11 48x48 Icons [95.4 kB]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/main DEP-11 64x64 Icons [173 kB]
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/main amd64 c-n-f Metadata [29.7 kB]
Get:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main amd64 Packages [204 kB]
Get:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main Translation-en [77.5 kB]
Get:25 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main amd64 DEP-11 Metadata [73.0 kB]
Get:26 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main DEP-11 48x48 Icons [9,948 B]
Get:27 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main DEP-11 64x64 Icons [15.1 kB]
Get:28 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main amd64 c-n-f Metadata [2,932 B]
Get:29 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/restricted amd64 Packages [8,904 B]
Get:30 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/restricted Translation-en [1,516 B]
Fetched 2,840 kB in 2s (1,339 kB/s)                      
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get update
Ign:1 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan InRelease
Hit:2 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan Release
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan InRelease                          
Hit:6 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan InRelease
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates InRelease
Reading package lists... Done

ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 boot-repair : Depends: boot-sav but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 boot-repair : Depends: boot-sav but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ sudo apt-get install -y boot-save
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-save
ubuntu@ubuntu:~$ sudo apt-get install -y boot-sav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 boot-sav : Depends: glade2script (>= 3) but it is not going to be installed or
                     glade2script-gtk2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ sudo apt-get install -y glade2script-gtk2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 glade2script-gtk2 : Depends: python but it is not installable
                     Depends: python-gtk2 but it is not installable
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ sudo apt-get install python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python' has no installation candidate
ubuntu@ubuntu:~$ sudo apt-get install python-gtk2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-gtk2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'python-gtk2' has no installation candidate
ubuntu@ubuntu:~$

python --version

Command 'python' not found, but can be installed with:

sudo apt install python3

You also have python3 installed, you can run 'python3' instead.

ubuntu@ubuntu:~$ sudo apt install python3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python3 is already the newest version (3.7.5-1).
python3 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 252 not upgraded.



If python is already installed why is the installation of boot-repair not finding it?

---

### Post by EuclideanCoffee on 2020-02-12
I guess it cannot find python-gtk2 in your repositories, but you can grab the individual package from Ubuntu's packaging website.

[https://packages.ubuntu.com/eoan/python-gtk2](https://packages.ubuntu.com/eoan/python-gtk2)

---

### Post by 7-webmaster on 2020-02-13
I am not going to bypass standard procedures just because the installation package is incorrectly set up.  For all I know once I resolve these immediate problems the install will just demand ANOTHER package which is missing. 

The only reason that I am trying to install boot-repair is because I cannot successfully install Ubuntu 19.10 and the ONLY advice I have been given is to install boot-repair so that it will identify why Ubuntu 19.10 is not coming up.  I do not believe this is relevant. I believe that the boot is working because it gets as far as the screen that is displayed while the Linux initialization is proceeding, but that display never completes.  I therefore conclude that the problem is in the Linux startup, not in the Boot.  So boot-repair is not going to find anything wrong.

---

### Post by EuclideanCoffee on 2020-02-13
I know it's inconvenient. I've installed boot repair 3 times while on the job and have installed it manually. I'm not so sure if it's incorrect or just old. I think it's simply 3 or 4 steps to install via dpkg. No need to take it personally. Good luck.

---

### Post by oldfred on 2020-02-13
Do you get grub menu?
Or if only Ubuntu, and install is UEFI press escape (perhaps several times) to get grub menu. Or if BIOS press & hold shift key from BIOS until menu appears.

What video card/chip?
What brand/model system?
If nVidia, you normally need nomodeset, but newer versions now install nVidia proprietary driver, so nomodeset not required. 

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by 7-webmaster on 2020-02-14
I created this thread on boot-repair to focus on how to install boot-repair when it won't install because some of the pre-requisites are not available in the Ubuntu repository.  Issues related to Ubuntu 19.10 refusing to run on my platform are on thread 2436558.  As you can see from the console log above I am trying to follow the instructions at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) but they do not work.

---

### Post by dragonfly41 on 2020-02-15
I cannot answer why boot-repair does not install but my suggestion (for all PPA management) is to install [**Y PPA Manager**]("https://itsfoss.com/y-ppa-manager/")

launch it (under System Tools category), click on Manage PPA's where you can remove/purge/ PPA's.

Then you can Add PPA or go to Advanced and test PPA's.  Some clues might surface with this tool.

---

### Post by 7-webmaster on 2020-02-15
As you can see from the console log I posted I had already included the required PPA for installing boot-repair. However if there are other PPAs which are required for this installation, since for some reason the Ubuntu repositories do not contain pythongtk2, then those PPAs should be part of the documentation of how to install boot-repair.   Having a GUI PPA manager is not going to help if I am expected to psychically know what PPAs need to be included to satisfy the installation when the installation documentation does not identify them!

---

### Post by dragonfly41 on 2020-02-15
> [COLOR=#000000]Having a GUI PPA manager is not going to help[/COLOR] .. I disagree, but that is my opinion since it does identify duplicates, BADSIG errors and the like. But it is your call.

---

### Post by oldfred on 2020-02-15
Do these run without error if Boot-Repair not installed.
Always best to make sure system is up to date, before Boot-Repair as sometimes other software can cause an issue.

sudo apt update
sudo apt upgrade

       # If later you do not want ppa, how to uninstall ppa
sudo add-apt-repository --remove        ppa:yannubuntu/boot-repair

---

### Post by 7-webmaster on 2020-02-15
I am doing all of this on the 19-10 install USB because I cannot install a working 19-10 onto the SSD.  I have followed your suggestion to do apt update and apt upgrade, which updated the 1920 install USB, which strikes me as an unproductive use of my time, but I still cannot install boot-repair because of missing pre-requisites with no help from anyone on this thread about how to actually install boot-repair.

ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 boot-repair : Depends: boot-sav but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ sudo apt-get install -y boot-sav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 boot-sav : Depends: glade2script (>= 3) but it is not going to be installed or
                     glade2script-gtk2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ sudo apt-get install -y glade2script-gtk2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 glade2script-gtk2 : Depends: python but it is not installable
                     Depends: python-gtk2 but it is not installable
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ sudo apt-get install -y glade2script
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 glade2script : Depends: python but it is not installable
                Depends: python-gi but it is not installable
E: Unable to correct problems, you have held broken packages.

I honestly do not understand why I am doing anything to do with the boot.   The boot is completing fine.  It is just that the operating system does not complete initialization.

However I opened this thread because there is clearly something wrong if the published instructions for installing boot-repair DO NOT WORK!

---

### Post by oldfred on 2020-02-15
What flavor of Ubuntu are you using.
There was another post or two where one of the flavors also had issues, but Ubuntu just worked.
I have Boot-Repair installed in my 18.04 Ubuntu using flashback.

```
fred@bionic-z97:~$ echo $DESKTOP_SESSION
gnome-flashback-metacity
fred@bionic-z97:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.4 LTS"


```

---

### Post by tea for one on 2020-02-16
> **7-webmaster said:**
> I am doing all of this on the 19-10 install USB because I cannot install a working 19-10 onto the SSD.  I have followed your suggestion to do apt update and apt upgrade, which updated the 1920 install USB, which strikes me as an unproductive use of my time, but I still cannot install boot-repair because of missing pre-requisites with no help from anyone on this thread about how to actually install boot-repair.

> **7-webmaster said:**
> However I opened this thread because there is clearly something wrong if the published instructions for installing boot-repair DO NOT WORK!

When you are in your **live** 19.10 session, can you double check that the software sources are all ticked as screenshot.

[ATTACH=CONFIG]285034[/ATTACH]

I'm fairly sure that the **universe** repository is the important source.

```
sudo add-apt-repository universe
```

Once the correct repositories are enabled, hopefully, boot-repair will install successfully.

---

### Post by 7-webmaster on 2020-02-16
Thank you.

ubuntu@ubuntu:~$ sudo add-apt-repository universe
'universe' distribution component enabled for all sources.
Ign:1 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan InRelease
Hit:2 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan Release
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease [97.5 kB]      
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan InRelease                          
Hit:6 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan InRelease
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/main amd64 DEP-11 Metadata [204 B]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates InRelease [97.5 kB]      
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/universe amd64 Packages [68.7 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/universe Translation-en [36.3 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/universe amd64 DEP-11 Metadata [1,672 B]
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/universe DEP-11 48x48 Icons [7,100 B]
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/universe DEP-11 64x64 Icons [6,242 B]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security/universe amd64 c-n-f Metadata [2,072 B]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/universe amd64 Packages [8,798 kB]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/universe Translation-en [5,198 kB]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/universe amd64 DEP-11 Metadata [3,587 kB]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/universe DEP-11 48x48 Icons [2,843 kB]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/universe DEP-11 64x64 Icons [8,121 kB]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/universe amd64 c-n-f Metadata [271 kB]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main amd64 DEP-11 Metadata [72.9 kB]
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main DEP-11 48x48 Icons [9,953 B]
Get:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/main DEP-11 64x64 Icons [15.1 kB]
Get:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/universe amd64 Packages [103 kB]
Get:25 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/universe Translation-en [52.7 kB]
Get:26 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/universe amd64 DEP-11 Metadata [26.2 kB]
Get:27 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/universe DEP-11 48x48 Icons [18.4 kB]
Get:28 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/universe DEP-11 64x64 Icons [22.9 kB]
Get:29 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/universe amd64 c-n-f Metadata [2,556 B]
Fetched 29.5 MB in 12s (2,479 kB/s)                                            
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt update
Ign:1 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan InRelease
Hit:2 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan Release
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan InRelease                          
Hit:6 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan InRelease
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  boot-sav boot-sav-extra efibootmgr gir1.2-appindicator3-0.1 glade2script
  libpython-stdlib libpython2-stdlib libpython2.7-minimal libpython2.7-stdlib
  pastebinit python python-gi python-minimal python2 python2-minimal python2.7
  python2.7-minimal
Suggested packages:
  boot-info mdadm os-uninstaller python-doc python-tk python-gi-cairo
  python2-doc python2.7-doc binfmt-support
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra efibootmgr gir1.2-appindicator3-0.1
  glade2script libpython-stdlib libpython2-stdlib libpython2.7-minimal
  libpython2.7-stdlib pastebinit python python-gi python-minimal python2
  python2-minimal python2.7 python2.7-minimal
0 upgraded, 18 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,697 kB/4,725 kB of archives.
After this operation, 20.4 MB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan/main amd64 glade2script all 3.2.3~ppa4 [36.0 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/universe amd64 libpython2.7-minimal amd64 2.7.17-1~19.10 [335 kB]
Get:3 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan/main amd64 efibootmgr amd64 15-1 [28.2 kB]
Get:4 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan/main amd64 boot-sav all 4ppa66 [425 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/universe amd64 python2.7-minimal amd64 2.7.17-1~19.10 [1,307 kB]
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/universe amd64 python2-minimal amd64 2.7.17-1 [27.8 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/universe amd64 python-minimal amd64 2.7.17-1 [5,996 B]
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/universe amd64 libpython2.7-stdlib amd64 2.7.17-1~19.10 [1,881 kB]
Get:9 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan/main amd64 boot-repair all 4ppa66 [12.5 kB]
Get:10 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) eoan/main amd64 boot-sav-extra all 4ppa66 [142 kB]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates/universe amd64 python2.7 amd64 2.7.17-1~19.10 [248 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/universe amd64 libpython2-stdlib amd64 2.7.17-1 [7,400 B]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/universe amd64 libpython-stdlib amd64 2.7.17-1 [5,836 B]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/universe amd64 python2 amd64 2.7.17-1 [26.5 kB]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/universe amd64 python amd64 2.7.17-1 [7,836 B]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/universe amd64 python-gi amd64 3.34.0-1 [211 kB]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/main amd64 gir1.2-appindicator3-0.1 amd64 12.10.1+18.04.20180322.1-0ubuntu4 [3,444 B]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan/main amd64 pastebinit all 1.5.1-1 [14.2 kB]
Fetched 4,697 kB in 3s (1,779 kB/s)                                          
Selecting previously unselected package libpython2.7-minimal:amd64.
(Reading database ... 224991 files and directories currently installed.)
Preparing to unpack .../0-libpython2.7-minimal_2.7.17-1~19.10_amd64.deb ...
Unpacking libpython2.7-minimal:amd64 (2.7.17-1~19.10) ...
Selecting previously unselected package python2.7-minimal.
Preparing to unpack .../1-python2.7-minimal_2.7.17-1~19.10_amd64.deb ...
Unpacking python2.7-minimal (2.7.17-1~19.10) ...
Selecting previously unselected package python2-minimal.
Preparing to unpack .../2-python2-minimal_2.7.17-1_amd64.deb ...
Unpacking python2-minimal (2.7.17-1) ...
Selecting previously unselected package python-minimal.
Preparing to unpack .../3-python-minimal_2.7.17-1_amd64.deb ...
Unpacking python-minimal (2.7.17-1) ...
Selecting previously unselected package libpython2.7-stdlib:amd64.
Preparing to unpack .../4-libpython2.7-stdlib_2.7.17-1~19.10_amd64.deb ...
Unpacking libpython2.7-stdlib:amd64 (2.7.17-1~19.10) ...
Selecting previously unselected package python2.7.
Preparing to unpack .../5-python2.7_2.7.17-1~19.10_amd64.deb ...
Unpacking python2.7 (2.7.17-1~19.10) ...
Selecting previously unselected package libpython2-stdlib:amd64.
Preparing to unpack .../6-libpython2-stdlib_2.7.17-1_amd64.deb ...
Unpacking libpython2-stdlib:amd64 (2.7.17-1) ...
Selecting previously unselected package libpython-stdlib:amd64.
Preparing to unpack .../7-libpython-stdlib_2.7.17-1_amd64.deb ...
Unpacking libpython-stdlib:amd64 (2.7.17-1) ...
Setting up libpython2.7-minimal:amd64 (2.7.17-1~19.10) ...
Setting up python2.7-minimal (2.7.17-1~19.10) ...
Linking and byte-compiling packages for runtime python2.7...
Setting up python2-minimal (2.7.17-1) ...
Selecting previously unselected package python2.
(Reading database ... 225747 files and directories currently installed.)
Preparing to unpack .../python2_2.7.17-1_amd64.deb ...
Unpacking python2 (2.7.17-1) ...
Setting up python-minimal (2.7.17-1) ...
Selecting previously unselected package python.
(Reading database ... 225776 files and directories currently installed.)
Preparing to unpack .../0-python_2.7.17-1_amd64.deb ...
Unpacking python (2.7.17-1) ...
Selecting previously unselected package python-gi.
Preparing to unpack .../1-python-gi_3.34.0-1_amd64.deb ...
Unpacking python-gi (3.34.0-1) ...
Selecting previously unselected package gir1.2-appindicator3-0.1.
Preparing to unpack .../2-gir1.2-appindicator3-0.1_12.10.1+18.04.20180322.1-0ubuntu4_amd64.deb ...
Unpacking gir1.2-appindicator3-0.1 (12.10.1+18.04.20180322.1-0ubuntu4) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../3-glade2script_3.2.3~ppa4_all.deb ...
Unpacking glade2script (3.2.3~ppa4) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../4-boot-sav_4ppa66_all.deb ...
Unpacking boot-sav (4ppa66) ...
Selecting previously unselected package boot-repair.
Preparing to unpack .../5-boot-repair_4ppa66_all.deb ...
Unpacking boot-repair (4ppa66) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../6-boot-sav-extra_4ppa66_all.deb ...
Unpacking boot-sav-extra (4ppa66) ...
Selecting previously unselected package efibootmgr.
Preparing to unpack .../7-efibootmgr_15-1_amd64.deb ...
Unpacking efibootmgr (15-1) ...
Selecting previously unselected package pastebinit.
Preparing to unpack .../8-pastebinit_1.5.1-1_all.deb ...
Unpacking pastebinit (1.5.1-1) ...
Setting up efibootmgr (15-1) ...
Setting up pastebinit (1.5.1-1) ...
Setting up libpython2.7-stdlib:amd64 (2.7.17-1~19.10) ...
Setting up gir1.2-appindicator3-0.1 (12.10.1+18.04.20180322.1-0ubuntu4) ...
Setting up python2.7 (2.7.17-1~19.10) ...
Setting up libpython2-stdlib:amd64 (2.7.17-1) ...
Setting up python2 (2.7.17-1) ...
Setting up libpython-stdlib:amd64 (2.7.17-1) ...
Setting up python (2.7.17-1) ...
Setting up python-gi (3.34.0-1) ...
Setting up glade2script (3.2.3~ppa4) ...
Setting up boot-sav (4ppa66) ...
Setting up boot-sav-extra (4ppa66) ...
Setting up boot-repair (4ppa66) ...
Processing triggers for mime-support (3.63ubuntu1) ...
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for man-db (2.8.7-3) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu1) ...

---

### Post by oldfred on 2020-04-22
Boot-Repair runs glade2script which is currently based on python2.
Only if python2 installed will it work currently.

[https://bugs.launchpad.net/boot-repair/+bug/1865378](https://bugs.launchpad.net/boot-repair/+bug/1865378)

---

### Post by hk42 on 2020-04-23
I too failed to install boot -repair.
But there is a bootable USB ISO of boot- repair.
It helped a lot.

---

### Post by dragonfly41 on 2020-04-23
Have you tried running Grub Customizer to inspect and edit classic Grub?

Personally I am very happy now using rEFInd as my boot loader with a [custom refind theme]("https://github.com/bobafetthotmail/refind-theme-regular").
Bypasses some grub problems.  Installs in selected ESP  (fat32 with boot flags) as /boot/efi/EFI/refind

[Earlier thread]("https://ubuntuforums.org/showthread.php?t=2434349&page=2&highlight=theme+rEFInd+dragonfly41").

---

