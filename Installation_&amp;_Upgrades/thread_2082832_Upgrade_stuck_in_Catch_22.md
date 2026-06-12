---
title: "Upgrade stuck in Catch 22"
date: 2012-11-10
forum: Installation &amp; Upgrades
---

### Post by MidnightJava on 2012-11-10
I'm trying to upgrade from 11.10 to 12.04, and I got stuck in a Catch 22 that there seems to be no way out of. While upgrading the libc6 package, a warning came up telling me that I had to restart or stop xscreensaver, or I could be locked out of my session and be unable to authenticate.

However, the upgrade process seems to have locked out any ability to get access to a separate terminal so I can stop the xscreensaver process. When I try to launch Terminal, the icon pulses slowly for several seconds, but no Terminal screen appears. Likewise I'm unable to launch System Settings, but I was ale to launch Chrome, through which I'm typing this post.

I thought maybe the Terminal window used by the Distribution Upgrade might be a way to stop xscreensaver. So I entered ctrl-Z, thinking I could background the upgrade process and then foreground it after stopping xscreensaver. Bad idea. It seems to have just frozen the upgrade process. At least nothing is happening in the Terminal window. The prompt never appeared when I entered ctrl-Z. I tried typing bg and fg anyway, but nothing changes. And even if it's still running in the background, I'm going to miss any further user prompts.I connected via ssh from a separate system and killed xscreensaver, but AFAICT the upgrade process remains in limbo.

Am I as screwed as I appear to be, or is there something I can do from here?

---

### Post by MidnightJava on 2012-11-10
I see that "kill pidnumber -SIGCONT" can be used to un-suspend the process, but I don't know which process to target. I ran ps -efA from the ssh session, and it's not obvious which process is the Distribution Upgrade.

---

### Post by MidnightJava on 2012-11-10
Sending the SIGCONT signal to all the likely processes was no help. I decided to kill the upgrade process and see if I could re-start the upgrade. I killed the dpkg process, and that had the effect of causing the upgrade to continue, though with many many errors. It kept reporting the errors but continued the upgrade process. After quite a while it reported "too many errors" and said processing would stop. But with the upgrade partially accomplished, I figured I'd have problems after  reboot, and I did indeed.

It boots into command line mode only. I configured the network interface and ran apt-get update successfully. But when I try to run sudo apt-get -f dist-upgrade or sudo apt-get upgrade or sudo apt-get -f install I get errors. It says it can't find a file name for lib6c, which is the package it was upgrading when the failure occurred. If I try to install lib6c, it fails because it can't satisfy the dependencies. I see numerous messages where it says failed to install the required version because an older version is set to be installed.

Is there something I can do from here to fix the installation?

---

### Post by MidnightJava on 2012-11-12
I realize it's difficult to figure out how to fix my system in the partial-update state I've gotten into, but let me try to highlight the specific question I'm asking about this.

The dependency failure messages when I try to install lib6c seem to be saying, for example, "I need version 5.14 of package XYZ to satisfy this dependency, but you've asked me to install version 5.12 of package XYZ." Sorry I don't have access to the system now to give the exact working. I interpreted the message to mean there's a conflict between the dependency and a queued upgrade request that has not yet been executed for some reason.

So what I'm wondering is, can I somehow tell apt-get to forget about installing those earlier versions, and just install the later version that it needs?

Is it worth messing with the files in /var/lib/apt/archives or /var/lib/apt/lists? Or is there a way to tell apt-get to install the later version anyway?

---

### Post by oldfred on 2012-11-13
Is there perhaps some inconsistency in sources?

cp /etc/apt/sources.list ~/sources.list.backup
gksu gedit /etc/apt/sources.list

Generally when upgrading you need to remove any extra sources you may have added as they may not have new versions or may cause conflicts.

Otherwise you seem to have done more than I know in trying to update.

---

### Post by MidnightJava on 2012-11-13
Thanks, I'll look at the sources list when I get home this evening. But what exactly am I looking for to identify new sources that were added during the partial upgrade?

---

### Post by oldfred on 2012-11-13
Anything that does not say precise. Beyond that I really do not know. 

You can post your entire sources file, but if you do include in inside code tags (Highlight & click # in edit panel).

---

### Post by MidnightJava on 2012-11-13
All entries not commented out in sources.list were precise sources except the last one. I commented it out and then tried

```

sudo apt-get -f clean
sudo apt-get -f autoclean
sudo apt-get -f install

```

As before, it fails at the very end, with error "no file name for libc6"

I tried

```
sudo apt-get -f install libc6
```

and that's when I get the dependency errors I mentioned previously, in which apt-get seems to be stuck on trying to install an earlier version of various packages, and so failing to resolve a dependency on a newer version.

I've pasted my sources.list file below, as I found it (before commenting out the last line). I pasted below that the output I get when trying to install libc6.

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ubuntu.mirrors.pair.com/archive/ precise main restricted
deb-src http://ubuntu.mirrors.pair.com/archive/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.mirrors.pair.com/archive/ precise-updates main restricted
deb-src http://ubuntu.mirrors.pair.com/archive/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.mirrors.pair.com/archive/ precise universe
deb-src http://ubuntu.mirrors.pair.com/archive/ precise universe
deb http://ubuntu.mirrors.pair.com/archive/ precise-updates universe
deb-src http://ubuntu.mirrors.pair.com/archive/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.mirrors.pair.com/archive/ precise multiverse
deb-src http://ubuntu.mirrors.pair.com/archive/ precise multiverse
deb http://ubuntu.mirrors.pair.com/archive/ precise-updates multiverse
deb-src http://ubuntu.mirrors.pair.com/archive/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://ubuntu.mirrors.pair.com/archive/ precise-security main restricted
deb-src http://ubuntu.mirrors.pair.com/archive/ precise-security main restricted
deb http://ubuntu.mirrors.pair.com/archive/ precise-security universe
deb-src http://ubuntu.mirrors.pair.com/archive/ precise-security universe
deb http://ubuntu.mirrors.pair.com/archive/ precise-security multiverse
deb-src http://ubuntu.mirrors.pair.com/archive/ precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
# deb http://archive.canonical.com/ lucid partner
deb-src http://archive.canonical.com/ lucid partner

```

```
Reading package lists...
Building dependency tree...
Reading state information...
libc6 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 e2fsprogs : PreDepends: e2fslibs (= 1.41.14-1ubuntu3) but 1.42-1ubuntu2 is to be installed
 evolution : Depends: libebook1.2-12 (>= 3.2.2)
             Depends: libecal1.2-10 (>= 3.2.2)
             Depends: libedataserver1.2-15 (>= 3.2.2)
             Depends: evolution-common (= 3.2.2-0ubuntu0.1) but 3.2.3-0ubuntu6 is to be installed
 evolution-plugins : Depends: evolution (= 3.2.3-0ubuntu6) but 3.2.2-0ubuntu0.1 is to be installed
 libaa1:i386 : Depends: libncurses5:i386 (>= 5.5-5~) but it is not going to be installed
 libalgorithm-diff-xs-perl : Depends: perlapi-5.14.2
 libapparmor-perl : Depends: perlapi-5.14.2
 libapt-pkg-perl : Depends: perl-base (>= 5.14.2-6ubuntu1) but 5.12.4-4 is to be installed
                   Depends: perlapi-5.14.2
 libcairo-perl : Depends: perlapi-5.14.2
 libclone-perl : Depends: perlapi-5.14.2
 libdatetime-perl : Depends: perlapi-5.14.2
 libdbd-mysql-perl : Depends: perlapi-5.14.2
 libdbi-perl : Depends: perlapi-5.14.2
 libgettextpo0:i386 : Depends: libncurses5:i386 (>= 5.5-5~) but it is not going to be installed
 libglib-perl : Depends: perlapi-5.14.2
 libgtk2-perl : Depends: perlapi-5.14.2
 libhtml-parser-perl : Depends: perlapi-5.14.2
 libio-pty-perl : Depends: perlapi-5.14.2
 liblist-moreutils-perl : Depends: perlapi-5.14.2
 libncurses5 : Depends: libtinfo5 (= 5.9-1ubuntu5) but 5.9-4 is to be installed
 libnet-dbus-perl : Depends: perlapi-5.14.2
 libnet-dns-perl : Depends: perlapi-5.14.2
 libnet-ssleay-perl : Depends: perlapi-5.14.2
 libnih-dbus1 : Depends: libnih1 (= 1.0.3-4ubuntu9) but 1.0.3-4ubuntu2 is to be installed
 libnih1 : Depends: libc6 (< 2.14) but 2.15-0ubuntu10.3 is to be installed
 libpackage-stash-xs-perl : Depends: perlapi-5.14.2
 libpam-modules : PreDepends: libpam-modules-bin (= 1.1.3-2ubuntu2.1)
 libpango-perl : Depends: perlapi-5.14.2
 libparams-classify-perl : Depends: perlapi-5.14.2
 libparams-util-perl : Depends: perlapi-5.14.2
 libparams-validate-perl : Depends: perlapi-5.14.2
 libperl5.14 : Depends: perl-base (= 5.14.2-6ubuntu2.1) but 5.12.4-4 is to be installed
 libpurple0 : Depends: perl-base (>= 5.14.2-6ubuntu2) but 5.12.4-4 is to be installed
              Depends: perlapi-5.14.2
 libsocket6-perl : Depends: perlapi-5.14.2
 libssl1.0.0 : Breaks: openssh-server (< 1:5.9p1-4)
 libssl1.0.0:i386 : Breaks: openssh-server (< 1:5.9p1-4)
 libsub-name-perl : Depends: perlapi-5.14.2
 libterm-readkey-perl : Depends: perlapi-5.14.2
 libtext-charwidth-perl : Depends: perl-base (>= 5.14.2-3) but 5.12.4-4 is to be installed
                          Depends: perlapi-5.14.2
 libtext-iconv-perl : Depends: perl-base (>= 5.14.2-6) but 5.12.4-4 is to be installed
                      Depends: perlapi-5.14.2
 libuuid-perl : Depends: perl-base (>= 5.14.2-6ubuntu1) but 5.12.4-4 is to be installed
                Depends: perlapi-5.14.2
 libxml-parser-perl : Depends: perlapi-5.14.2
 linux-image-generic : Depends: linux-image-3.2.0-32-generic but it is not going to be installed
 mysql-common : Breaks: mysql-server-5.1 but 5.1.63-0ubuntu0.11.10.1 is to be installed
 mysql-server-5.1 : Depends: mysql-client-5.1 (>= 5.1.63-0ubuntu0.11.10.1) but it is not installable
                    Depends: mysql-server-core-5.1 (= 5.1.63-0ubuntu0.11.10.1) but it is not installable
 mysql-server-5.5 : Breaks: mysql-server-5.1 but 5.1.63-0ubuntu0.11.10.1 is to be installed
 mysql-server-core-5.5 : Breaks: mysql-server-5.0
                         Breaks: mysql-server-5.1 but 5.1.63-0ubuntu0.11.10.1 is to be installed
 openssh-server : Depends: openssh-client (= 1:5.8p1-7ubuntu1)
 perl : Depends: perl-base (= 5.14.2-6ubuntu2.1) but 5.12.4-4 is to be installed
 wine1.4 : Breaks: wine1.3 (< 1.4-0ubuntu1)
 wine1.4-amd64 : Breaks: wine1.3 (< 1.4-0ubuntu1)
 wine1.4-i386:i386 : Depends: libncurses5:i386 but it is not going to be installed
                     Recommends: gettext:i386 but it is not going to be installed
                     Breaks: wine1.3 (< 1.4-0ubuntu1)

```

---

### Post by oldfred on 2012-11-13
I do not really know what to look for. But it seems to be trying to install two different versions of some of the apps.

I went back to my precise and my two archive entries are both commented out. You still have several??

Some other threads with sources issues that may tell you something that I cannot.

Best command to reset apt sources to distro release defaults?
[http://ubuntuforums.org/showthread.php?t=1858451](http://ubuntuforums.org/showthread.php?t=1858451)

Repair sources issues, delete old/obsolete & refresh:
[http://ubuntuforums.org/showthread.php?t=2037992](http://ubuntuforums.org/showthread.php?t=2037992)

---

### Post by MidnightJava on 2012-11-18
Thanks for the suggestions. None of those methods worked for me, so I went ahead and created a fresh installation of 12.10. When installing from the LiveCD, I selected the option to upgrade the existing (broken) installation at first. This seemed to work, as I was able to boot into the GUI again. But I was getting strange errors in apt-get, so it was apparent that my installation was still not 100% right. So I did a fresh install from the LiveCD.

I'll mark the thread SOLVED because I think I've established that when you ctrl-Z the upgrade process, the only reasonable recovery option is a fresh install. I'll never do that again.

---

