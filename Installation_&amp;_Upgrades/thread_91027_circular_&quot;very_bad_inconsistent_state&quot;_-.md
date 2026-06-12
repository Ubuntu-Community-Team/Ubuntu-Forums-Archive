---
title: "circular &quot;very bad inconsistent state&quot; -- am I toast?"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by dmintz on 2005-11-16
I edited my sources.list changing 'hoary' to 'breezy', and tried a dist-ugrade with synaptic. I got an error: 

[FONT="Courier New"]dpks-db: failed to read archive /var/cache/apt/archives/xlibs_6.8.2-77_all.deb: no such file or directory.[/FONT]

Then it told me to run [FONT="Courier New"] sudo dpkg --configure -a [/FONT]manually.

I tried that and got (this is an excerpt):

[FONT="Courier New"]Setting up net-tools (1.60-15ubuntu2) ...
Setting up linux-kernel-headers (2.6.11.2-0ubuntu13) ...
Setting up bsdmainutils (6.1.2) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

dpkg: dependency problems prevent configuration of ubuntu-base:
 ubuntu-base depends on ubuntu-minimal; however:
  Package ubuntu-minimal is not installed.
 ubuntu-base depends on ubuntu-standard; however:
  Package ubuntu-standard is not installed.
dpkg: error processing ubuntu-base (--configure):
 dependency problems - leaving unconfigured[/FONT]

So I tried apt-get -f dist-upgrade and it quits with (excerpt):

[FONT="Courier New"] gimp depends on libxpm4 | xlibs (>> 4.1.0); however:
  Package libxpm4 is not configured yet.
  Package xlibs is to be removed.
 gimp depends on libxt6 | xlibs (>> 4.1.0); however:
  Package libxt6 is not configured yet.
  Package xlibs is to be removed.
dpkg: error processing xlibs (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
david@vernon0:~$ Errors were encountered while processing:
 xlibs
[/FONT]

So I try apt-get remove xlibs (to be followed by install) and I get 

[...]
[FONT="Courier New"] nautilus-sendto: Depends: libgnomevfs2-0 (>= 2.11.3) but 2.10.0-0ubuntu5 is to be installed
  sound-juicer: Depends: libgnomevfs2-0 (>= 2.11.3) but 2.10.0-0ubuntu5 is to be installed
  xbase-clients: Depends: xsm but it is not going to be installed
                 Depends: xstdcmap but it is not going to be installed
                 Depends: xtrap but it is not going to be installed
                 Depends: xvidtune but it is not going to be installed
                 Depends: xwd but it is not going to be installed
                 Depends: xwininfo but it is not going to be installed
                 Depends: xwud but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/FONT]

So I try 'apt-get -f install' and I get

[FONT="Courier New"]dpkg: error processing xlibs (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 xlibs
Aborted[/FONT]

I seem to be in an endless loop where I have to uninstall xlibs in order to uninstall xlibs in order be able to reinstall xlibs and proceed. 

Suggestions? 

Thanks!

---

### Post by rjwood on 2005-11-16
can you post your sources.list here please

---

### Post by dmintz on 2005-11-16
[QUOTE=rjwood]can you post your sources.list here please[/QUOTE]

david@vernon0:~$ cat /etc/apt/sources.list
[FONT="Courier New"]#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Backports
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
[/FONT]

I commented out the CD because I don't have any such CD and was getting complaints. I commented out the mirrormax.net stuff as a desperation shot because I found a post somewhere that sort of suggested that maybe...

---

### Post by rjwood on 2005-11-16
remove the "us." out of any line that it is in. Only the letters "us" and the dot after it. save the file. then do 
```
sudo apt-get dist-upgrade
```

---

### Post by dmintz on 2005-11-16
[QUOTE=rjwood]remove the "us." out of any line that it is in. Only the letters "us" and the dot after it. save the file. then do 
```
sudo apt-get dist-upgrade
```[/QUOTE]

Same story.

I removed all the occurences of 'us.' , ran dist-ugrade, it puked, I ran update just for kicks and tried sudo apt-get -f dist-upgrade:

[...]
 [FONT="Courier New"]gimp depends on libxpm4 | xlibs (>> 4.1.0); however:
  Package libxpm4 is not configured yet.
  Package xlibs is to be removed.
 gimp depends on libxt6 | xlibs (>> 4.1.0); however:
  Package libxt6 is not configured yet.
  Package xlibs is to be removed.
 gimp depends on libice6 | xlibs (>> 4.1.0); however:
  Package libice6 is not configured yet.
  Package xlibs is to be removed.
 gimp depends on libsm6 | xlibs (>> 4.1.0); however:
  Package libsm6 is not configured yet.
  Package xlibs is to be removed.
 gimp depends on libxmu6 | xlibs (>> 4.1.0); however:
  Package libxmu6 is not configured yet.
  Package xlibs is to be removed.
 gimp depends on libxpm4 | xlibs (>> 4.1.0); however:
  Package libxpm4 is not configured yet.
  Package xlibs is to be removed.
 gimp depends on libxt6 | xlibs (>> 4.1.0); however:
  Package libxt6 is not configured yet.
  Package xlibs is to be removed.
dpkg: error processing xlibs (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
[/FONT]

What's next? :)

---

### Post by rjwood on 2005-11-16
here's mine --copy and paste if you like.

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted



## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted  
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse

#deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") dapper main restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe

deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") breezy-extras main restricted universe multiverse
then
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by dmintz on 2005-11-16
Tried that, same result.

```
dpkg: error processing xlibs (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
```

I can't stress enough how much I appreciate your efforts. Care to keep trying? :) I am starting to see a full OS reinstallation looming on my horizon.

---

### Post by rjwood on 2005-11-16
perhaps a fresh install is best. just back-up what you need to.   Good luck. Sorry I couldn't be more help to you.

---

### Post by dmintz on 2005-11-16
I knew the risks, and this will hardly be first time I've done a full blown Linux installation. 

The sad part is that I will probably switch to Fedora, because I do not have an Ubuntu  Breezy installation disc, because I was never able to get Ubuntu Hoary to write to my old Sony CD-RW -- whereas I do have a set of Fedora Core IV install discs. I got my Ubuntu Hoary disk by burning it with my old Red Hat 9!

Fedora distro version upgrades can suck, too  -- I know this from experience. But it wasn't this bad.

Thanks again.

---

