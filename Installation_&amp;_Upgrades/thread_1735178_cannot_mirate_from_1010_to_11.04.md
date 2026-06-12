---
title: "cannot mirate from 10/10 to 11.04"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by kazik1616 on 2011-04-21
Hello,
I recently tried to migrate ubuntu from 10.10 to newest beta 11.04. I typed ```
sudo update-manager -d
```

After some time I received following message
When trying to upgrade from 10.10 to 11.04 (sudo update-manager -d), I am getting following error message:

> An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve returned error, It may be caused by stopped packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

I have found many following messages in */var/log/dist-upgrade/apt.log*:

>   Installing libmutter0 as Wymaga of mutter
Starting
Starting 2
Investigating (0) gir1.2-glib-2.0 [ i386 ] < none -> 0.10.7-0ubuntu1 > ( libs )
Broken gir1.2-glib-2.0:i386 Jest w konflikcie z on gir1.0-glib-2.0 [ i386 ] < 0.9.3-0ubuntu4 > ( libs )
  Considering gir1.0-glib-2.0:i386 -1 as a solution to gir1.2-glib-2.0:i386 71
  Added gir1.0-glib-2.0:i386 to the remove list
  Fixing gir1.2-glib-2.0:i386 via remove of gir1.0-glib-2.0:i386
Investigating (0) xserver-xorg-core [ i386 ] < 2:1.9.2.901+git20101129+server-1.9-branch.65f2ab20-0ubuntu0sarvatt2~maverick -> 2:1.10.0.902-1ubuntu1 > ( x11 )
Broken xserver-xorg-core:i386 Psuje on xserver-xorg-video-8 [ i386 ] < none > ( none )
  Considering xserver-xorg-video-tseng:i386 -1 as a solution to xserver-xorg-core:i386 70
  Added xserver-xorg-video-tseng:i386 to the remove list
  Fixing xserver-xorg-core:i386 via remove of xserver-xorg-video-tseng:i386
Investigating (0) ure [ i386 ] < 1.6.1+OOo3.2.1-7ubuntu1.1 -> 1.7.0+LibO3.3.2-1ubuntu3 > ( libs )
Broken ure:i386 Psuje on openoffice.org-core [ i386 ] < 1:3.2.1-7ubuntu1.1 > ( editors ) (< 1:3.3~)
  Considering openoffice.org-core:i386 4 as a solution to ure:i386 57
  Added openoffice.org-core:i386 to the remove list
  Fixing ure:i386 via remove of openoffice.org-core:i386


Is that a root cause of the problem? Any ideas how I could fix it?

---

### Post by dino99 on 2011-04-21
open your sources.list and change maverick by natty, then update

sudo gedit /etc/apt/sources.list

---

### Post by Frogs Hair on 2011-04-21
Disable PPA/s and third party software if you have any.

---

### Post by kazik1616 on 2011-04-22
dino99 - could you clarify the steps you recommend? Did you mean modify sources.list and then run **sudo update-manager -d** or other?

Frogs Hair - I disabled it in sources.list but still I have the same error message and the same entry in apt.log. Did you mean disabling it in sources.list or something else? Attaching sources.list file.

---

### Post by dino99 on 2011-04-22
to simplify, use this generator: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by kazik1616 on 2011-04-26
Hello,
Performed following operations:
replaced all maverick words with natty in /etc/apt/sources.list (as mentioned in this thread) and then ransudo apt-get upgrade. After upgrading and restarting server. I get following popup window:

> It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment.

The problem is that I cannot close this popup window in any way as I do not have mouse cursor on the screen. What can be a root cause of this message? How can I fix that?

---

