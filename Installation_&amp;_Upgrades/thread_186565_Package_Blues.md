---
title: "Package Blues"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Harold P on 2006-06-02
Hello,

I'm trying to get this machine to work properly. A lot of packages were broken and such, and I'm *constantly* getting errors about "locale(s)". It's quite annoying, it's keeping me from installing any new packages. So, I went into terminal, updated, and dist-upgraded to resolve the problem... but I encountered the following error. Here is the output:

```

harold@ubuntu:~$ sudo apt-get update
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Fetched 4B in 1s (3B/s)
Reading package lists... Done
harold@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  belocs-locales-bin: Depends: locales
E: Unmet dependencies. Try using -f.
harold@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  locales
The following NEW packages will be installed:
  locales
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/3283kB of archives.
After unpacking 13.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 120494 files and directories currently installed.)
Unpacking locales (from .../locales_2.3.18_all.deb) ...
dpkg: error processing /var/cache/apt/archives/locales_2.3.18_all.deb (--unpack):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package tzdata
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.3.18_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
harold@ubuntu:~$

``` 
[This]("http://www.psychocats.net/ubuntu/sources.php") is my sources.list (if it helps...)

I would **really** like to do a fresh install, but my dad forgot the password to this machine's bios. (just great. :-|) And because of that, it always boots in this order: Floppy, IDE, and then CD drive. So this leaves me no choice but to dist-upgrade, unless there is another approach? Also, I'd like to say that when I was upgrading, I was doing too much (running at 100% CPU) at one time and so X crashed on me, so (not thinking) I restarted it (CTRL + ALT + Backspace). I was bombarded with around 3 errors regarding that X could not start, and that things were missing. So I thought, eh... no big deal, and followed with an apt-get update'd and dist-upgrade. After about a few hours of downloading new packages and installing, X finally started up. I logged in as normal, and saw new sleek start-up thingy and reddish background then was prompted with a notice. "blah blah blah icon could not be found". I immediately knew a bunch of my packages were broken. I tried opening Gaim, amarok, and a few other apps but they just didn't work. Thankfully firefox wasn't harmed. Anyways, that's where I am right now: I'm stuck with this package that just **won't** update, blocking me from installing newer applications, and it's keeping me from getting back to where I need to be.

Any help would be **GREATLY** appreciated.

Thanks in advance,
HP

P.S. I *am* willing to wipe this drive so this box will boot past IDE to a CD, but I need a sufficient way of doing this.

---

### Post by taavi on 2006-06-02
I would too like to see an official solution to this "locales" case. I'm trying to set my box up to use an ISO-8859-1, but can't get that nice menu that was on Breezy with 
"dpkg-reconfigure locales" 

What to do, thanks?

---

### Post by taavi on 2006-06-02
This is how I solved this problem now. I don't know, if it is nice, but at least it works...

I added one line to "/var/lib/locales/supported.d/en"

```
en_US.ISO-8859-1 ISO-8859-1
```

then ran:

```
sudo dpkg-reconfigure locales
```

Then edited my "/etc/enviroment"

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_US.iso88591"
LANGUAGE="en_US.iso88591"
### BEGIN DEBCONF SECTION FOR localeconf
# Do not edit within this region if you want your changes to be preserved
# by debconf.  Instead, make changes before the "### BEGIN DEBCONF SECTION
# FOR localeconf" line, and/or after the "### END DEBCONF SECTION FOR
# localeconf" line.
LANG="en_US.UTF-8"
### END DEBCONF SECTION FOR localeconf
LANG="en_US.iso88591"
```

I logged out of Gnome and selected "A Default System Language" from Languages and all was like needed.

---

### Post by Harold P on 2006-06-02
Sigh, still doesn't work. :(

```
harold@ubuntu:/usr/java$ sudo apt-get install mozilla-browser
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  belocs-locales-bin: Depends: locales
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
harold@ubuntu:/usr/java$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  locales
The following NEW packages will be installed:
  locales
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/3283kB of archives.
After unpacking 13.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 120494 files and directories currently installed.)
Unpacking locales (from .../locales_2.3.18_all.deb) ...
dpkg: error processing /var/cache/apt/archives/locales_2.3.18_all.deb (--unpack):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package tzdata
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.3.18_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
harold@ubuntu:/usr/java$

``` 
Help, please, anyone? :-|

Edit: Last night I tried removing the conflicting package with Synaptic and it didn't work. Seems to work today, though. I did do what is mentioned above. And, today I installed mozilla-browser and it works, but it STILL prompts me with errors.

---

### Post by ubuntu_demon on 2006-06-02
try this guide :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

### Post by Harold P on 2006-06-02
[quote=ubuntu_demon]try this guide :
[http://www.ubuntuforums.org/showthread.php?t=186672]("http://www.ubuntuforums.org/showthread.php?t=186672")[/quote] Sigh. That halped somewhat with removing some files, and upgrading others... but  I STILL am getting the same error if I want to install/remove this "locales" package.

```
harold@ubuntu:~$ sudo apt-get remove locales
Reading package lists... Done
Building dependency tree... Done
Package locales is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  belocs-locales-bin: Depends: locales
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
harold@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  locales
The following NEW packages will be installed:
  locales
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/3283kB of archives.
After unpacking 13.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 121524 files and directories currently installed.)
Unpacking locales (from .../locales_2.3.18_all.deb) ...
dpkg: error processing /var/cache/apt/archives/locales_2.3.18_all.deb (--unpack):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package tzdata
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.3.18_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
harold@ubuntu:~$


``` 
It's conflicting with tzdata. I tried removing that, but it said I have unresolved dependancies (locales), and if I try removing it, the error just comes back. It's like a non-ending circle. :(

```
harold@ubuntu:~$ sudo apt-get remove locales
Reading package lists... Done
Building dependency tree... Done
Package locales is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  belocs-locales-bin: Depends: locales
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
harold@ubuntu:~$

```

Is there anything I can do... ? 

Thanks,
Harold

---

### Post by ubuntu_demon on 2006-06-02
Try to remove it including all dependencies and the dependencies of those dependencies.................and the dependencies of those dependencies.........and the dependencies of those dependencies........

So start with :
$sudo apt-get remove locales belocs-locales-bin 

Maybe this thread helps :
[http://www.ubuntuforums.org/showthread.php?t=186617](http://www.ubuntuforums.org/showthread.php?t=186617)

---

### Post by Harold P on 2006-06-02
[quote=ubuntu_demon]Try to remove it including all dependencies and the dependencies of those dependencies.................and the dependencies of those dependencies.........and the dependencies of those dependencies........

So start with :
$sudo apt-get remove locales belocs-locales-bin 

Maybe this thread helps :
[http://www.ubuntuforums.org/showthread.php?t=186617]("http://www.ubuntuforums.org/showthread.php?t=186617")[/quote] The last dependencies are the ones you listed above, I think


I tried sudo aptitude update & aptitude install ubuntu-desktop (if it will help...)
```

harold@ubuntu:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Get:5 http://security.ubuntu.com dapper-security Release [19.6kB]
Get:6 http://archive.ubuntu.com dapper-updates Release [23.4kB]
Get:7 http://archive.ubuntu.com dapper-backports Release [19.6kB]
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Get:8 http://security.ubuntu.com dapper-security/main Packages [14B]
Get:9 http://archive.ubuntu.com dapper-updates/main Packages [6196B]
Get:10 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:11 http://archive.ubuntu.com dapper-updates/main Sources [3947B]
Get:12 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:13 http://security.ubuntu.com dapper-security/restricted Packages [14B]
Get:14 http://security.ubuntu.com dapper-security/main Sources [14B]
Get:15 http://security.ubuntu.com dapper-security/restricted Sources [14B]
Get:16 http://security.ubuntu.com dapper-security/universe Packages [14B]
Get:17 http://archive.ubuntu.com dapper-backports/main Packages [14B]
Get:18 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:19 http://archive.ubuntu.com dapper-backports/universe Packages [14B]
Get:20 http://archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Get:21 http://security.ubuntu.com dapper-security/universe Sources [14B]
Fetched 73.5kB in 1s (37.6kB/s)
Reading package lists... Done
harold@ubuntu:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  alacarte avahi-daemon brltty-x11 deskbar-applet ekiga festival
  festlex-cmu festlex-poslex festvox-kallpc16k gnome-accessibility-themes
  gnome-mag gnome-screensaver gnopernicus gok gstreamer0.10-esd
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-ugly
  gstreamer0.10-tools gtk2-engines-highcontrast libavahi-core4 libdaemon0
  libestools1.2 libgail-gnome-module libgnome-mag2 libgnome-speech3
  libgnomevfs2-bin libgnomevfs2-extra libopal-2.2.0 libpt-plugins-avc
  libpt-plugins-dc libpt-plugins-oss openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  python-beagle screensaver-default-images tangerine-icon-theme
The following packages will be automatically REMOVED:
  openoffice.org-debian-files openoffice.org2-java-common
  openoffice.org2-l10n-en-us smeg
The following NEW packages will be installed:
  alacarte avahi-daemon brltty-x11 deskbar-applet ekiga festival
  festlex-cmu festlex-poslex festvox-kallpc16k gnome-accessibility-themes
  gnome-mag gnome-screensaver gnopernicus gok gstreamer0.10-esd
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-ugly
  gstreamer0.10-tools gtk2-engines-highcontrast libavahi-core4 libdaemon0
  libestools1.2 libgail-gnome-module libgnome-mag2 libgnome-speech3
  libgnomevfs2-bin libgnomevfs2-extra libopal-2.2.0 libpt-plugins-avc
  libpt-plugins-dc libpt-plugins-oss openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  python-beagle python-uno rhythmbox screensaver-default-images
  sound-juicer tangerine-icon-theme ubuntu-desktop
The following packages will be REMOVED:
  openoffice.org-debian-files openoffice.org2-java-common
  openoffice.org2-l10n-en-us smeg
0 packages upgraded, 52 newly installed, 4 to remove and 0 not upgraded.
Need to get 97.8MB of archives. After unpacking 270MB will be used.
Do you want to continue? [Y/n/?] y
``` 
The install went fine . I read your guide, though and it said reinstall ubuntu-minimal, and I got this:

```
harold@ubuntu:~$ sudo apt-get install ubuntu-minimal
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
  ubuntu-minimal: Depends: libc6-i686 but it is not going to be installed
E: Broken packages
harold@ubuntu:~$ sudo apt-get install libc6-i686
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
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-9 is to be installed
E: Broken packages
harold@ubuntu:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
harold@ubuntu:~$

``` 
Dependency errors, everywhere. :( Any suggestions?

---

### Post by ubuntu_demon on 2006-06-02
First make sure your /etc/apt/sources.list is in order. So there should be no non-official there. Post your /etc/apt/sources.list if you are not really sure whether it's in order.

Read my guide carefully and make sure you understand it :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

I try to explain that you first have to make sure to remove all packages with errors and/or broken dependencies. Then check for any unconfigured packages and only after that start installing stuff again. Please start at the top and follow the steps.

libc6 is probably installed but it's probably the wrong version so remove it (including all dependencies).
$sudo apt-get remove libc6

good luck ! :)

---

### Post by Harold P on 2006-06-02
[quote=ubuntu_demon]First make sure your /etc/apt/sources.list is in order. So there should be no non-official there. Post your /etc/apt/sources.list if you are not really sure whether it's in order.

Read my guide carefully and make sure you understand it :
[http://www.ubuntuforums.org/showthread.php?t=186672]("http://www.ubuntuforums.org/showthread.php?t=186672")

I try to explain that you first have to make sure to remove all packages with errors and/or broken dependencies. Then check for any unconfigured packages and only after that start installing stuff again. Please start at the top and follow the steps.

libc6 is probably installed but it's probably the wrong version so remove it (including all dependencies).
$sudo apt-get remove libc6

good luck ! :)[/quote] 
Alright, I read the guide and removed everything I could that had that had to do with locales and  belocs-locales-bin. They are the only packages there that needed removal. dokg --configure -a returns with nothing, so I assume that that is fine.

Okay, here is my sources.list:

```
harold@ubuntu:~$ cat /etc/apt/sources.list
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
harold@ubuntu:~$

``` 
Is it "in order"?

And here is the result of the libc6 removal:

```
harold@ubuntu:~$ sudo apt-get remove libc6
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
  openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.2) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-us: Depends: openoffice.org-common (>= 2.0.2) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-za: Depends: openoffice.org-common (>= 2.0.2) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
E: Broken packages
harold@ubuntu:~$

``` 
Should I install **openoffice.org-common**?

---

### Post by ubuntu_demon on 2006-06-02
Your sources.list appears to be in order on first sight.

**As explained** in my guide :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

Don't install things with problems but remove them including all dependencies. Do everything from ctrl-alt-f1.

So for example :

$sudo apt-get remove libc6 openoffice.org-l10n-en-gb openoffice.org-l10n-en-us openoffice.org-l10n-en-za openoffice.org-common language-support-en

After you have removed everything issue :
$sudo apt-get remove -f
$sudo apt-get dpkg --configure -a

good luck! :)

---

### Post by Harold P on 2006-06-02
[quote=ubuntu_demon]Your sources.list appears to be in order on first sight.

**As explained** in my guide :

Don't install things with problems but remove them including all dependencies. Do everything from ctrl-alt-f1.

So for example :

$sudo apt-get remove libc6 openoffice.org-l10n-en-gb openoffice.org-l10n-en-us openoffice.org-l10n-en-za openoffice.org-common language-support-en

After you have removed everything issue :
$sudo apt-get remove -f
$sudo apt-get dpkg --configure -a

good luck! :)[/quote]
Okay, trying to remove libc6 along with openoffice.org-common gives the same output, so I need to do openoffice.org-common first.

```
harold@ubuntu:~$ sudo apt-get remove openoffice.org-common
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-java-common openoffice.org-math
  openoffice.org-writer python-uno ubuntu-desktop
0 upgraded, 0 newly installed, 15 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 183MB disk space will be freed.
Do you want to continue [Y/n]?

```

Okay, that's fine... but it's removing ubuntu-desktop, and your guide says it's fine... but just to be safe, is that okay? I'm just concerened if I try to reinstall ubuntu-desktop later, I'll encoutner dependancy errors. :???:

---

### Post by ubuntu_demon on 2006-06-02
It's probably fine. First you have to remove everything which gives troubles to make sure there isn't any dependencies problem left. Just make sure you are doing everything from ctrl-alt-f1.

After you have removed everything issue :
$sudo apt-get remove -f
$sudo apt-get dpkg --configure -a

and follow the guide from there

good luck :)

---

### Post by Harold P on 2006-06-02
Sigh, this doesn't look good:


```
harold@ubuntu:~$ sudo apt-get remove libc6 openoffice.org-l10n-en-gb openoffice.org-l10n-en-us openoffice.org-l10n-en-za openoffice.org-common language-support-en
Reading package lists... Done
Building dependency tree... Done
Package openoffice.org-common is not installed, so not removed
The following packages will be REMOVED:
  3dchess aa3d abiword abiword-common abiword-plugins acm acpi acpi-support
  acpid acroread adduser adept akregator alacarte alien alsa-base alsa-utils
  amarok amarok-xine anacron anthy apache2 apache2-common apache2-mpm-prefork
  apache2-utils apmd appres apt apt-utils aptitude ark arts artsbuilder aspell
  aspell-en at at-spi automatix avahi-daemon avglinux base-files base-passwd
  bash bc beep-media-player beforelight bicyclerepair bind9-host
  binfmt-support binutils binutils-static bison bitmap bittorrent blt
  bluez-cups bluez-pcmcia-support bluez-pin bluez-utils bmp-docklet bogofilter
  bogofilter-bdb brltty brltty-x11 bsdmainutils bsdutils bsh bug-buddy bzip2
  ca-certificates cabextract capplets-data cdparanoia cdrdao cdrecord
  centericq console-common console-data console-tools contact-lookup-applet
  coreutils cpio cpp cpp-4.0 cron cupsys cupsys-bsd cupsys-client
  cupsys-driver-gimpprint cupsys-driver-gutenprint cvs dash db4.2-util dbus
  dbus-1-utils dc debconf debconf-i18n debconf-utils debfoster debhelper
  debianutils debtags defoma deskbar-applet desktop-file-utils dhcp3-client
  dhcp3-common dictionaries-common diff discover1 diveintopython dmidecode
  dmsetup dnsutils doc-base docbook-xml dosfstools dpkg dpkg-dev dselect
  dvd+rw-tools e2fslibs e2fsprogs ed editres eject ekiga enscript eog
  epiphany-browser epiphany-extensions esound ethtool evince evms evms-ncurses
  evolution evolution-data-server evolution-exchange evolution-plugins
  evolution-webcal fastjar fdutils feh festival festlex-cmu festlex-poslex
  festvox-kallpc16k fetchmail ffmpeg fftw3 file file-roller findutils finger
  firefox firefox-gnome-support flashplayer-mozilla fluxbox fontconfig foo2zjs
  foomatic-db-engine foomatic-db-gimp-print foomatic-db-gutenprint
  foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fortune-mod
  fortunes-min fping freeglut3 frostwire fstobdf ftp gaim gamin gcalctool gcc
  gcc-4.0 gcc-4.0-locales gconf-editor gconf2 gconf2-common gcursor gdb gdebi
  gdesklets gdesklets-data gdm gedit gettext gettext-base gftp gftp-gtk
  gftp-text giblib1 gij gij-4.0 gij-4.1 gimp gimp-print gimp-python gksu glade
  gnome-about gnome-accessibility-themes gnome-app-install gnome-applets
  gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager
  gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring
  gnome-mag gnome-media gnome-menus gnome-netstatus-applet gnome-nettool
  gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits
  gnome-power-manager gnome-screensaver gnome-session gnome-spell
  gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data
  gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus
  gnumeric-gtk gnupg gok gqview graveman grep grepmap groff-base grub
  gs-common gs-esp gsfonts gsfonts-x11 gstreamer0.10-alsa gstreamer0.10-esd
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer0.10-tools gstreamer0.8-a52dec
  gstreamer0.8-aa gstreamer0.8-alsa gstreamer0.8-artsd gstreamer0.8-audiofile
  gstreamer0.8-caca gstreamer0.8-cdio gstreamer0.8-cdparanoia gstreamer0.8-dv
  gstreamer0.8-dvd gstreamer0.8-esd gstreamer0.8-faac gstreamer0.8-faad
  gstreamer0.8-festival gstreamer0.8-ffmpeg gstreamer0.8-flac
  gstreamer0.8-gnomevfs gstreamer0.8-gsm gstreamer0.8-gtk gstreamer0.8-hermes
  gstreamer0.8-jpeg gstreamer0.8-lame gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-misc gstreamer0.8-mms gstreamer0.8-mpeg2dec
  gstreamer0.8-musepack gstreamer0.8-oss gstreamer0.8-plugin-apps
  gstreamer0.8-plugins gstreamer0.8-sdl gstreamer0.8-sid gstreamer0.8-speex
  gstreamer0.8-swfdec gstreamer0.8-theora gstreamer0.8-tools
  gstreamer0.8-vorbis gstreamer0.8-x gthumb gtk-gnutella
  gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-gtk-qt
  gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice
  gtk2-engines-ubuntulooks gtk2-engines-xfce gtkhtml3.8 gucharmap
  guile-1.6-libs gwenview gzip hal hal-device-manager hdparm hermes1 hostname
  hotkey-setup hpijs hplip html2text hwdb-client iceauth ico id3v2 ifupdown
  ijsgimpprint ijsgutenprint imagemagick imake info initramfs-tools
  initscripts inputattach intltool-debian iproute iptables iputils-arping
  iputils-ping iputils-tracepath irssi irssi-text ivman jackd java-gcj-compat
  jfsutils kaddressbook kamera kappfinder karm katapult kate kaudiocreator
  kcontrol kcron kde-guidance kde-style-lipstik kde-systemsettings
  kdeadmin-kfile-plugins kdebase-bin kdebase-kio-plugins kdebluetooth
  kdegraphics-kfile-plugins kdelibs-bin kdelibs4c2a
  kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins
  kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint
  kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt
  kio-locate klaptopdaemon klipper klogd kmail kmailcvt kmenuedit kmilo kmix
  kmplayer-base kmplayer-konq-plugins knetworkconf knotes koffice-libs
  konq-plugins konqueror konqueror-nsplugins konserve konsole kontact
  konversation kooka korganizer kpdf kpf kppp krdc krfb krita kscd
  kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg
  ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash
  kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kuser
  kwalletmanager kwifimanager kwin kwin-style-crystal lame language-selector
  language-selector-common language-selector-qt language-support-en
  laptop-detect laptop-mode laptop-mode-tools launchpad-integration less lftp
  liba52-0.7.4 libaa1 libacl1 libadns1 libaiksaurus-1.2-0c2a
  libaiksaurusgtk-1.2-0c2a libanthy0 libao2 libapache2-mod-php5 libapm1
  libapr0 libart-2.0-2 libarts1c2a libartsc0 libasound2 libaspell15
  libatk1.0-0 libatm1 libatspi1.0-0 libattr1 libaudio2 libaudiofile0
  libavahi-client3 libavahi-common3 libavahi-core4 libavahi-glib1
  libavahi-qt3-1 libavc1394-0 libbeagle0 libbeecrypt6 libbind9-0 libblkid1
  libbluetooth1 libbonobo2-0 libbonobo2-common libbonoboui2-0
  libboost-python1.33.0 libbrlapi1 libbtctl2 libbz2-1.0 libc6 libcairo2
  libcamel1.2-8 libcap1 libcdio3 libcdio6 libcdparanoia0 libchewing2
  libcomerr2 libcompfaceg1 libconsole libcroco3 libcupsimage2 libcupsys2
  libcupsys2-gnutls10 libcurl3 libcurl3-gnutls libdaemon0 libdb1-compat libdb3
  libdb4.2 libdb4.3 libdbd-mysql-perl libdbh1.0-1 libdbi-perl libdbus-1-2
  libdbus-glib-1-2 libdbus-qt-1-1c2 libdc1394-13 libdevmapper1.01
  libdevmapper1.02 libdirectfb-0.9-22 libdiscover1 libdjvulibre15 libdmx1
  libdns20 libdns21 libdrm1 libdrm2 libdv4 libdvbpsi3 libdvbpsi4 libdvdnav4
  libdvdread3 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1
  libedataserver1.2-4 libedataserver1.2-7 libedataserverui1.2-6 libedit2
  libeel2-2 libegroupwise1.2-8 libegroupwise1.2-9 libelfg0 libenchant1c2a
  libesd-alsa0 libestools1.2 libevms-2.5 libexchange-storage1.2-0
  libexchange-storage1.2-1 libexif12 libexo-0.3-0 libexpat1 libfaac0
  libfaad2-0 libflac++5c2 libflac7 libfontconfig1 libfontenc1 libfreetype6
  libfribidi0 libfs6 libgadu3 libgail-common libgail-gnome-module libgail17
  libgamin0 libgc1c2 libgcc1 libgcj6 libgcj6-common libgcj7 libgcj7-jar
  libgconf2-4 libgcrypt11 libgd1-noxpm libgd2 libgd2-noxpm libgda2-3
  libgda2-common libgdbm3 libgdchart-gd1-noxpm libgdl-1-0 libgdl-1-common
  libgdome2-0 libgdome2-cpp-smart0c2a libgeoip1 libggi2 libgii0
  libgii0-target-x libgimp2.0 libgimpprint1 libgksu1.2-1 libgksuui1.0-1
  libgl1-mesa libgl1-mesa-dri libglade2-0 libglademm-2.4-1c2a libgle3 libglew1
  libglib-perl libglib1.2 libglib2.0-0 libglib2.0-data libglibmm-2.4-1c2a
  libglide2 libglu1-mesa libglut3 libgmp3c2 libgnokii2 libgnome-desktop-2
  libgnome-keyring0 libgnome-mag2 libgnome-menu2 libgnome-pilot2
  libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common
  libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecanvas2-0
  libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomeprint2.2-0
  libgnomeprintui2.2-0 libgnomeui-0 libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgnucrypto-java libgnujaxp-java
  libgnujaxp-jni libgnutls11 libgnutls12 libgoffice-gtk-1-2 libgpg-error0
  libgpgme11 libgphoto2-2 libgphoto2-port0 libgpmg1 libgpod0 libgsf-1
  libgsf-1-113 libgsf-gnome-1-113 libgsl0 libgsm1 libgstreamer-gconf0.8-0
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins0.8-0 libgstreamer0.10-0
  libgstreamer0.8-0 libgtk1.2 libgtk2-perl libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15 libgtkmathview0c2a
  libgtkmm-2.4-1c2a libgtksourceview1.0-0 libgtkspell0 libgtop2-5 libgtop2-7
  libgucharmap4 libguile-ltdl-1 libgutenprint2 libgutenprintui2-1
  libhal-storage1 libhal1 libhsqldb-java libice-dev libice6 libicu34
  libid3-3.8.3c2a libid3tag0 libidl0 libidn11 libieee1284-3 libifp4
  libijs-0.35 libimlib2 libisc11 libisc9 libisccc0 libisccfg1 libiso9660-4
  libiw28 libjack0.100.0-0 libjasper-1.701-1 libjaxp1.2-java libjessie-java
  libjline-java libjpeg-progs libjpeg62 libkcal2b libkcddb1 libkdepim1a
  libkipi0 libkleopatra1 libkmime2 libkonq4 libkpathsea3 libkpathsea4
  libkpimexchange1 libkpimidentities1 libkrb53 libkscan1 libksieve0 libktnef1
  liblame0 liblaunchpad-integration0 liblcms1 libldap2 liblircclient0
  liblocale-gettext-perl liblockdev1 liblockfile1 liblpint-bonobo0 libltdl3
  liblwres1 liblwres9 liblzo1 libmad0 libmagic1 libmagick6 libmagick9
  libmdbtools libmetacity0 libmikmod2 libmimelib1c2a libmjpegtools0
  libmjpegtools0c2a libmms0 libmng1 libmodplug0c2 libmono0 libmp4v2-0
  libmpcdec3 libmpeg2-4 libmusicbrainz2c2 libmusicbrainz4c2a libmyspell3c2
  libmysqlclient12 libmysqlclient14 libmysqlclient15off libnautilus-burn3
  libnautilus-extension1 libncurses5 libncursesw5 libneon24 libneon25
  libnet-daemon-perl libnetcdf3 libnetpbm10 libnewt0.51 libnotify1 libnspr4
  libnss-mdns libnss3 libogg0 liboggflac3 liboil0.3 libopal-2.2.0 libopenal0
  libopencdk8 libopenexr2c2a libopenobex-1.0-0 liborbit2 libosp4 libosp5
  libots0 libpam-foreground libpam-modules libpam-runtime libpam0g
  libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpaper1
  libparted1.6-12 libparted1.6-13 libpcap0.8 libpcre3 libperl5.8 libpisock8
  libpisync0 libplrpc-perl libpng12-0 libpolyp0 libpoppler0c2
  libpoppler0c2-glib libpoppler0c2-qt libpoppler1 libpoppler1-glib
  libpoppler1-qt libpopt0 libportaudio0 libpq4 libpt-1.10.0 libpt-plugins-alsa
  libpt-plugins-avc libpt-plugins-dc libpt-plugins-oss libpt-plugins-v4l
  libpt-plugins-v4l2 libpythonize0 libqt3-mt libqthreads-12 libquicktime0
  libraptor1 librasqal0 libraw1394-5 librdf0 libreadline4 libreadline5
  librecode0 libreiserfs0.3-0 librpm4 librsvg2-2 librsvg2-common librsync1
  libruby1.8 libsamplerate0 libsane libsasl2 libsasl2-modules libscim8c2a
  libscrollkeeper0 libsdl1.2debian libsdl1.2debian-oss libselinux1 libsensors3
  libsepol1 libservlet2.3-java libsexy2 libshout3 libsidplay1
  libsigc++-1.2-5c2 libsigc++-2.0-0c2a libskim0 libslang2 libslp1 libsm-dev
  libsm6 libsmbclient libsmpeg0 libsndfile1 libsnmp5 libsnmp9 libsoup2.2-8
  libspeex1 libsqlite0 libsqlite3-0 libss2 libssl0.9.7 libssl0.9.8
  libstartup-notification0 libstdc++2.10-glibc2.2 libstdc++5 libstdc++6
  libstlport4.6c2 libsvga1 libsvn0 libswfdec0.3 libsysfs1 libsysfs2 libt1-5
  libtag1c2a libtagc0 libtar libtasn1-2 libtdb1 libtext-charwidth-perl
  libtext-iconv-perl libtext-wrapi18n-perl libtheora0 libthunar-vfs-1 libtiff4
  libtotem-plparser0 libtotem-plparser1 libtunepimp2c2a libungif4g
  libunicode-string-perl libuniconf4.2 libusb-0.1-4 libuuid1 libvcdinfo0
  libvisual0.2 libvorbis0a libvorbisenc2 libvorbisfile3 libvte4 libwavpack0
  libwmf0.2-7 libwnck18 libwpd-stream8c2a libwpd8c2a libwrap0
  libwvstreams4.0c2-base libwvstreams4.0c2-extras libwvstreams4.2-base
  libwvstreams4.2-extras libwxgtk2.4-1 libwxgtk2.6-0 libx11-6 libx11-dev
  libxalan2-java libxau-dev libxau6 libxaw7 libxcomposite1 libxcursor-dev
  libxcursor1 libxdamage1 libxdmcp-dev libxdmcp6 libxerces2-java libxext-dev
  libxext6 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4
  libxfcegui4-4 libxfixes-dev libxfixes3 libxfont1 libxft2 libxi-dev libxi6
  libxine-extracodecs libxine-main1 libxine1c2 libxinerama-dev libxinerama1
  libxkbfile1 libxklavier10 libxml2 libxml2-utils libxmlsec1 libxmlsec1-nss
  libxmlsec1-openssl libxmu-dev libxmu-headers libxmu6 libxmuu-dev libxmuu1
  libxosd2 libxp6 libxplc0.3.11c2 libxplc0.3.13 libxpm-dev libxpm4
  libxrandr-dev libxrandr2 libxrender-dev libxrender1 libxres1 libxslt1.1
  libxss1 libxt-dev libxt-java libxt6 libxtrap-dev libxtrap6 libxtst-dev
  libxtst6 libxv-dev libxv1 libxvidcore4 libxvmc1 libxxf86dga1 libxxf86misc1
  libxxf86vm1 links2 linux-386 linux-image-2.6.12-10-386
  linux-image-2.6.12-10-k7 linux-image-2.6.12-9-386 linux-image-2.6.15-23-386
  linux-image-2.6.15-23-k7 linux-image-386 linux-image-k7 linux-k7
  linux-restricted-modules-2.6.12-10-386 linux-restricted-modules-2.6.12-10-k7
  linux-restricted-modules-2.6.12-9-386 linux-restricted-modules-2.6.15-23-386
  linux-restricted-modules-2.6.15-23-k7 linux-restricted-modules-386
  linux-restricted-modules-common linux-restricted-modules-k7 linux-sound-base
  listres login logrotate lsb-base lsb-release lshw lsof ltrace lvm-common
  lvm2 m4 mailx make makedepend makedev man-db mawk mcpp mdadm mdetect menu
  mesa-utils metacity mii-diag min12xxw mjpegtools mkisofs module-init-tools
  mono mono-common mono-jit mount mousepad mozilla-acroread mozilla-browser
  mozilla-firefox-locale-en-gb mozilla-mplayer mozilla-thunderbird mpg321
  mplayer mplayer-386 mplayer-fonts msttcorefonts mtr-tiny myspell-en-gb
  myspell-en-us mysql-client mysql-client-5.0 mysql-server mysql-server-5.0
  nano nautilus nautilus-cd-burner nautilus-data nautilus-sendto ncurses-base
  ncurses-bin net-tools netbase netcat netpbm nmap notification-daemon ntpdate
  numlockx nvidia-kernel-common oclock odbcinst1debian1
  openoffice.org-help-en-us openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-us openoffice.org-l10n-en-za
  openoffice.org-thesaurus-en-us openssh-client openssl opera parted passwd
  patch pciutils pcmcia-cs perl perl-base perl-modules perl-suid php-auth
  php-db php-http php-mail php-net-smtp php-net-socket php-pear php-xml-parser
  php4-common php4-pear php5 php5-cli php5-common php5-mysql php5-mysqli
  picasa pkg-config pmount pnm2ppa po-debconf poppler-utils popularity-contest
  poster postfix powermanagement-interface powermgmt-base powernowd ppp
  pppconfig pppoeconf procmail procps psmisc psutils pykdeextensions python
  python-adns python-apt python-beagle python-cddb python-clientcookie
  python-crypto python-egenix-mxproxy python-egenix-mxstack
  python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs
  python-examples python-gadfly python-gd python-gdbm python-gdchart
  python-genetic python-geoip python-glade2 python-gmenu python-gnome2
  python-gnome2-desktop python-gnome2-extras python-gnupginterface python-gst
  python-gst0.10 python-gtk2 python-htmlgen python-htmltmpl python-id3lib
  python-imaging python-imaging-sane python-jabber python-kde3
  python-kjbuckets python-launchpad-integration python-ldap python-libxml2
  python-minimal python-musicbrainz python-mysqldb python-netcdf python-newt
  python-numeric python-opengl python-osd python-pam python-parted
  python-pexpect python-pgsql python-pisock python-pqueue python-pyao
  python-pylibacl python-pymad python-pyogg python-pyopenssl python-pyorbit
  python-pysqlite2 python-pyvorbis python-pyxattr python-reportlab
  python-simpletal python-soappy python-sqlite python-stats python-syck
  python-tk python-unit python-vte python-wxgtk2.6 python-xdg python-xml
  python-xmpp python2.4 python2.4-adns python2.4-apt python2.4-cairo
  python2.4-clientcookie python2.4-crypto python2.4-dbus python2.4-dev
  python2.4-dictclient python2.4-egenix-mxdatetime python2.4-egenix-mxproxy
  python2.4-egenix-mxstack python2.4-egenix-mxtexttools
  python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs
  python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm
  python2.4-geoip python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop
  python2.4-gnome2-extras python2.4-gobject python2.4-gtk2 python2.4-htmlgen
  python2.4-htmltmpl python2.4-id3lib python2.4-imaging python2.4-imaging-sane
  python2.4-jabber python2.4-kde3 python2.4-kjbuckets python2.4-ldap
  python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-minimal
  python2.4-musicbrainz python2.4-mysqldb python2.4-numeric python2.4-opengl
  python2.4-osd python2.4-pam python2.4-pexpect python2.4-pgsql
  python2.4-pycurl python2.4-pylibacl python2.4-pymad python2.4-pyopenssl
  python2.4-pyorbit python2.4-pysqlite2 python2.4-pyxattr python2.4-qt3
  python2.4-reportlab python2.4-simpletal python2.4-sip4-qt3 python2.4-soappy
  python2.4-sqlite python2.4-syck python2.4-tk python2.4-unit python2.4-xml
  python2.4-xmpp qca-tls qobex radeontool rdesktop rdiff-backup readahead
  realplay reiser4progs reiserfsprogs reportbug rhythmbox rox-filer rpm
  rss-glx rsync samba-common sane-utils scim scim-anthy scim-chewing
  scim-gtk2-immodule scim-hangul scim-modules-socket scim-pinyin scim-qtimm
  screen screensaver-default-images scrollkeeper sed serpentine sessreg
  sgml-base sgml-data shared-mime-info skim slocate smartdimmer smbclient
  smproxy sound-juicer sox speedcrunch ssh-askpass-gnome ssl-cert strace
  subversion sudo sun-j2re1.5 sylpheed sylpheed-i18n synaptic sysklogd
  sysvinit tangerine-icon-theme tango-icon-theme-common tar tcl8.4 tcpd
  tcpdump telnet thunar thunar-media-tags-plugin thunderbird-locale-en-gb time
  tk8.4 toshset totem totem-xine tsclient ttf-arabeyes ttf-arphic-bkai00mp
  ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ttf-arphic-ukai
  ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts ttf-bitstream-vera ttf-dejavu
  ttf-devanagari-fonts ttf-freefont ttf-gentium ttf-gujarati-fonts
  ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao
  ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts ttf-punjabi-fonts
  ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg ubuntu-artwork ubuntu-docs
  ubuntu-keyring ubuntu-standard ucf udev unattended-upgrades unrar-nonfree
  unzip update-manager update-notifier usbutils usplash util-linux vbetool
  viewres vim vino visualboyadvance vlc vlc-plugin-alsa vlc-plugin-arts
  vnc-common vorbis-tools w32codecs w3c-dtd-xhtml w3m wamerican wbritish wget
  whiptail whois wine wireless-tools wlassistant wvdial wxvlc x-dev
  x-ttcidfont-conf x-window-system-core x11-common x11perf x11proto-core-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-record-dev x11proto-render-dev x11proto-trap-dev x11proto-video-dev
  x11proto-xext-dev x11proto-xinerama-dev xarchiver xauth xaw3dg xbase-clients
  xbiff xcalc xchat xchat-common xclipboard xclock xconsole xcursorgen
  xditview xdpyinfo xdriinfo xev xeyes xf86dga xfburn xfce4 xfce4-appfinder
  xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin
  xfce4-diskperf-plugin xfce4-fsguard-plugin xfce4-genmon-plugin xfce4-goodies
  xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins
  xfce4-minicmd-plugin xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin
  xfce4-netload-plugin xfce4-panel xfce4-quicklauncher-plugin
  xfce4-screenshooter-plugin xfce4-sensors-plugin xfce4-session
  xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal
  xfce4-trigger-launcher xfce4-utils xfce4-verve-plugin xfce4-wavelan-plugin
  xfce4-weather-plugin xfce4-xkb-plugin xfd xfdesktop4 xffm4 xfmedia
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable xfonts-utils xfontsel
  xfprint4 xfsprogs xfwm4 xfwm4-themes xgamma xgc xhost xinit xkbutils
  xkeyboard-config xkill xlibs xload xlogo xlsatoms xlsclients xlsfonts xmag
  xman xmessage xml-core xmms xmodmap xmore xpmutils xprop xrandr xrdb
  xrefresh xresprobe xrgb xsane xscreensaver xscreensaver-data xscreensaver-gl
  xserver-xorg xserver-xorg-core xserver-xorg-driver-apm
  xserver-xorg-driver-ark xserver-xorg-driver-ati xserver-xorg-driver-chips
  xserver-xorg-driver-cirrus xserver-xorg-driver-cyrix
  xserver-xorg-driver-dummy xserver-xorg-driver-fbdev
  xserver-xorg-driver-glide xserver-xorg-driver-glint xserver-xorg-driver-i128
  xserver-xorg-driver-i740 xserver-xorg-driver-i810 xserver-xorg-driver-imstt
  xserver-xorg-driver-mga xserver-xorg-driver-neomagic
  xserver-xorg-driver-newport xserver-xorg-driver-nsc xserver-xorg-driver-nv
  xserver-xorg-driver-rendition xserver-xorg-driver-s3
  xserver-xorg-driver-s3virge xserver-xorg-driver-savage
  xserver-xorg-driver-siliconmotion xserver-xorg-driver-sis
  xserver-xorg-driver-tdfx xserver-xorg-driver-tga xserver-xorg-driver-trident
  xserver-xorg-driver-tseng xserver-xorg-driver-v4l xserver-xorg-driver-vesa
  xserver-xorg-driver-vga xserver-xorg-driver-via xserver-xorg-driver-vmware
  xserver-xorg-input-acecad xserver-xorg-input-aiptek
  xserver-xorg-input-calcomp xserver-xorg-input-citron
  xserver-xorg-input-digitaledge xserver-xorg-input-dmc
  xserver-xorg-input-dynapro xserver-xorg-input-elographics
  xserver-xorg-input-fpit xserver-xorg-input-hyperpen xserver-xorg-input-kbd
  xserver-xorg-input-magellan xserver-xorg-input-microtouch
  xserver-xorg-input-mouse xserver-xorg-input-mutouch
  xserver-xorg-input-palmax xserver-xorg-input-penmount
  xserver-xorg-input-spaceorb xserver-xorg-input-summa
  xserver-xorg-input-synaptics xserver-xorg-input-tek4957
  xserver-xorg-input-void xserver-xorg-input-wacom xset xsetmode xsetpointer
  xsetroot xsltproc xsm xstdcmap xterm xtrap xubuntu-artwork-usplash xutils
  xvidtune xvinfo xvncviewer xwd xwininfo xwud yelp zenity zip zlib1g
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libc6 (due to apt) libgcc1 (due to apt) libstdc++6 (due to apt)
  base-files base-passwd (due to base-files) libpam-modules (due to
  base-files) bash debianutils (due to bash) libncurses5 (due to bash)
  bsdutils coreutils libacl1 (due to coreutils) libselinux1 (due to coreutils)
  diff dpkg e2fsprogs e2fslibs (due to e2fsprogs) libblkid1 (due to e2fsprogs)
  libcomerr2 (due to e2fsprogs) libss2 (due to e2fsprogs) libuuid1 (due to
  e2fsprogs) findutils grep gzip hostname login libpam0g (due to login)
  libpam-runtime (due to login) mount ncurses-base ncurses-bin perl-base
  python-minimal python2.4-minimal (due to python-minimal) sed sysvinit
  initscripts (due to sysvinit) tar util-linux lsb-base (due to util-linux)
  libslang2 (due to util-linux) zlib1g (due to util-linux)
0 upgraded, 0 newly installed, 1586 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 3205MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]

``` 
Are these included in ubuntu-minimal/desktop/etc. ? I don't even know if I can get them back... It's removing apt. :S

---

### Post by ubuntu_demon on 2006-06-02
Press no!
Do **not** remove apt!

If you don't have apt you can't do anything anymore.

Solving these dependencies problems can sometimes be a **big puzzle**.

I see now that locales had a problem with the package tzdata which I don't have installed. So removing tzdata with all it's dependencies is probably the way to go for now.

Please post the output of :

$ sudo dpkg --configure -a
$ sudo apt-get remove -f
$sudo apt-get remove tzdata (and any dependencies like how I "teached" you)
$ sudo apt-get remove -f
$ sudo dpkg --configure -a

If that succeeds continue with this part of the guide :

> 
Let's run this command again to make sure it has removed everything that's problematic :
$ sudo apt-get -f remove

Let's now configure all packages that are still unconfigured :
$ sudo dpkg --configure -a

Now there are no more broken dependencies and all packages are configured. Let's install everything :

$ sudo apt-get install ubuntu-minimal
$ sudo apt-get install ubuntu-base
$ sudo apt-get install ubuntu-desktop
(or kubuntu / edubuntu / xubuntu)


If it doesn't succeed posts all the results and in the meantime I have something for you to read.

Please read here and make sure you understand :
[http://www.linux.com/article.pl?sid=05/10/12/1952217](http://www.linux.com/article.pl?sid=05/10/12/1952217)

Or try debfoster. Using debfoster it's relatively easy to remove packages including all it's "children". This guide is for breezy. But the principal is the same. **Only use it if you really understand it** because it's easy to delete too much. **Be very careful** :
[http://ubuntuforums.org/showthread.php?t=90675](http://ubuntuforums.org/showthread.php?t=90675)

PS I don't know when I'm going to sleep so if I don't respond anymore for like an hour I'm probably sleeping.

---

### Post by Harold P on 2006-06-02
[quote=ubuntu_demon]Press no!
Do **not** remove apt!

If you don't have apt you can't do anything anymore.[/quote]
Thought so. This really isn't working. I'd rather just do a clean install on this machine, but I need to remove the boot record from my hard drive (IDE). How can I go about doing this? The reason i need to is because my dad lost the password to our BIOS setup and I can't change it to boot to a disc before IDE. It goes in this order:

Floppy, IDE, and then disc.

---

### Post by ubuntu_demon on 2006-06-02
Hey be positive :)

We'll figure it out but it may cost a little time. 

I've helped a couple of people today. I've just helped someone else with a similar problem see :
[http://www.ubuntuforums.org/showthread.php?t=186936](http://www.ubuntuforums.org/showthread.php?t=186936)

And yeah reinstalling would maybe be faster but that's not really exciting isn't it ? :)

Make sure you read and understand what you are doing and you'll learn a lot in the meantime!

I've added some more information in my previous post.

Like my guide explains : you should make a backup of your personal files though.

Don't be afraid to ask any question and post the result of **every command** here.

I hope you have acces to a second machine. Because you won't be able to post here easily if you can't run firefox. Another option might be to install a commandline messaging program so we can chat in that case. If you want that :
$sudo apt-get install irssi

$irssi -c irc.freenode.net -n *yournickname*

if you have a password for freenode :
$/msg NickServ IDENTIFY *yourpassword*

$/join #ubuntuforums

If it's too busy there go here :

$/join #ubuntu_demon
Type away :
$hi, how are you doing ?

---

### Post by Harold P on 2006-06-02
[quote=ubuntu_demon]Hey be positive :)

We'll figure it out but it may cost a little time. And yeah reinstalling would maybe be faster but that's not really exciting isn't it ? :)

Make sure you read and understand what you are doing and you'll learn a lot in the meantime!

I've added some more information in my previous post.

I've just helped someone else with a similar problem see :
[http://www.ubuntuforums.org/showthread.php?t=186936]("http://www.ubuntuforums.org/showthread.php?t=186936")

Like my guide explains : you should make a backup of your personal files though.

Don't be afraid to ask any question and post the result of **every command** here.

I hope you have acces to a second machine. Because you won't be able to post here easily if you can't run firefox. Another option might be to install a commandline messaging program so we can chat in that case.[/quote] True, there really isn't any fun.. and I have learned a few things... :p I definitely understand what's going on, but it feels like I'm going in circles. (Even though that's what it basically is...) Is there some way we could do this a little faster, like IRC or MSN? (oops, didn't read!)

I'll try what you posted on the previous post. Thanks for helping. :o Appreciate it. :)

---

### Post by Harold P on 2006-06-02
[quote=ubuntu_demon]Press no!
Do **not** remove apt!

If you don't have apt you can't do anything anymore.

Solving these dependencies problems can sometimes be a **big puzzle**.

I see now that locales had a problem with the package tzdata which I don't have installed. So removing tzdata with all it's dependencies is probably the way to go for now.

Please post the output of :

$ sudo dpkg --configure -a
$ sudo apt-get remove -f
$sudo apt-get remove tzdata (and any dependencies like how I "teached" you)
$ sudo apt-get remove -f
$ sudo dpkg --configure -a

If that succeeds continue with this part of the guide :



If it doesn't succeed posts all the results and in the meantime I have something for you to read.

Please read here and make sure you understand :
[http://www.linux.com/article.pl?sid=05/10/12/1952217]("http://www.linux.com/article.pl?sid=05/10/12/1952217")

Or try debfoster. Using debfoster it's relatively easy to remove packages including all it's "children". This guide is for breezy. But the principal is the same. **Only use it if you really understand it** because it's easy to delete too much. **Be very careful** :
[http://ubuntuforums.org/showthread.php?t=90675]("http://ubuntuforums.org/showthread.php?t=90675")

PS I don't know when I'm going to sleep so if I don't respond anymore for like an hour I'm probably sleeping.[/quote] Okay, here's trying to remove tzdata:

```
harold@ubuntu:~$ sudo apt-get remove tzdata
Password:
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
  libc6: Depends: tzdata but it is not going to be installed
E: Broken packages
harold@ubuntu:~$ sudo apt-get remove libc6
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
  openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.2) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-us: Depends: openoffice.org-common (>= 2.0.2) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
  openoffice.org-l10n-en-za: Depends: openoffice.org-common (>= 2.0.2) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
E: Broken packages
harold@ubuntu:~$


``` 
libc6. Poo. :(

**Edit: **I have centericq and links installed, i'll go ahead and do irssi. :D

---

### Post by ubuntu_demon on 2006-06-02
You'll see my other IM accounts left of this post under my avatar.

Please post the results of :

$ sudo dpkg --configure -a
$ sudo apt-get remove -f
$ sudo dpkg --configure -a

You can do all the commands in ctrl-alt-f1 and do all the chatting in ctrl-alt-f2. That way if you lose X temporary it won't be as problematic.

---

### Post by Harold P on 2006-06-02
[quote=ubuntu_demon]You'll see my other IM accounts left of this post under my avatar.

Please post the results of :

$ sudo dpkg --configure -a
$ sudo apt-get remove -f
$ sudo dpkg --configure -a[/quote]

Here we go... I'm in IRC at the moment... in #ubuntuforums and #ubuntu_demon

```
harold@ubuntu:~$ sudo dpkg --configure -a
Password:
harold@ubuntu:~$ sudo apt-get remove -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
harold@ubuntu:~$ sudo dpkg --configure -a
harold@ubuntu:~$

```

---

### Post by Ptero-4 on 2006-06-02
Do you have a DOS boot floppy there? If you have one boot into it and do fdisk. Wipe your HD and put one FAT partition, reboot and format it. This blanks your HD forcing the boot sequence to skip it and go to the CD drive. Then you can reboot with the ubuntu CD and install it.

---

### Post by ubuntu_demon on 2006-06-02
That's a good result!.

Now let's see what happens when you continue with this part of my guide :

> 
Let's install everything :

$ sudo apt-get install ubuntu-minimal
$ sudo apt-get install ubuntu-base
$ sudo apt-get install ubuntu-desktop
(or kubuntu / edubuntu / xubuntu)

And make sure everything is upgraded :
$ sudo apt-get update
$ sudo apt-get dist-upgrade

If everything went well your broken dependencies problem is fixed. 


Please post the results of all commands.

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=Ptero-4]Do you have a DOS boot floppy there? If you have one boot into it and do fdisk. Wipe your HD and put one FAT partition, reboot and format it. This blanks your HD forcing the boot sequence to skip it and go to the CD drive. Then you can reboot with the ubuntu CD and install it.[/QUOTE]

thnx for this idea. It won't be necessary yet. 

Also are you 100% sure there's 0% chance that it won't result in a boot error instead of trying to boot from cd ?

---

### Post by Harold P on 2006-06-02
[quote=ubuntu_demon]That's a good result!.

Now let's see what happens when you continue with this part of my guide :



Please post the results of all commands.[/quote] 

```
harold@ubuntu:~$ sudo apt-get install ubuntu-minimal
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
  ubuntu-minimal: Depends: libc6-i686 but it is not going to be installed
E: Broken packages
harold@ubuntu:~$ sudo apt-get install ubuntu-base
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
  ubuntu-base: Depends: ubuntu-minimal but it is not going to be installed
E: Broken packages
harold@ubuntu:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-math openoffice.org-writer
  python-uno
Suggested packages:
  openoffice.org-help oooqs-kde unixodbc prelink openoffice.org-hyphenation
  openoffice.org-thesaurus xlibmesa-gl libgl1 openoffice.org-officebean
  openclipart-openoffice.org pstoedit openoffice.org-filter-so52 libmyodbc
  odbc-postgresql tdsodbc mdbtools libmysql-java libpg-java libsapdbc-java
  openoffice.org-gcj
The following NEW packages will be installed:
  openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-java-common openoffice.org-math openoffice.org-writer
  python-uno ubuntu-desktop
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/73.5MB of archives.
After unpacking 183MB of additional disk space will be used.
Do you want to continue [Y/n]?

```

[quote=Ptero-4]Do you have a DOS boot floppy there? If you have one boot into it and do fdisk. Wipe your HD and put one FAT partition, reboot and format it. This blanks your HD forcing the boot sequence to skip it and go to the CD drive. Then you can reboot with the ubuntu CD and install it.[/quote]

If all else fails, then maybe. My dad has some old windows floppies around somewhere... But it looks fine so far.

---

### Post by ubuntu_demon on 2006-06-02
try :
$sudo apt-get install ubuntu-minimal -f

---

### Post by Harold P on 2006-06-02
```
harold@ubuntu:~$ sudo apt-get install ubuntu-minimal -f
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
  ubuntu-minimal: Depends: libc6-i686 but it is not going to be installed
E: Broken packages
harold@ubuntu:~$

```

Okie...

---

### Post by ubuntu_demon on 2006-06-02
Use my sources.list from here :
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)
But **comment** all non-official repo's. (in this case the cipherfunk repo).

$sudo apt-get update 
$ sudo dpkg --configure -a
$ sudo apt-get remove -f
$ sudo dpkg --configure -a
$sudo apt-get install ubuntu-minimal -f

Post the results as always.

If that didn't work you should spend some time reading. 

Please read here and make sure you understand this :
[http://www.linux.com/article.pl?sid=05/10/12/1952217](http://www.linux.com/article.pl?sid=05/10/12/1952217)
and this about debfoster :
[http://ubuntuforums.org/showthread.php?t=90675](http://ubuntuforums.org/showthread.php?t=90675)

In the meantime I'll spend some time thinking and looking through the results. We'll probably have to go for the debfoster way. If that happens We'll do it one command at a time.

---

### Post by Harold P on 2006-06-02
Okay, everytime I open some programs like firefox, gedit, and gaim from command line, I am given this:

```
harold@ubuntu:~$ gedit

(gedit:22464): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:22464): Gdk-WARNING **: locale not supported by C library

```

Here is the output:
```

harold@ubuntu:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-backports/main Sources
Hit http://archive.ubuntu.com dapper-backports/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 4B in 1s (3B/s)
Reading package lists... Done
harold@ubuntu:~$ sudo dpkg --configure -a
harold@ubuntu:~$ sudo apt-get remove -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
harold@ubuntu:~$ sudo dpkg --configure -a
harold@ubuntu:~$ sudo apt-get remove -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
harold@ubuntu:~$ sudo apt-get install ubuntu-minimal -f
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
  ubuntu-minimal: Depends: libc6-i686 but it is not going to be installed
E: Broken packages
harold@ubuntu:~$

```

Here is my .x-session-errors
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "harold"
/etc/gdm/Xsession: Beginning session setup...

(gnome-session:10793): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-session:10793): Gdk-WARNING **: locale not supported by C library
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/10793
Window manager warning: Locale not understood by C library, internationalization will not work

(metacity:10861): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-panel:10869): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-panel:10869): Gdk-WARNING **: locale not supported by C library

(nautilus:10871): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(nautilus:10871): Gdk-WARNING **: locale not supported by C library

(gnome-volume-manager:10873): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-volume-manager:10873): Gdk-WARNING **: locale not supported by C library
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(gnome-cups-icon:10889): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-cups-icon:10889): Gdk-WARNING **: locale not supported by C library

(update-notifier:10883): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(update-notifier:10883): Gdk-WARNING **: locale not supported by C library

(gnome-power-manager:10885): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

** (update-notifier:10883): WARNING **: hal_initialize failed: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused


(gnome-power-manager:10885): Gdk-WARNING **: locale not supported by C library

(firefox-bin:10939): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
GNOME Terminal: locale not understood by C library, internationalization will not work

(gnome-terminal:10950): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-terminal:10950): Gdk-WARNING **: locale not supported by C library

(gedit:11370): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gedit:11370): Gdk-WARNING **: locale not supported by C library
GNOME Terminal: locale not understood by C library, internationalization will not work

(gnome-terminal:11380): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-terminal:11380): Gdk-WARNING **: locale not supported by C library
GNOME Terminal: locale not understood by C library, internationalization will not work

(gnome-terminal:11508): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-terminal:11508): Gdk-WARNING **: locale not supported by C library

(gnome-panel:10869): GnomeUI-CRITICAL **: gnome_icon_selection_clear: assertion `gis != NULL' failed

(gnome-panel:10869): GnomeUI-CRITICAL **: gnome_icon_selection_add_directory: assertion `gis != NULL' failed

(gnome-panel:10869): GnomeUI-CRITICAL **: gnome_icon_selection_show_icons: assertion `gis != NULL' failed

(gnome-panel:10869): GnomeUI-CRITICAL **: gnome_icon_selection_clear: assertion `gis != NULL' failed

(gnome-panel:10869): GnomeUI-CRITICAL **: gnome_icon_selection_add_directory: assertion `gis != NULL' failed

(gnome-panel:10869): GnomeUI-CRITICAL **: gnome_icon_selection_show_icons: assertion `gis != NULL' failed
/usr/bin/mozilla-suite: line 235: locale: command not found
GNOME Terminal: locale not understood by C library, internationalization will not work

(gnome-terminal:12311): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-terminal:12311): Gdk-WARNING **: locale not supported by C library
GNOME Terminal: locale not understood by C library, internationalization will not work

(gnome-terminal:12433): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-terminal:12433): Gdk-WARNING **: locale not supported by C library

(gedit:12487): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gedit:12487): Gdk-WARNING **: locale not supported by C library
/usr/bin/mozilla-suite: line 235: locale: command not found
/usr/bin/mozilla-suite: line 235: locale: command not found
GNOME Terminal: locale not understood by C library, internationalization will not work

(gnome-terminal:12761): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-terminal:12761): Gdk-WARNING **: locale not supported by C library

(gaim:12862): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(firefox-bin:12963): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(firefox-bin:13169): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(firefox-bin:13224): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(firefox-bin:13247): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(metacity-dialog:13515): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gaim:13528): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(firefox-bin:13598): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-theme-manager:13681): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-theme-manager:13680): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-theme-manager:13680): Gdk-WARNING **: locale not supported by C library

(gnome-theme-manager:13681): Gtk-CRITICAL **: gtk_icon_info_get_filename: assertion `icon_info != NULL' failed

(gnome-theme-manager:13681): Gtk-CRITICAL **: gtk_icon_info_free: assertion `icon_info != NULL' failed
make transparent again

(gnome-theme-manager:13680): capplet-common-CRITICAL **: generate_theme_thumbnail: assertion `async_data.set == FALSE' failed
make transparent again
GNOME Terminal: locale not understood by C library, internationalization will not work

(gnome-terminal:13869): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-terminal:13869): Gdk-WARNING **: locale not supported by C library
make transparent again
make transparent again
GNOME Terminal: locale not understood by C library, internationalization will not work

(gnome-terminal:14830): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-terminal:14830): Gdk-WARNING **: locale not supported by C library
kbuildsycoca running...
Reusing existing ksycoca
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
amaroK: [Loader] amaroK is taking a long time to load! Perhaps something has gone wrong?
ScimInputContextPlugin()
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.

(xchat:15174): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
make transparent again
make transparent again
GNOME Terminal: locale not understood by C library, internationalization will not work

(gnome-terminal:17215): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-terminal:17215): Gdk-WARNING **: locale not supported by C library
GNOME Terminal: locale not understood by C library, internationalization will not work

(gnome-terminal:17511): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-terminal:17511): Gdk-WARNING **: locale not supported by C library

(firefox-bin:18444): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
make transparent again
make transparent again
GNOME Terminal: locale not understood by C library, internationalization will not work

(gnome-terminal:19675): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-terminal:19675): Gdk-WARNING **: locale not supported by C library

(evolution-2.6:20048): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(evolution-2.6:20048): Gdk-WARNING **: locale not supported by C library
CalDAV Eplugin starting up ...

(evolution-2.6:20048): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.6:20048): e-utils-WARNING **: Plugin 'Spamassassin junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'

(evolution-2.6:20048): camel-WARNING **: camel_exception_get_id called with NULL parameter.
Can't open file 'wordlist.db' in directory '/home/harold/.bogofilter'.
error #2 - No such file or directory.

Remember to register some spam and ham messages before you
use bogofilter to evaluate mail for its probable spam status!
Can't open file 'wordlist.db' in directory '/home/harold/.bogofilter'.
error #2 - No such file or directory.

Remember to register some spam and ham messages before you
use bogofilter to evaluate mail for its probable spam status!
Can't open file 'wordlist.db' in directory '/home/harold/.bogofilter'.
error #2 - No such file or directory.

Remember to register some spam and ham messages before you
use bogofilter to evaluate mail for its probable spam status!
Can't open file 'wordlist.db' in directory '/home/harold/.bogofilter'.
error #2 - No such file or directory.

Remember to register some spam and ham messages before you
use bogofilter to evaluate mail for its probable spam status!
Can't open file 'wordlist.db' in directory '/home/harold/.bogofilter'.
error #2 - No such file or directory.

Remember to register some spam and ham messages before you
use bogofilter to evaluate mail for its probable spam status!
closing
GNOME Terminal: locale not understood by C library, internationalization will not work

(gnome-terminal:21352): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.

(gnome-terminal:21352): Gdk-WARNING **: locale not supported by C library

```

I've already read up on debfoster, but not on the linux article. I'll go ahead and do that. :)

---

### Post by ubuntu_demon on 2006-06-02
You did use my sources.list with cipherfunk commented right ?

---

### Post by Harold P on 2006-06-02
[quote=ubuntu_demon]You did use my sources.list with cipherfunk commented right ?[/quote]

Yep:

```
harold@ubuntu:~$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
## deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

## Breezy PLF
## only uncomment it if you need it
## since the Dapper PLF repository isn't available yet
## deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
## deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## Dapper PLF repository.
## NOT YET AVAILABLE
## deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
## deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
## deb http://wine.budgetdedicated.com/apt dapper main
## deb-src http://wine.budgetdedicated.com/apt dapper main

## skype
## only uncomment it if you need it
## deb http://download.skype.com/linux/repos/debian/ stable non-free
harold@ubuntu:~$

```

---

### Post by ubuntu_demon on 2006-06-02
We are loosely going to follow scenario 3 of :
[http://ubuntuforums.org/showthread.php?t=90675](http://ubuntuforums.org/showthread.php?t=90675)

I want you to run 1 command at a time. I will post the commands you have to type here as always. You should post the result of each command. Be very careful and make sure you understand what you are doing. This is of course on your own risk.

---

### Post by ubuntu_demon on 2006-06-02
Okay here we go :

$sudo debfoster -q ; cat /var/lib/debfoster/keepers

---

### Post by ubuntu_demon on 2006-06-02
what's the result of :
$ls -al /etc/apt/sources.list

---

### Post by Harold P on 2006-06-02
Okay:

```
harold@ubuntu:~$ sudo debfoster -q ; cat /var/lib/debfoster/keepers
Password:
3dchess
aa3d
abiword-plugins
acm
acpi
alien
amarok
anacron
apache2
apmd
aptitude
arts
artsbuilder
automatix
avglinux
bicyclerepair
bison
bluez-cups
bluez-pcmcia-support
bluez-pin
bmp-docklet
brltty-x11
bsh
bug-buddy
cdparanoia
centericq
contact-lookup-applet
cupsys-driver-gimpprint
cvs
dash
db4.2-util
dc
debfoster
diveintopython
doc-base
doc-debian
dosfstools
ekiga
eog
epiphany-browser
esound
ethtool
evince
evolution-exchange
evolution-webcal
example-content
feh
fetchmail
ffmpeg
fftw3
file-roller
flashplayer-mozilla
fluxbox
foo2zjs
foomatic-db-gimp-print
foomatic-db-hpijs
frostwire
gaim-libnotify
gcalctool
gcc
gcc-4.0-locales
gconf-editor
gcursor
gdebi
gdesklets
gdm
gedit
gftp
gij
gij-4.0
gimp
gimp-python
glade
gnome-accessibility-themes
gnome-app-install
gnome-btdownload
gnome-cups-manager
gnome-games
gnome-nettool
gnome-screensaver
gnome-spell
gnome-system-tools
gnome-terminal
gnome-themes
gnome-utils
gnome-volume-manager
gnopernicus
gnumeric-gtk
gok
gqview
graveman
grub
gstreamer0.10-esd
gstreamer0.10-plugins-base-apps
gstreamer0.8-faac
gstreamer0.8-faad
gstreamer0.8-ffmpeg
gstreamer0.8-lame
gstreamer0.8-plugin-apps
gtk-gnutella
gtk2-engines-gtk-qt
gtk2-engines-industrial
gucharmap
gwenview
hal-device-manager
hotkey-setup
hplip
id3v2
ijsgimpprint
installation-report
iproute
irssi-text
ivman
jackd
java-gcj-compat
karm
katapult
kate
kaudiocreator
kcron
kde-guidance
kde-systemsettings
kdeadmin-kfile-plugins
kdebluetooth
kdemultimedia-kappfinder-data
kdemultimedia-kfile-plugins
kdenetwork-filesharing
kdenetwork-kfile-plugins
kdepasswd
kdepim-wizards
kdeprint
kdnssd
keep
kio-apt
kio-locate
klaptopdaemon
klipper
kmailcvt
kmenuedit
kmilo
kmix
kmplayer-konq-plugins
knetworkconf
konq-plugins
konqueror-nsplugins
konserve
kontact
konversation
kooka
kpdf
kpf
kppp
krdc
krfb
krita
kscd
kscreensaver
ksmserver
ksnapshot
ksvg
ksysguard
ksystemlog
ktorrent
kubuntu-artwork-usplash
kubuntu-default-settings
kubuntu-docs
kubuntu-konqueror-shortcuts
kuser
kwalletmanager
kwifimanager
lame
landscape-client
language-selector
language-selector-qt
language-support-en
laptop-mode
less
lftp
libboost-python1.33.0
libcdio3
libcupsys2-gnutls10
libdevmapper1.01
libdns20
libdrm1
libdvbpsi3
libedataserver1.2-4
libegroupwise1.2-8
libexchange-storage1.2-0
libflac++5c2
libgadu3
libgcj6-common
libgd2
libgimpprint1
libgle3
libglut3
libgnokii2
libgnomevfs2-bin
libgnujaxp-java
libgsf-1
libgsf-gnome-1-113
libgtop2-5
libhsqldb-java
libicu34
libifp4
libkpathsea3
liblwres1
libmagick6
libmdbtools
libmjpegtools0
libmyspell3c2
libmysqlclient12
libmysqlclient14
libneon24
libopenal0
libosp4
libparted1.6-12
libpolyp0
libpoppler0c2-glib
libpoppler0c2-qt
libportaudio0
libreadline4
libreiserfs0.3-0
libsamplerate0
libsigc++-1.2-5c2
libsnmp5
libstlport4.6c2
libsysfs1
libtotem-plparser0
libvisual0.2
libwvstreams4.0c2-extras
libwxgtk2.4-1
libxalan2-java
libxcursor-dev
libxine1c2
libxinerama-dev
libxmlsec1-nss
libxmlsec1-openssl
libxmu-dev
libxmuu-dev
libxpm-dev
libxrandr-dev
libxt-java
libxtrap-dev
libxtst-dev
libxv-dev
links2
linux-386
linux-k7
linux-kernel-headers
linux-restricted-modules-2.6.12-10-386
linux-restricted-modules-2.6.12-10-k7
linux-restricted-modules-2.6.12-9-386
memtest86+
mii-diag
min12xxw
mjpegtools
mono
mousepad
mozilla-acroread
mozilla-browser
mozilla-mplayer
mozilla-thunderbird
mpg321
mplayer-386
mplayer-fonts
msttcorefonts
mysql-client
mysql-server
nautilus-sendto
netpbm
nmap
ntpdate
numlockx
odbcinst1debian1
opera
php-auth
php5
php5-mysql
picasa
pnm2ppa
powernowd
python-adns
python-cddb
python-clientcookie
python-crypto
python-egenix-mxproxy
python-egenix-mxstack
python-egenix-mxtexttools
python-egenix-mxtools
python-epydoc
python-eunuchs
python-examples
python-gadfly
python-gd
python-gdbm
python-gdchart
python-genetic
python-geoip
python-gst
python-htmlgen
python-htmltmpl
python-id3lib
python-imaging-sane
python-jabber
python-ldap
python-musicbrainz
python-mysqldb
python-netcdf
python-newt
python-opengl
python-osd
python-pam
python-parted
python-pexpect
python-pgsql
python-pisock
python-pqueue
python-pyao
python-pylibacl
python-pymad
python-pyopenssl
python-pyorbit
python-pysqlite2
python-pyvorbis
python-pyxattr
python-reportlab
python-simpletal
python-sqlite
python-stats
python-syck
python-unit
python-wxgtk2.6
python-xmpp
python2.4-dictclient
python2.4-librdf
python2.4-libxslt1
python2.4-pycurl
qca-tls
readahead
realplay
reiser4progs
rhythmbox
rox-filer
scim-anthy
scim-chewing
scim-hangul
scim-pinyin
scim-qtimm
screen
screensaver-default-images
serpentine
skim
slocate
sound-juicer
speedcrunch
ssh-askpass-gnome
strace
subversion
sun-j2re1.5
sylpheed
tangerine-icon-theme
tango-icon-theme-common
thunar-media-tags-plugin
tsclient
ttf-arabeyes
ttf-arphic-bkai00mp
ttf-arphic-bsmi00lp
ttf-arphic-gbsn00lp
ttf-arphic-gkai00mp
ttf-baekmuk
ttf-freefont
ttf-gentium
ttf-indic-fonts
ttf-kochi-gothic
ttf-kochi-mincho
ttf-lao
ttf-mgopen
ttf-opensymbol
ttf-thai-tlwg
ubuntu-artwork
ubuntu-docs
ubuntu-standard
unrar-nonfree
update-notifier
vim
vino
visualboyadvance
vlc-plugin-arts
w32codecs
wine
wlassistant
wvdial
x-dev
x-window-system-core
xarchiver
xchat
xcursor-themes
xfburn
xfce4
xfce4-appfinder
xfce4-cpugraph-plugin
xfce4-fsguard-plugin
xfce4-genmon-plugin
xfce4-goodies
xfce4-mailwatch-plugin
xfce4-minicmd-plugin
xfce4-mount-plugin
xfce4-quicklauncher-plugin
xfce4-screenshooter-plugin
xfce4-sensors-plugin
xfce4-taskmanager
xfce4-terminal
xfce4-trigger-launcher
xfce4-verve-plugin
xfce4-weather-plugin
xfce4-xkb-plugin
xffm4
xfmedia
xsane
xserver-xorg-driver-apm
xserver-xorg-driver-ark
xserver-xorg-driver-ati
xserver-xorg-driver-chips
xserver-xorg-driver-cirrus
xserver-xorg-driver-cyrix
xserver-xorg-driver-dummy
xserver-xorg-driver-fbdev
xserver-xorg-driver-glide
xserver-xorg-driver-glint
xserver-xorg-driver-i128
xserver-xorg-driver-i740
xserver-xorg-driver-i810
xserver-xorg-driver-imstt
xserver-xorg-driver-mga
xserver-xorg-driver-neomagic
xserver-xorg-driver-newport
xserver-xorg-driver-nsc
xserver-xorg-driver-nv
xserver-xorg-driver-rendition
xserver-xorg-driver-s3
xserver-xorg-driver-s3virge
xserver-xorg-driver-savage
xserver-xorg-driver-siliconmotion
xserver-xorg-driver-sis
xserver-xorg-driver-tdfx
xserver-xorg-driver-tga
xserver-xorg-driver-trident
xserver-xorg-driver-tseng
xserver-xorg-driver-v4l
xserver-xorg-driver-vesa
xserver-xorg-driver-vga
xserver-xorg-driver-via
xserver-xorg-driver-vmware
xserver-xorg-input-acecad
xserver-xorg-input-aiptek
xserver-xorg-input-calcomp
xserver-xorg-input-citron
xserver-xorg-input-digitaledge
xserver-xorg-input-dmc
xserver-xorg-input-dynapro
xserver-xorg-input-elographics
xserver-xorg-input-fpit
xserver-xorg-input-hyperpen
xserver-xorg-input-kbd
xserver-xorg-input-magellan
xserver-xorg-input-microtouch
xserver-xorg-input-mouse
xserver-xorg-input-mutouch
xserver-xorg-input-palmax
xserver-xorg-input-penmount
xserver-xorg-input-spaceorb
xserver-xorg-input-summa
xserver-xorg-input-synaptics
xserver-xorg-input-tek4957
xserver-xorg-input-void
xserver-xorg-input-wacom
xubuntu-artwork-usplash
xubuntu-docs
xvncviewer
harold@ubuntu:~$

```

the k7 kernel is there because I thought it'd work better with my AMD athlon, but the *86 one worked better.

I was following scenario 3, and the screen just froze up on me, couldn't move the mouse/type after doing "sudo init 1"

---

### Post by Harold P on 2006-06-02
k...

```
harold@ubuntu:~$ ls -al /etc/apt/sources.list
-rw-r--r-- 1 root root 2680 Jun  2 18:46 /etc/apt/sources.list

```

---

### Post by ubuntu_demon on 2006-06-02
$sudo pico /var/lib/debfoster/keepers

and make it like this. Please check for typo's :

```

acpi
debfoster
grub
installation-report
irssi-text
links2
linux-386
centericq
memtest86+
ubuntu-minimal
ubuntu-base
ubuntu-desktop
firefox
x-window-system-core
xserver-xorg
irssi

```

(I know ubuntu-base contains ubuntu-minimal and ubuntu-desktop contains firefox and such I just mention them explicitely)

You might want to add ssh. If you want to have acces to your computer from a terminal on another computer.

If your hardware requires certain packages. For example if you are running lvm or raid for example please add those packages.

If there are any other text-mode tools you think are essential please add them. But add as little packages as possible.

Please tell me which packages you have added.

We'll first try it like this. If there are still problems we'll strip some more.

Do you understand ?

---

### Post by Harold P on 2006-06-02
Okay, done. I didn't add anything. What next?

Sorry for replying late, friends are bugging me. :/

---

### Post by ubuntu_demon on 2006-06-02
first read before doing anything and do it only if you understand it and on your own risk :

Be sure that you backup important configuration files that you have edited yourself!

To force debfoster to remove all packages that aren't listed in this list or dependencies of packages that are listed in this list.It will also add all packages in this list that aren't installed. So it makes your system comply with this list. Do this :

$ sudo debfoster -f

from the manpage of debfoster :

> 
-f, --force
Don&#8217;t ask anything and assume &#8216;no&#8217; as the answer to all questions. It also installs any packages that seem to be missing, thus forcing your
system to comply with the debfoster database. Can have &#8216;interesting&#8217; results if you&#8217;re not careful.


After this your system is compatible with the keepers file.

Report the results here.

If it didn't succeeded we are going to need to strip the keepers file some more.

---

### Post by Harold P on 2006-06-02
results:
```
harold@ubuntu:~$ sudo debfoster -f
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-minimal: Depends: libc6-i686 but it is not going to be installed
E: Broken packages
harold@ubuntu:~$

```

---

### Post by ubuntu_demon on 2006-06-02
$sudo pico /var/lib/debfoster/keepers

and make it like this. Please check for typo's :

```

debfoster
grub
irssi-text
links2
linux-386
centericq
memtest86+
ubuntu-minimal
ubuntu-base
irssi

```

$ sudo debfoster -f

---

### Post by Harold P on 2006-06-02
From that database, that'll only keep those things and their dependancies, right? what about the other applications and stuff?

---

### Post by Harold P on 2006-06-02
output from **sudo debfoster -f**

```
harold@ubuntu:~$ sudo debfoster -f
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-minimal: Depends: libc6-i686 but it is not going to be installed
E: Broken packages
harold@ubuntu:~$

```

---

### Post by ubuntu_demon on 2006-06-02
The "sudo debfoster -f"  command will try to force the system to comply to the keepers file. It will try to remove all packages who aren't children to those packages. It will keep installed or try to install all packages who are in the keepers including the children. It will purge all configuration files of the packages that get removed (that's why you should back them up if you editted them).

It won't remove any personal files.

---

### Post by Harold P on 2006-06-02
[quote=ubuntu_demon]The "sudu debfoster -f"  command will try to force the system to comply to the keepers file. It will try to remove all packages who aren't children to those packages. It will keep installed or try to install all packages who are in the keepers including the children. It will purge all configuration files of the packages that get removed (that's why you should back them up if you editted them).

It won't remove any personal files.[/quote]
oh, okay. I haven't edited anything. this is really just a home machine with no documents to keep.

---

### Post by ubuntu_demon on 2006-06-02
$sudo pico /var/lib/debfoster/keepers

and make it like this. Please check for typo's :
```

libc6-i686
debfoster
grub
irssi-text
links2
linux-386
centericq
memtest86+
ubuntu-minimal
ubuntu-base
irssi
libc6-i686

```

$ sudo debfoster -f

---

### Post by Harold P on 2006-06-02
```
harold@ubuntu:~$ sudo debfoster -f
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-9 is to be installed
E: Broken packages
harold@ubuntu:~$


```

---

### Post by ubuntu_demon on 2006-06-02
what to do when you have acces to another machine which can connect to the internet (so you can browse the forums and chat with me). Because if you are doing the following you might get stuck without internet :

$sudo pico /var/lib/debfoster/keepers

and make it like this. Please check for typo's :

```

irssi
ubuntu-minimal
linux-386
debfoster
grub

```

$sudo debfoster -f

If it doesn't work :

$apt-cache show packagename
gives information about a package. The section which starts with "Depends:" is important. This shows all the packages that are required for this package to work and stay installed.

Do $ dpkg -l to get a list of all packages currently installed on your system. 

Remove all packages which are not children of any packages in the new keepers file.

so for example :
$sudo apt-get remove packageA packageB packageC

Now do again :

$sudo debfoster -f

I really hope this works. If it doesn't I will have to think hard.

If it succeeded go ahead with this part of my guide :
> 
Let's now configure all packages that are still unconfigured :
$ sudo dpkg --configure -a

Now there are no more broken dependencies and all packages are configured. Let's install everything :

$ sudo apt-get install ubuntu-minimal
$ sudo apt-get install ubuntu-base
$ sudo apt-get install ubuntu-desktop
(or kubuntu / edubuntu / xubuntu)

And make sure everything is upgraded :
$ sudo apt-get update
$ sudo apt-get dist-upgrade

If everything went well your broken dependencies problem is fixed.

Now do a reboot :
$ sudo reboot


---

### Post by ubuntu_demon on 2006-06-02
Please give me the result of :
$apt-cache show libc6-i686 | grep Version

I get :
```

Version: 2.3.6-0ubuntu20

```

I don't see how "but 2.3.6-9 is to be installed". Do you have any idea ?

Also we might try to force libc6-i686 to be 2.3.6-0ubuntu20

---

### Post by Harold P on 2006-06-02
No clue, here is the output:

```
harold@ubuntu:~$ apt-cache show libc6-i686 | grep Version
Version: 2.3.6-0ubuntu20
Version: 2.3.5-1ubuntu12.5.10.1
Config-Version: 2.3.5-1ubuntu12.5.10.1
harold@ubuntu:~$

```

---

### Post by ubuntu_demon on 2006-06-02
Please post the entire result :
$apt-cache show libc6-i686

---

### Post by ubuntu_demon on 2006-06-02
Please post the result of :
$apt-get upgrade -f dist-upgrade

---

### Post by ubuntu_demon on 2006-06-02
Please post the result of :
$apt-get -f install packagename=2.3.6-0ubuntu20

---

### Post by Harold P on 2006-06-02
```

harold@ubuntu:~$ apt-cache show libc6-i686
Package: libc6-i686
Priority: important
Section: libs
Installed-Size: 2344
Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: i386
Source: glibc
Version: 2.3.6-0ubuntu20
Pre-Depends: libc6 (= 2.3.6-0ubuntu20)
Filename: pool/main/g/glibc/libc6-i686_2.3.6-0ubuntu20_i386.deb
Size: 1078224
MD5sum: c5cc2b6f40bd02e4a4a1ed7f363a2cef
Description: GNU C Library: Shared libraries [i686 optimized]
 Contains the standard libraries that are used by nearly all programs on
 the system. This package includes shared versions of the standard C
 library and the standard math library, as well as many others.
 .
 This set of libraries is optimized for i686 machines, and will only be
 used if you are running a 2.6 kernel on an i686 class CPU (check the
 output of `uname -m').  This includes Pentium Pro, Pentium II/III/IV,
 Celeron CPU's and similar class CPU's (including clones such as AMD
 Athlon/Opteron, VIA C3 Nehemiah, but not VIA C3 Ezla).
 .
 This package includes support for NPTL.
 .
 WARNING: Some third-party binaries may not work well with these libraries.
 Most notably, IBM's JDK. If you experience problems with such
 applications, you will need to remove this package.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

Package: libc6-i686
Status: deinstall ok config-files
Priority: extra
Section: libs
Installed-Size: 2196
Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: i386
Source: glibc
Version: 2.3.5-1ubuntu12.5.10.1
Config-Version: 2.3.5-1ubuntu12.5.10.1
Pre-Depends: libc6 (= 2.3.5-1ubuntu12.5.10.1)
Description: GNU C Library: Shared libraries [i686 optimized]
 Contains the standard libraries that are used by nearly all programs on
 the system. This package includes shared versions of the standard C
 library and the standard math library, as well as many others.
 .
 This set of libraries is optimized for i686 machines, and will only be
 used if you are running a 2.6 kernel on an i686 class CPU (check the
 output of `uname -m').  This includes Pentium Pro, Pentium II/III/IV,
 Celeron CPU's and similar class CPU's (including clones such as AMD
 Athlon/Opteron, VIA C3 Nehemiah, but not VIA C3 Ezla).
 .
 This package includes support for NPTL.
 .
 WARNING: Some third-party binaries may not work well with these libraries.
 Most notably, IBM's JDK. If you experience problems with such
 applications, you will need to remove this package.

harold@ubuntu:~$



```


And...

```
harold@ubuntu:~$ sudo apt-get upgrade -f dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
harold@ubuntu:~$

```

---

### Post by Harold P on 2006-06-02
```
harold@ubuntu:~$ sudo apt-get -f install packagename=2.3.6-0ubuntu20
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package packagename
harold@ubuntu:~$

```

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=Harold P]```
harold@ubuntu:~$ sudo apt-get -f install packagename=2.3.6-0ubuntu20
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package packagename
harold@ubuntu:~$

```[/QUOTE]

LOL :-D
Oops I meant :

$apt-get -f install libc6-i686=2.3.6-0ubuntu20

---

### Post by Harold P on 2006-06-02
Here we go...

```
harold@ubuntu:~$ sudo apt-get -f install libc6-i686=2.3.6-0ubuntu20
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
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-9 is to be installed
E: Broken packages
harold@ubuntu:~$

```

---

### Post by ubuntu_demon on 2006-06-02
$sudo apt-get -f install libc6-i686=2.3.6-0ubuntu20 libc6=2.3.6-0ubuntu20

---

### Post by Harold P on 2006-06-02
I think we're on to something now...

```
harold@ubuntu:~$ sudo apt-get -f install libc6-i686=2.3.6-0ubuntu20 libc6=2.3.6-0ubuntu20
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  belocs-locales-bin libc6 libc6-i686 locales
Suggested packages:
  glibc-doc
The following NEW packages will be installed:
  belocs-locales-bin libc6-i686 locales
The following packages will be DOWNGRADED:
  libc6
0 upgraded, 3 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 5666kB/9114kB of archives.
After unpacking 15.0MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by ubuntu_demon on 2006-06-02
Okay good.  Press Y.

And if everything succeeds go again to this post :
[http://www.ubuntuforums.org/showpost.php?p=1084500&postcount=37](http://www.ubuntuforums.org/showpost.php?p=1084500&postcount=37)

And after that continue with my original guide here : 
> 
Let's run this command again to make sure it has removed everything that's problematic :
$ sudo apt-get -f remove

Let's now configure all packages that are still unconfigured :
$ sudo dpkg --configure -a

Now there are no more broken dependencies and all packages are configured. Let's install everything :

$ sudo apt-get install ubuntu-minimal
$ sudo apt-get install ubuntu-base
$ sudo apt-get install ubuntu-desktop
(or kubuntu / edubuntu / xubuntu)


---

### Post by Harold P on 2006-06-02
```
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com dapper/main libc6 2.3.6-0ubuntu20 [4588kB]
Get:2 http://archive.ubuntu.com dapper/main libc6-i686 2.3.6-0ubuntu20 [1078kB]
Fetched 5666kB in 10s (518kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Selecting previously deselected package belocs-locales-bin.
(Reading database ... 125808 files and directories currently installed.)
Unpacking belocs-locales-bin (from .../belocs-locales-bin_2.3.5-5ubuntu7_i386.deb) ...
Unpacking locales (from .../locales_2.3.18_all.deb) ...
dpkg: error processing /var/cache/apt/archives/locales_2.3.18_all.deb (--unpack):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package tzdata
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg - warning: downgrading libc6 from 2.3.6-9 to 2.3.6-0ubuntu20.
Preparing to replace libc6 2.3.6-9 (using .../libc6_2.3.6-0ubuntu20_i386.deb) ...
Unpacking replacement libc6 ...
Replaced by files in installed package tzdata ...
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.3.18_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
harold@ubuntu:~$

```

Locales... :-#

---

### Post by ubuntu_demon on 2006-06-02
$ apt-cache show locales

---

### Post by Harold P on 2006-06-02
```
harold@ubuntu:~$ sudo apt-cache show locales
Package: locales
Priority: required
Section: base
Installed-Size: 12716
Maintainer: Martin Pitt <martin.pitt@ubuntu.com>
Architecture: all
Source: langpack-locales
Version: 2.3.18
Replaces: belocs-locale-data, base-config, libc6 (<< 2.3.6-0ubuntu6), libc6.1 (<< 2.3.6-0ubuntu6)
Depends: belocs-locales-bin (>= 2.3.5-5ubuntu1)
Conflicts: belocs-locale-data, base-config
Filename: pool/main/l/langpack-locales/locales_2.3.18_all.deb
Size: 3282568
MD5sum: 03132494d00d3d70aa7d922654b7dc9f
Description: common files for locale support
 This package provides support for localized environments (locales).
 It installs character and transliteration maps, provides the POSIX
 locale definition and provides common scripts for language pack
 handling.
 .
 The actual locale definitions are not part of this package, these are
 shipped in the language packs and are installed and removed
 automatically.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

harold@ubuntu:~$

```

---

### Post by ubuntu_demon on 2006-06-02
Now I want to know what this tzdata package is. 

$apt-cache show tzdata

and it's status :
$dpkg -l | grep tzdata

---

### Post by Harold P on 2006-06-02
```
harold@ubuntu:~$ sudo apt-cache show tzdata
Package: tzdata
Status: install ok installed
Priority: required
Section: libs
Installed-Size: 5692
Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: all
Version: 2006c-2
Replaces: libc0.1, libc0.3, libc6, libc6.1
Description: Time Zone and Daylight Saving Time Data
 This package contains data that represent the history of local time for many
 representative locations around the globe. It is updated periodically to
 reflect changes made by political bodies to time zone boundaries, UTC offsets,
 and daylight-saving rules

harold@ubuntu:~$

```

```
harold@ubuntu:~$ dpkg -l | grep tzdata
ii  tzdata                                 2006c-2  Time Zone and Daylight Saving Time Data
harold@ubuntu:~$

```

---

### Post by ubuntu_demon on 2006-06-02
$sudo apt-get remove -f tzdata

---

### Post by Harold P on 2006-06-02
```
harold@ubuntu:~$ sudo apt-get remove -f tzdata
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  belocs-locales-bin: Depends: locales
  libc6: Depends: locales (>= 2.3.11)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
harold@ubuntu:~$

```

---

### Post by ubuntu_demon on 2006-06-02
$sudo apt-get remove tzdata locales -f

---

### Post by Harold P on 2006-06-02
```
harold@ubuntu:~$ sudo apt-get remove tzdata locales -f
Reading package lists... Done
Building dependency tree... Done
Package locales is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  belocs-locales-bin: Depends: locales
  libc6: Depends: locales (>= 2.3.11)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
harold@ubuntu:~$


```

---

### Post by ubuntu_demon on 2006-06-02
print the instructions of these posts on your printer or put them into a text file if you don't have a printer. 
[http://www.ubuntuforums.org/showpost.php?p=1084614&postcount=48](http://www.ubuntuforums.org/showpost.php?p=1084614&postcount=48)
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

Now follow the instructions of this post carefully and make sure you understand what you are doing. Be very careful :
[http://www.ubuntuforums.org/showpost.php?p=1084614&postcount=48](http://www.ubuntuforums.org/showpost.php?p=1084614&postcount=48)

Do everything from ctrl-alt-f1 ctrl-alt-f2 and such. We'll chat on irc while you do it.

okay ?

this is on your **own risk** ofcourse

I wish you luck! :)

---

### Post by ubuntu_demon on 2006-06-02
**This is a big puzzle.** But IMHO it's still possible to fix it. I don't know how much more time it is going to take to fix it though.

If after a while you will get really desperate you can always try the suggestion here :
[http://www.ubuntuforums.org/showpost.php?p=1084219&postcount=22](http://www.ubuntuforums.org/showpost.php?p=1084219&postcount=22)

For most motherboards there are overriding master passwords to be found on the internet. 
If you know exactly what motherboard you have and if you write down which bios version you might be lucky and find it fast.

to get some information about your motherboard :
$lspci 
$lspci -vv

you could also open up the case and read the fine print on the motherboard to try to discover exactly which motherboard you have.

some information about your bios is shown during the starting up of your pc. You can also try to press pause or some other keys.

---

### Post by ubuntu_demon on 2006-06-02
my /var/lib/locales/supported.d/en :

```

en_HK.UTF-8 UTF-8
en_DK.UTF-8 UTF-8
en_IN UTF-8
en_ZW.UTF-8 UTF-8
en_NZ.UTF-8 UTF-8
en_PH.UTF-8 UTF-8
en_US.UTF-8 UTF-8
en_GB.UTF-8 UTF-8
en_AU.UTF-8 UTF-8
en_SG.UTF-8 UTF-8
en_BW.UTF-8 UTF-8
en_ZA.UTF-8 UTF-8
en_CA.UTF-8 UTF-8
en_IE.UTF-8 UTF-8

```

backup yours and try to replace it with mine.

what's the result of :
$cat /etc/environment

---

### Post by Harold P on 2006-06-02
Okay, here's my /etc/environment

```
harold@ubuntu:~$ cat /etc/environment
LANGUAGE="en"

LANG=en_US.UTF-8
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
harold@ubuntu:~$

```

---

### Post by ubuntu_demon on 2006-06-02
your /etc/environment looks fine

Try the usual things that I have suggested to see whether changing "/var/lib/locales/supported.d/en" made any difference.

---

### Post by Harold P on 2006-06-02
[quote=ubuntu_demon]your /etc/environment looks fine[/quote]
Yep... suggestions?

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=Harold P]Yep... suggestions?[/QUOTE]
Try the usual things that I have suggested to see whether changing "/var/lib/locales/supported.d/en" made any difference.

Do some reading here :
[http://www.linux.com/article.pl?sid=05/10/12/1952217](http://www.linux.com/article.pl?sid=05/10/12/1952217)

search the forums installation and upgrade forum for similar problems. Search for key packages and errors.

If you don't know what to do anymore and you are getting frustrated you might want to take this into consideration :
[http://www.ubuntuforums.org/showpost.php?p=1084924&postcount=71](http://www.ubuntuforums.org/showpost.php?p=1084924&postcount=71)

Anyhow I'm willing to help next time that I have time. I'm going to sleep now :-D.

---

### Post by Harold P on 2006-06-03
[quote=ubuntu_demon]If after a while you will get really desperate you can always try the suggestion here :
[http://www.ubuntuforums.org/showpost.php?p=1084219&postcount=22]("http://www.ubuntuforums.org/showpost.php?p=1084219&postcount=22")
[/quote]

sudo rm -f / won't work?
[SIZE=6]*_**PEOPLE WHO ARE READING THIS DON'T DO IT!**_*[/SIZE]

---

### Post by ubuntu_demon on 2006-06-03
no sudo rm -f **won't** work. **Don't do that!** But wait until you follow this guys advice. I have some idea's left.

The most important one here :
[http://www.ubuntuforums.org/showpost.php?p=1057281&postcount=8](http://www.ubuntuforums.org/showpost.php?p=1057281&postcount=8)


After that try this commands in all orders :
$sudo apt-get remove tzdata 
$sudo apt-get remove tzdata -f
$sudo apt-get -f install libc6-i686=2.3.6-0ubuntu20 libc6=2.3.6-0ubuntu20

And follow my guide after that as usual.

[I]If you would have had acces to booting from cd-rom these might have helped :
[http://ubuntuforums.org/showthread.php?t=137189](http://ubuntuforums.org/showthread.php?t=137189)
[https://wiki.ubuntu.com/Installation/FromAnotherDistro](https://wiki.ubuntu.com/Installation/FromAnotherDistro)
[https://wiki.ubuntu.com/Installation/FromKnoppix](https://wiki.ubuntu.com/Installation/FromKnoppix)

although if you would be able to boot from cd then you could easily reinstall :-P[/I]

I have to go now but I'll check later on you.

---

### Post by Harold P on 2006-06-03
[quote=ubuntu_demon]no sudo rm -f **won't** work. **Don't do that!** But wait until you follow this guys advice. I have some idea's left.

The most important one here :
[http://www.ubuntuforums.org/showpost.php?p=1057281&postcount=8]("http://www.ubuntuforums.org/showpost.php?p=1057281&postcount=8")


After that try this commands in all orders :
$sudo apt-get remove tzdata 
$sudo apt-get remove tzdata -f
$sudo apt-get -f install libc6-i686=2.3.6-0ubuntu20 libc6=2.3.6-0ubuntu20

And follow my guide after that as usual.

[I]If you would have had acces to booting from cd-rom these might have helped :
[http://ubuntuforums.org/showthread.php?t=137189]("http://ubuntuforums.org/showthread.php?t=137189")
[https://wiki.ubuntu.com/Installation/FromAnotherDistro]("https://wiki.ubuntu.com/Installation/FromAnotherDistro")
[https://wiki.ubuntu.com/Installation/FromKnoppix]("https://wiki.ubuntu.com/Installation/FromKnoppix")

although if you would be able to boot from cd then you could easily reinstall :-P[/I]

I have to go now but I'll check later on you.[/quote]

```
harold@ubuntu:~$ sudo cp /var/lib/locales/supported.d/local /var/lib/locales/supported.d/local.old
harold@ubuntu:~$ sudo cp /usr/share/i18n/SUPPORTED /var/lib/locales/supported.d/local
cp: cannot stat `/usr/share/i18n/SUPPORTED': No such file or directory
harold@ubuntu:~$ sudo dpkg-reconfigure --force locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
harold@ubuntu:~$

```

I found a DOS floppy, and i'm just going to fdisk it. I really appreciate the help you gave, ubuntu_demon. :)

Thanks,
Harold

---

### Post by Harold P on 2006-06-03
[quote=Harold P]```
harold@ubuntu:~$ sudo cp /var/lib/locales/supported.d/local /var/lib/locales/supported.d/local.old
harold@ubuntu:~$ sudo cp /usr/share/i18n/SUPPORTED /var/lib/locales/supported.d/local
cp: cannot stat `/usr/share/i18n/SUPPORTED': No such file or directory
harold@ubuntu:~$ sudo dpkg-reconfigure --force locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
harold@ubuntu:~$

``` 
I found a DOS floppy, and i'm just going to fdisk it. I really appreciate the help you gave, ubuntu_demon. :)

Thanks,
Harold[/quote]
And... done! I'm running Breezy on this machine, though. My dapper cd had a read error... Since this machine is pretty much wiped clean, would an upgrade be smart, or clean install?

---

### Post by ubuntu_demon on 2006-06-03
Since you have a nice and clean breezy installation without packages from non-official repositories there's a good chance a dist-upgrade to Dapper won't result in any problems.

make sure you read this thread prior to upgrading :
[http://www.ubuntuforums.org/showthread.php?t=185467](http://www.ubuntuforums.org/showthread.php?t=185467)

---

### Post by Hausi on 2008-06-03
> **Harold P said:**
> Hello,

I'm trying to get this machine to work properly. A lot of packages were broken and such, and I'm *constantly* getting errors about "locale(s)". It's quite annoying, it's keeping me from installing any new packages. So, I went into terminal, updated, and dist-upgraded to resolve the problem... but I encountered the following error. Here is the output:

```

harold@ubuntu:~$ sudo apt-get update
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Fetched 4B in 1s (3B/s)
Reading package lists... Done
harold@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  belocs-locales-bin: Depends: locales
E: Unmet dependencies. Try using -f.
harold@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  locales
The following NEW packages will be installed:
  locales
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/3283kB of archives.
After unpacking 13.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 120494 files and directories currently installed.)
Unpacking locales (from .../locales_2.3.18_all.deb) ...
dpkg: error processing /var/cache/apt/archives/locales_2.3.18_all.deb (--unpack):
 trying to overwrite `/usr/share/zoneinfo/Africa/Algiers', which is also in package tzdata
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.3.18_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
harold@ubuntu:~$

``` 
[This]("http://www.psychocats.net/ubuntu/sources.php") is my sources.list (if it helps...)

I would **really** like to do a fresh install, but my dad forgot the password to this machine's bios. (just great. :-|) And because of that, it always boots in this order: Floppy, IDE, and then CD drive. So this leaves me no choice but to dist-upgrade, unless there is another approach? Also, I'd like to say that when I was upgrading, I was doing too much (running at 100% CPU) at one time and so X crashed on me, so (not thinking) I restarted it (CTRL + ALT + Backspace). I was bombarded with around 3 errors regarding that X could not start, and that things were missing. So I thought, eh... no big deal, and followed with an apt-get update'd and dist-upgrade. After about a few hours of downloading new packages and installing, X finally started up. I logged in as normal, and saw new sleek start-up thingy and reddish background then was prompted with a notice. "blah blah blah icon could not be found". I immediately knew a bunch of my packages were broken. I tried opening Gaim, amarok, and a few other apps but they just didn't work. Thankfully firefox wasn't harmed. Anyways, that's where I am right now: I'm stuck with this package that just **won't** update, blocking me from installing newer applications, and it's keeping me from getting back to where I need to be.

Any help would be **GREATLY** appreciated.

Thanks in advance,
HP

P.S. I *am* willing to wipe this drive so this box will boot past IDE to a CD, but I need a sufficient way of doing this.
harold, if can open the notebook and get at the cmos battery, taking this out for 15 minutes should clear the bios password for good :-) of course you must check/configure all bios settings afterwards
_hans

---

