---
title: "[SOLVED] apt-get issue - firefox-3.0 firefox ubufox..."
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by anywebloco on 2008-10-24
***SOLVED***
1) followed dinxter's suggestion and created  sudo vim /var/lib/dpkg/alternatives/x-www-browser containing the information suggested - this file didn't exist on my system.

2) followed fabertawe and phoogkamer's suggestions

all works fine now.

Thanks very much for your assistance!

***********


Hello - 

I'm receiving the following error output when using apt-get to update:

```
anywebloco@home:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firefox-3.0 (3.0.3+nobinonly-0ubuntu2) ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/x-www-browser for update_mode ()
dpkg: error processing firefox-3.0 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of ubufox:
 ubufox depends on firefox | abrowser | firefox-3.0 | firefox-2; however:
  Package firefox is not configured yet.
  Package abrowser is not installed.
  Package firefox-3.0 is not configured yet.
  Package firefox-2 is not installed.
dpkg: error processing ubufox (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 firefox-3.0
 firefox
 ubufox
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Does anyone know what this means and how to fix it? I've got firefox 3.0.3 installed and it all works fine so I don't know what this is.

---

### Post by fabertawe on 2008-10-24
Not trying to be patronising but did you try "apt-get update" before "upgrade"? Also, you could try completely removing Firefox...
```
sudo apt-get purge firefox-3.0
```
This will pull out all the Firefox related stuff in one go....
```
firefox
firefox-3.0-branding
firefox-3.0-gnome-support
firefox-gnome-support
ubufox
```
Then just re-install "firefox-3.0".

You may have to re-install any related things like "mozilla-mplayer" you've installed if they get removed along with it.

EDIT: It's probably better purging the lot actually...
```
sudo apt-get purge firefox-3.0 firefox firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support ubufox
```

Paul

---

### Post by phoogkamer on 2008-10-24
You could try and fix this with

sudo apt-get autoclean
sudo apt-get clean

then

sudo aptitude update
sudo aptitude safe-upgrade

Good luck

---

### Post by anywebloco on 2008-10-24
Sadly, none of these suggestions seem to work. I end up with the following error message after the general purge:

```
anywebloco@home:~$ sudo apt-get purge firefox-3.0 firefox firefox-3.0-branding firefox-3.0-gnome-support firefox-gnome-support ubufox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package firefox is not installed, so not removed
Package firefox-3.0-branding is not installed, so not removed
Package firefox-3.0-gnome-support is not installed, so not removed
Package firefox-gnome-support is not installed, so not removed
Package ubufox is not installed, so not removed
The following packages will be REMOVED
  firefox-3.0*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 3518kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128470 files and directories currently installed.)
Removing firefox-3.0 ...
update-alternatives: error or eof reading /var/lib/dpkg/alternatives/x-www-browser for update_mode ()
dpkg: error processing firefox-3.0 (--purge):
 subprocess pre-removal script returned error exit status 2
Please restart all running instances of firefox-3.0, or you will experience problems.
Errors were encountered while processing:
 firefox-3.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

There were no instances of firefox running. FWIW I'm running Kubuntu (hence no "gnome-support").

thanks,

awl

---

### Post by dinxter on 2008-10-24
looks like /var/lib/dpkg/alternatives/x-www-browser is corrupted which is blocking the post install script. what does it look like? it should vaguely resemble the one below (for firefox only installed)
```

manual
/usr/bin/x-www-browser

/usr/bin/firefox-3.0
40

```

nb. there should be a new line at the end of the above but it doesnt seem to show up

---

### Post by dinxter on 2008-10-24
it seems the blank line at the end is crucial and if missing will give you exactly the error your getting so for firefox installed only it should be (on auto setting) as the one attached

---

