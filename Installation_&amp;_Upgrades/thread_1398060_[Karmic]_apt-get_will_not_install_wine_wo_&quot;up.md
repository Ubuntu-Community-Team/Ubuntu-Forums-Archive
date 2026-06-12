---
title: "[Karmic] apt-get will not install wine w/o &quot;upgrading&quot; libc6"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by studout on 2010-02-04
I am trying to install wine on a Karmic box, but apt-get is trying to upgrade libc6 at the same time. [COLOR="White"]_[/COLOR]I know better than to touch the runtime C library. [COLOR="White"]_[/COLOR]
When I boot the same computer with a live session of Karmic, apt-get installs wine flawlessly.

What is going on here? [COLOR="White"]_[/COLOR]Why is apt-get trying to do this?

Thank you,
Studout

____________________
Here is the output from Karmic where it *did not* work.
```
root@machine:~# apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract cpp-4.4 gcc-4.4 gcc-4.4-base ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32nss-mdns lib32stdc++6
  lib32v4l-0 lib32z1 libasound2 libc-bin libc-dev-bin libc6 libc6-dev libc6-i386 libgcc1 libgomp1 libstdc++6 samba-common smbclient
  ttf-liberation ttf-mscorefonts-installer winbind wine-gecko
Suggested packages:
  gcc-4.4-locales gcc-4.4-multilib libmudflap0-4.4-dev gcc-4.4-doc libgcc1-dbg libgomp1-dbg libmudflap0-dbg libcloog-ppl0 libppl-c2
  libppl7 lib32asound2-plugins glibc-doc manpages-dev smbfs
The following NEW packages will be installed:
  cabextract ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32nss-mdns lib32stdc++6 lib32v4l-0 lib32z1 libc6-i386
  ttf-liberation ttf-mscorefonts-installer winbind wine wine-gecko
The following packages will be upgraded:
  cpp-4.4 gcc-4.4 gcc-4.4-base libasound2 libc-bin libc-dev-bin libc6 libc6-dev libgcc1 libgomp1 libstdc++6 samba-common smbclient
13 upgraded, 16 newly installed, 0 to remove and 198 not upgraded.
Need to get 81.7MB of archives.
After this operation, 221MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
root@machine:~#
```


Here is the output showing when it *did* work (under the live session.)
```
ubuntu@ubuntu:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract libaudio2 samba-common smbclient ttf-liberation
  ttf-mscorefonts-installer winbind wine-gecko
Suggested packages:
  nas smbfs
The following NEW packages will be installed:
  cabextract libaudio2 ttf-liberation ttf-mscorefonts-installer winbind wine
  wine-gecko
The following packages will be upgraded:
  samba-common smbclient
2 upgraded, 7 newly installed, 0 to remove and 214 not upgraded.
Need to get 30.7MB of archives.
After this operation, 73.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(snip)

```

---

### Post by gmargo on 2010-02-04
> 
Why is apt-get trying to do this?
13 upgraded, 16 newly installed, 0 to remove and **198 not  upgraded**.
Because your system is out of date. Security updates have been issued since you installed or last upgraded. There is no problem with upgrading your libc, just reboot afterwards.

---

### Post by studout on 2010-02-04
Thank for the reply.

Realizing that apt-get was willing to install wine under the live session, but not the recently installed version, I decided to back it up, wipe it, and reinstall.  Lo, apt-get decides it's willing to install wine w/o updating libc6.

I had installed some packages such as openssh-server, compizconfig-settings-manager, mplayer, and vim.  The hardware tool (sys->admin->hw) has also installed the nVidia driver/s for my video card.

I can only assume that one of those packages, one that I installed but do not recall, or a package that was installed/upgraded as a result of the previous; has somehow caused apt-get's version/dependency tracking to fail.

Regardless... it is working now, so I'm set until this happens again :rolleyes:

Thank you again for the reply, and to all those that looked and considered my question.

---

