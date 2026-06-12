---
title: "Still need advice !!!!!!"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by KegHead on 2009-10-22
HELP !!!

jim@jim-laptop:~$ sudo apt-get upgrade a
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-headers-2.6.31-14
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B/9,526kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 208263 files and directories currently installed.)
Preparing to replace linux-headers-2.6.31-14 2.6.31-14.47 (using .../linux-headers-2.6.31-14_2.6.31-14.48_all.deb) ...
Unpacking replacement linux-headers-2.6.31-14 ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.31-14_2.6.31-14.48_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-2.6.31-14/include/sound/Kbuild.dpkg-new' (while processing `./usr/src/linux-headers-2.6.31-14/include/sound/Kbuild'): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.31-14_2.6.31-14.48_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jim@jim-laptop:~$

---

### Post by viralmeme on 2009-10-22
> **KegHead said:**
> unable to create `/usr/src/ ..

Are you running out of space ?

$df - kTh

---

### Post by KegHead on 2009-10-22
No,

I have 9gb.

KegHead

---

### Post by philinux on 2009-10-22
Do whats been said above in a terminal.

```
df -h
```

---

### Post by philinux on 2009-10-22
Do whats been said above in a terminal.

```
df -kTh
```

---

### Post by KegHead on 2009-10-22
jim@jim-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  4.0G  8.9G  31% /
udev                 1003M  256K 1002M   1% /dev
none                 1003M  1.5M 1001M   1% /dev/shm
none                 1003M   92K 1003M   1% /var/run
none                 1003M     0 1003M   0% /var/lock
none                 1003M     0 1003M   0% /lib/init/rw
jim@jim-laptop:~$ 

thanks for your help!

KegHead

---

### Post by KegHead on 2009-10-22
jim@jim-laptop:~$ df -kTh
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4     14G  4.0G  8.9G  31% /
udev         tmpfs   1003M  256K 1002M   1% /dev
none         tmpfs   1003M  1.5M 1001M   1% /dev/shm
none         tmpfs   1003M   92K 1003M   1% /var/run
none         tmpfs   1003M     0 1003M   0% /var/lock
none         tmpfs   1003M     0 1003M   0% /lib/init/rw
jim@jim-laptop:~$

---

### Post by philinux on 2009-10-22
Nothing wrong with disk space. Not sure how to cure your problem though. Having a think.

---

### Post by KegHead on 2009-10-22
hi!

thanks!

BTW-a family friend played for chelsea.

KegHead

---

### Post by kansasnoob on 2009-10-22
My thought:

First of all verify that you're either running a mutli-boot with another *buntu or you have a *buntu Live CD so you can use this:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

to mount and chroot your *buntu if something goes wrong.

Second (only if the first step is verified) I'd run the command:

```
sudo apt-get update && sudo apt-get -f install
```

But [COLOR="Red"]DO NOT[/COLOR] say yes (y) or run any suggested commands until you've posted the full output from that here!

Also post the output of:

```
df -H
```

and:

```
cat /etc/issue
```

```

```

---

### Post by KegHead on 2009-10-22
Hi!

Please see attached.

KegHead

jim@jim-laptop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               15G   4.2G   9.7G  31% /
udev                   1.1G   263k   1.1G   1% /dev
none                   1.1G   1.5M   1.1G   1% /dev/shm
none                   1.1G    95k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
jim@jim-laptop:~$ cat /etc/issue
Ubuntu 9.10 \n \l

---

### Post by philinux on 2009-10-22
You aint done this yet as kansasnoob asked.

```
sudo apt-get update && sudo apt-get -f install
```

> But DO NOT say yes (y) or run any suggested commands until you've posted the full output from that here!


Make sure you hit the N key and post the result.

---

### Post by KegHead on 2009-10-22
Hi!

Sorry!

jim@jim-laptop:~$ sudo apt-get update && sudo apt-get -f install
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [654B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
Fetched 3,383B in 2s (1,603B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
8 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up google-chrome-unstable (4.0.223.5-r29497) ...

Setting up linux-restricted-modules-2.6.28-15-generic (2.6.28-15.20) ...
Bus error (core dumped)
dpkg: error processing linux-restricted-modules-2.6.28-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 135
Setting up python-problem-report (1.9.3-0ubuntu3) ...
Compiling /usr/lib/python2.5/site-packages/problem_report.py ...
Sorry: LookupError: ("no codec search functions registered: can't find encoding",)
pycentral: pycentral pkginstall: error byte-compiling files (1)
pycentral pkginstall: error byte-compiling files (1)
dpkg: error processing python-problem-report (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python-apport (>= 0.120); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python-apport (>= 0.80); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leavingNo apport report written because the error message indicates its a followup error from a previous failure.
                                                        No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
  No apport report written because MaxReports is reached already
                                                                 unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on python-apport; however:
  Package python-apport is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.0.2-0ubuntu1); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
Processing triggers for menu ...
Errors were encountered while processing:
 linux-restricted-modules-2.6.28-15-generic
 python-problem-report
 python-apport
 apport
 apport-gtk
 ubuntuone-client
 ubuntuone-client-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
jim@jim-laptop:~$

---

### Post by nanog on 2009-10-22
I do not recommend running apt-get install -f yet:


Please try deleting:

```
sudo rm /var/cache/apt/archives/linux-headers-2.6.31-14_2.6.31-14.48_all.deb
```


and purging this package linux-headers-2.6.31-14 2.6.31-14.47 


```
dpkg --purge linux-headers-2.6.31-14
```
or 
```
sudo apt-get --purge linux-headers-2.6.31-14
```
 

Only after you try this should you attempt to force the install.

```
sudo dpkg -i --force-all linux-headers-2.6.31-14
```

Its possible that you did not notice a failed install or that the  cached headers package is corrupt (it happens).

---

### Post by nanog on 2009-10-22
It looks like you have some more package borkage. Its generally not a good idea to "apt-get install -f" unless you know why your package broke.


Before you do anything else try this:

> sudo dpkg --configure -a

You can also try fixing broken packages in synaptic or by trying this:

> sudo dpkg-reconfigure packagename

If the above does not work you can try purging and updating failed packages or hacking /var/lib/dpkg (probably better to reinstall if you get to that point).

---

### Post by KegHead on 2009-10-22
Results

jim@jim-laptop:~$ sudo dpkg --configure -a
Setting up linux-restricted-modules-2.6.28-15-generic (2.6.28-15.20) ...
Bus error (core dumped)
dpkg: error processing linux-restricted-modules-2.6.28-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 135
Setting up python-problem-report (1.9.3-0ubuntu3) ...
Compiling /usr/lib/python2.5/site-packages/problem_report.py ...
Sorry: LookupError: ("no codec search functions registered: can't find encoding",)
pycentral: pycentral pkginstall: error byte-compiling files (1)
pycentral pkginstall: error byte-compiling files (1)
dpkg: error processing python-problem-report (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python-apport (>= 0.120); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python-apport (>= 0.80); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on python-apport; however:
  Package python-apport is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.0.2-0ubuntu1); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-restricted-modules-2.6.28-15-generic
 python-problem-report
 python-apport
 apport
 apport-gtk
 ubuntuone-client
 ubuntuone-client-gnome
jim@jim-laptop:~$

---

### Post by kansasnoob on 2009-10-22
Did anyone else notice this:

> Setting up linux-restricted-modules-2.6.28-15-generic (2.6.28-15.20) ...
Bus error (core dumped)
dpkg: error processing linux-restricted-modules-2.6.28-15-generic (--configure):

Yes, it says **2.6.28-15**.

This is from his output 9.10 and I think we're all on **2.6.31-14-generic**.

Not sure what to do, but I'm sure that's a large part of the problem!

---

### Post by kansasnoob on 2009-10-22
I think we should see what kernel you're actually running right now:

```
uname -a
```

And since it's clearly an upgrade lets see some things about grub:

```
grub-install -v
```

and:

```
ls ~ /boot/grub
```

---

### Post by viralmeme on 2009-10-22
[http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usrbindpkg-returned-an-error-code-1-171107/)

---

### Post by KegHead on 2009-10-22
Here you go!

jim@jim-laptop:~$ grub-install -v
grub-install (GNU GRUB 0.97)
jim@jim-laptop:~$ uname -a
Linux jim-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
jim@jim-laptop:~$  ~ /boot/grub
bash: /home/jim: is a directory
jim@jim-laptop:~$

---

### Post by nanog on 2009-10-23
> **kansasnoob said:**
> Did anyone else notice this:



Yes, it says **2.6.28-15**.

This is from his output 9.10 and I think we're all on **2.6.31-14-generic**.

Not sure what to do, but I'm sure that's a large part of the problem!

The first problem reported was a dpkg failure on a headers install. They should have purged the package and deleted it from cache and tried reinstalling instead they forced a bad package...

I think you need to purge all remnants of 2.6.31 and delete the cached debs (/var/cache/apt/archives/). Then try reinstalling this kernel (use synaptic to get all the necessary bits).  Following this I would try to repair any broken packages in synaptic (look around the menu items) and retry sudo dpkg --configure -a.  

You might want to do this while chrooted (see link in post above).

If none of this works (and you are really desperate) you can hack at  dpkg to manually "remove" the problematic packages from dpkg oackage lists. This bypasses apt and *could* leave stray libraries/binaries that compromise your system at a later time.

---

### Post by KegHead on 2009-10-23
Hi!

Thanks for all of your replies.

There has to be a very simple solution.

Please advise!

KegHead

---

### Post by vinutux on 2009-10-23
**[COLOR="red"]Do at your own risk...................[/COLOR]**


1. press Alt + F2 and type &#8220;gksu nautilus&#8221; (without quatos)

2. Type password &#8230;it open super user enabled nautilus

3. go to /var/lib/dpkg/info in nautilus

4. Delete all files related your broken package (if your broken package is cgmail delete all package related to cgmail)

5. done &#8230;.. open synaptic now and remove broken package

NB : [COLOR="Red"]before deleting any system file just backup it.[/COLOR]

From here.... [for post installation script errors]**[http://ubuntuxpress.wordpress.com/2009/10/07/post-installation-script-returned-error/]("http://ubuntuxpress.wordpress.com/2009/10/07/post-installation-script-returned-error/")**

---

### Post by kansasnoob on 2009-10-23
> **nanog said:**
> The first problem reported was a dpkg failure on a headers install. They should have purged the package and deleted it from cache and tried reinstalling instead they forced a bad package...

I think you need to purge all remnants of 2.6.31 and delete the cached debs (/var/cache/apt/archives/). Then try reinstalling this kernel (use synaptic to get all the necessary bits).  Following this I would try to repair any broken packages in synaptic (look around the menu items) and retry sudo dpkg --configure -a.  

You might want to do this while chrooted (see link in post above).

If none of this works (and you are really desperate) you can hack at  dpkg to manually "remove" the problematic packages from dpkg oackage lists. This bypasses apt and *could* leave stray libraries/binaries that compromise your system at a later time.

Thank you.

But I still don't quite understand. Yes, you can color me dense I guess, but if I don't understand something I've found the only way to learn is ask.

I understand mounting and chrooting:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

I also somewhat understand what you're saying here:

[http://ubuntuforums.org/showpost.php?p=8146943&postcount=15](http://ubuntuforums.org/showpost.php?p=8146943&postcount=15)

and here:

[http://ubuntuforums.org/showpost.php?p=8146842&postcount=14](http://ubuntuforums.org/showpost.php?p=8146842&postcount=14)

But I'm thinking KegHead needs specifics (I've been at this for about 22 months and I still get confused).

So I'm thinking:

#1. The computer is in an unstable state so look into how much data needs backed up and options to create a full backup because a reinstall might be needed.

#2. This was obviously an upgrade from Jaunty, so does KegHead have a Live CD and if so what version?

#3. Does KegHead know how to mount and chroot?

#4. I'm somewhat unfamiliar with using dpkg (I can usually figure out what I need to do by referring to the dpkg manual) but I'm thinking the equivalent of:

```
sudo apt-get install --reinstall linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic linux-image-2.6.31-14-generic linux-restricted-modules-2.6.31-14-generic

```

#5. We'll still have to deal with this:

> Errors were encountered while processing:
linux-restricted-modules-2.6.28-15-generic
python-problem-report
python-apport
apport
apport-gtk
ubuntuone-client
ubuntuone-client-gnome

So, can we help KegHead out in detail?

---

### Post by xebian on 2009-10-23
Get rid of the restricted-modules.  It's a relic of jaunty.

---

### Post by kansasnoob on 2009-10-23
> **xebian said:**
> Get rid of the restricted-modules.  It's a relic of jaunty.

Easy answer but if you read everything that may leave the OP unable to boot!

How about some detailed instructions?

---

### Post by KegHead on 2009-10-24
Hi Kansas noob,

see the attached.

KegHead

jim@jim-laptop:~$ sudo apt-get install --reinstall linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic linux-image-2.6.31-14-generic linux-restricted-modules-2.6.31-14-generic
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules-2.6.31-14-generic
jim@jim-laptop:~$

---

### Post by kansasnoob on 2009-10-24
> **KegHead said:**
> Hi Kansas noob,

see the attached.

KegHead

jim@jim-laptop:~$ sudo apt-get install --reinstall linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic linux-image-2.6.31-14-generic linux-restricted-modules-2.6.31-14-generic
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules-2.6.31-14-generic
jim@jim-laptop:~$

Arrgh, I had not intended for you to run that command, I was just asking nanog questions. I should have tossed in a warning in red I guess, but we are where we are now.

**[COLOR="Red"]Warning: I'm just gathering info, don't run any more commands unless I (or someone else) explicitly tells you to![/COLOR]**

Anyway I hadn't parsed that command for accuracy since I was just asking questions, but the proper command would have been:

"sudo apt-get install --reinstall linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic linux-image-2.6.31-14-generic"

The "linux-restricted-modules" package has been deprecated.

Anyway before we proceed at least answer these three questions (from my previous post):

> #1. The computer is in an unstable state so look into how much data needs backed up and options to create a full backup because a reinstall might be needed.

#2. This was obviously an upgrade from Jaunty, so does KegHead have a Live CD and if so what version?

#3. Does KegHead know how to mount and chroot

Also **do run these commands now:**

```
sudo fdisk -l
```

(BTW that's a lower case L.)

and lets see what this shows now:

```
sudo dpkg --configure -a
```

I need to see the output of those two commands before proceeding any further.

---

### Post by KegHead on 2009-10-24
Hi!

jim@jim-laptop:~$ sudo fdisk -l
[sudo] password for jim: 

Disk /dev/sda: 15.4 GB, 15434883072 bytes
255 heads, 63 sectors/track, 1876 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10bfb69a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1792    14394208+  83  Linux
/dev/sda2            1793        1876      674730    5  Extended
/dev/sda5            1793        1876      674698+  82  Linux swap / Solaris
jim@jim-laptop:~$ sudo dpkg --configure -a
Setting up libgnome-desktop-2-11 (1:2.28.1-0ubuntu2) ...

Setting up libgdict-1.0-6 (2.28.1-0ubuntu1) ...

Setting up tzdata-java (2009o-1ubuntu2) ...
Setting up grub-common (1.97~beta4-1ubuntu3) ...

Setting up dbus (1.2.16-0ubuntu9) ...
Installing new version of config file /etc/dbus-1/system.conf ...
The system user `messagebus' already exists. Exiting.
start: Job is already running: dbus

Setting up linux-restricted-modules-2.6.28-15-generic (2.6.28-15.20) ...
Bus error (core dumped)
dpkg: error processing linux-restricted-modules-2.6.28-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 135
Setting up python-problem-report (1.9.3-0ubuntu4) ...
Compiling /usr/lib/python2.5/site-packages/problem_report.py ...
Sorry: LookupError: ("no codec search functions registered: can't find encoding",)
pycentral: pycentral pkginstall: error byte-compiling files (1)
pycentral pkginstall: error byte-compiling files (1)
dpkg: error processing python-problem-report (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up dbus-x11 (1.2.16-0ubuntu9) ...
Setting up gnome-utils (2.28.1-0ubuntu1) ...

Setting up gnome-desktop-data (1:2.28.1-0ubuntu2) ...
Setting up google-chrome-unstable (4.0.223.11-r29900) ...

Setting up language-selector-common (0.4.18) ...

Setting up gnome-about (1:2.28.1-0ubuntu2) ...
Setting up language-selector (0.4.18) ...

dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python-apport (>= 0.120); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python-apport (>= 0.80); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on python-apport; however:
  Package python-apport is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.0.2-0ubuntu1); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
Setting up language-pack-en (1:9.10+20091022) ...
Setting up language-pack-en-base (1:9.10+20091022) ...
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... cannot open locale definition file `da_DK': No such file or directory
failed
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... cannot open locale definition file `hi_IN': No such file or directory
failed
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... cannot open locale definition file `tl_PH': No such file or directory
failed
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.

Setting up language-pack-gnome-en (1:9.10+20091022) ...
Setting up language-pack-gnome-en-base (1:9.10+20091022) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 linux-restricted-modules-2.6.28-15-generic
 python-problem-report
 python-apport
 apport
 apport-gtk
 ubuntuone-client
 ubuntuone-client-gnome
jim@jim-laptop:~$ 

I do not have a live cd- done via terminal.
 i don,t know how to mount ect.

KegHead

---

### Post by xebian on 2009-10-24
If you think back for a moment, the linux-restricted modules is from jaunty and no longer used in karmic.  So why bother with it, and because it's preventing you from moving on, get rid of it.

Plus you would be using a kernel version of "31-14" so it's pointless to be having modules of "28-15" version.  If you haven't noticed yet version numbers of modules/images/headers should match.

sudo apt-get purge linux-restricted-modules-2.6.28-15-generic

then

sudo dpkg --configure -a

---

### Post by kansasnoob on 2009-10-24
> **xebian said:**
> If you think back for a moment, the linux-restricted modules is from jaunty and no longer used in karmic.  So why bother with it, and because it's preventing you from moving on, get rid of it.

Plus you would be using a kernel version of "31-14" so it's pointless to be having modules of "28-15" version.  If you haven't noticed yet version numbers of modules/images/headers should match.

sudo apt-get purge linux-restricted-modules-2.6.28-15-generic

then

sudo dpkg --configure -a

I agree!

Then lets see what the new ouput of dpkg --configure -a is.

I do wish however that you had some type of installation media.

If you have a CD ROM you really should consider getting a Live CD, but nothing we can do about that right now.

---

### Post by KegHead on 2009-10-25
Hi!

jim@jim-laptop:~$ sudo apt-get purge linux-restricted-modules-2.6.28-15-generic
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-restricted-modules-2.6.28-15-generic*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
7 not fully installed or removed.
After this operation, 2,421kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 208388 files and directories currently installed.)
Removing linux-restricted-modules-2.6.28-15-generic ...
Bus error (core dumped)
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic
Purging configuration files for linux-restricted-modules-2.6.28-15-generic ...
Setting up python-problem-report (1.9.3-0ubuntu4) ...
Compiling /usr/lib/python2.5/site-packages/problem_report.py ...
Sorry: LookupError: ("no codec search functions registered: can't find encoding",)
pycentral: pycentral pkginstall: error byte-compiling files (1)
pycentral pkginstall: error byte-compiling files (1)
dpkg: error processing python-problem-report (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python-apport (>= 0.120); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python-apport (>= 0.80); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already

                                                                                Package python-apport is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.0.2-0ubuntu1); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-problem-report
 python-apport
 apport
 apport-gtk
 ubuntuone-client
 ubuntuone-client-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
jim@jim-laptop:~$ sudo dpkg --configure -a
Setting up python-problem-report (1.9.3-0ubuntu4) ...
Compiling /usr/lib/python2.5/site-packages/problem_report.py ...
Sorry: LookupError: ("no codec search functions registered: can't find encoding",)
pycentral: pycentral pkginstall: error byte-compiling files (1)
pycentral pkginstall: error byte-compiling files (1)
dpkg: error processing python-problem-report (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python-apport (>= 0.120); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python-apport (>= 0.80); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on python-apport; however:
  Package python-apport is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.0.2-0ubuntu1); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-problem-report
 python-apport
 apport
 apport-gtk
 ubuntuone-client
 ubuntuone-client-gnome
jim@jim-laptop:~$

---

### Post by vinutux on 2009-10-25
> **KegHead said:**
> HELP !!!

jim@jim-laptop:~$ sudo apt-get upgrade a
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-headers-2.6.31-14
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B/9,526kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 208263 files and directories currently installed.)
Preparing to replace linux-headers-2.6.31-14 2.6.31-14.47 (using .../linux-headers-2.6.31-14_2.6.31-14.48_all.deb) ...
Unpacking replacement linux-headers-2.6.31-14 ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.31-14_2.6.31-14.48_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-2.6.31-14/include/sound/Kbuild.dpkg-new' (while processing `./usr/src/linux-headers-2.6.31-14/include/sound/Kbuild'): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.31-14_2.6.31-14.48_all.deb
E: Sub-process /usr/bin/dpkg [COLOR="Red"]returned an error code (1)[/COLOR]
jim@jim-laptop:~$

[COLOR="YellowGreen"]**ARE YOU TRIED THIS THING.......... Take a look**[/COLOR]


> **vinutux said:**
> **[COLOR="red"]Do at your own risk...................[/COLOR]**


1. press Alt + F2 and type “gksu nautilus” (without quatos)

2. Type password …it open super user enabled nautilus

3. go to /var/lib/dpkg/info in nautilus

4. Delete all files related your broken package (if your broken package is cgmail delete all package related to cgmail)

5. done ….. open synaptic now and remove broken package

NB : [COLOR="Red"]before deleting any system file just backup it.[/COLOR]

From here.... [for post installation script errors]**[http://ubuntuxpress.wordpress.com/2009/10/07/post-installation-script-returned-error/]("http://ubuntuxpress.wordpress.com/2009/10/07/post-installation-script-returned-error/")**

---

### Post by philinux on 2009-10-25
There is a simple way, reinstall. After all it's only still beta.

I will be doing this anyway.

---

### Post by KegHead on 2009-10-25
Hi!

Thanks for your responses!

I learned a lot!

I think I'll reinstall after the final comes out.

Is there an easy way to remove the beta and install the final product via terminal?

Thanks in advance.

KegHead

---

### Post by kansasnoob on 2009-10-25
Well that cleared one error. So now run:

```
sudo apt-get purge python-problem-report python-apport apport apport-gtk ubuntuone-client ubuntuone-client-gnome
```

I even tried it just to be sure things wouldn't implode:

> lance@lance-desktop:~$ sudo apt-get purge python-problem-report python-apport apport apport-gtk ubuntuone-client ubuntuone-client-gnome
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apport* apport-gtk* python-apport* python-problem-report* ubuntuone-client*
  ubuntuone-client-gnome*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 3,445kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 176328 files and directories currently installed.)
Removing apport-gtk ...
Removing apport ...
stop: Unknown instance: 
Purging configuration files for apport ...
Removing ubuntuone-client-gnome ...
Removing ubuntuone-client ...
Removing python-apport ...
Purging configuration files for python-apport ...
Removing python-problem-report ...
Processing triggers for desktop-file-utils ...
Processing triggers for sreadahead ...
sreadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
lance@lance-desktop:~$ 


Then run:

```
sudo apt-get update && sudo apt-get install python-problem-report python-apport apport apport-gtk ubuntuone-client ubuntuone-client-gnome
```

There are a variety of netboot install methods discussed here:

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

Do you have a way of burning or using a Live CD? Or Live USB?

I've used these guys more than once:

[http://www.linuxcd.org/view_distro.php](http://www.linuxcd.org/view_distro.php)

I'd personally be lost without a Live CD!

---

### Post by KegHead on 2009-10-26
Hi!

I have a mini9 with no cd drive--i can use a live update--please advise.

KegHead

jim@jim-laptop:~$ sudo apt-get purge python-problem-report python-apport apport apport-gtk ubuntuone-client ubuntuone-client-gnome
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apport* apport-gtk* python-apport* python-problem-report* ubuntuone-client*
  ubuntuone-client-gnome*
0 upgraded, 0 newly installed, 6 to remove and 27 not upgraded.
6 not fully installed or removed.
After this operation, 3,445kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 208327 files and directories currently installed.)
Removing apport-gtk ...
Removing apport ...
Purging configuration files for apport ...
Removing ubuntuone-client-gnome ...
Removing ubuntuone-client ...
Removing python-apport ...
Purging configuration files for python-apport ...
dpkg: warning: while removing python-apport, directory '/usr/lib/python2.6/dist-packages/apport' not empty so not removed.
Removing python-problem-report ...
Processing triggers for desktop-file-utils ...
Processing triggers for sreadahead ...
sreadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
jim@jim-laptop:~$ sudo apt-get update && sudo apt-get install python-problem-report python-apport apport apport-gtk ubuntuone-client ubuntuone-client-gnome
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [665B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
Fetched 3,394B in 1s (2,485B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apport apport-gtk python-apport python-problem-report ubuntuone-client
  ubuntuone-client-gnome
0 upgraded, 6 newly installed, 0 to remove and 27 not upgraded.
Need to get 418kB of archives.
After this operation, 3,445kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main python-problem-report 1.9.3-0ubuntu4 [87.3kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main python-apport 1.9.3-0ubuntu4 [91.0kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main apport 1.9.3-0ubuntu4 [52.8kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main apport-gtk 1.9.3-0ubuntu4 [84.8kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main ubuntuone-client 1.0.2-0ubuntu1 [22.2kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main ubuntuone-client-gnome 1.0.2-0ubuntu1 [79.5kB]
Fetched 418kB in 2s (189kB/s)                
Selecting previously deselected package python-problem-report.
(Reading database ... 208125 files and directories currently installed.)
Unpacking python-problem-report (from .../python-problem-report_1.9.3-0ubuntu4_all.deb) ...
Selecting previously deselected package python-apport.
Unpacking python-apport (from .../python-apport_1.9.3-0ubuntu4_all.deb) ...
Selecting previously deselected package apport.
Unpacking apport (from .../apport_1.9.3-0ubuntu4_all.deb) ...
Selecting previously deselected package apport-gtk.
Unpacking apport-gtk (from .../apport-gtk_1.9.3-0ubuntu4_all.deb) ...
Selecting previously deselected package ubuntuone-client.
Unpacking ubuntuone-client (from .../ubuntuone-client_1.0.2-0ubuntu1_all.deb) ...
Selecting previously deselected package ubuntuone-client-gnome.
Unpacking ubuntuone-client-gnome (from .../ubuntuone-client-gnome_1.0.2-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Processing triggers for sreadahead ...
Processing triggers for desktop-file-utils ...
Setting up python-problem-report (1.9.3-0ubuntu4) ...
Compiling /usr/lib/python2.5/site-packages/problem_report.py ...
Sorry: LookupError: ("no codec search functions registered: can't find encoding",)
pycentral: pycentral pkginstall: error byte-compiling files (1)
pycentral pkginstall: error byte-compiling files (1)
dpkg: error processing python-problem-report (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-problem-report (>= 0.94); however:
  Package python-problem-report is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python-apport (>= 0.120); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python-apport (>= 0.80); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leavingNo apport report written because the error message indicates its a followup error from a previous failure.
                                                        No apport report written because the error message indicates its a followup error from a previous failure.
  No apport report written because MaxReports is reached already
                                                                No apport report written because MaxReports is reached already
                                              No apport report written because MaxReports is reached already
                             unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on python-apport; however:
  Package python-apport is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client-gnome:
 ubuntuone-client-gnome depends on ubuntuone-client (= 1.0.2-0ubuntu1); however:
  Package ubuntuone-client is not configured yet.
dpkg: error processing ubuntuone-client-gnome (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-problem-report
 python-apport
 apport
 apport-gtk
 ubuntuone-client
 ubuntuone-client-gnome
E: Sub-process /usr/bin/dpkg returned an error code (1)
jim@jim-laptop:~$

---

