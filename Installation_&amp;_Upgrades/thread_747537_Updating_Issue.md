---
title: "Updating Issue"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by deadowl on 2008-04-06
I get a similar error message for every package, both through Synaptic Package Manager and Update Manager:

---------------
E: /var/cache/apt/archives/tzdata_2008a-0ubuntu0.7.10_all.deb: failed in buffer_read(fd)

Gu
----------------
E: /var/cache/apt/archives/openssh-server_1%3a4.6p1-5ubuntu0.2_i386.deb: failed in buffer_read(fd)

all 
----------------
(...)
----------------
I've tried setting aside different updates; it happens for all of them.
Any clue? I can also note that "Gu" and "all" have been fragments of something I've typed. However, I don't have enough info to pinpoint it to that.

In addition, Firefox Web Browser from the .deb won't work, so I'm using Gran Paradiso Alpha 8, which I had installed from source a while back.

---

### Post by Rocket2DMn on 2008-04-06
Try
```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
Post back any errors you still get.

---

### Post by deadowl on 2008-04-07
Ditto...

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/tzdata_2008a-0ubuntu0.7.10_all.deb (--unpack):
 failed in buffer_read(fd): files list for package `ifupdown': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2008a-0ubuntu0.7.10_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Rocket2DMn on 2008-04-07
Run
```
sudo rm /var/cache/apt/archives/tzdata_2008a-0ubuntu0.7.10_all.deb
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```
That should get you going, but again, post back any errors.

---

### Post by deadowl on 2008-04-07
same error:

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/tzdata_2008a-0ubuntu0.7.10_all.deb (--unpack):
 failed in buffer_read(fd): files list for package `ifupdown': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2008a-0ubuntu0.7.10_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Rocket2DMn on 2008-04-07
After which command do you get that error?
Try running
```
sudo apt-get install -f
```
and/or
```
sudo apt-get install --reinstall tzdata
```
or even
```
sudo apt-get remove tzdata
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```
then reinstall tzdata
```
sudo apt-get install tzdata
```
When you post errors, please include the command you issued as well.

---

### Post by deadowl on 2008-04-07
I don't know what you're thinking with the last set of commands. The scope of this problem isn't limited to tzdata for one, and if I were to remove tzdata then I'd pretty much be screwed.

So I picked a package I've never tried installing before, abiword-help:

Selecting previously deselected package abiword-help.
(Reading database ... dpkg: error processing /var/cache/apt/archives/abiword-help_2.4.6-2ubuntu2_all.deb (--unpack):
 failed in buffer_read(fd): files list for package `ifupdown': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/abiword-help_2.4.6-2ubuntu2_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


Same error.

---

### Post by Rocket2DMn on 2008-04-07
> **deadowl said:**
> I don't know what you're thinking with the last set of commands. The scope of this problem isn't limited to tzdata for one, and if I were to remove tzdata then I'd pretty much be screwed.

That is an extremely useful piece of information, I thought we had fixed other ones.  I need the complete output of all of these commands, just copy and paste all the stuff that shows in terminal, including the command you issue
```
sudo rm /var/cache/apt/archives/*.deb
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```
Please don't cut off any of the output, you can wrap it all it these tags, without spaces: [ c o d e ] output here [ / c o d e ]

---

### Post by deadowl on 2008-04-07
My guess: A, B, C, will output nothing of value, D will output the same error. That is, if apt-get clean actually works
A: None
B:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfaad2-0 guile-1.8 lilypond-data libportaudio2 texlive-base texlive
  texlive-fonts-recommended libsilc-1.1-2 ggzcore-bin libggzmod4
  guile-1.8-libs tetex-bin libggz2 texlive-latex-recommended
  texlive-latex-base libggzcore9 libquicktime1 libntfs-3g5 texlive-doc-base
  libboost-python1.33.1 texinfo
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.

C:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US               
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Release.gpg   
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Translation-en_US                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Release       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release              
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Packages                           
Hit [http://ftp.osuosl.org](http://ftp.osuosl.org) gutsy/ Packages                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Fetched 3B in 1s (3B/s)  
Reading package lists... Done

D:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  bzip2 cupsys cupsys-bsd cupsys-client cupsys-common firefox firefox-dev
  firefox-gnome-support gthumb libbz2-1.0 libcupsimage2 libcupsys2 libicu36
  libpq5 libruby1.8 libsdl-image1.2 libsdl-image1.2-dev mplayer openssh-client
  openssh-server ruby1.8 ssh-askpass-gnome tzdata
23 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.5MB of archives.
After unpacking 16.4kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main tzdata 2008a-0ubuntu0.7.10 [652kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main openssh-server 1:4.6p1-5ubuntu0.2 [248kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main openssh-client 1:4.6p1-5ubuntu0.2 [657kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libcupsys2 1.3.2-1ubuntu7.6 [183kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libcupsimage2 1.3.2-1ubuntu7.6 [46.1kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main cupsys-common 1.3.2-1ubuntu7.6 [1080kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main bzip2 1.0.4-0ubuntu2.1 [44.7kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libbz2-1.0 1.0.4-0ubuntu2.1 [43.1kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main firefox-gnome-support 2.0.0.13+1nobinonly-0ubuntu0.7.10 [91.8kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main firefox-dev 2.0.0.13+1nobinonly-0ubuntu0.7.10 [3183kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main cupsys 1.3.2-1ubuntu7.6 [2018kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main cupsys-bsd 1.3.2-1ubuntu7.6 [36.5kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main cupsys-client 1.3.2-1ubuntu7.6 [86.5kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libruby1.8 1.8.6.36-1ubuntu3.1 [1566kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libsdl-image1.2-dev 1.2.5-3ubuntu0.1 [34.7kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libsdl-image1.2 1.2.5-3ubuntu0.1 [29.9kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main ruby1.8 1.8.6.36-1ubuntu3.1 [239kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main ssh-askpass-gnome 1:4.6p1-5ubuntu0.2 [88.0kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main firefox 2.0.0.13+1nobinonly-0ubuntu0.7.10 [9197kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main gthumb 3:2.10.6-0ubuntu1.1 [1369kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libicu36 3.6-3ubuntu0.1 [5507kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libpq5 8.2.7-0ubuntu0.7.10 [238kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse mplayer 2:1.0~rc1-0ubuntu13.2 [3866kB]
Fetched 30.5MB in 27s (1096kB/s)                                               
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/tzdata_2008a-0ubuntu0.7.10_all.deb (--unpack):
 failed in buffer_read(fd): files list for package `ifupdown': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/tzdata_2008a-0ubuntu0.7.10_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Rocket2DMn on 2008-04-08
OK, we're going to run autoremove to get rid of those old packages, then we're going to try to remove the package "ifupdown" (we will reinstall it at the end).  Again, please post all output, you don't need to break it down by A, B, C, etc, just copy and paste everything from the terminal, the command will be included there - otherwise you're just making work for yourself.  I'm also going to have you post the contents of a file by the "cat" command - I think this is the files list for "ifupdown".  The file may not exist, which would be a problem that should get fixed by reinstalling the program.
```
cat /var/lib/dpkg/info/ifupdown.list
sudo apt-get autoremove
sudo rm /var/cache/apt/archives/tzdata_2008a-0ubuntu0.7.10_all.deb
sudo apt-get remove --purge ifupdown
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ifupdown
```

---

### Post by deadowl on 2008-04-08
As for ifupdown.list:
cat: /var/lib/dpkg/info/ifupdown.list: Input/output error

I don't think that autoremove is a useful feature to actually have me use, other than maybe to stop apt-get from bringing up the "holy cow you ought to remove these!," but because it only bases deletion on dependencies rather than if you actually use the package.

It's pretty clear that removing the tzdata package will do nothing.

What I'm unclear on, however, how can you count on reinstalling the package of all of the apt-get problems since apparently apt-get is using it? Would you try it on your own computer?

---

### Post by Rocket2DMn on 2008-04-08
I'm not in front of my linux machine at the moment, but even if I were I can't reproduce your problem.  If it doesn't let you uninstall/install the package, you can try downloading ifupdown from packages.ubuntu.com - [http://packages.ubuntu.com/gutsy/ifupdown](http://packages.ubuntu.com/gutsy/ifupdown)
then removing and installing it with dpkg
```
sudo dpkg -r --purge ifupdown
cd /path/to/downloaded/deb/file
sudo dpkg -i ifupdown_0.6.8ubuntu8_i386.deb
```
Alternatively, you can try reconfiguring the package since it seems to be a little corrupted (probably because of a filesystem error - no fault of your own).
```
sudo dpkg --configure ifupdown
```

Give that a try (maybe the last command first, otherwise try the uninstall then reinstall).  If this fails, I will have you delete the list file and post my own for you to try and use.

---

### Post by deadowl on 2008-04-10
Alright, finally got a gap of time. For the first one, -r and --purge were conflicting parameters, so I just tried purge. No luck.

$ sudo dpkg --purge ifupdown
dpkg: dependency problems prevent removal of ifupdown:
 ubuntu-minimal depends on ifupdown.
 network-manager depends on ifupdown.
 netbase depends on ifupdown (>= 0.6.4-4.9).
dpkg: error processing ifupdown (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 ifupdown

$ sudo dpkg --configure ifupdown
dpkg: error processing ifupdown (--configure):
 package ifupdown is already installed and configured
Errors were encountered while processing:
 ifupdown

$ sudo dpkg -i ifupdown_0.6.8ubuntu8_i386.deb
Selecting previously deselected package ifupdown.
(Reading database ... dpkg: error processing ifupdown_0.6.8ubuntu8_i386.deb (--install):
 failed in buffer_read(fd): files list for package `ifupdown': Input/output error
Errors were encountered while processing:
 ifupdown_0.6.8ubuntu8_i386.deb
Processing was halted because there were too many errors.

I now wonder if I can dpkg anything at all.

---

### Post by Rocket2DMn on 2008-04-10
OK let's try to replace that list file.  Theoretically, mine should be the same as yours.
```
sudo mv /var/lib/dpkg/info/ifupdown.list /var/lib/dpkg/info/ifupdown.list.old
```
Now that we have moved it to a backup, create the file at that location by opening it and copying and pasting in the content I give you.
```
gksudo gedit /var/lib/dpkg/info/ifupdown.list
```
And put in
```
/.
/usr
/usr/bin
/usr/sbin
/usr/share
/usr/share/doc
/usr/share/doc/ifupdown
/usr/share/doc/ifupdown/examples
/usr/share/doc/ifupdown/examples/bridge
/usr/share/doc/ifupdown/examples/check-mac-address.sh
/usr/share/doc/ifupdown/examples/network-interfaces.gz
/usr/share/doc/ifupdown/examples/get-mac-address.sh
/usr/share/doc/ifupdown/examples/pcmcia-compat.sh
/usr/share/doc/ifupdown/examples/ping-places.sh
/usr/share/doc/ifupdown/examples/generate-interfaces.pl.gz
/usr/share/doc/ifupdown/TODO
/usr/share/doc/ifupdown/copyright
/usr/share/doc/ifupdown/contrib
/usr/share/doc/ifupdown/contrib/ensureifup
/usr/share/doc/ifupdown/contrib/ifstate
/usr/share/doc/ifupdown/contrib/ifstate-check
/usr/share/doc/ifupdown/changelog.gz
/usr/share/doc/ifupdown/changelog.Debian.gz
/usr/share/ifupdown
/usr/share/ifupdown/upgrade-from-0.5.x.pl
/usr/share/ifupdown/upgrade-from-hotplug.pl
/usr/share/man
/usr/share/man/man5
/usr/share/man/man5/interfaces.5.gz
/usr/share/man/man8
/usr/share/man/man8/ifup.8.gz
/etc
/etc/network
/etc/network/if-pre-up.d
/etc/network/if-up.d
/etc/network/if-down.d
/etc/network/if-post-down.d
/etc/init.d
/etc/init.d/loopback
/etc/udev
/etc/udev/rules.d
/etc/udev/rules.d/85-ifupdown.rules
/sbin
/sbin/ifup
/sbin/ifdown
/usr/share/man/man8/ifdown.8.gz
```

IF this fails, it may indicate a problem with your file system, in which case you should boot from the LiveCD and run a check on your filesystem:
```
sudo fsck /dev/sda1
```
where /dev/sda1 is your root partition as declared in /etc/fstab, you can also check fdisk:
```
sudo fdisk -l
``` to see the device identifier.

---

### Post by deadowl on 2008-05-01
I gave up and did a fresh install of Gutsy the other night. The hardware support for my laptop is infinitely better now.

---

