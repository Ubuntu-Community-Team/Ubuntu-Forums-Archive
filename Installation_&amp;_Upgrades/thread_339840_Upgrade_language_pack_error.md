---
title: "Upgrade language pack error"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by neok on 2007-01-16
Hi!

Today I upgraded the language packs for my Ubuntu Dapper, and after a reboot the language has changed to english from spanish.

Now I have the GNOME menu in english and all other stuff in spanish, I tried change the language from de language selector and locale, but it doesn't work.

Somebody help me?

Thanks!

---

### Post by bapoumba on 2007-01-16
Hello,

what do you call language selector ? > System > Administration > Language Support ?
I have both French and English ticked (so all the spell checkers get installed) but English is selected in Default Language. And all the menus are in English.

---

### Post by todoporron on 2007-01-17
Hi, I will try to explain this a little better since I have the same problem:

After upgrading the gnome language support packages via Update Manager, the menu entries on the gnome menu bar were turned to English as well as some sub-menu entries. The rest of the menus (e.g. see date on attached picture) are in spanish... 

My default session language is set to Spanish but I get this language mix anyway.

What is wrong?

Thanks

[[IMG]http://www.subirimagenes.com/imagenes/previo/thump_706185Pantallazo.png[/IMG]](http://www.subirimagenes.com/imagen-de-Pantallazo-706185.html)

---

### Post by bapoumba on 2007-01-18
Hello,
I am not facing this problem, not sure what to recommend and how to check it :/
What do you have in /etc/environment ?
```
~ $ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"

```

---

### Post by todoporron on 2007-01-18
Hi, as I said before, my default language is spanish:

```

secretaria@secretaria-pc:~$ cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="es_CO.UTF-8"
LANGUAGE="es_CO:es"

```

But I keep having menu entries in English...  :(

I also notice that all the menus, and SOME buttons in Evolution Mail were also changed to English...

---

### Post by bapoumba on 2007-01-18
Here what I have installed :
```
language-pack-en
language-pack-en-base
language-pack-fr
language-pack-fr-base
language-pack-gnome-en
language-pack-gnome-en-base
language-pack-gnome-fr
language-pack-gnome-fr-base
language-support-en
language-support-fr

```
For both French and English environment (not at the same time ;))
Do you have the same packages for Spanish installed ?

---

### Post by bapoumba on 2007-01-19
Hi, there is a bug :
[https://bugs.launchpad.net/ubuntu/+source/language-pack-gnome-es/+bug/79589]("https://bugs.launchpad.net/ubuntu/+source/language-pack-gnome-es/+bug/79589")
Reinstalling the proper language-packs and login back again to your session seem to solve the problem.

---

### Post by todoporron on 2007-01-19
SOLVED.

After reinstalling the language-gnome-es package and restarting gnome, everything was in spanish.

Thanks to Bapoumpa !

---

### Post by bapoumba on 2007-01-19
You are welcome.
Do you have the -proposed repositories in your sources.list ?
Just a guess. These are meant for tests.

---

### Post by todoporron on 2007-01-19
No, I do not have these repositories.

---

### Post by bapoumba on 2007-01-19
Okay, thanks :)

---

### Post by Abdoun on 2008-01-16
Sorry to re-open the thread but I have exactly the same problem in  Gutsy using GNOME. Deleting and reinstalling the language packs did not help. I have a mix of English and German with German as the default language. My etc/default/locale looks like that:

LANG="de_DE.UTF-8"
LANGUAGE="de_DE:de:en_GB:en"

My etc/environment  is this:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="de_DE.UTF-8"
LANGUAGE="de_DE:de:en_GB:en"

And when I start sudo nautilus I get this:

(nautilus:12697): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(nautilus:12697): Gdk-WARNING **: locale not supported by C library
Initializing gnome-mount extension

(gedit:12889): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:12889): Gdk-WARNING **: locale not supported by C library

I have seen the same problem in  other forums but not found any solution.

Can anyone help?

Abdoun

---

### Post by bapoumba on 2008-01-17
Please make sure that in the Language Support menu, everything is setup correctly. You may be prompted to install new packages.

Other than that, make sure ubuntu-desktop is installed and run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Please paste the errors if you have any.

---

### Post by Abdoun on 2008-01-18
Thanks for caring bapoumba. 

In the Language Support Manager I have now only German installed and activated as default. Still a lot of menus are in English (for instance Evolution) but not all (for instance Firefox is all in German)

In sudo apt-get update I am getting the following errors:
Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/main Packages

  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/restricted Packages

  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


and at the end:
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Reading package lists... Done

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: You may want to run apt-get update to correct these problems

E: Some index files failed to download, they have been ignored, or old ones used instead.


sudo apt-get dist-upgrade does not give me any errors.

Greetings

---

### Post by Abdoun on 2008-01-18
Sorry but after  sudo apt-cdrom add I got only this error:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

Regards

---

### Post by alexzzz on 2008-01-19
I had the same problem. After an update I lost Greek writing support but all menus continued to be in Greek.
After a lot of (meaningless) searching I found out that all I had to do is to re-add Greek in my keyboard menu (sorry but all my menus are in Greek and I can't tell you the exact names of them).

Hope I helped!!!

---

### Post by Abdoun on 2008-01-20
Thanks for trying alexzzz but it did not work for me.

I think it has something to do with the locales but I do not know how to fix it.

Regards

---

### Post by bapoumba on 2008-01-20
Sorry, I have been away.

What repos do you have in your sources.list?
```
cat /etc/apt/sources.list
```

And you can find about your locale. Here is mine for example:
```
isabella@yeti:~ $ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
```
```
isabella@yeti:~ $ cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
```

I know I have notes somewhere on how to fix locales. If these do not return something similar (and adapted to your own environment), I'll dig through my notes :)

---

### Post by Abdoun on 2008-01-20
Hi. great you are back.

My sources seem to be totally messed up:

 cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties

## Medibuntu - Ubuntu 7.10 “gutsy gibbon”
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free

deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/
deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) lenny main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted


And here is the locale (I have only activated German at the moment although I still have a lot of English menus):

LANG=de_DE@euro
LC_CTYPE="de_DE@euro"
LC_NUMERIC="de_DE@euro"
LC_TIME="de_DE@euro"
LC_COLLATE="de_DE@euro"
LC_MONETARY="de_DE@euro"
LC_MESSAGES="de_DE@euro"
LC_PAPER="de_DE@euro"
LC_NAME="de_DE@euro"
LC_ADDRESS="de_DE@euro"
LC_TELEPHONE="de_DE@euro"
LC_MEASUREMENT="de_DE@euro"
LC_IDENTIFICATION="de_DE@euro"
LC_ALL=

Sorry for the trouble.

Best wishes.

---

### Post by Abdoun on 2008-01-21
Sorry forgot the environment:

cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="de_DE.UTF-8"
LANGUAGE="de_DE:de:en_GB:en"

---

### Post by bapoumba on 2008-01-21
You should  remove the cdrom line in your sources.list and the lenny repos (it is not recommended to run with debian repos on Ubuntu).

Here is mine, as an example. You can add the partner and medibuntu repos after your current problem is fixed.
I do not know what this one is: deb [http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu](http://ftp.osuosl.org/pub/pculture.o...itories/ubuntu) gutsy/

```
isabella@yeti:~ $ cat /etc/apt/sources.list
# Base.
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

# Bug fix updates.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

# Security.
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

```

Medibuntu repos that you can use, after the language is fixed (they have changed):
```
# Medibuntu.
# deb http://packages.medibuntu.org/ gutsy free non-free
```

After you have made the changes, run again 
```
sudo apt-get update
sudo apt-get dist-upgrade
```

For the locale thing, I'm not sure with you are using the @euro.
What does return:
```
isabella@yeti:~ $ cat /var/lib/locales/supported.d/local
fr_FR.UTF-8 UTF-8
en_US.UTF-8 UTF-8
```
I have both French and English installed.

---

### Post by Abdoun on 2008-01-21
Well, My sources list now looks like this:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties

deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) gutsy/
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted

But I still have a lot of out commented lines like this:

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

I do not know if this means anything. 


Finally:

wolfgang@wolfgang-laptop:~$ cat /var/lib/locales/supported.d/local
de_DE.UTF-8 UTF-8
en_US.UTF-8 UTF-8
de_DE@euro ISO-8859-15

I am also a bit puzzled by the @euro thing?

 Presently, I have only German activated.

---

### Post by Abdoun on 2008-01-28
Hi, still have no clue. But I found out the following which looks a bit strange to me:

etc/default/locale looks like that:

LANG="de_DE.UTF-8"
LANGUAGE="de_DE:de:en_GB:en"

etc/environment is this:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="de_DE.UTF-8"
LANGUAGE="de_DE:de:en_GB:en"

But when I run "locale" in the terminal I get this:

LANG=de_DE@euro
LC_CTYPE="de_DE@euro"
LC_NUMERIC="de_DE@euro"
LC_TIME="de_DE@euro"
LC_COLLATE="de_DE@euro"
LC_MONETARY="de_DE@euro"
LC_MESSAGES="de_DE@euro"
LC_PAPER="de_DE@euro"
LC_NAME="de_DE@euro"
LC_ADDRESS="de_DE@euro"
LC_TELEPHONE="de_DE@euro"
LC_MEASUREMENT="de_DE@euro"
LC_IDENTIFICATION="de_DE@euro"
LC_ALL=

???

---

