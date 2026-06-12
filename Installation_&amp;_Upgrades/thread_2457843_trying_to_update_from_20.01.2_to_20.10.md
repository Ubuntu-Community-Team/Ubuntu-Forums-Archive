---
title: "trying to update from 20.01.2 to 20.10"
date: 2021-02-10
forum: Installation &amp; Upgrades
---

### Post by jgw on 2021-02-10
I am trying to update from 20.01.2 to 20.10  
I was following instructions found on the internet.  
I was told to run sudo apt update.  When I did that I got an error.  Here is what I had:

```

[sudo] password for greg: 
Ign:1 cdrom://Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731) focal InRelease
Err:2 cdrom://Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731) focal Release
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit:3 http://us.archive.ubuntu.com/ubuntu focal InRelease
Hit:4 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:5 http://us.archive.ubuntu.com/ubuntu focal-updates InRelease              
Hit:6 http://ppa.launchpad.net/jcfp/nobetas/ubuntu focal InRelease             
Hit:7 http://us.archive.ubuntu.com/ubuntu focal-backports InRelease            
Hit:8 http://archive.canonical.com/ubuntu focal InRelease                      
Hit:9 http://security.ubuntu.com/ubuntu focal-security InRelease               
Hit:10 http://ppa.launchpad.net/jcfp/sab-addons/ubuntu focal InRelease   
Hit:11 http://ppa.launchpad.net/mkusb/ppa/ubuntu focal InRelease
Hit:12 http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu focal InRelease
Hit:13 http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu focal InRelease
Hit:14 http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu focal InRelease
Reading package lists... Done
E: The repository 'cdrom://Ubuntu 20.04.1 LTS _Focal Fossa_ - Release amd64 (20200731) focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
greg@gregdown:~$ 

```

It appears that I might have a problem with my cd.  As far as I know it runs fine but maybe not.  My first thought was to just disconnect it as I don't use it much anymore but then figured I better fix it.  I got an error "Failed to download repository information".  When I try and start the update I am told to take care of all updates on the current (20.04.2) system.  I am basically stuck.  I thought about just downloading the update and having at it but that too may be a mistake. 

Oh, neither Software & Updates or Software Updater will note that there is an update (ubuntu 20.10)

thoughts?

---

### Post by GhX6GZMB on 2021-02-10
I'm not sure why you are using DVD for upgrading, DVD is normally only for reinstall.

To upgrade your OS version, the command is:

```
sudo do-release-upgrade
```

Run this first:

```
sudo apt update
sudo apt full-upgrade
```

---

### Post by kansasnoob on 2021-02-11
First of all you need to know that 20.04 is supported until April 2025 but 20.10 is only supported until July 2021:

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

That business of trying to get updates via CD is probably the result of having the Cdrom with focal fossa checked in the software settings UI (under the Ubuntu Software tab).

After considering the much shorter life span of 20.10 if you still want to upgrade you'll need to click on the Updates tab while you have the software settings UI open and at the very bottom where it says "notify me of a new version" change it from LTS to Any version.

---

### Post by Impavidus on 2021-02-11
That cdrom source is the Ubuntu live disk from where you installed Ubuntu. It can be used as a repository for installing additional software, which may be useful if you've got no network. But after installation, that should normally be disabled. You can disable it in the software & updates settings GUI or by editing /etc/apt/sources.list in a text editor.

The sudo apt update command only refreshes the list of available software. To install the updates, you need sudo apt upgrade.

In the software & settings GUI, you'll find an option to inform you of new versions of Ubuntu. It's probably set to LTS releases only. If you want to upgrade to 20.10, you have to set it to any release.

During the upgrade, your PPAs will be disabled. You can enable them after the upgrade, if they are available for 20.10. Check that first.

---

### Post by jgw on 2021-02-11
Thank you for the replies.

I apparently did a lousy job explaining my problem.  When upgrading the system apparently Ubuntu demands that all updates be accomplished.  I seem to have a problem with my dvd which means that something to do with that dvd cannot be upgraded so I cannot upgrade my system.  I have no idea why this is and have no idea how to fix the problem, other than to just disconnect the dvd which I would prefer not to do.

Thanks again!

---

### Post by grahammechanical on 2021-02-11
As stated above open Software & Updates. Go to the Other Software tab and disable (un-tick) the box where is says CD-ROM with Ubuntu ......

Now, try running the apt update & apt upgrade commands.

[https://www.omgubuntu.co.uk/2020/10/how-to-upgrade-to-ubuntu-20-10-from-ubuntu-20-04](https://www.omgubuntu.co.uk/2020/10/how-to-upgrade-to-ubuntu-20-10-from-ubuntu-20-04)

Regards

---

### Post by CelticWarrior on 2021-02-11
The error message has NOTHING to do with your DVD drive.

It has to do with you or someone else using your system having enabled the "cdrom" repository in Software & Updates. This refers to the installation MEDIA regardless of it having been optical (DVD) or USB. As suggested above just disable it. Then run
```
sudo apt update
sudo apt full-upgrade
```
to assure your system is fully updated as it should be regardless of proceeding or not with the likely irrational decision to do the release upgrade.

---

