---
title: "So my dist-upgrade got interrupted..."
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by nach0 on 2007-10-18
So earlier today I tried to update from 7.04 to 7.10 using ```
update-manager -d
```

This was interrupted.

When I started the computer back up, I was greeted by the following ```
Starting up ...
Loading, please wait...
kinit: name_to_dev_t(dev/disk/by-uid/e3142ee9-af87-48b8-834f-77370d889f05) = sda(8,5)
kinit: trying to resume from /dev/disk/by-uuid/e3142ee9-af87-48b8-834f-77370d889f05
kinit: no resume image, doing normal boot...

Ubuntu 7.10 desktop tty1
```

Then it presents me with a login. It does not boot automatically thereafter, as older threads have suggested. I have attempted a startx, which fails and presents me the following ```
(II) Module already built-in
(II) Module already built-in
(EE) AIGLX: Screen 0 is not DRI capable
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:    Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>             Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
     No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
     No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
     No such file or directory.
Error opening /dev/wacom : Success
Could not init font path element /usr/share/fonts/X11/cryllic, removing from list!

waiting for X server to shut down FreeFontPath: FPE "usr/share/fonts/X11/misc"
refcount is 2, should be 1; fixing.


xauth: error in locking authority file /home/nach0/.Xauthority
```


Please advise :(

---

### Post by mattpker on 2007-10-18
Have you tried loading the privous kernel in grub and then reinstalling 7.10 again?

---

### Post by Whiffle on 2007-10-18
Try doing a combination of:

'sudo apt-get -f install' 

'sudo dpkg --configure -a'

'sudo apt-get upgrade'




You might have to do them each a few times.  The idea is that the update manager has already updated your sources list, so it thinks its running gutsy.  It'll look at the packages you have installed and realize that they're out of date, and update them to the right ones.  The first command installs missing dependencies of already installed packages, the second upgrade packages, and the last one configures packages that may have not been fully configured when update manager crashed.

---

### Post by pinion on 2007-10-18
I tried to upgrade from update manager like the website says but mine stopped halfway through installation too.  I believe it got caught up on util-linux or something like that.  I tried running that first command you suggested and I get errors:

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswfdec0.3 liboggflac3 libjack0.100.0-0 libpostproc0d libavformat0d libavcodec0d
  libquicktime0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of locales:
 locales depends on tzdata; however:
  Package tzdata is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en-base:
 language-pack-gnome-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-jre:
 sun-java5-jre depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing sun-java5-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-bin:
 sun-java5-bin depends on sun-java5-jre (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-jre is not configured yet.
dpkg: error processing sun-java5-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux-locales:
 util-linux-locales depends on util-linux (>= 2.13-0); however:
  Package util-linux is not configured yet.
 util-linux-locales depends on util-linux (<< 2.13.0-0); however:
  Package util-linux is not configured yet.
dpkg: error processing util-linux-locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on locales; however:
  Package locales is not configured yet.
 ubuntu-minimal depends on tzdata; however:
  Package tzdata is not configured yet.
 ubuntu-minimal depends on util-linux; however:
  Package util-linux is not configured yet.
 ubuntu-minimal depends on util-linux-locales; however:
  Package util-linux-locales is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on sun-java5-bin (= 1.5.0-13-0ubuntu1); however:
  Package sun-java5-bin is not configured yet.
dpkg: error processing sun-java5-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en:
 language-pack-gnome-en depends on language-pack-gnome-en-base; however:
  Package language-pack-gnome-en-base is not configured yet.
dpkg: error processing language-pack-gnome-en (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
 locales
 language-pack-en-base
 language-pack-gnome-en-base
 sun-java5-jre
 sun-java5-bin
 util-linux-locales
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by nach0 on 2007-10-18
> **mattpker said:**
> Have you tried loading the privous kernel in grub and then reinstalling 7.10 again?

My grub only shows variants of 7.10, all of which have the same outcome as before. :(

> Try doing a combination of:

'sudo apt-get -f install'

'sudo dpkg --configure -a'

'sudo apt-get upgrade'




You might have to do them each a few times. The idea is that the update manager has already updated your sources list, so it thinks its running gutsy. It'll look at the packages you have installed and realize that they're out of date, and update them to the right ones. The first command installs missing dependencies of already installed packages, the second upgrade packages, and the last one configures packages that may have not been fully configured when update manager crashed.

This didn't work either, 'gnome-themes', 'gnome-accessibility-themes' and 'ubuntu-desktop' all return errors.

 :-| Have i killed it?

---

### Post by freed0m on 2007-10-18
Nach0, 
Try this.

Go to -> System -> Administration -> Time and Date -> and change the time zone to America/Phoenix.
Then reinstall tzdata from Synaptic. Or apt-get -f install and so on.

Cheers

---

### Post by nach0 on 2007-10-19
freed0m,

I can't; X won't start. Is there a terminal command I can try?

Thanks...

---

### Post by cmavr8 on 2007-10-19
Almost the same case...
[http://ubuntuforums.org/showthread.php?p=3572683#post3572683](http://ubuntuforums.org/showthread.php?p=3572683#post3572683)

Same problems.. missing 'gnome-themes', 'gnome-accessibility-themes' and 'ubuntu-desktop'.
Should I reinstall using some command?

maybe apt-get something?

---

### Post by OhMyScience on 2007-10-20
> **cmavr8 said:**
> Almost the same case...
[http://ubuntuforums.org/showthread.php?p=3572683#post3572683](http://ubuntuforums.org/showthread.php?p=3572683#post3572683)

Same problems.. missing 'gnome-themes', 'gnome-accessibility-themes' and 'ubuntu-desktop'.
Should I reinstall using some command?

maybe apt-get something?

I've got exactly the same errors
Missing 'gnome-themes', 'gnome-accessibility-themes' and 'ubuntu-desktop'.

I was using Beryl, maybe that caused the problem, allthrough Beryl was disabled while i upgraded to 7.10

---

### Post by nach0 on 2007-10-20
> **OhMyScience said:**
> I was using Beryl, maybe that caused the problem, allthrough Beryl was disabled while i upgraded to 7.10

Unlikely caused by Beryl, as I wasn't running it myself, and we're in the same position.

[B]NEED HELP ! 
[/B]

---

### Post by jonny_sicoli on 2007-10-23
I seem to be having this same problem.  Would it be at all possible to (temporarily) install an older version of gnome-themes?  un/reinstalling it seems to do nothing at all.

Also, how could I change the Grub boot menu list from the command line?

---

### Post by cmavr8 on 2007-10-24
> **jonny_sicoli said:**
> I seem to be having this same problem.  Would it be at all possible to (temporarily) install an older version of gnome-themes?  un/reinstalling it seems to do nothing at all.

Also, how could I change the Grub boot menu list from the command line?

Maybe
#sudo nano /boot/grub/menu.lst

---

### Post by drewster1829 on 2007-10-24
I have the exact same problem...

gnome-themes
gnome-accessibility-themes
ubuntu-desktop

all come up with errors.  I sure am glad I have two boxes, and I managed to install it on one of them without interrupting it. :)

---

