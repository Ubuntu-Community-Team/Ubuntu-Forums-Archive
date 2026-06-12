---
title: "Unable to install updates"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by udito on 2010-10-12
hello,

I'm struggling updating ubuntu 10.10 via
[LIST]
[*]System > Administration > Update Manager
[/LIST]
I have a list of packages to update but installation does not start because there is the following window indicating this error:
[LIST]
[*]Package operation failed
[*]The installation or removal of a software package failed.
[*]Details:
[*]installArchives() failed:
[/LIST]
Help is highly appreciated.

thanks, udo

---

### Post by mörgæs on 2010-10-12
What happens if you boot the machine and run

```
sudo apt-get update
sudo apt-get upgrade
```?

---

### Post by oneup on 2010-10-12
I had same problem and did update/upgrade and it worked fine,I cannot get ubuntu software centre to work and whilst I can use apt-get and synaptic for what I want it would be nice to know if this is a problem to anyone else? I am using a dell inspiron 1100,2200 celeron laptop with 1 gig of ram,at one time ,4 years ago it would not run ubuntu 6.06 or xandros 4 but it just about ran xubuntu 10.04 but not ubuntu 10.04!one very nice thing is that my wireless usb card runs just as well in 10.10 as it did in 10.04 !I have often been critical of new ubuntu releases but I think this one is great not withstanding this early problem !
Thank you to all the people who have done so much hard work to make it possible !

Regards
          Nico

---

### Post by wmichaelb on 2010-10-12
I had exactly the same problem. I installed 10.10 on an older Dell 2.4 GHz P4 test machine this afternoon, and found that it would not successfully install updates, or software from the software center. I had exactly the same error message. 

So...is this a bug or a feature? I think I'll try the sudo/apt-get/upgrade route, and then try the software center again.

---

### Post by mörgæs on 2010-10-12
Best is forgetting about Software Centre and only use Synaptic. There are basically to many bugs in SC (take a look in Launchpad for confirmation).

---

### Post by anonomo on 2010-10-12
hi similar issue with update manager
downloads but cant unpackage to install:

> dpkg: parse error, in file /var/lib/dpkg/available' near line 10152:
newline in field name '[main]'
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:

so from terminal 

sudo apt-get update returns the same update packages
sudo apt-get upgrade installs 95 of them no problem, just errors with 3:

> 
95 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

but if 95 update packages have installed, why does update manager continue to pop up saying these same packages are available for this computer?
is update manager tripping or am i?
sorry i know this seems trivial, but having 1 million problems with this system, and i figure if i can't get the basics right theres no point even trying to fix them.

cheers for your advices
lhoping we can get freemix running smoothly b4 saturday night:)
:guitar:

---

### Post by anonomo on 2010-10-12
btw synaptic package manager gives me the same list of updates to be installed
and the same errors as update manager

---

### Post by tommcd on 2010-10-12
> **anonomo said:**
> 
sudo apt-get upgrade installs 95 of them no problem, just errors with 3:

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory 

but if 95 update packages have installed, why does update manager continue to pop up saying these same packages are available for this computer?
is update manager tripping or am i?

Try using: "*sudo apt-get dist-upgrade*" instead of: "*sudo apt-get upgrade*". Update-Manager uses dist-upgrade.
Also, make sure that synaptic, update manager, and the software center are not running when you use apt-get in the terminal.

---

### Post by DougieFresh4U on 2010-10-13
Also try:
```
sudo apt-get update
sudo apt-get dist-upgrade
[B]sudo apt-get -f install
sudo dpkg --configure -a[/B]
```

---

### Post by anonomo on 2010-10-13
hi thanks for the tips
cheers for getting back so quick!
```

sudo apt-get update 
```
downloads no problem

```
sudo apt-get dist-upgrade 
```
same error as before
CODE]dpkg: parse error, in file /var/lib/dpkg/available' near line 10152:
 newline in field name '[main]'[/CODE]

but after it says this 1st
> 97 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/203MB of archives.
After this operation, 130MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%


update manager and synaptic continue to suggest the same updates
and continue to give me the error 
			 				[
so had a look at file /var/lib/dpkg/available' near line 10152:
it says 
   	 	 	 	 	 		 	 	   	 	 		 			
			This 			package 			contains 			various 			fonts 			from 			dustismo.com 			licensed 			under 			
		 		 			
			the 			GPL. 			
			
			
			
			
			
			
			
		 	  counted the lines in spreadsheet, is that gonna mess with it? but that sounds pretty harmless to me! 
```


sudo apt-get -f install
```
tells me to 
```
The following packages were automatically installed and are no longer required:
....
Use 'apt-get autoremove' to remove them.
```

so why not i try sudo apt-get autoremove
... guess what???
```

After this operation, 53.6MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: parse error, in file '/var/lib/dpkg/available' near line 10152:
 newline in field name `[main]'

```

and i guess that you can guess what happens when i write
```
sudo dpkg --configure -a
```


well i'm confused.
could you point me where to check if i've actually upgraded anything?
any clues whats wrong?
whats up with fonts?

what is unusual about the /dpkg/available file is that all the packages say:
   	 	 	 	 	 		 	 	   	 	 		 			Architecture: 			amd64 		 	  um, unless i got ripped off, this box is using intel processor...
could it be that its downloading packages designed for the wrong processor:confused:

---

### Post by anonomo on 2010-10-13
um,
ouch
just tried to install LiVES using software centre
and got the same same wierd problem
and realised its doing the same thing for all software!

```
installArchives() failed: dpkg: parse error, in file '/var/lib/dpkg/available' near line 10152: 
 newline in field name `[main]' 

```

this is getting a bit serious 

p.s i'm sorry but don't know the best forum etiquete, would it be best to start a new thread since this problem turns out to be somethign different?

---

### Post by udito on 2010-10-13
Everything works well when executing:
```
sudo apt-get update
sudo apt-get upgrade
```

When executing
[LIST]
[*]sudo apt-get dist-upgrade
[/LIST]
I get this
```
root@X100e:~# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  adduser apt apt-utils base-files base-passwd bash bash-completion bsdmainutils bsdutils busybox-initramfs consolekit coreutils cpio
  cpp cpp-4.4 dash dbus debconf debconf-i18n debianutils diffutils dpkg e2fslibs e2fsprogs file findutils gawk gcc-4.4-base gcc-4.5-base
  gpgv grep gzip hostname ifupdown initramfs-tools initramfs-tools-bin initscripts insserv klibc-utils libacl1 libattr1 libblkid1
  libbz2-1.0 libc-bin libc6 libck-connector0 libcomerr2 libdb4.8 libdbus-1-3 libdbus-glib-1-2 libdconf0 libdrm-intel1 libdrm-nouveau1
  libdrm-radeon1 libdrm2 libeggdbus-1-0 libexpat1 libgcc1 libgdbm3 libglib2.0-0 libglib2.0-data libgmp3c2 libgpm2 libklibc
  liblocale-gettext-perl liblzma2 libmagic1 libmpfr4 libncurses5 libncursesw5 libnih-dbus1 libnih1 libpam-ck-connector libpam-modules
  libpam-runtime libpam0g libpcre3 libplymouth2 libpng12-0 libpolkit-gobject-1-0 libreadline6 libselinux1 libsepol1 libslang2
  libsqlite3-0 libss2 libssl0.9.8 libstdc++6 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libudev0 libusb-0.1-4
  libuuid1 libx11-6 libx11-data libxau6 libxcb1 libxdmcp6 libxml2 login lsb-base make makedev mime-support module-init-tools mount
  mountall ncurses-base ncurses-bin net-tools netbase passwd perl perl-base perl-modules plymouth plymouth-theme-ubuntu-text procps
  psmisc python python-minimal python2.6 python2.6-minimal readline-common sed sensible-utils sgml-base shared-mime-info sysv-rc
  sysvinit-utils tar tzdata ubuntu-keyring udev upstart util-linux uuid-runtime xml-core xz-utils zlib1g
0 upgraded, 141 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/49.7MB of archives.
After this operation, 177MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
E: Could not perform immediate configuration on 'libbz2-1.0'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```
At this point I'm stucked... Any clues?

---

### Post by udito on 2010-10-13
> **anonomo said:**
> p.s i'm sorry but don't know the best forum etiquete, would it be best to start a new thread since this problem turns out to be somethign different?

I think it would be best to open a new thread for this... Otherwise there will be the risk that nobody replies because there is a big confusion...

---

### Post by anonomo on 2010-10-13
yep good idea
i'll ask the question at 
[http://ubuntuforums.org/showthread.php?t=1595491](http://ubuntuforums.org/showthread.php?t=1595491)

E: Could not perform immediate configuration on 'libbz2-1.0'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)sounds like heaps diff problem. 
sorry cant help tho. good luck!

---

### Post by wmichaelb on 2010-10-13
Hi, as an update, last night I ran:

```
sudo apt-get update
sudo apt-get upgrade
```

and the system successfully upgraded. Now, when I open Update Manager, it tells me that all the updates are current. In addition, I've been able to successfully install software from the Software Center.

One obvious question is, why did we have to do this to get our iso installs to work properly? It looks as if the rev on the iso server hasn't caught up with the updates. 

I'm on Launchpad, and will file a bug report. This needs to get fixed.

---

### Post by tommcd on 2010-10-14
> **udito said:**
> 
When executing
sudo apt-get dist-upgrade
I get this
The following NEW packages will be installed: ...
0 upgraded, **141 newly installed**, 0 to remove and 0 not upgraded.

What third party repos have you added to your system?
Is this a clean install of 10.10? Did you install 10.10 from the 10.10-beta or something? Or is this a dist-upgrade from 10.04?
Post your *etc/apt/sources.list* file, and any files in your *etc/apt/sources.d/* directory.

---

### Post by udito on 2010-10-14
I upgraded from 10.04 to 10.10.

**/etc/apt/sources.list**
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb-src http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe
deb-src http://archive.ubuntu.com/ubuntu maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ch.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse #maverick-backports
# deb-src http://ch.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ch.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse #maverick-backports
# deb-src http://ch.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb-src http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-security multiverse
```

I don't have an
[LIST]
[*]/etc/apt/sources.d/
[/LIST]
directory. Instead I have this:
```
root@X100e:~# ls -al /etc/apt/sources.list.d
total 44
drwxr-xr-x 2 root root 4096 2010-10-10 22:41 .
drwxr-xr-x 6 root root 4096 2010-10-14 10:12 ..
-rw-r--r-- 1 root root    0 2010-10-11 21:40 dropbox.list
-rw-r--r-- 1 root root   47 2010-10-10 20:17 dropbox.list.distUpgrade
-rw-r--r-- 1 root root   86 2010-10-11 21:40 dropbox.list.save
-rw-r--r-- 1 root root  176 2010-10-12 23:34 google-chrome.list
-rw-r--r-- 1 root root  176 2010-10-10 20:17 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root  176 2010-10-12 23:34 google-chrome.list.save
-rw-r--r-- 1 root root    0 2010-09-17 21:47 ubuntu-wine-ppa-lucid.list
-rw-r--r-- 1 root root   63 2010-09-17 21:47 ubuntu-wine-ppa-lucid.list.save
-rwxr-xr-x 1 root root   58 2010-10-12 23:34 zend.list
-rwxr-xr-x 1 root root   58 2010-10-10 20:17 zend.list.distUpgrade
-rwxr-xr-x 1 root root   60 2010-10-12 23:34 zend.list.save
```
thanks, udo

---

### Post by udito on 2010-10-14
because the error was related to **libbz2-1.0** I tried this:
```
root@X100e:~# apt-get build-dep libbz2-1.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'bzip2' as source package instead of 'libbz2-1.0'
The following NEW packages will be installed:
  adduser apt apt-utils base-files base-passwd binutils build-essential busybox-initramfs bzip2 consolekit coreutils cpio cpp
  cpp-4.4 dbus debconf debconf-i18n debianutils dpkg dpkg-dev e2fslibs e2fsprogs fakeroot findutils g++ g++-4.4 gawk gcc gcc-4.4
  gcc-4.4-base gcc-4.4-multilib gcc-4.5-base gcc-multilib gnupg gpgv ifupdown initramfs-tools initramfs-tools-bin initscripts
  insserv klibc-utils lib64gcc1 lib64gomp1 libacl1 libalgorithm-diff-perl libalgorithm-merge-perl libattr1 libblkid1 libbz2-1.0
  libc-bin libc-dev-bin libc6 libc6-amd64 libc6-dev libc6-dev-amd64 libck-connector0 libcomerr2 libdb4.8 libdbus-1-3
  libdbus-glib-1-2 libdconf0 libdpkg-perl libdrm-intel1 libdrm-nouveau1 libdrm-radeon1 libdrm2 libeggdbus-1-0 libexpat1 libgcc1
  libgdbm3 libglib2.0-0 libglib2.0-data libgmp3c2 libgomp1 libgpm2 libklibc liblocale-gettext-perl liblzma2 libmpfr4 libncurses5
  libncursesw5 libnih-dbus1 libnih1 libpam-ck-connector libpam-modules libpam-runtime libpam0g libpcre3 libplymouth2 libpng12-0
  libpolkit-gobject-1-0 libreadline6 libselinux1 libsepol1 libslang2 libss2 libstdc++6 libstdc++6-4.4-dev libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libtimedate-perl libudev0 libusb-0.1-4 libuuid1 libx11-6 libx11-data libxau6 libxcb1
  libxdmcp6 libxml2 linux-libc-dev lsb-base make makedev manpages manpages-dev module-init-tools mount mountall ncurses-bin
  net-tools netbase passwd patch perl perl-base perl-modules plymouth plymouth-theme-ubuntu-text procps psmisc readline-common sed
  sensible-utils sgml-base shared-mime-info sysv-rc sysvinit-utils texinfo tzdata ubuntu-keyring udev upstart util-linux
  uuid-runtime xml-core xz-utils zlib1g
0 upgraded, 149 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/73.5MB of archives.
After this operation, 241MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
E: Could not perform immediate configuration on 'libbz2-1.0'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
E: Failed to process build dependencies
root@X100e:~#
```
unfortunately with no luck... any clues? thanks, udo

---

### Post by tommcd on 2010-10-15
> **udito said:**
> 
I don't have an
[*]/etc/apt/sources.d/

Sorry, the correct file path is: *etc/apt/sources.list.d* directory. Do you have any third party repos listed in that directory?
I am not sure why you are getting this error. I did a clean install of Xubuntu and Lubuntu on my systems and libbz2-1.0 is already installed.

---

### Post by udito on 2010-10-15
thanks tommcd, regarding the directory content, please take a look 3 postings back...

---

### Post by bhardie on 2010-10-15
> **udito said:**
> hello,

I'm struggling updating ubuntu 10.10 via
[LIST]
[*]System > Administration > Update Manager
[/LIST]
I have a list of packages to update but installation does not start because there is the following window indicating this error:
[LIST]
[*]Package operation failed
[*]The installation or removal of a software package failed.
[*]Details:
[*]installArchives() failed:
[/LIST]
Help is highly appreciated.

thanks, udo
I have a similar problem. I downloaded 10.10 onto my netbook but when I try to download from the software manager I get "package operation failed". also "low power chip with PCI ID 14e4:4315!"
This means nothing to me at all.
I hope the member helping you can also help me, and possible numerous other 'newbies'.
bhardie

---

### Post by ozPATT on 2010-10-16
I have the same error appearing, but it seems that everything does actually install fine. I have installed several applications, and they have all displayed that error, but the apps work. 

When I try the apt-get dis-upgrade as mentioned previously, I get the following:

```
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer

```

I'm using a Broadcom wireless chip, but it has installed the STA driver and it's working great, so I don't actually want to make any changes to Broadcom. 

Is there a way to stop it trying to set up the firmware for this? 

Thanks

Patrick

---

### Post by tommcd on 2010-10-16
> **ozPATT said:**
> I have the same error appearing, but it seems that everything does actually install fine. ...
When I try the apt-get dis-upgrade as mentioned previously, I get the following:

dpkg: error processing firmware-b43-installer (--configure):

If the errors are not causing you any problem, then I would probably just leave them alone.
Are you still running Ubuntu 9.04? If so, you should probably do a clean install (to a dedicated partition on your hard drive, and not using Wubi) of Ubuntu 10.10. Ubuntu 9.04 reaches end of life (EOL) on 10-23-10:
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
After EOL you will no longer get updates or be able to install additional programs.

See this for the b43 firmware:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
I have no experience with Broadcom wireless drivers though. I use RAlink, since they are open source and are supported in the linux kernel.

---

### Post by tommcd on 2010-10-16
> **bhardie said:**
> I have a similar problem. I downloaded 10.10 onto my netbook but when I try to download from the software manager I get "package operation failed". also "low power chip with PCI ID 14e4:4315!"

This sounds like a different problem.
Please start a new thread about this.
Include:
What netbook you installed Ubuntu on; and the version of Ubuntu you are using.
Please do a real install to a dedicated partition on your hard drive. Don't bother with a Wubi install inside Windows.

Are you able to access the internet after you install Ubuntu???
How do you connect to the internet?? Wireless?? Wired ethernet DSL?? or USB DSL?? Or cable??
Post the output from the terminal of:
```

sudo apt-get update
sudo apt-get dist-upgrade

``` 
And welcome to the Ubuntu forums!

---

### Post by udito on 2010-10-16
Hello,

I was able to solve the issue. See [http://superuser.com/questions/199582/apt-error-could-not-perform-immediate-configuration-on]("http://superuser.com/questions/199582/apt-error-could-not-perform-immediate-configuration-on") for solution.

Thanks for the help provided in this forum.

---

### Post by UsedBits on 2011-04-16
update manager insists on ...

Errors were encountered while processing:
 wine1.2
 tzdata
 wine
 grub-c

Prior to this, the update manager display of errors includes several lines of "Use of unitialized value [whatever]

Having tried several apt-get commands in this and other threads, nothing has yet worked.

HELP! I can't update anything.

---

### Post by mörgæs on 2011-04-17
Please write the exact commands you have tried and the corresponding error messages. Did you reboot the machine before trying?

By the way, if you system is 9.10 as indicated, I would go for a clean install of 10.04.2 or 10.10 rather than troubleshooting.

---

### Post by UsedBits on 2011-04-18
stephen@QuadBits:~$ sudo apt-get install
sudo: unable to resolve host QuadBits
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 102 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up tzdata (2011e-0ubuntu0.10.04) ...
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN1> line 7.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 7.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN1> line 8.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 8.
Can't call method "i18n" on an undefined value at /usr/share/perl5/Debconf/Element/Noninteractive/Select.pm line 13, <GEN1> line 8.
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 9
Setting up wine1.2 (1.2.2-0ubuntu2~lucid1) ...
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN1> line 2.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 2.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN1> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 3.
Can't call method "i18n" on an undefined value at /usr/share/perl5/Debconf/Element/Noninteractive/Select.pm line 13, <GEN1> line 3.
dpkg: error processing wine1.2 (--configure):
 subprocess installed post-installation script returned error exit status 9
Setting up grub-pc (1.98-1ubuntu10) ...
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN1> line 5.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 5.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN1> line 6.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 6.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN6> line 6.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN6> line 6.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN6> line 10.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN6> line 10.
Can't call method "description" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 93, <GEN6> line 10.
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of wine:
 wine depends on wine1.2; however:
  Package wine1.2 is not configured yet.
dpkg: error processing wine (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 tzdata
 wine1.2
 grub-pc
 wine
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

