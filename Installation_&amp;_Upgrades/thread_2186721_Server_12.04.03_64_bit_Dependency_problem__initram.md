---
title: "Server 12.04.03 64 bit Dependency problem  initramfs-tool and  initramfs-tool-bin"
date: 2013-11-08
forum: Installation &amp; Upgrades
---

### Post by nlinecomputers on 2013-11-08
Note this problem is very similar to this thread:   [http://ubuntuforums.org/showthread.php?t=2175574](http://ubuntuforums.org/showthread.php?t=2175574)

I have tried much in that thread without much success.

My server at my church ran out of hard drive space on root because the backup, flexbackup, was backing up to /media/usb which was not mounted.  The server filled up and crashed.  I have cleared out the backup files and everything seems to be running normally.   The server is just a simple samba file server that also runs webmin and no-ip.   Very basic no GUI installed all command line.

When I try to update the system I get the following:
```
Hit http://us.archive.ubuntu.com precise Release.gpg
Hit http://us.archive.ubuntu.com precise-updates Release.gpg
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://us.archive.ubuntu.com precise Release
Hit http://security.ubuntu.com precise-security Release
Hit http://us.archive.ubuntu.com precise-updates Release
Hit http://security.ubuntu.com precise-security/main Sources
Hit http://us.archive.ubuntu.com precise/main Sources
Hit http://us.archive.ubuntu.com precise/restricted Sources
Hit http://us.archive.ubuntu.com precise/main amd64 Packages
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise/main i386 Packages
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted Sources
Hit http://security.ubuntu.com precise-security/universe Sources
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/main Sources
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Reading package lists...Done
```
```
nathan@abraham:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.1.1~) but 0.99ubuntu13.3 is installed
E: Unmet dependencies. Try using -f.
nathan@abraham:~$

```

Thanks and let me know what other info you need me to provide.

---

### Post by TheFu on 2013-11-08
Did you try [B]
sudo apt-get -f install[/B]
What resulted?

Is /boot on a different partition? Is that partition full?

---

### Post by nlinecomputers on 2013-11-08
Yes.  I tried that.  I get this:

```
nathan@abraham:~$ sudo apt-get -f install
[sudo] password for nathan:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  initramfs-tools
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
5 not fully installed or removed.
Need to get 0 B/50.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.3.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of mdadm:
 mdadm depends on initramfs-tools (>= 0.85eubuntu24); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing mdadm (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of plymouth:
 plymouth depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing plymouth (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
 dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-text:
 plymouth-theme-ubuntu-text depends on plymouth; however:
  Package plymouth is not configured yet.
dpkg: error processing plymouth-theme-ubuntu-text (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of udev:
 udev depends on initramfs-tools (>= 0.92bubuntu63); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing udev (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 initramfs-tools
 mdadm
 plymouth
 plymouth-theme-ubuntu-text
 udev
E: Sub-process /usr/bin/dpkg returned an error code (1)
nathan@abraham:~$

```

/boot is on / and did run out of space when / was filled but that has been corrected. (But who knows if anything was damaged....)

Right now a df -h reports this:
Filesystem      Size  Used Avail Use% Mounted on
/dev/md0        184G   40G  135G  23% /
udev            989M  4.0K  989M   1% /dev
tmpfs           400M  1.2M  398M   1% /run
none            5.0M  4.0K  5.0M   1% /run/lock
none            998M     0  998M   0% /run/shm
/dev/md3        1.3T   47G  1.2T   4% /data
/dev/md1        367G  225M  348G   1% /home

---

### Post by TheFu on 2013-11-08
I would attempt to --reinstall these :
initramfs-tools
 mdadm
 plymouth
 plymouth-theme-ubuntu-text
 udev

If it does not work, I would punt and restore from the prior day's backup - at least for the system files.

---

### Post by nlinecomputers on 2013-11-08
Any attempt to remove the packages gets the same errors.

There are no backups.  The backup procedure wasn't working correctly which is what caused the problem to begin with.   External drive never mounted so the backups were being written off of root and not on a mounted drive.   Drive filled up and crashed before backup was completed.   Gotta fix this or re-install everything.

---

### Post by TheFu on 2013-11-08
Not using incremental backups? Ouch.

Before you try to start over, let me know.  We should be able to create a reasonable backup that will make life easier during restore, plus the /home being on a different partition is good.

To give you an idea about a quick backup, read this: [http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) - pay special attention to the dpkg commands.  For a pure samba server, if you get the list of packages, /etc/ and have the data shared ... that should be all you need.  As long as no software was installed outside the repos.

Less time on mirrors/RAID and more time on backups is needed, IHMO.  I've totally screwed up a few things like this over the years. The lessons that taught me the most were my deployment failures. BTW, also had a backup area not mount, but saw it the same day of the failures thanks to limited / storage.  Modified the backup script to verify that partition was mounted before continuing. .... here's the important part of that script.
```
# Need to verify that the backup partition is mounted
MNT=`/bin/df | grep -c $MNT_POINT`
if [ "X0" == "X$MNT" ] ; then

   echo "ERROR: Mount point not mounted: $MNT_POINT $TARGET_DIR "
   exit 1;
fi
```

---

### Post by nlinecomputers on 2013-11-08
Dude I know HOW to do a backup. Been using Flexbackup for years or more then one server.   We had a hardware failure of a USB port.  So it isn't sensing the drive being plugged up.   I don't want to get into a backup issue here.  It is off topic.   Please stay on the topic.

---

### Post by pyry-9 on 2013-11-16
I had the exact same problem after running out of space in /. Tried these tips with no luck, but stumbled upon some (seemingly unrelated) hint suggesting reinstalling package manually with apt-get download initramfs-tools && dpkg -i initramfs-tools_0.99ubuntu13.3_all.deb. In my case, this in turn failed with message about unmet dependency udev. Then, after I installed udev with apt-get install udev I was able to install all the broken packages with apt-get -f install.

So, I'm not sure if my solution is valid for anyone else or if it is even recommended or considered good practice, but this procedure did the trick for me:
[FONT=courier new]
(as root:)
apt-get download initramfs-tools
dpkg -i initramfs-tools_0.99ubuntu13.3_all.deb (depending on the downloaded package filename)
[/FONT]
Take a look at the dpkg output to find the potential unmet dependency, for me it was udev. Then:

[FONT=courier new]apt-get install udev
apt-get -f install
apt-get upgrade

[/FONT]Hope this helps.
Pyry

---

### Post by nlinecomputers on 2013-11-16
> **pyry-9 said:**
> I had the exact same problem after running out of space in /. Tried these tips with no luck, but stumbled upon some (seemingly unrelated) hint suggesting reinstalling package manually with apt-get download initramfs-tools && dpkg -i initramfs-tools_0.99ubuntu13.3_all.deb. In my case, this in turn failed with message about unmet dependency udev. Then, after I installed udev with apt-get install udev I was able to install all the broken packages with apt-get -f install.

So, I'm not sure if my solution is valid for anyone else or if it is even recommended or considered good practice, but this procedure did the trick for me:
[FONT=courier new]
(as root:)
apt-get download initramfs-tools
dpkg -i initramfs-tools_0.99ubuntu13.3_all.deb (depending on the downloaded package filename)
[/FONT]
Take a look at the dpkg output to find the potential unmet dependency, for me it was udev. Then:

[FONT=courier new]apt-get install udev
apt-get -f install
apt-get upgrade

[/FONT]Hope this helps.
Pyry

DING!!!DING!!!  WE HAVE A WINNER!
I was literally preparing to travel on site and wipe and reinstall that server this morning.  I SSHed in and that has fixed it as far as I can see.  I've got a few other minor tweaks to fix onsite but at least now it will update properly and I don't have to nuke and pave.

Mark this solved!

---

