---
title: "Apt-get broken : how to repair ?"
date: 2005-10-12
forum: Installation &amp; Upgrades
---

### Post by EcliptuX on 2005-10-12
Hello,

I would install the ltmodem package for my winmodem and it's seems I had broked apt-get :(

There, the result of apt-get check :
```
root@Narayan:~ # apt-get check
Reading package lists... Done
Building dependency tree... Done
E: The package ltmodem-2.6.8-2-386 needs to be reinstalled, but I can't find an archive for it.
root@Narayan:~ #
```
Reinstallation or delete don't work :
> root@Narayan:/home/ecliptux/Download # dpkg -r ltmodem-2.6.8-2-386
dpkg: error processing ltmodem-2.6.8-2-386 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ltmodem-2.6.8-2-386
root@Narayan:/home/ecliptux/Download #
> root@Narayan:/home/ecliptux/Download # dpkg -i ltmodem-2.6.8-2-386_8.31a11_i386.deb
Selecting previously deselected package ltmodem-2.6.8-2-386.
(Reading database ... 95730 files and directories currently installed.)
Preparing to replace ltmodem-2.6.8-2-386 8.31a11 (using ltmodem-2.6.8-2-386_8.31a11_i386.deb) ...
Unpacking replacement ltmodem-2.6.8-2-386 ...
find: warning: you have specified the -mindepth option after a non-option argument -name, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.


Could not identify your distribution's way of automatically loading modules,
Exiting.

dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
find: warning: you have specified the -mindepth option after a non-option argument -name, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.


Could not identify your distribution's way of automatically loading modules,
Exiting.

dpkg: error processing ltmodem-2.6.8-2-386_8.31a11_i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
find: warning: you have specified the -mindepth option after a non-option argument -name, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.


Could not identify your distribution's way of automatically loading modules,
Exiting.

dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 ltmodem-2.6.8-2-386_8.31a11_i386.deb
root@Narayan:/home/ecliptux/Download #
When I'm ruuning, Synaptic, I have :
> E: The package ltmodem-2.6.8-2-386 needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
Howcan I repair apt-get ??!!!

---

### Post by adwait on 2005-10-12
Try
```
sudo apt-get remove ltmodem
```
or
```
sudo apt-get install -f 
```

---

### Post by EcliptuX on 2005-10-12
Same bad reslut :( :
> root@Narayan:/home/ecliptux/Download/ltmodem # apt-get remove ltmodem
Reading package lists... Done
Building dependency tree... Done
E: The package ltmodem-2.6.8-2-386 needs to be reinstalled, but I can't find an archive for it.
root@Narayan:/home/ecliptux/Download/ltmodem # apt-get install -f
Reading package lists... Done
Building dependency tree... Done
E: The package ltmodem-2.6.8-2-386 needs to be reinstalled, but I can't find an archive for it.

---

### Post by mlomker on 2005-10-12
You'll have to delete the package information:

```

sudo rm /var/lib/dpkg/info/ltmodem*

```

---

### Post by EcliptuX on 2005-10-12
OK I did it, the files have been deleted.
Unfortunately, it's not enough and I can't use again apt-get or synaptic correctly :(

---

### Post by mlomker on 2005-10-12
> Unfortunately, it's not enough and I can't use again apt-get or synaptic correctly 

Post the output.  You could also try downloading that file and reinstalling it.  It's complaining because the file is missing.  Do you still have it?

```

sudo dpkg -i [I]packagename.deb
[/I]
```

---

### Post by heimo on 2005-10-12
Where did you get that package originally? (repositroy / url) I'd probably try to reinstall it manually (dpkg -i ltmodem-version.deb)

EDIT: mlomker: excellent idea ;)

---

### Post by EcliptuX on 2005-10-12
I find the package on this page : [http://www.heby.de/ltmodem](http://www.heby.de/ltmodem) (and more exactly [http://www.sfu.ca/~cth/ltmodem/dists/debian/8.31a11/](http://www.sfu.ca/~cth/ltmodem/dists/debian/8.31a11/))
I tried to install this package : [http://www.sfu.ca/~cth/ltmodem/dists/debian/8.31a11/ltmodem-2.6.8-2-386_8.31a11_i386.deb](http://www.sfu.ca/~cth/ltmodem/dists/debian/8.31a11/ltmodem-2.6.8-2-386_8.31a11_i386.deb)

There, the output when I try to reinstall it :
> root@Narayan:/home/ecliptux/Download # dpkg -i ltmodem-2.6.8-2-386_8.31a11_i386.deb
Selecting previously deselected package ltmodem-2.6.8-2-386.
(Reading database ... 95793 files and directories currently installed.)
Preparing to replace ltmodem-2.6.8-2-386 8.31a11 (using ltmodem-2.6.8-2-386_8.31a11_i386.deb) ...
Unpacking replacement ltmodem-2.6.8-2-386 ...
find: warning: you have specified the -mindepth option after a non-option argument -name, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.



Updating the modules configuration files with:
  update-modules
Checking dependencies of remaining modules.

dpkg: dependency problems prevent configuration of ltmodem-2.6.8-2-386:
 ltmodem-2.6.8-2-386 depends on kernel-image-2.6.8-2-386; however:
  Package kernel-image-2.6.8-2-386 is not installed.
dpkg: error processing ltmodem-2.6.8-2-386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ltmodem-2.6.8-2-386


---

### Post by heimo on 2005-10-12
Ok, now try:
```
dpkg -r ltmodem-2.6.8-2-386
mv /var/lib/dpkg/info/ltmodem-2.6.8-2-386.* /tmp
apt-get install -f

``` 

EDIT: added a line
EDIT2: error... :)

---

### Post by EcliptuX on 2005-10-12
Yes !!!!
That's working now !!!

Thanks a lot [B]heimo :)
[/B]

---

