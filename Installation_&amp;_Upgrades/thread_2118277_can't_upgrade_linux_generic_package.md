---
title: "can't upgrade linux generic package"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by dsikl on 2013-02-20
Hello everyone, can someone please tell me what's wrong with my puter, the upgrade always fails on installing linux generic package. For more than half a year now... Here's what the update manager spits out:

```

E: /usr/share/syslinux/themes/debian/extlinux: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-31-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-30-generic (3.2.0-30.48) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-38-generic...
P: Writing config for /boot/vmlinuz-3.2.0-33-generic...
P: Writing config for /boot/vmlinuz-3.2.0-32-generic...
P: Writing config for /boot/vmlinuz-3.2.0-31-generic...
P: Writing config for /boot/vmlinuz-3.2.0-30-generic...
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-27-generic...
P: Writing config for /boot/vmlinuz-3.2.0-26-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.0.0-12-generic...
P: Writing config for /boot/vmlinuz-2.6.38-15-generic...
P: Writing config for /boot/vmlinuz-2.6.32-41-generic...
P: Writing config for Windows 7 (loader) on /dev/sda1...
P: Writing config for Windows Recovery Environment (loader) on /dev/sda4...
E: /usr/share/syslinux/themes/debian/extlinux: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-30-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-30-generic; however:
  Package linux-image-3.2.0-30-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.30.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured

```

Any help would be much appreciated!

Cheers!

---

### Post by dsikl on 2013-02-21
anyone?:confused:

---

### Post by dino99 on 2013-02-21
> **dsikl said:**
> anyone?:confused:

What to say ?  ;);)
i wonder how many kernels you need (the last 2 are enough, so purge the others)

have you already heard something called "maintenance" ?
Cleaning the room is not loosing time  , run the usual command to make room
(clean/autoclean/autoremove/gtkorphan/bleachbit)

then run:
```
sudo dpkg-reconfigure -phigh -a
```
(be patient it can take a while, dont stop it yourself)

note: post the output of: 
```
cat /etc/apt/sources.list
```

note2: use the tag icon for posting, instead of an endless/unreadable list

):P):P

---

### Post by dsikl on 2013-02-21
hey dino99, nice to hear from you again! :)

i'm quite far from your level of understanding, but i'll try my best.

i looked up purging kernels, and i came up with the following commands and outputs:

```
moreflux@lenux:~$ uname -a
Linux lenux 3.2.0-38-generic #60-Ubuntu SMP Wed Feb 13 13:27:35 UTC 2013 i686 i686 i386 GNU/Linux
moreflux@lenux:~$ dpkg-query -l | awk '/linux-image-*/ {print $2}'
linux-image-2.6.32-21-generic
linux-image-2.6.32-30-generic
linux-image-2.6.32-32-generic
linux-image-2.6.32-33-generic
linux-image-2.6.32-34-generic
linux-image-2.6.32-35-generic
linux-image-2.6.32-36-generic
linux-image-2.6.32-37-generic
linux-image-2.6.32-38-generic
linux-image-2.6.32-39-generic
linux-image-2.6.32-40-generic
linux-image-2.6.32-41-generic
linux-image-2.6.35-32-generic
linux-image-2.6.38-15-generic
linux-image-3.0.0-12-generic
linux-image-3.2.0-24-generic
linux-image-3.2.0-25-generic
linux-image-3.2.0-26-generic
linux-image-3.2.0-27-generic
linux-image-3.2.0-29-generic
linux-image-3.2.0-30-generic
linux-image-3.2.0-31-generic
linux-image-3.2.0-32-generic
linux-image-3.2.0-33-generic
linux-image-3.2.0-38-generic
linux-image-generic
moreflux@lenux:~$ sudo apt-get --purge remove <linux-image-2.6.32-21-generic>
bash: syntax error near unexpected token `newline'
moreflux@lenux:~$ sudo apt-get --purge remove linux-image-2.6.32-21-generic
[sudo] password for moreflux: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libutouch-grail1 libutouch-evemu1 libutouch-frame1 libutouch-geis1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  linux-image-2.6.32-21-generic*
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 411671 files and directories currently installed.)
Removing linux-image-2.6.32-21-generic ...
Purging configuration files for linux-image-2.6.32-21-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-21-generic /boot/vmlinuz-2.6.32-21-generic
update-initramfs: Deleting /boot/initrd.img-2.6.32-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 2.6.32-21-generic /boot/vmlinuz-2.6.32-21-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-38-generic...
P: Writing config for /boot/vmlinuz-3.2.0-33-generic...
P: Writing config for /boot/vmlinuz-3.2.0-32-generic...
P: Writing config for /boot/vmlinuz-3.2.0-31-generic...
P: Writing config for /boot/vmlinuz-3.2.0-30-generic...
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-27-generic...
P: Writing config for /boot/vmlinuz-3.2.0-26-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.0.0-12-generic...
P: Writing config for /boot/vmlinuz-2.6.38-15-generic...
P: Writing config for /boot/vmlinuz-2.6.32-41-generic...
P: Writing config for Windows 7 (loader) on /dev/sda1...
P: Writing config for Windows Recovery Environment (loader) on /dev/sda4...
E: /usr/share/syslinux/themes/debian/extlinux: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-21-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-21-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.32-21-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

as you can see, the error keeps appearing, and i also always receive a crash report popup with the same error.

i also tried installing bleachbit for instance, had the same problem appear. i can't seem to install or remove anything anymore, probably because it decided it wanted to solve this issue before doing anything else??

and even after running

```
sudo dpkg-reconfigure -phigh -a
```

and completing the couple hours long process, i get the same error as above :(

here's the output that you requested, although i'm not sure if that's useful yet:

```
moreflux@lenux:~$ cat /etc/apt/sources.list
# added by the release upgrader
deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423.2)]/ precise main restricted
# added by the release upgrader
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111011)]/ oneiric main restricted
# deb cdrom:[Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)]/ lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
# deb http://ftp.de.debian.org/debian squeeze main
deb http://archive.canonical.com/ precise partner
deb-src http://archive.canonical.com/ precise partner
```

i can't even begin to try and decipher it, but i wouldn't mind understanding what seems to be the trouble (if you can be bothered explaining, that is).......

any chance we can still fix it?

---

### Post by dsikl on 2013-02-22
oh and btw. what did you mean with "tag icon"?

cheers!

---

### Post by dsikl on 2013-02-22
i seem to be having a similar problem on my desktop......

---

### Post by dsikl on 2013-02-24
:nudge: :)

---

### Post by dsikl on 2013-02-25
anyone else perhaps?

---

### Post by steeldriver on 2013-02-25
Did you at some point add extlinux from a debian repository? 

> **dsikl said:**
> ```

E: /usr/share/syslinux/themes/[COLOR=Red]**debian**[/COLOR]/extlinux: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-extlinux exited with return code 1

``````

# deb http://ftp.de.**[COLOR=Red]debian[/COLOR]**.org/debian squeeze main

```

What does

```
dpkg-query --list extlinux
```show?

---

### Post by dsikl on 2013-02-25
whoa am i happy to see your reply!!! thank you so much!

no idea what an extlinux is, i might have added it, but wouldn't have a clue when or how or why :(

```
moreflux@lenux:~$ dpkg-query --list extlinux
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  extlinux                          2:4.05+dfsg-2                     collection of boot loaders (ext2/3/4 and btrfs bootloader)

```

any hint much appreciated! i'll cooperate best i can ):P):P

---

### Post by steeldriver on 2013-02-25
I'm groping in the dark, really - I just wondered based on your errors whether 'extlinux' was broken / partially installed - it doesn't seem to be (ii)

---

### Post by dsikl on 2013-02-26
oh, ok well a big thanks for trying in that case! heaps appreciated!

everyone's welcome to try and help :D

cheers!

---

### Post by dsikl on 2013-03-06
:nudge: \\:D/

---

### Post by dsikl on 2013-04-13
Alright, may I ask if this is common practice, that my problem is being ignored? Or is there too much to do otherwise? Or should I be thankful for what I received so far? I mean, I am thankful, but it hasn't helped :(

The problem developed even further, I'm afraid I won't be able to use my puter much longer. It would be great if someone would try and help me out with this.

Cheers!

---

### Post by mörgæs on 2013-04-13
Now you have been repeatedly bumping your thread for a month and a half. It should indicate to you that not many people are able to give advice so please stop.

The kernel 2.6.32 shows that your installation was born as 10.04 (maybe older). Why not erase it and install a fresh 12.10?

---

### Post by dsikl on 2013-04-14
oh?... well, now I understand, thank you for that insight! I was really just totally confused, and this is seriously the first time I bump across the idea, that there may be issues in buntu that cannot be solved. Sure, it was silly to think otherwise, but hey, I'm also just a user :)

Thank you for the advice as well! I think I might do just that. I never would have thought of it myself, though.

Cheers!

---

