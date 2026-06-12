---
title: "cat start x session after upgrading !"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by fahad on 2005-11-18
Hi,

i was using the older version of ubuntu (hoary),
last night i upgraded my whole sys by the following:

1- change my respos list from hoary to breezy
2- " sudo apt-get update"
3- " sudo apt-get dist-upgrade"

after that i restarted my machine, but right now i cant start the x server :( :(

i faced the following box msg:
""
i cannot start the x server ( your graphical interface ). it is likely that it is not set up correctly. would you like to view the X server output to diagnose the problem?
""

i pressed yes, but it gives me nothing, just blue screen with crazy letters.

Next, i typed the following command " startx " and it gives me the following:
"
xauth: creating new authority file /home/fahad/.serverauth.4914
/user/bin/startx: line 143: /dev/null: permission denied
/user/bin/startx: line 143: .dev.null: permission denied

giving up.
xinit: connection refused ( error 111): unable to connect to X server
xinit: no such process ( errno 3): server error.
/usr/bin/startx: line 172: /dev/null: permission denied

"

after that i tried to start the program "/etc/X11/gdm/`xsession" but it gives the following "
./Xsession: Beginning session setup...
./Xsession: line 121: /dev/null: permission denied
./Xsession: line 122: /dev/null: permission denied
./Xsession: starting the failsafe xterm session
./Xsession: line 136:exec: xterm: not found
"



What should i do next ?

please its my primary machine :(

thanks in advance,

---

### Post by frodon on 2005-11-18
According to this wiki link : [https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28breezy%29](https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28breezy%29) you should have re-installed ubuntu-desktop metapackages before the beginning of the upgrade.
If you didn't, it might be the problem. So you should try to re-install it with command lines : ```
sudo apt-get install ubuntu-base ubuntu-desktop
```Not sure it will solve the problem, but you may try that.

---

### Post by fahad on 2005-11-18
i tried, it gives me alot of lines !!
i tried " apt-get -f install" also 

But
i still cant use x server:(

-
here is the output of the " apt-get install ubuntu-base ubuntu-desktop, and also apt-get -f install"
====

Reading package lists...
Building dependency tree...
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  language-support-en: Depends: openoffice.org2-help-en-us but it is not going to be installed
  openoffice.org-bin: Depends: openoffice.org (> 1.1.4+1.1.5) but 1.1.3-8ubuntu2.3 is to be installed
  ubuntu-base: Depends: ubuntu-minimal but it is not going to be installed
               Depends: ubuntu-standard but it is not going to be installed




================


ubuntu-desktop:

Reading package lists...
Building dependency tree...
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  language-support-en: Depends: openoffice.org2-help-en-us but it is not going to be installed
  openoffice.org-bin: Depends: openoffice.org (> 1.1.4+1.1.5) but 1.1.3-8ubuntu2.3 is to be installed
  ubuntu-desktop: Depends: bluez-cups but it is not going to be installed
                  Depends: bluez-pcmcia-support but it is not going to be installed
                  Depends: bluez-pin but it is not going to be installed
                  Depends: bluez-utils but it is not going to be installed
                  Depends: evolution-plugins but it is not going to be installed
                  Depends: firefox-gnome-support but it is not going to be installed
                  Depends: gnomemeeting but it is not going to be installed
                  Depends: gstreamer0.8-musepack but it is not going to be installed
                  Depends: hotkey-setup but it is not going to be installed
                  Depends: hplip-base but it is not going to be installed
                  Depends: hplip-ppds but it is not going to be installed
                  Depends: language-selector but it is not going to be installed
                  Depends: libesd-alsa0 but it is not going to be installed
                  Depends: libpt-plugins-v4l but it is not going to be installed
                  Depends: openoffice.org2-evolution but it is not going to be installed
                  Depends: openoffice.org2-gnome but it is not going to be installed
                  Depends: serpentine but it is not going to be installed
                  Depends: smeg but it is not going to be installed
                  Depends: ttf-mgopen but it is not going to be installed
                  Depends: usplash but it is not going to be installed



=======
apt-get -f install output:


Reading package lists...
Building dependency tree...
Correcting dependencies... Done
The following extra packages will be installed:
  openoffice.org openoffice.org-l10n-ar openoffice.org-l10n-en
  openoffice.org1-debian-files openoffice.org2-help-en-us
Suggested packages:
  menu ooqstart-gnome oooqs-kde unixodbc prelink openoffice.org-thesaurus
  msttcorefonts openoffice.org-mimelnk openoffice.org-gnomevfs xlibmesa-gl
  libgl1 openclipart myspell-dictionary-ar openoffice.org-hyphenation-ar
  openoffice.org-thesaurus-ar openoffice.org-help-ar
  openoffice.org-thesaurus-en
The following NEW packages will be installed:
  openoffice.org1-debian-files openoffice.org2-help-en-us
The following packages will be upgraded:
  openoffice.org openoffice.org-l10n-ar openoffice.org-l10n-en
3 upgraded, 2 newly installed, 0 to remove and 469 not upgraded.
551 not fully installed or removed.
Need to get 0B/24.1MB of archives.
After unpacking 24.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Preconfiguring packages ...
(Reading database ... 100537 files and directories currently installed.)
Unpacking openoffice.org2-help-en-us (from .../openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb) ...

====

---

### Post by fahad on 2005-11-18
sorry the rest of the output didnot shown, but it contains alot of errors.
i wish i could post all the output msg.

but " apt-get -f install | tee f.txt " for example, only capture the above lines

---

### Post by dj_flx on 2005-11-19
I had I think the same problem. I had to change my nvidia driver in xorg.conf to nv. I haven't figured out how to get it back. :???:

---

### Post by Arktis on 2005-11-19
[QUOTE=dj_flx]I had I think the same problem. I had to change my nvidia driver in xorg.conf to nv. I haven't figured out how to get it back. :???:[/QUOTE]
Sounds like you need to reinstall your graphics drivers, since you have a new kernel.

---

### Post by fahad on 2005-11-19
iam still not able to start the x server :(

---

### Post by rjwood on 2005-11-19
did you try
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by fahad on 2005-11-19
back,
after some tweaking , here where i reached.....
i did remove the openoffice packages , now the system is better alittle, i could install nvidia packages. and runs " apt-get -f install " but the earlier command gives me some error telling that he encountred erroes while processing postfix lsb-core lsb-graphics lsb-cxx, 

but
when i type: sudo startx , the x server start !
but i login root account, its hoary ! every thing is old.

when i type :startx inside my normal account it says fatal server error , xinit: no such process



----
iam lost :(
but i think its all because of the errors associated with " apt-get -f install " command.

---

### Post by fahad on 2005-11-19
well,
idid solve the errors associated with " apt-get -f install ", by removing postfix and install it again.


now every things is clean with the apt-get stuff.

its remain to start the damn x server :( :( any suggestions ?

---

### Post by fahad on 2005-11-19
rjwood, i did,

the problem now is to start the x server by the normal user who is the only user in the machine

---

### Post by rjwood on 2005-11-19
from the command line 
```
ls -a
```
look for a file with .Xauthority or .ICEauthority
then remove the file or change owership of that file
then you should be ok
probably some program like k3b or gnomebaker has put that file in your home directory

---

### Post by fahad on 2005-11-19
now i can to login normally :)

i have some other problems, i will try to solve it .


bye

---

