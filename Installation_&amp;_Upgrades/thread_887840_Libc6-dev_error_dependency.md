---
title: "Libc6-dev error dependency"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by ZeroRider13 on 2008-08-12
Hey, I have been trying to get my USRobotics modem to work for a while, but I've sorta given up on that and moved onto trying to get my internal Conexant to work.  I got the first package listed on linuxant.com, and got an error dependency for alsa-linux-driver.  I went back on linuxant and got the alsa-linux-driver.deb.  When I tried to install this, I got an error dependency for libc6-dev.  Where can I get this and any other error dependency or any other things Im going to run into while trying to install this?

Thanks alot.

---

### Post by ZeroRider13 on 2008-08-12
Sorry to double post but Im sorta at a deadend if I dont do this, anyone know what I should do?

---

### Post by mc4man on 2008-08-12
you'll need to post some add. info.

What version of ubuntu are you using?
Go into synaptic and get the ver. # of the installed libc6.
While there see if libc6-dev is installed, if not see if it will install.
Post the error mess. from attempting to install the.deb.
If possible provide a link to where your getting the.deb

Don't mess around/force versions with libc6 or you can easily be looking at a re install.

---

### Post by ZeroRider13 on 2008-08-12
I am using the 8.04 of Ubuntu
Synaptic says Libc6 current version 2.7-10ubuntu3, then the latest version is the same.  I do not have an internet connection on that computer so I cant download libc6-dev, and no i dont see it installed there, can I download it onto a flash drive on this computer and put it onto that one?  

If I can, from there am i supposed to install libc6-dev, then the alsa driver, then the conexant driver?  Or will i get another error while trying to download libc6-dev?

I got the conexant driver from [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php) It is the first one on that list in the first list.
Then the alsa driver was from [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) it is the .deb there.

---

### Post by mc4man on 2008-08-13
> can I download it onto a flash drive on this computer and put it onto that one
Yeah, here's the ver. (i386 one for 32bit)
[http://packages.ubuntu.com/hardy/libc6-dev](http://packages.ubuntu.com/hardy/libc6-dev)
Choose to save file and then install on yours.

> If I can, from there am i supposed to install libc6-dev, then the alsa driver, then the conexant driver

Install the -dev First. 
I haven't fooled with those drivers (no need to ) so don't know. Any problems with above post back, problems w/ drivers better to start a new thread title


Edit: if you need to post on the drivers, you should know what your hardware is, this tells you alot in a very readable format (look in home for > hardware.html

> sudo lshw -html > hardware.html

---

### Post by ZeroRider13 on 2008-08-13
Thanks for your help, but I got another error dependency for "linux-libc-dev" and I posted it on general, aywhere I could get all these libs so i dnt keep running into this?  How many more errors will i get and other drivers will i need to install?

---

### Post by mc4man on 2008-08-13
[http://packages.ubuntu.com/hardy/linux-libc-dev](http://packages.ubuntu.com/hardy/linux-libc-dev)

Here's the -dev (if you didn't already get.

That's should do it, didn't mention before,wrongly assumed you had it


Here's an easy way you can find packages when needed, just search as such, usually first result will be packages.ubuntu........
or go here and search (bookmark page

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by ZeroRider13 on 2008-08-13
Thank you a lot, only a question or two left =)  The alsa-linux-driver says Error:Dependency not satisfiable: patch.  
I went to that linand got it, then loaded it u and it ran patch.man.  Alsa still wont work.  Am I dong something wrong or did I download the wrong thing?

---

### Post by mc4man on 2008-08-13
[http://packages.ubuntu.com/hardy/patch](http://packages.ubuntu.com/hardy/patch)

What you can do is after you download a .deb is -  right click on it -> open with archive manager -> d. click on the control.tar.gz -> double click on the folder that pops up -> and d. click on the control file. 
(don't extract, just d. click thru
Below is typical

> 
Package: alsa-driver-linuxant
Version: 1.0.17.5-1
Section: unknown
Priority: extra
Architecture: all
[COLOR="Red"]Depends: gcc, perl, make, libc6-dev, patch[/COLOR]
Installed-Size: 22524
Maintainer: Linuxant inc. <support@linuxant.com>
Source: alsa-driver
Description: ALSA driver enhanced for Conexant HDA modem support

---

### Post by ZeroRider13 on 2008-08-13
Ohnevermnd, I did everything you said and the control file says this:

Package: patch
Version: 2.5.9-4
Section: utils
Priority: standard
Architecture: i386
Depends: libc6 (>= 2.4-1)
Suggests: ed, diff-doc
Installed-Size: 188
Maintainer: Christoph Berg <myon@debian.org>
Description: Apply a diff file to an original
 Patch will take a patch file containing any of the four forms
 of difference listing produced by the diff program and apply
 those differences to an original file, producing a patched
 version.

What do I do from here?

---

### Post by mc4man on 2008-08-13
> What do I do from here? you needed the package patch installed (a dependency  of the alsa packeage you were trying to install)
So just install it.

As far as the control file

I was just trying to show you a way to find the dependencies of packages your trying to install (now or in the future) by looking in the control file of said package.

Ie. for the alsa package - Depends: gcc, perl, make, libc6-dev, patch
now you'd know beforehand what it needs to compare to what you have installed. Merely a possible way to save time.


edit; so looking at your alsa package you'll also need 'make', (no problem just dl. the hardy ver. & install),  perl and gcc

They are going to a bit trickier, perl will need maybe 4 packages total, gcc will need 5 or so depending on the ver. you install and for both you must pay attention to versions. It would be best to collect **all** the needed packages for both in **proper versions**, put them in a folder, cd to that folder and run
> dpkg -i *.deb

For perl probably this ver.
```
Package: perl
[COLOR="Red"]Version: 5.8.8-12[/COLOR]
Architecture: i386
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Brendan O'Dea <bod@debian.org>
Installed-Size: 11440
Depends: perl-base ([COLOR="Red"]= 5.8.8-12[/COLOR]), perl-modules ([COLOR="Red"]>= 5.8.8-12)[/COLOR], [COLOR="Blue"]libc6 (>= 2.6.1-1)[/COLOR], libdb4.6, libgdbm3
...................................
Conflicts: perl-doc (<< 5.8.8-1), libdigest-md5-perl (<< 3.07-1), libmime-base64-perl (<< 3.07-1), libtime-hires-perl (<< 1.86-1), libstorable-perl (<< 2.15-1)
Replaces: perl-base (<< 5.8.8-1), perl-doc (<< 5.8.0-1), perl-modules (<< 5.8.1-1), libdigest-md5-perl, libmime-base64-perl, libtime-hires-perl, libstorable-perl
```

for gcc there are several versions - latest hardy 4.2

```
Package: gcc-4.2
[COLOR="Red"]Version: 4.2.3-2ubuntu7[/COLOR]
Architecture: i386
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Installed-Size: 1304
Depends: binutils ([COLOR="Red"]>= 2.17cvs20070426[/COLOR]), cpp-4.2 ([COLOR="Red"]= 4.2.3-2ubuntu7[/COLOR]), gcc-4.2-base ([COLOR="Red"]= 4.2.3-2ubuntu7[/COLOR]), [COLOR="Blue"]libc6 (>= 2.7-1)[/COLOR], libgcc1 ([COLOR="Red"]>= 1:4.2.3-2ubuntu7[/COLOR]), libgomp1 ([COLOR="Red"]>= 4.2.3-2ubuntu7[/COLOR])
Recommends: libc6-dev (>= 2.5)
Suggests: gcc-4.2-doc (>= 4.2.3-1), gcc-4.2-locales (>= 4.2.3-1), gcc-4.2-multilib, libgcc1-dbg, libgomp1-dbg, libmudflap0-4.2-dbg, libmudflap0-4.2-dev (>= 4.2.3-2ubuntu7)
Replaces: gcc-4.2-base (<< 4.2.1-5)
Provides: c-compiler
```

Pay close attention to versions of all packages

If there are conflicts listed ck. if they're installed first

You already have what's in blue, if any package you try to install conflicts with that (libc6) the you have **the wrong package**, **not the wrong libc6**

You may also need binutils-dev if so get same version as binutils

Generally speaking you would need to also ck. the dependencies of all these new packages looking for deps that weren't either already installed or part of the group and if so add to the folder.(also keeping an eye on versions if warranted. 
In this case I think it's should be self contained though you might want to ck.

---

