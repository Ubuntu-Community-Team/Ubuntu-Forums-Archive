---
title: "base-config problem"
date: 2004-11-20
forum: Installation &amp; Upgrades
---

### Post by Mr Fancypants on 2004-11-20
I am a bit confounded by this problem I'm having.  I'll start with the short version in case the solution is obvious, and then proceed with some background.

Trying to install Warty on my dual-booted PC, the initial install goes fine. After reboot when the base-config is running, I *believe* I am having problems with the X setup. 

It allows me to create a user, installs some packages, but then when it gets to the group with X, it says

```
Extracting templates from packages: 100%
Preconfiguring packages ...
```
and then just sits there. I can switch to tty2 and log-in.  A **ps -ae**  gives me the following (edited for possible relevancy):

```
  PID TTY          TIME CMD
 3567 tty1     00:00:00 termwrap
 3769 tty1     00:00:00 script
 3782 tty1     00:00:00 script
 3783 pts/0    00:00:00 base-config
 4222 pts/0    00:00:00 pkgsel
 4307 pts/0    00:00:31 aptitude
 4308 pts/0    00:00:00 sh
 4309 pts/0    00:00:02 dpkg-preconfigu
 4315 pts/0    00:00:00 echo <defunct>
 5579 ?        00:00:00 cleanup
 5582 ?        00:00:00 trivial-rewrite
 5583 ?        00:00:00 local
 5609 pts/0    00:00:00 xserver-xfree86
 5623 pts/0    00:00:00 xserver-xfree86
 5629 pts/0    00:00:00 xserver-xfree86
 5630 pts/0    00:00:00 discover
```

When I hit Ctrl-C at the "Preconfiguring packages ..."  I get the message

[INDENT]Aborting xserver-xfree86 package config script.[/INDENT]
So that's the foreground, here's the background. In a nutshell, it seems I'm having some X related issues.

I downloaded the warty/4.10 iso and burned to a CD and actually successfully installed on my computer with it and everything operated satisfactorily. I dual boot and have been using XP for a while. I went back and booted into Ubuntu, but once gdm fired up, I got a blank screen from which I could not exit.

I booted into recovery mode, and from the root account I could run /etc/X11/X directly and it behaved as expected, but if I ran startx from my user account the same blank screen would result.

Being an Ubuntu (and apt)  newbie, I just decided to re-install, and I imagine that my current errors (inability to complete the install) are related to this strange X behavior.

The only hardware change that transpired was that I removed an old ISA modem, and added a PCI Firewire/USB 2.0  card. I tried again with the new PCI card removed, but had the same issues.

Fwiw, I have a Matrox Millenium G400 dualhead, which, as I said before, worked beautifully the first time I installed. Also, XP is running fine. (The re-install has wiped out any X-logs that may have existed before. Since the base-config does not run to completion, X doesn't seem to be installed yet now)

Any thoughts on what might be causing this issue and/or how to complete my install as I managed to do once before would be greatly appreciated.

~Jerod

---

### Post by wallijonn on 2004-11-26
sounds like you need to rerun xfree86config again at the # prompt. you will of course have to use the sudo command. 

```

sudo /etc/init 1
sudo /usr/X11R6/bin/xf86config

```
or 
```

sudo /etc/telinit 1
sudo sh /etc/X11/gdm/XKeepsCrashing

```

---

### Post by Mr Fancypants on 2004-12-04
Thanks, but that doesn't help because X is not installed. Rather, it is apparently trying to install X.

This happens when I run base-config. Again, when it hangs at "Preconfiguring packages ...", this is a little more detail from **ps**.

```
USER       PID COMMAND          COMMAND
root      3650 script           script -q -a /var/log/base-config.log -t
root      3651 script           script -q -a /var/log/base-config.log -t
root      3652 base-config      /bin/sh /usr/sbin/base-config -i
root      3924 pkgsel           /bin/sh ./menu/pkgsel
root      3943 aptitude         aptitude --without-recommends
root      3946 sh               /bin/sh -c /usr/sbin/dpkg-preconfigure --apt || true
root      3947 dpkg-preconfigu  /usr/bin/perl -w /usr/sbin/dpkg-preconfigure --apt
root      3953 echo <defunct>   [echo] <defunct>
root      5272 xserver-xfree86  /bin/sh /tmp/base-config.3652/xserver-xfree86.config.51121 configure 
root      5286 xserver-xfree86  /bin/sh /tmp/base-config.3652/xserver-xfree86.config.51121 configure 
root      5292 xserver-xfree86  /bin/sh /tmp/base-config.3652/xserver-xfree86.config.51121 configure 
root      5293 discover         discover --disable=serial,parallel --format=%V %M\t%S\t%D\n video
jerod     5347 ps               ps -aeo user,pid,comm,args

```

I ran the **discover** command from another tty and (assuming it's an artifact of ps that the space in the --format  option appears without an escape) the equivalent command worked just fine.

Does anyone have any ideas? Any log files I could investigate? 

I really really liked my brief tango with Ubuntu, and I hope to be able to use it soon. Thanks so much for any help.

~Jerod

---

### Post by Mr Fancypants on 2004-12-14
Anyone? Just looking for a clue or two; where can I look for errors? Please don't make me go back to RedHat.  :sad:

---

