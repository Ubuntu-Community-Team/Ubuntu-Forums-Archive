---
title: "dist upgrade is failing me."
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by searayman on 2007-01-18
I am using ubuntu edgy eft, and just recently its been askign me to do a distribution upgrade, but when i do it, it dont work and tells me to look at the log files, so i have them copied below:

the log file named apt.log is here: [http://pastebin.ca/320936]("http://pastebin.ca/320936")

the log file called main.log is here: [http://pastebin.ca/320932]("http://pastebin.ca/320932")

please help me fix this. By the way i have been running beryl smoothly for the past few months.

---

### Post by hal10000 on 2007-01-18
Please post the content of your /etc/apt/sources.list file

Have  you updated from dapper to edgy (or what else)?
I can see in the main.log that there are mixed edgy and dapper entries. This should not happen. For an upgrade from dapper to edgy you should use the command [COLOR="Red"]sudo update-manager -c[/COLOR]

---

### Post by searayman on 2007-01-18
I stated in my first post that i was running Ubuntu Edgy already, since it first came out.

Source list is posted here: [http://pastebin.ca/321004]("http://pastebin.ca/321004")

---

### Post by hal10000 on 2007-01-18
You sources.list seems to be correct
The package which inhibits the upgrade is ubuntu-desktop.
What if you open synaptic and manually remove this package (though it's not recommended to remove it) and reinstall it after the upgrade.
Maybe other packages will then be removed too, but after upgrading they may all br reinstalled. 
I guess this is the easiest way to get a clean system again.

btw, in synaptic you can use the "File"--->"History" option to see which packages were been removed (or installed)at a given time/date.

---

### Post by bkeithly on 2007-01-18
Dist upgrade was failing me,

I did this:

sudo apt-get update
sudo apt-get upgrade

problem seems to have gone away...  I was using the GUI package manager previously and that kept failing....

Give it a shot.

---

### Post by searayman on 2007-01-18
> **bkeithly said:**
> Dist upgrade was failing me,

I did this:

sudo apt-get update
sudo apt-get upgrade

problem seems to have gone away...  I was using the GUI package manager previously and that kept failing....

Give it a shot.


that worked, your awsome!

---

### Post by bkeithly on 2007-01-20
ARGH!!!!!!!!!!!!


ITS Happening again!!!!  

ANYONE ELSE STILL SEING THIS ISSUE?

---

### Post by bkeithly on 2007-01-20
Ahh looked around and found out that Envy is working for most folks.

I tried it and now we are good to go!!!!

---

### Post by searayman on 2007-01-23
> **bkeithly said:**
> ARGH!!!!!!!!!!!!


ITS Happening again!!!!  

ANYONE ELSE STILL SEING THIS ISSUE?

yea your fixed worked but then a week later it does it again.

---

### Post by searayman on 2007-01-23
> **bkeithly said:**
> Ahh looked around and found out that Envy is working for most folks.

I tried it and now we are good to go!!!!

what is envy?

also coudl this be a problem for me, when i do suod apt-get update i get this at the end:

Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: You may want to run apt-get update to correct these problems
mike@mike-desktop:~$

---

### Post by hal10000 on 2007-01-23
[QUOTE][W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C/QUOTE]
this happens when the gpg key is incorrect or if you imported none, but the packages will be available though.

---

### Post by searayman on 2007-01-23
> **hal10000 said:**
> [QUOTE][W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C/QUOTE]
this happens when the gpg key is incorrect or if you imported none, but the packages will be available though.


is this part of my problem? I thought it was so i removed automtix but it didnt do anything.

---

### Post by searayman on 2007-01-24
i need help somone!! I cant install certain updates untill the disrtibution upgrade!! any ideas cause the dist upgrade dotn work!!!

---

### Post by hal10000 on 2007-01-25
Just try what bkeithly did, use [COLOR="Red"]sudo apt-get update[/COLOR], [COLOR="Red"]sudo apt-get upgrade[/COLOR] and [COLOR="Red"]sudo apt-get dist-upgrade[/COLOR] (in a terminal window, do them ALL).
Don't mind if you get a gpg error, this is just a minor error for you now.
Please post the result.

You may put tha automatix line into your /etc/apt/sources.list again.

---

### Post by searayman on 2007-01-25
ok here is what i did:

mike@mike-desktop:~$ sudo apt-get update
Password:
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
  
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release [6733B]                         
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US             
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                          
Get:6 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release.gpg [189B]                    
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Translation-en_US   
Ign [http://albertomilone.com](http://albertomilone.com) binary/ Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Get:7 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release [14.2kB]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                            
Ign [http://albertomilone.com](http://albertomilone.com) binary/ Translation-en_US                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Ign [http://albertomilone.com](http://albertomilone.com) binary/ Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources            
Hit [http://albertomilone.com](http://albertomilone.com) binary/ Packages                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Get:8 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn Packages [9156B]
Fetched 30.5kB in 1s (22.2kB/s)
Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: You may want to run apt-get update to correct these problems
mike@mike-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  beryl linux-restricted-modules-2.6.17-10-386 totem totem-mozilla
The following packages will be upgraded:
  automatix2 beryl-core beryl-plugins beryl-plugins-data libberylsettings0
5 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 3806kB of archives.
After unpacking 184kB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  automatix2
Install these packages without verification [y/N]? y
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main automatix2 1.1-2.12-6.10edgy_i386 [195kB]
Get:2 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn libberylsettings0 0.2.0+svn20070125-r3128+3v1ubuntu0 [40.9kB]
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn beryl-core 0.2.0+svn20070125-r3128+3v1ubuntu0 [355kB]
Get:4 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn beryl-plugins-data 0.2.0+svn20070125-r3123+3v1ubuntu1 [2748kB]
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn beryl-plugins 0.2.0+svn20070125-r3123+3v1ubuntu1 [468kB]
Fetched 3806kB in 4s (792kB/s)               
(Reading database ... 122087 files and directories currently installed.)
Preparing to replace automatix2 1.1-2.11-6.10edgy_i386 (using .../automatix2_1.1-2.12-6.10edgy%5fi386_i386.deb) ...
Unpacking replacement automatix2 ...
Preparing to replace libberylsettings0 0.2.0+svn20070124-r3094+3v1ubuntu0 (using .../libberylsettings0_0.2.0+svn20070125-r3128+3v1ubuntu0_i386.deb) ...
Unpacking replacement libberylsettings0 ...
Preparing to replace beryl-core 0.2.0+svn20070124-r3094+3v1ubuntu0 (using .../beryl-core_0.2.0+svn20070125-r3128+3v1ubuntu0_i386.deb) ...
Unpacking replacement beryl-core ...
Preparing to replace beryl-plugins-data 0.2.0+svn20070124-r3091+3v1ubuntu0 (using .../beryl-plugins-data_0.2.0+svn20070125-r3123+3v1ubuntu1_all.deb) ...
Unpacking replacement beryl-plugins-data ...
Preparing to replace beryl-plugins 0.2.0+svn20070124-r3091+3v1ubuntu0 (using .../beryl-plugins_0.2.0+svn20070125-r3123+3v1ubuntu1_i386.deb) ...
Unpacking replacement beryl-plugins ...
Setting up automatix2 (1.1-2.12-6.10edgy_i386) ...
Setting up libberylsettings0 (0.2.0+svn20070125-r3128+3v1ubuntu0) ...

Setting up beryl-core (0.2.0+svn20070125-r3128+3v1ubuntu0) ...

Setting up beryl-plugins-data (0.2.0+svn20070125-r3123+3v1ubuntu1) ...
Setting up beryl-plugins (0.2.0+svn20070125-r3123+3v1ubuntu1) ...
mike@mike-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  nvidia-glx
The following NEW packages will be installed:
  libberyldecoration0
The following packages have been kept back:
  totem totem-mozilla
The following packages will be upgraded:
  beryl linux-restricted-modules-2.6.17-10-386
2 upgraded, 1 newly installed, 1 to remove and 2 not upgraded.
Need to get 7921kB of archives.
After unpacking 13.8MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted linux-restricted-modules-2.6.17-10-386 2.6.17.7-10.1 [7886kB]
Get:2 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn libberyldecoration0 0.2.0+svn20070125-r3128+3v1ubuntu0 [24.1kB]
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy/beryl-svn beryl 0.2.0+svn20070125-r3128+3v1ubuntu0 [10.7kB]
Fetched 7921kB in 9s (849kB/s)                                                 
(Reading database ... 122084 files and directories currently installed.)
Removing nvidia-glx ...
Selecting previously deselected package libberyldecoration0.
(Reading database ... 122038 files and directories currently installed.)
Unpacking libberyldecoration0 (from .../libberyldecoration0_0.2.0+svn20070125-r3128+3v1ubuntu0_i386.deb) ...
Preparing to replace beryl 0.1.5+svn20070107-r2464+3v1ubuntu0 (using .../beryl_0.2.0+svn20070125-r3128+3v1ubuntu0_i386.deb) ...
Unpacking replacement beryl ...
Preparing to replace linux-restricted-modules-2.6.17-10-386 2.6.17.7-1 (using .../linux-restricted-modules-2.6.17-10-386_2.6.17.7-10.1_i386.deb) ...
Unpacking replacement linux-restricted-modules-2.6.17-10-386 ...
Setting up libberyldecoration0 (0.2.0+svn20070125-r3128+3v1ubuntu0) ...

Setting up beryl (0.2.0+svn20070125-r3128+3v1ubuntu0) ...
Setting up linux-restricted-modules-2.6.17-10-386 (2.6.17.7-10.1) ...

mike@mike-desktop:~$ 




wont know if it worked untill next update, will keep you posted

---

### Post by hal10000 on 2007-01-25
It may be necessary that you repeat these commands two or three times to get everything correct if  there remain some unsolved dependencies.

If you install the synaptic package ([COLOR="Red"]sudo apt-get install synaptic[/COLOR]) you get a great gui for handling your packages and repositories (better than gnome update manager or most other package managing tools).

---

### Post by bkeithly on 2007-01-25
Sorry for the delay...

Envy did something with the install of the nvidia drivers.

The nvidia drivers were causing the distro upgrade to fail me.

So I found something on the forums on how to install Envy.  

If memory serves I de-installed nvidia drivers, installed Envy, got out of X, ran Envy.  Then did the upgrade and it worked.


Now don't qoute me on the exact steps.   Search the forums for the Envy installation process.  Follow that.  Then try the distupgrade.

YOu should be all good to go then.

---

