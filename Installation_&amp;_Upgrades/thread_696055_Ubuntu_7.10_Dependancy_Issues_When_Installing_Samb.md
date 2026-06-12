---
title: "Ubuntu 7.10: Dependancy Issues When Installing Samba"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by edwa5823 on 2008-02-13
Hello to All!

I am pleased to finally become a part of this community and want to thank everyone in advance for helping a beginner out.

I decided to convert my only Windows Desktop PC over to Ubuntu this week and become Open Source ONLY at home.  Subsequently I have installed the server (Dapper Drake) and the desktop (7.10) about 3-4 times each in the last few days just for practice.

My goal is to run a web server, samba server and the desktop GUI all on one machine (and all on a private network) so that I can program for personal use, and still have a working desktop for email and such.

The one problem that I have encountered is getting Samba to install after I have installed Ubuntu 7.10.  I am having some dependency issues with the version of a specific file.  I will log in later and post the file name as I am at work at the moment and do not remember exactly.

Having seen a few other posts regarding this problem in a much more broad fashion, I want to ask how I can circumvent or correct the problem.  I am willing to re-install either the server or the desktop solution as long as the end result is a working Apache/MySQL web server, Samba server, and Ubuntu GUI.

Thank you all for your help, I hope I have stated the problem and my requirements (and the reasons for each) clearly.

---

### Post by satx on 2008-02-13
edwa5823:

I use smb4k to manage my Samba configurations. Nice GUI, and very easy to use. It is under the Synaptic Package Manager. It also downloads the KDE, but that is no big deal.

Hope this helps. What does your smb.conf look like?

---

### Post by edwa5823 on 2008-02-13
Actually, I have made some headway this afternoon, but am having a new issue now that I could use some help with.

I have installed DAPPER (Ubuntu Server 6.06.2) and have successfully setup webmin, Apache, php, perl, and samba.  I am having some strange issues when I now try to install CUPS and/or the ubuntu desktop.  The only thing I can figure is that there is a problem with cupsys and they all depend on that package..  

When I attempt to run [sudo apt-get install ubuntu-desktop] I get the following:

```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: bluez-cups but it is not going to be installed
                  Depends: cupsys but it is not going to be installed
                  Depends: cupsys-driver-gutenprint but it is not going to be installed
                  Depends: hplip but it is not going to be installed
E: Broken packages
```

I also get the same type of error when installing CUPS and Subversion.  Have I done something that would cause these errors?

SUBVERSION:
sudo apt-get install subversion libapache2-svn
```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  subversion: Depends: patch but it is not going to be installed
E: Broken packages
```

CUPS:
sudo apt-get install cupsys cupsys-client
```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cupsys: Depends: patch but it is not going to be installed
E: Broken packages
```

---

### Post by edwa5823 on 2008-02-13
Well, I guess I should just wait a few minutes before posting questions.  If anyone else is seeing this problem and is lost like I was...  Comment out the CD lines in your /etc/apt/sources.list

Example:
```
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
#deb cdrom:[Ubuntu-Server 6.06.2 _Dapper Drake_ - Release i386 (20080110.1)]/ dapper main restricted
```

If these are uncommented it apparently tries to find files and dependencies there first and will fail!

---

### Post by zvacet on 2008-02-14
System>admin>software sources>be sure that you have cheke all boxes under ubuntu software and updates tab.Rload.**Synaptic>edit<fix broken packages**

---

### Post by ecridium on 2008-05-18
A similar thing happens to me when I want to install samba via apt-get in the terminal using : apt-get install samba.  It says about un met dependencies, and broken packages so that it won't install.  I'm using ubuntu 8.04, and such a thing never happened in the 7.10.

I tried zvacet way, and changes the software source to download from another place.  I think this bug happens because of the repository server that I used to download from was not updated yet.. If you change the download source to another place, voila...  The installation can now begun smoothly...

So next time, maybe if a similar problem occur...  We can try to change the download source by : 
System>Admin>Software Sources>Ubuntu Software>Download from : Server for ....

---

