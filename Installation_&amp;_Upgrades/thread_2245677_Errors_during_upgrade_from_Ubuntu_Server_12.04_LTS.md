---
title: "Errors during upgrade from Ubuntu Server 12.04 LTS to 14.04 LTS"
date: 2014-09-25
forum: Installation &amp; Upgrades
---

### Post by hidde2 on 2014-09-25
Hi, I got some errors while upgrading my Ubuntu Server from 12.04 LTS to 14.04 LTS and I am wondering what I should do now.
I followed this guide to do the update: [http://ubuntuserverguide.com/2014/06/how-to-upgrade-ubuntu-server-12-04-to-ubuntu-server-14-04-lts.html](http://ubuntuserverguide.com/2014/06/how-to-upgrade-ubuntu-server-12-04-to-ubuntu-server-14-04-lts.html)

I got the following message:
Errors were encountered while processing:
 python-aptdaemon
 empathy
 gdm
 libgoa-backend-1.0-1:amd64
 dconf-tools
 libpango1.0-0:amd64
 gnome-online-accounts

As I copied it I also accidentally ended the installation, but it seemed like it was at the end.

I am not an expert with linux but I do know how to operate it through shell, but with this I am completely lost.

What should I do?

---

### Post by ibjsb4 on 2014-09-25
Did you make it to 14o4?
```
lsb_release -a
```
Also take a look at your sources list, should be all trusy and no precise.
```
cat /etc/apt/sources.list
```
Try to fix broken packages.
```
sudo apt-get -f install
```

---

### Post by hidde2 on 2014-09-25
Thanks for your reply

lsb_release -a  shows me that I did make it to 14.04

my sources.list does still seem to have some precise entries so I guess I should take those out? 
these:
```
# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted


# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted

```

also when I log in through SSH it shows me the following welcome message:
```

Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.8.0-44-generic x86_64)


 * Documentation:  https://help.ubuntu.com/


 System information disabled due to load higher than 2.0



Your current Hardware Enablement Stack (HWE) is no longer supported
since 2014-08-07.  Security updates for critical parts (kernel
and graphics stack) of your system are no longer available.


For more information, please see:
http://wiki.ubuntu.com/1204_HWE_EOL


To upgrade to a supported (or longer supported) configuration:


* Upgrade from Ubuntu 12.04 LTS to Ubuntu 14.04 LTS by running:
sudo do-release-upgrade


OR


* Install a newer HWE version by running:
sudo apt-get install


and reboot your system.


Last login: Thu Sep 25 14:10:24 2014 from *******

```

should I just delete the precise pangolin entries from the sources.list and then fix broken packages?

---

### Post by ibjsb4 on 2014-09-25
Your sources list is ok.  Those precise entries are commented (#) out.

Looks like you for some reason have ended up on the wrong kernel (3.8.xx).
[https://wiki.ubuntu.com/1204_HWE_EOL#Packages](https://wiki.ubuntu.com/1204_HWE_EOL#Packages)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.Ubuntu_Kernel_Release_Schedule](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.Ubuntu_Kernel_Release_Schedule)

So go with this ..
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
```
Hopefully that will upgrade the kernel.

---

### Post by Patrick_Refondini on 2014-09-26
@ibjsb4 the 'dist-upgrade' was helpful in my situation facing similar problem but with a desktop upgrade.
To force kernel 3.5 to 3.13 upgrade I did a: [INDENT][FONT=courier new]sudo apt-get linux-generic install[/FONT]
[/INDENT]
 then your proposed:[INDENT] [FONT=courier new]    sudo apt-get dist-upgrade[/FONT]
[/INDENT]
 followed by:[INDENT] [FONT=courier new]    sudo apt-get autoremove[/FONT]
[/INDENT]
 which removed packages I suppose related to the 1204_HWE_EOL I was having trouble with.
Then I had a clean situation to perform my `ubuntu-desktop` package successful installation, obviously 
not relevant to this server thread.

---

### Post by hidde2 on 2014-09-26
after running: sudo apt-get dist-upgrade -f
twice, I added the -f because it wouldn't run without it and I hoped it would fix broken packages, and it did fix some of them.
it now shows me the following error if I try to run it again
```



$ sudo apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  consolekit foomatic-db-engine gcalctool gccxml gir1.2-dbusmenu-glib-0.4
  gir1.2-dee-1.0 gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10
  gir1.2-rb-3.0 gir1.2-unity-5.0 gnome-js-common gnome-session-fallback
  html2text launchpad-integration libarchive12 libavahi-ui-gtk3-0 libblas3gf
  libboost-date-time-dev libboost-date-time1.46.1 libboost-dev
  libboost-filesystem-dev libboost-filesystem1.46.1 libboost-graph1.46.1
  libboost-iostreams-dev libboost-iostreams1.46.1 libboost-math-dev
  libboost-math1.46.1 libboost-mpi-dev libboost-mpi-python-dev
  libboost-program-options-dev libboost-program-options1.46.1
  libboost-python-dev libboost-python1.46.1 libboost-regex-dev
  libboost-regex1.46.1 libboost-serialization-dev libboost-serialization1.46.1
  libboost-signals-dev libboost-signals1.46.1 libboost-system-dev
  libboost-system1.46.1 libboost-test1.46.1 libboost-thread-dev
  libboost-thread1.46.1 libboost-wave-dev libboost-wave1.46.1 libcurl3-nss
  libdmapsharing-3.0-2 libebml3 libgcr-3-1 libgd2-xpm libgdu-gtk0 libgdu0
  libgnome-bluetooth8 libgnome-menu2 libgnomekbd7 libgphoto2-2
  libgphoto2-port0 libgpod-common libgpod4 libgweather-3-0 libhpmud0
  libimobiledevice2 libindicate-gtk3 libindicate5 libkpathsea5 liblapack3gf
  liblaunchpad-integration-3.0-1 liblaunchpad-integration-common libllvm3.0
  liblvm2app2.2 libmatroska5 libmpc2 libmusicbrainz3-6 libpam-ck-connector
  libpoppler19 libpthread-stubs0 libqt4-gui libquvi-scripts libquvi7
  librhythmbox-core5 librpmio2 libseed-gtk3-0 libsgutils2-2 libssl-dev
  libssl-doc libtelepathy-logger2 libtiff4 libtorrent-rasterbar6
  libtotem-plparser17 libunique-3.0-0 libusbmuxd1 libxatracker1
  linux-headers-3.8.0-42 linux-headers-3.8.0-42-generic
  linux-image-3.8.0-42-generic linux-signed-image-3.8.0-42-generic
  media-player-info openjdk-6-jdk printer-driver-hpijs printer-driver-min12xxw
  printer-driver-pnm2ppa python-aptdaemon.gtk3widgets python-central
  python-dirspec python-gmenu python-magic python-packagekit
  python-software-properties rhythmbox rhythmbox-data rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-zeitgeist rhythmbox-plugins
  rhythmbox-ubuntuone udisks wwwconfig-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up gdm (3.10.0.1-0ubuntu3) ...
dpkg: error processing package gdm (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-core:
 gnome-core depends on gdm (>= 3.4); however:
  Package gdm is not configured yet.


dpkg: error processing package gnome-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 gdm
 gnome-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
$ uname -r
3.8.0-44-generic

```

I didn't run the sudo apt-get install -f because of the errors I got during the previous command.
What should I do next?

---

### Post by Bashing-om on 2014-09-26
hidde2; Hey !

Does not look too bad.
What returns when you take the package manager's advise and do:
```

sudo dpkg-reconfigure gdm

```

All good now, or more work ? The package manager will hint.

[INDENT][INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-27
Hi, it already looks a lot better than it did before, that's true :p

when I run what you told me it gives me the following error:

```
$ sudo dpkg-reconfigure gdm
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory/usr/sbin/dpkg-reconfigure: gdm is broken or not fully installed

```

Then I tried to reinstall & reconfigure gdm, it gave the following error message:
```
$ sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for gdm:amd64

```

I tried to google that error but I can't really find anything useful, hopefully it means something to you :)

---

### Post by Bashing-om on 2014-09-27
hidde2; Well, shoot !

Let's try this :
```

sudo apt-get install --reinstall gdm

```
Post that complete output. We get the package manager stable, we need next to work on all those left-over files.

Small steps, here ->
[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-27
Something has changed. The system told me I needed to reboot, so I did, now it says I am on a different kernel.
```

$ uname -r
3.13.0-36-generic

```

I also get no more errors when I log in through SSH
```

Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-36-generic x86_64)


 * Documentation:  https://help.ubuntu.com/


  System information as of Sat Sep 27 18:08:29 CEST 2014


  System load: 0.82               Memory usage: 1%   Processes:       88
  Usage of /:  83.9% of 37.73GB   Swap usage:   0%   Users logged in: 0


  Graph this data and manage this system at:
    https://landscape.canonical.com/


0 packages can be updated.
0 updates are security updates.

```

Before I rebooted I ran the command you suggested but that just gave the same error as in my previous post.

what should I run to make sure everything is okay?

---

### Post by Bashing-om on 2014-09-27
hidde2; Things look'n better alla the time.
You are now up up on the latest kernel !

As to gdm .. I have another thought in mind to try. What GUI did you install on your server ? And how is the GUI started ?

[INDENT][INDENT]if at 1st you do not succeed 
[INDENT][INDENT][INDENT]do something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-27
I installed Gnome and it is started through vncserver I believe,

Here is the guide I used to set it up:
```
http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html
```

I hope this is what you mean.

---

### Post by Bashing-om on 2014-09-27
hidde2; Yepper, that helps.

Did you refer back to that link and see the updated instructions for 14.04 ?

Anyway, back to our gdm:
```

sudo apt-get install --reinstall gnome-core

```

Let's see what that does for us.

[INDENT][INDENT]poke at it enough
[INDENT][INDENT][INDENT]something is going to give
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-27
Thanks for the tip on referring back to that link, I completely forgot. I did make the changes suggested there now.

Reinstalling gnome-core gave me an error which looks an awful lot like the error gdm gave me when I tried to reinstall that
```

$ sudo apt-get install --reinstall gnome-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for gnome-core:amd64

```

---

### Post by Bashing-om on 2014-09-27
hidde2; Well !

Something is in common, and the hunt is on;

```

ls -al /var/cache/apt/archives/gnome-core*
ls -al /var/cache/apt/archives/gdm*

```

maybe if the files exist we can try and clean up,  'dpkg -i",  and re-configure  to get them to install ?

[INDENT][INDENT]still poke'n 
[INDENT][INDENT][INDENT][INDENT]see what stirs
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-27
I did what you said and here is the output:

```
$ ls -al /var/cache/apt/archives/gnome-core*
ls: cannot access /var/cache/apt/archives/gnome-core*: No such file or directory

$ ls -al /var/cache/apt/archives/gdm*
ls: cannot access /var/cache/apt/archives/gdm*: No such file or directory

```

looks like nothing is there, I hope that is not bad news!

---

### Post by Bashing-om on 2014-09-27
hidde2; Humm ..

I am surprised, though not distressed, that the files are not there.
It does give us pause to consider.

Let's do this:
```

sudo apt-get update
sudo apt-get clean
sudo apt-get install -fy
sudo dpkg -i /var/cache/apt/archives/*.deb
sudo dpkg --configure -a
sudo apt-get install -fy
sudo apt-get dist-upgrade

```

That cleans out the archive directory, reloads it with the current index files, looks about for broken packages and tries to configure them, and finally apt-get's smart mode for resolving dependency issues and installing new packages.

[INDENT][INDENT][INDENT]maybe now yes
[INDENT][INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-27
I get the following messages:

```

$ sudo apt-get install -fy
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up gdm (3.10.0.1-0ubuntu3) ...
dpkg: error processing package gdm (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-core:
 gnome-core depends on gdm (>= 3.4); however:
  Package gdm is not configured yet.

dpkg: error processing package gnome-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 gdm
 gnome-core
E: Sub-process /usr/bin/dpkg returned an error code (1)



$ sudo dpkg -i /var/cache/apt/archives/*.deb
dpkg: error processing archive /var/cache/apt/archives/*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/*.deb

```

so the broken gdm and gnome-core are still preventing dpkg from getting anywhere?
I didn't run the last couple of commands, should I try them? I take it I will run into the same errors :p

---

### Post by Bashing-om on 2014-09-27
hidde2; Yuk,

This:
> 
cannot access archive: No such file or directory

Bothers me a bunch. Why did it not rebuild ?
Let's look-about:
```

ls -al ls -al /var/cache/apt/

```
does the directory " drwxr-xr-x  3 root root    65536 Sep 27 10:32 archives " exist ?

And now is that directory "archives" populated ?
```

ls -al /var/cache/apt/archives/

``` with hundreds of files ( no need to post that output, just need to know that the directory is populated) .

If the directory is in fact non-existent:
```

sudo apt-get update
sudo apt-get upgrade

```

Now is the 'archives' directory populated ? Maybe time I did some more homework.

[INDENT][INDENT]always something, new to learn
[/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-27
Actually the directory exists but only holds a folder and a lock file, maybe that is the problem?
here is the output:
```

$ ls -al /var/cache/apt/
/var/cache/apt/:
total 80460
drwxr-xr-x  3 root root     4096 Sep 27 21:59 .
drwxr-xr-x 22 root root     4096 Sep 26 19:41 ..
drwxr-xr-x  3 root root   135168 Sep 27 21:54 archives
-rw-r--r--  1 root root 41218463 Sep 27 21:59 pkgcache.bin
-rw-r--r--  1 root root 41060949 Sep 27 21:59 srcpkgcache.bin


$ ls -al /var/cache/apt/archives/
total 144
drwxr-xr-x 3 root root 135168 Sep 27 21:54 .
drwxr-xr-x 3 root root   4096 Sep 27 21:59 ..
-rw-r----- 1 root root      0 Nov  7  2013 lock
drwxr-xr-x 2 root root   4096 Sep 27 16:25 partial

```

---

### Post by Bashing-om on 2014-09-27
hidde2; Yeah !

That is a problem - but only in this instance.
Testing on my system reveals I am out in left field somewhere, the "/var/cache/apt/archives/" directory does not get rebuilt.

That directory not populated is of no relation to the your situation - duh, left field.

This though retains my attention:
> 
gnome-core depends on gdm (>= 3.4); however:
  Package gdm is not configured yet.

We have tried to 'configure' and as well 're-install' them to no effect.
SO, what is installed :
```

dpkg -l gnome-core
dpkg -l gdm

```
and what options are available ?
```

apt-cache policy gnome-core
apt-cache policy gdm

```

As I wonder and puzzle , scratch my head, and think about what to do, oh what to do.

---

### Post by hidde2 on 2014-09-27
that gives me the following output:

```

$ dpkg -l gnome-core
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
iU  gnome-core     1:3.8+4ubunt amd64        GNOME Desktop Environment -- esse


$ dpkg -l gdm
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
iF  gdm            3.10.0.1-0ub amd64        Next generation GNOME Display Man


$ apt-cache policy gnome-core
gnome-core:
  Installed: 1:3.8+4ubuntu3
  Candidate: 1:3.8+4ubuntu3
  Version table:
 *** 1:3.8+4ubuntu3 0
        500 http://nl.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status


$ apt-cache policy gdm
gdm:
  Installed: 3.10.0.1-0ubuntu3
  Candidate: 3.10.0.1-0ubuntu3
  Version table:
 *** 3.10.0.1-0ubuntu3 0
        500 http://nl.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status

```

I hope you can crack the code, if not don't worry too much, I do have backups of the important stuff :)

---

### Post by Bashing-om on 2014-09-27
hidde2; Hey;

We can "crack the code" , we know that there are no conflicting packages installed, we Know we have a round robin in effect here between gdm and gnome-core . Additionally. we know gnome-core is installed but only unpacked, the installation has not completed, We know gdm is installed but only half configured.
Now here is the deal, as this is a fresh upgrade to release 14.04 I have no faith in using any of the old backup files and that DO place some limitations on what we can do.

Let's take a peek at what would happen if we were to remove gdm. We can 'simulate' what will take place, and get an idea of how deep the waters are before we step off into them:
```

sudo apt-get remove -s gdm

``` gets us a bit more information, and perhaps some more help from the package manager, then IF removed, see what happens when we (RE-)install it.. keeping in mind that gnome-core is the big picture.

Worst comes to worst, we can down load the .deb file(s) and force-depends install !

[INDENT][INDENT]ain't gonna let a little thing like this whoop us
[/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-28
Good morning!

I mean't I have backups of the important programs and data that is on the server. If I have to reinstall I probably wouldn't lose anything. But I rather not so I really appreciate the help!

```

$ sudo apt-get remove -s gdm
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  baobab dconf-tools empathy empathy-common folks-common fonts-cantarell
  gir1.2-accountsservice-1.0 gir1.2-gkbd-3.0 gir1.2-mutter-3.0
  gir1.2-polkit-1.0 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0
  gir1.2-xkl-1.0 gjs gnome-backgrounds gnome-contacts gnome-dictionary
  gnome-disk-utility gnome-font-viewer gnome-icon-theme-extras
  gnome-online-accounts gnome-screenshot gnome-search-tool gnome-shell
  gnome-shell-common gnome-system-log gtk2-engines gucharmap libfolks-eds25
  libfolks-telepathy25 libfolks25 libgdict-1.0-6 libgdict-common libmeanwhile1
  libminiupnpc8 libmission-control-plugins0 libpurple-bin libpurple0
  libzephyr4 nautilus-sendto nautilus-sendto-empathy telepathy-gabble
  telepathy-haze telepathy-logger telepathy-mission-control-5 telepathy-salut
  vino
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gdm gnome-core
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
Remv gnome-core [1:3.8+4ubuntu3]
Remv gdm [3.10.0.1-0ubuntu3]

```

Seems like it would uninstall both gdm and gnome-core, is this expected?
And once again a lot of obsolete packages appear, but I guess that is not really a problem :p

---

### Post by Bashing-om on 2014-09-28
hidde2; Yeah !

I do not see a problem with removing gdm. Then (RE-)installing what does look like gnome-core.
Let's see what happens - for real this time:
```

sudo apt-get remove gdm

```
And no, I had not expected removing 'gdm' ( Gnome display manager ) to also remove gnome-core, but I am sure the package manager has it's reasons. To be honest I expected the reverse that removing gnome-core would rip out a bunch.
What is even more surprising; do:
```
 
apt-cache depends gdm
apt-cache rdepends gdm

```
On my system I see no correlation to gnome-core .. hummm ??

we get the system stable, then yeas, let's remove the "automatically installed and are no longer required" packages.

[INDENT][INDENT]I think, I think
[INDENT][INDENT][INDENT][INDENT]the thing yo do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-28
On my system I do get a reverse dependency to gnome-core:
```

$ apt-cache depends gdm
gdm
  Depends: libaccountsservice0
  Depends: libaudit1
  Depends: libc6
  Depends: libcanberra-gtk3-0
  Depends: libcanberra0
  Depends: libgdk-pixbuf2.0-0
  Depends: libgdm1
  Depends: libglib2.0-0
  Depends: libgtk-3-0
  Depends: libpam0g
  Depends: libselinux1
  Depends: libsystemd-daemon0
  Depends: libsystemd-login0
  Depends: libwrap0
  Depends: libx11-6
  Depends: libxau6
  Depends: libxdmcp6
  Depends: libxrandr2
 |Depends: debconf
  Depends: <debconf-2.0>
    cdebconf
    debconf
 |Depends: sysv-rc
  Depends: <file-rc>
  Depends: gir1.2-gdm-1.0
  Depends: adduser
  Depends: libpam-modules
  Depends: libpam-runtime
  Depends: libpam-systemd
  Depends: gnome-session-bin
  Depends: gnome-settings-daemon
  Depends: gnome-shell
  Depends: plymouth
 |Depends: gnome-session
 |Depends: <x-session-manager>
    gnome-session
    gnome-session-flashback
    lxsession
    openbox
    razorqt-session
    ubuntu-session
    xfce4-session
 |Depends: <x-window-manager>
    fvwm1
    mutter
    notion
    ratpoison
    subtle
    9wm
    aewm
    aewm++
    afterstep
    amiwm
    awesome
    blackbox
    clfswm
    compiz
    ctwm
    dwm
    e17
    evilwm
    fluxbox
    flwm
    fvwm
    fvwm-crystal
    herbstluftwm
    i3-wm
    icewm
    icewm-experimental
    icewm-lite
    jwm
    kde-window-manager
    kde-window-manager-active
    larswm
    lwm
    matchbox-window-manager
    metacity
    miwm
    muffin
    mwm:i386
    mwm
    olvwm
    olwm
    openbox
    oroborus
    pekwm
    sapphire
    sawfish
    spectrwm
    stumpwm
    tinywm
    twm
    vtwm
    w9wm
    windowlab
    wm2
    wmaker
    wmii
    xfwm4
  Depends: <x-terminal-emulator>
    kterm
    lxterminal
    vala-terminal
    aterm
    aterm-ml
    eterm
    evilvte
    gnome-terminal
    guake
    konsole
    mlterm
    mlterm-tiny
    mrxvt
    mrxvt-cjk
    mrxvt-mini
    pterm
    roxterm-gtk2
    roxterm-gtk3
    rxvt
    rxvt-ml
    rxvt-unicode
    rxvt-unicode-256color
    rxvt-unicode-lite
    sakura
    stterm
    terminal.app
    terminator
    termit
    xfce4-terminal
    xiterm+thai
    xterm:i386
    xterm
    xvt
  Depends: lsb-base
  Depends: librsvg2-common
  Depends: accountsservice
  Depends: gsettings-desktop-schemas
  Depends: libglib2.0-bin
    libglib2.0-bin:i386
  Depends: dconf-cli
  Depends: dconf-gsettings-backend
  Depends: x11-common
  Depends: x11-xserver-utils
  Suggests: libpam-gnome-keyring
  Suggests: gnome-orca
  Recommends: zenity
    zenity:i386
  Recommends: xserver-xephyr
  Recommends: x11-xkb-utils
  Recommends: xserver-xorg
  Recommends: at-spi2-core
    at-spi2-core:i386
  Recommends: gnome-icon-theme
  Recommends: gnome-icon-theme-symbolic
  Breaks: gnome-control-center
  Breaks: gnome-control-center:i386
  Breaks: gnome-orca
  Breaks: <gnome-orca:i386>
  Breaks: gnome-panel
  Breaks: gnome-panel:i386
  Breaks: gnome-screensaver
  Breaks: gnome-screensaver:i386
  Breaks: gnome-shell
  Breaks: gnome-shell:i386
  Conflicts: gdm:i386


$ apt-cache rdepends gdm
gdm
Reverse Depends:
  gnome-shell:i386
  gnome-shell
  gnome-shell
  gnome-control-center-data
  gnome-control-center-data
  libgdm1:i386
  libgdm1:i386
  gnome-shell:i386
  gdm:i386
  plymouth:i386
  xfswitch-plugin
  ubuntu-mobile-default-settings
  ubuntu-gnome-desktop
  libgdm1
  libgdm1
  gnome-shell
  gnome-shell
  gnome-core
  altos
  plymouth
 |nvidia-prime
  numlockx
  gnome-control-center-data
  gnome-control-center-data

```

after running those commands I have removed gdm and gnome-core was removed too as expected. What now?

---

### Post by Bashing-om on 2014-09-28
hidde2; Ho Kay;

Let's see what happens when we try and put gdm back,
```

sudo apt-get install gdm

```

Will not be shocked if the package manager screams and hollers about gnome-core, but let's see .

[INDENT][INDENT]poke, poke
[INDENT][INDENT][INDENT]'till something gives
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-28
I am installing gdm, it is installing a couple of dependencies but not gnome-core.
Now it gives me a message about multiple display managers installed on the system:
 - gdm
 - lightdm

I'm not sure where lightdm came from, I don't think I have installed it, so I for now I chose gdm as default.

I guess the best option would be to remove lightdm to make sure there are no more conflicts? :)

---

### Post by Bashing-om on 2014-09-28
hidde2; Well !

Naw, let's live with the fact there is lightdm installed, for whatever reason. Get the system stable and then we see about getting rid of whatever is not required.
Let's see what is now, at the point of our concentration:
```

dpkg -l gdm
dpkg -l gnome-core

```
and just for some confirmation of the system's status:
```

sudo dpkg -C

```

[INDENT][INDENT]a stable system
[INDENT][INDENT][INDENT]is a warm fuzzy feeling
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-28
Here are the results:

```

$ dpkg -l gdm
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  gdm            3.10.0.1-0ub amd64        Next generation GNOME Display Man


$ dpkg -l gnome-core
dpkg-query: no packages found matching gnome-core


$ sudo dpkg -C
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 webmin               web-based administration interface for Unix systems
 libjson0:amd64       JSON manipulation library (transitional package)

```

---

### Post by Bashing-om on 2014-09-28
hidde2; Well, looking better, no ?

Let's install gnome-core !
```

sudo apt-get install gnome-core

```

(ain't I glad we looked for other problems):
> 
$ sudo dpkg -C
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 webmin               web-based administration interface for Unix systems
 libjson0:amd64       JSON manipulation library (transitional package)

I see  libjson0 breakage a lot, in situations like this. Now, if I were really smart, I would know why it gets broke.

IF gnome-core installs with no problems, then let's do:
```

sudo apt-get install --reinstall webmin
sudo apt-get install --reinstall libjson0:amd64

```

[INDENT][INDENT][INDENT]maybe yes !
[/INDENT][/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-28
I think it is looking better the only problems I see so far are webmin, libjson0 and apache2 which isn't working. But I will look into apache when the system is stable :p

gnome-core installed without any problems, yay!

libjson0:amd64 also installed without problems.
for webmin I had to add the right depositories to my sources.list but after doing so that also reinstalled without any warnings or errors.

So far so good! What shall we throw at it next?

---

### Post by Bashing-om on 2014-09-28
hidde2; Hey hey !

Good news ..

Let's check and clean up and see just how stable we are:
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,A dist-upgrade will install new dependencies for packages already installed and may remove packages if they are no longer needed. This will not bring you to a new release of ubuntu. 
sudo apt-get dist-upgrade
sudo apt-get -f install
dpkg --configure -a
sudo dpkg --configure -a

```
NOW, if all the sweating is over with, lets deal with lightdm.

[INDENT][INDENT]see, where there is a will
[INDENT][INDENT][INDENT][INDENT]there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-28
All of those commands ran without errors or warnings. Nothing had to be updated or removed.

Looking so much better already, you are a life saver! :D

---

### Post by Bashing-om on 2014-09-28
hidde2; Hey ...

Wonders never cease.

As this is a server, I want to do one further check .. space constraints and what is in the /boot partition.
```

df -h
df -i
ls -al /boot
dpkg -l | grep linux-

```

I bet though

[INDENT][INDENT][INDENT]we are home free and
[INDENT][INDENT][INDENT][INDENT]shining like a new penny
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-29
Space is always a problem on this server, I had to use an old hdd I had lying around. I am already planning on investing in a new primary HDD for it as the current one is just too small. I still have to save up a little money to get it though.

here are the results:
```

$ df -h
Filesystem                          Size  Used Avail Use% Mounted on
/dev/mapper/TheBurrow--vg-root       38G   32G  4.0G  89% /
none                                4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                3.6G  4.0K  3.6G   1% /dev
tmpfs                               737M  1.9M  736M   1% /run
none                                5.0M     0  5.0M   0% /run/lock
none                                3.6G  8.0K  3.6G   1% /run/shm
none                                100M   20K  100M   1% /run/user
/dev/sda2                           229M  106M  112M  49% /boot
/dev/mapper/TheBurrow--vg-UserData   68G   24G   42G  36% /media/UserData
/dev/sda1                           188M  3.4M  184M   2% /boot/efi


$ df -i
Filesystem                           Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/TheBurrow--vg-root      2523136 863354  1659782   35% /
none                                 943277     11   943266    1% /sys/fs/cgroup
udev                                 940484    520   939964    1% /dev
tmpfs                                943277    597   942680    1% /run
none                                 943277      6   943271    1% /run/lock
none                                 943277      3   943274    1% /run/shm
none                                 943277      9   943268    1% /run/user
/dev/sda2                            124992    308   124684    1% /boot
/dev/mapper/TheBurrow--vg-UserData  4521984    385  4521599    1% /media/UserData
/dev/sda1                                 0      0        0     - /boot/efi


$ ls -al /boot
total 99949
drwxr-xr-x  5 root root     2048 Sep 26 20:03 .
drwxr-xr-x 25 root root     4096 Sep 26 19:54 ..
-rw-r--r--  1 root root  1163858 Sep  4 00:24 abi-3.13.0-36-generic
-rw-r--r--  1 root root   921104 Jul  4 23:31 abi-3.8.0-42-generic
-rw-r--r--  1 root root   921155 Jul 15 06:22 abi-3.8.0-44-generic
-rw-r--r--  1 root root   165671 Sep  4 00:24 config-3.13.0-36-generic
-rw-r--r--  1 root root   154959 Jul  4 23:31 config-3.8.0-42-generic
-rw-r--r--  1 root root   154959 Jul 15 06:22 config-3.8.0-44-generic
drwxr-xr-x  3 root root      512 Jan  1  1970 efi
drwxr-xr-x  5 root root     4096 Sep 26 19:58 grub
-rw-r--r--  1 root root 19973658 Sep 26 20:03 initrd.img-3.13.0-36-generic
-rw-r--r--  1 root root 17101865 Jul 18 01:29 initrd.img-3.8.0-42-generic
-rw-r--r--  1 root root 17557006 Sep 25 14:01 initrd.img-3.8.0-44-generic
drwxr-xr-x  2 root root    12288 Nov  7  2013 lost+found
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3386479 Sep  4 00:24 System.map-3.13.0-36-generic
-rw-------  1 root root  3196246 Jul  4 23:31 System.map-3.8.0-42-generic
-rw-------  1 root root  3196521 Jul 15 06:22 System.map-3.8.0-44-generic
-rw-------  1 root root  5806848 Sep  4 00:24 vmlinuz-3.13.0-36-generic
-rw-------  1 root root  5808760 Sep 26 19:58 vmlinuz-3.13.0-36-generic.efi.signed
-rw-------  1 root root  5460784 Jul  4 23:31 vmlinuz-3.8.0-42-generic
-rw-------  1 root root  5462712 Jul 18 01:30 vmlinuz-3.8.0-42-generic.efi.signed
-rw-------  1 root root  5461488 Jul 15 06:22 vmlinuz-3.8.0-44-generic
-rw-------  1 root root  5463416 Jul 18 01:31 vmlinuz-3.8.0-44-generic.efi.signed


$ dpkg -l | grep linux-
ii  linux-firmware                            1.127.7                                             all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-36                   3.13.0-36.63                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic           3.13.0-36.63                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-42                    3.8.0-42.63~precise1                                all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-42-generic            3.8.0-42.63~precise1                                amd64        Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-3.8.0-44                    3.8.0-44.66~precise1                                all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-44-generic            3.8.0-44.66~precise1                                amd64        Linux kernel headers for version 3.8.0 on 64 bit x86 SMP
ii  linux-headers-generic                     3.13.0.36.43                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-raring          3.13.0.36.43                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-36-generic             3.13.0-36.63                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-32-generic              3.8.0-32.47~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-33-generic              3.8.0-33.48~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-42-generic              3.8.0-42.63~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-44-generic              3.8.0-44.66~precise1                                amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic       3.13.0-36.63                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                      3.13.0-36.63                                        amd64        Linux Kernel Headers for development
ii  linux-signed-generic                      3.13.0.36.43                                        amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-generic-lts-raring           3.13.0.36.43                                        amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-3.13.0-36-generic      3.13.0-36.63                                        amd64        Signed kernel image generic
rc  linux-signed-image-3.8.0-32-generic       3.8.0-32.47~precise1                                amd64        Signed kernel image generic
rc  linux-signed-image-3.8.0-33-generic       3.8.0-33.48~precise1                                amd64        Signed kernel image generic
ii  linux-signed-image-3.8.0-42-generic       3.8.0-42.63~precise1                                amd64        Signed kernel image generic
ii  linux-signed-image-3.8.0-44-generic       3.8.0-44.66~precise1                                amd64        Signed kernel image generic
ii  linux-signed-image-generic                3.13.0.36.43                                        amd64        Signed Generic Linux kernel image
ii  linux-signed-image-generic-lts-raring     3.13.0.36.43                                        amd64        Signed Generic Linux kernel image
ii  linux-sound-base                          1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems

```

---

### Post by hidde2 on 2014-09-29
Just found another problem, I logged in through vnc (the vncserver and gdm are working great again!) just to clear out some space in case I needed it.

Now strangely I get an error when I try to open the Computer and Trash locations.
I will attach screenshots of the error messages.

[ATTACH=CONFIG]256800[/ATTACH][ATTACH=CONFIG]256799[/ATTACH]

I can use the filemanager to browse to the corresponding locations ("/" and "~/.local/share/Trash/files")
But I can't use the links under "Places"

I'm not too worried about this though I wouldn't know what would cause it. Maybe something wrong with permissions?

Anyway, I will leave this to rest for now until the system is stable, I will then start googling all the little kinks I find until everything works again :)

---

### Post by Bashing-om on 2014-09-29
hidde2; Hey, hey ;

I like what I see, Glad you are aware that the VG for '/' is too small, and to watch it !
As to the "the links under "Places"" ; I would hazard to guess as a broken symlink issue. Let's start another thread on that issue as I propose we close this thread solved - top of post -> thread tools.

Solved by finally realizing that gdm had to be replaced.

[INDENT]we did pick our selves up, brush off
[INDENT][INDENT][INDENT]now we get dirty in another issue
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-29
Hey Bashing-om, 

I just want to say thank you so much for helping me this far, it is much appreciated!

I will mark this thread as solved so we can dive into the next adventure :p

---

### Post by Bashing-om on 2014-09-29
hidde2; Outstanding !

It has been a pleasure, and I look forward to that next adventure.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]all things are possible
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by hidde2 on 2014-09-29
the new adventure is started here: [http://ubuntuforums.org/showthread.php?t=2246256](http://ubuntuforums.org/showthread.php?t=2246256) :p

also I have almost completely fixed apache2, it looks like I only have to tackle one last problem; installing xml2enc. I'm sure I will figure that one out soon enough :D

---

