---
title: "Skip Plymouth?"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hsartoris on 2010-03-28
When I boot, the ubuntu splashcreen comes up, and just sits ther, loading. I can get into a command prompt in recovery mode, and I tries uninstalling Plymouth there. The next time I booted up, it said, "cannot locate Plymouth", and went to commas prompt. I have since reinstalled Plymouth, but still cannot aces the GUI of ubuntu. Is ther a way I can skip Plymouth, or replace it, so I can use my computer again?

---

### Post by caryb on 2010-03-28
I would reinstall Plymouth & hold the shift key on boot up for the grub menu 


Cary

---

### Post by grandtoubab on 2010-03-28
if you remove Plymouth it is better to remove the splash option from grub
```
sudo dpkg-reconfigure grub-pc
```
hit enter twice
then remove splash

see the reverse to use plymouth and grub
[http://www.khattam.info/2010/01/31/solved-error-mountall-could-not-connect-to-plymouth-mountall-main-process-x-terminated-with-status-1/](http://www.khattam.info/2010/01/31/solved-error-mountall-could-not-connect-to-plymouth-mountall-main-process-x-terminated-with-status-1/)

---

### Post by hsartoris on 2010-03-28
Thanks for the help. I tried reinstalling, to no avail. While I was trying the method on the website posted here, I discovered something: as far as most of my install is concerned, Plymouth is not installed. I ran ```
plymouth-set-default-theme --list
``` in the root shell prompt, now my only access to the computer. It returned "package Plymouth is not installed. Try apt-get install Plymouth". I did, and apt returned that Plymouth was already installed. Can I make the otherparts of the system recognize it?

Sorry for bad spelling; I'm using my itouch to post right now.

---

### Post by grandtoubab on 2010-03-29
that is a bug
refer to
[http://ubuntuforums.org/showthread.php?t=1440223](http://ubuntuforums.org/showthread.php?t=1440223)

expect to be solved in next updates of plymouth

---

### Post by hugmenot on 2010-03-29
You cannot remove plymouth. It is needed to boot, and if you remove it your drives won't be mounted.

You can suppress the graphical boot splash by removing the "splash" grub option, or by uninstalling all of the plymouth-theme-* packages.

---

### Post by tad1073 on 2010-03-29
> **hugmenot said:**
> You cannot remove plymouth. It is needed to boot, and if you remove it your drives won't be mounted.

You can suppress the graphical boot splash by removing the "splash" grub option, or by uninstalling all of the plymouth-theme-* packages.

plymouth has nothing to do with booting the OS, it is purely aesthetic.

---

### Post by tad1073 on 2010-03-29
> **hsartoris said:**
> Thanks for the help. I tried reinstalling, to no avail. While I was trying the method on the website posted here, I discovered something: as far as most of my install is concerned, Plymouth is not installed. I ran ```
plymouth-set-default-theme --list
``` in the root shell prompt, now my only access to the computer. It returned "package Plymouth is not installed. Try apt-get install Plymouth". I did, and apt returned that Plymouth was already installed. Can I make the otherparts of the system recognize it?

Sorry for bad spelling; I'm using my itouch to post right now.

> **grandtoubab said:**
> that is a bug
refer to
[http://ubuntuforums.org/showthread.php?t=1440223](http://ubuntuforums.org/showthread.php?t=1440223)

expect to be solved in next updates of plymouth


```
sudo update-alternatives --config default.plymouth
```

is what your looking for

---

### Post by hugmenot on 2010-03-29
> **tad1073 said:**
> plymouth has nothing to do with booting the OS, it is purely aesthetic.

Sorry, you’re mistaken:

[http://ubuntuforums.org/showpost.php?p=9008529&postcount=2](http://ubuntuforums.org/showpost.php?p=9008529&postcount=2)

(he is the responsible developer.)

---

### Post by ranch hand on 2010-03-29
> **hugmenot said:**
> Sorry, you’re mistaken:

[http://ubuntuforums.org/showpost.php?p=9008529&postcount=2](http://ubuntuforums.org/showpost.php?p=9008529&postcount=2)

(he is the responsible developer.)
I am currently writing this from 10.04 that has had plymouth removed.  With plymouth removed it will actually boot which is more than it will do with plymouth installed.

I only remove plymouth, not libplymouth2.

Plymouth is not needed at all, for anything except the splash.

---

### Post by grandtoubab on 2010-03-29
> **tad1073 said:**
> ```
sudo update-alternatives --config default.plymouth
```is what your looking for
```

ubuntu-desktop:~$ sudo update-alternatives --config default.plymouth

Il existe 6 choix pour l'alternative default.plymouth (qui fournit /lib/plymouth/themes/default.plymouth).

  Sélection   Chemin                                                 Priorité  État
------------------------------------------------------------
* 0            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       mode automatique
  1            /lib/plymouth/themes/fade-in/fade-in.plymouth           10        mode manuel
  2            /lib/plymouth/themes/glow/glow.plymouth                 10        mode manuel
  3            /lib/plymouth/themes/script/script.plymouth             10        mode manuel
  4            /lib/plymouth/themes/solar/solar.plymouth               10        mode manuel
  5            /lib/plymouth/themes/spinfinity/spinfinity.plymouth     10        mode manuel
  6            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       mode manuel

Appuyez sur <Entrée> pour conserver la valeur par défaut
[*] ou choisissez le numéro sélectionné :4
update-alternatives: utilisation de « /lib/plymouth/themes/solar/solar.plymouth » pour fournir « /lib/plymouth/themes/default.plymouth » (default.plymouth) en mode manuel.

```Ok thanks

---

