---
title: "ttf-mscorefonts-ins won't complete"
date: 2016-12-28
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2016-12-28
This is just the simplest of the attempts made.  Hopefully there are clues in there that someone can follow.

On Ubuntu 16.04, 64 bit
--------------------------------------------
```
roger@roger-desktop:~$ sudo apt-get install --reinstall ttf-mscorefonts-installer  
[sudo] password for roger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/29.5 kB of archives.
After this operation, 0 B of additional disk space will be used.
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
Preconfiguring packages ...
(Reading database ... 329314 files and directories currently installed.)
Preparing to unpack .../ttf-mscorefonts-installer_3.4+nmu1ubuntu2_all.deb ...
mscorefonts-eula license has already been accepted
Unpacking ttf-mscorefonts-installer (3.4+nmu1ubuntu2) over (3.4+nmu1ubuntu2) ...
Processing triggers for fontconfig (2.11.94-0ubuntu1.1) ...
Processing triggers for update-notifier-common (3.168.2) ...
ttf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe) [198 kB]
Fetched 198 kB in 2s (66.5 kB/s)                                               
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/andale32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
Err:1 [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
  The HTTP server sent an invalid Content-Range header
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/arial32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
E: Failed to fetch [https://cytranet.dl.sourceforge.net/project/corefonts/the](https://cytranet.dl.sourceforge.net/project/corefonts/the) fonts/final/arial32.exe  The HTTP server sent an invalid Content-Range header

E: Download Failed
Setting up ttf-mscorefonts-installer (3.4+nmu1ubuntu2) ...
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
roger@roger-desktop:~$ 
-----------------------------------------------------
```
At several times I have accepted the EULA, no help.

Thanks!

---

### Post by wildmanne39 on 2016-12-28
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by RogerDavis on 2016-12-28
I have a wired connection.  I used the wired commands, got this result
-------------------
```
roger@roger-desktop:~$ sudo apt-get update
[sudo] password for roger: 
Ign:1 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:4 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release                      
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Fetched 306 kB in 1s (257 kB/s)                                                
Reading package lists... Done
**N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension**
roger@roger-desktop:~$ 
roger@roger-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
**N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension**
roger@roger-desktop:~$ 
```
---------------------------------------------
I'll now reboot and see what happens.

The problem still exists.  This is a desktop with no wireless capability, so I guess the wireless into script would have no function and no use.

---

### Post by slickymaster on 2016-12-28
> **RogerDavis said:**
> I have a wired connection.  I used the wired commands, got this result
-------------------
```
roger@roger-desktop:~$ sudo apt-get update
[sudo] password for roger: 
Ign:1 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:4 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release                      
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Fetched 306 kB in 1s (257 kB/s)                                                
Reading package lists... Done
[COLOR=#FF0000]**N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension**[/COLOR]
roger@roger-desktop:~$ 
roger@roger-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[COLOR=#FF0000]**N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension**[/COLOR]
roger@roger-desktop:~$ 
```
---------------------------------------------
I'll now reboot and see what happens.

The problem still exists.  This is a desktop with no wireless capability, so I guess the wireless into script would have no function and no use.
The prefix N: means that it's merely a notice and didn't block any action of apt like updating and upgrading. See this explanation of the origin and [purpose of .ucf-dist files]("http://askubuntu.com/a/573091/175814").

---

### Post by howefield on 2016-12-28
The script that the the package runs in order to download the fonts from the sourceforge server is pointing at the wrong location, as I understand it.

Try the following command in a terminal..

```
sudo touch /var/lib/update-notifier/package-data-downloads/ttf-mscorefonts-installer
```

You won't get any feedback in the terminal after entering the command but it should stop the prompts.

I'd suggest purging the 3.4 version of the package and install the 3.6 version instead as follows..

```
sudo apt purge ttf-mscorefonts-installer[code]

and then

[code]wget [http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb](http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb) -P ~/Downloads
```

will download the package to your Downloads folder, and

```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

to install the package.

---

