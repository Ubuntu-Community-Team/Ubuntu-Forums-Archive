---
title: "Problems with Xfe (and fox)"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by Markstar on 2008-10-23
Hi,
I am new to Ubuntu and someone here recommended me Xfe as a file manager and it seemed to be exactly what I was looking for and imho far superior to Nautilus or common NC-clones like Midnight Commander. 

Now I would like to upgrade to the most recent version of Xfe, but I have run into a few problems. 
I followed the the Xfe documentation and checked in the Synaptic Package Manager if libfox was installed (it was) and installed libfox-dev. Then I downloaded the latest xfe version (*xfe-1.19.2.tar.gz*), unpacked it and ran ./configure, make and make install int the directory. Everything finished without errors, but when I run xfe from the console now, it says
> $ xfe
Error: Failed to load switchpanels.png icon. Please check your icon path...
Error: Failed to load syncpanels.png icon. Please check your icon path...
Error: Failed to load newlink.png icon. Please check your icon path...
 in the console. At the startup of xfe I then get the error message: 
> Error loading icons

Unable to load some icons. Please check your icons path!:(
This is all version 1.19.2. However, I have noticed that if I run ```
/usr/bin/xfe
```, I get xfe version 1.04. :confused:

What did I do wrong? Where is the new xfe located? 

Thank you in advance!

Kind regards
  Markstar

---

### Post by kerry_s on 2008-10-23
did you check synaptic if you removed the old one first?

**sudo apt-get install --purge remove xfe**

---

### Post by Markstar on 2008-10-23
> **kerry_s said:**
> did you check synaptic if you removed the old one first?

**sudo apt-get install --purge remove xfe**When I enter this command I get:
```
sudo apt-get install --purge remove xfe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package remove

```...and xfe 1.04 still starts...

---

### Post by kerry_s on 2008-10-23
> **Markstar said:**
> When I enter this command I get:
```
sudo apt-get install --purge remove xfe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package remove

```...and xfe 1.04 still starts...

my bag, it's:
**sudo apt-get --purge remove xfe**

just open synaptic then and check if xfe is installed, if it is remove it, locally compiled programs won't be in synaptic unless you used make deb.

---

### Post by Markstar on 2008-10-23
> **kerry_s said:**
> my bag, it's:
**sudo apt-get --purge remove xfe**Yes, that removed it. :)
I can still start Xfe ... with the errors (and another one):


> just open synaptic then and check if xfe is installed, It's not.
> if it is remove it, locally compiled programs won't be in synaptic unless you used make deb.I'm sorry, I don't know what you mean by that. :(  Are you saying that when I make a deb file out of the compiled program and install it, then it will show up in Synaptic again and install updates?

Anyways, after I checked if Xfe is gone in Synaptic, I compiled it again. However, I get even more errors now (looks like hundreds):
```
$ xfe
Error: Failed to load archadd.png icon. Please check your icon path...
Error: Failed to load archext.png icon. Please check your icon path...
..
Error: Failed to load syncpanels.png icon. Please check your icon path...
Error: Failed to load newlink.png icon. Please check your icon path...

```

I don't know if it helps, but those were the last lines of the "make install" command:
```
ln -s -f ../xfe-theme/zoomwin.png /usr/local/share/xfe/icons/windows-theme/zoomwin.png
ln -s -f ../xfe-theme/zoomwin.png /usr/local/share/xfe/icons/windows-theme/zoomwin.png

```

---

### Post by kerry_s on 2008-10-23
why are you building it from source?
they have a deb for debian systems:
[http://downloads.sourceforge.net/xfe/xfe_1.19.2-1_i386.deb?modtime=1217600796&big_mirror=0](http://downloads.sourceforge.net/xfe/xfe_1.19.2-1_i386.deb?modtime=1217600796&big_mirror=0)

just download it an:
sudo dpkg -i xfe_1.19.2-1_i386.deb
or 
in ubuntu just double click on the deb.

if you don't have libfox, the deb's are here:
[http://roland65.free.fr/xfe/index.php?page=fox-deb](http://roland65.free.fr/xfe/index.php?page=fox-deb)

there's no need to compile when there's debs.

first clean up what you have already:
sudo make clean
sudo make uninstall

---

### Post by oldos2er on 2008-10-23
After you've run ./configure and make, run "sudo make install".

---

### Post by Markstar on 2008-10-24
> **kerry_s said:**
> why are you building it from source?
they have a deb for debian systems:
[http://downloads.sourceforge.net/xfe/xfe_1.19.2-1_i386.deb?modtime=1217600796&big_mirror=0](http://downloads.sourceforge.net/xfe/xfe_1.19.2-1_i386.deb?modtime=1217600796&big_mirror=0)

just download it an:
sudo dpkg -i xfe_1.19.2-1_i386.deb
or 
in ubuntu just double click on the deb.

if you don't have libfox, the deb's are here:
[http://roland65.free.fr/xfe/index.php?page=fox-deb](http://roland65.free.fr/xfe/index.php?page=fox-deb)

there's no need to compile when there's debs.But those are for i386, my Ubuntu is 64bit. Doesn't that make a difference? 

Also, I did install it via Synaptic. Are you saying I should upgrade to the most recent version? Again, I only see the 32bit version there...sorry, but I'm really confused. :(

> first clean up what you have already:
sudo make clean
sudo make uninstallI did that, but I got:
```
$ sudo make clean
[sudo] password for markstar: 
make: *** No rule to make target `clean'.  Stop.

```Where exactly am I supposed to do that?


@oldos2er: I ran all commands as superuser.

---

### Post by oldos2er on 2008-10-24
> **Markstar said:**
> 
@oldos2er: I ran all commands as superuser.

 You should run ./configure and make without sudo, then run sudo make install. Since it appears you already ran make clean, you might want to try this again.

---

### Post by kerry_s on 2008-10-24
okay, so you want 64bit.

grab this 1:
[ftp://ftp.pbone.net/mirror/ftp5.gwdg.de/pub/opensuse/repositories/X11:/FOX/SLE_10/x86_64/xfe-1.19.2-1.1.x86_64.rpm](ftp://ftp.pbone.net/mirror/ftp5.gwdg.de/pub/opensuse/repositories/X11:/FOX/SLE_10/x86_64/xfe-1.19.2-1.1.x86_64.rpm)

your going to convert it for a debian system, so first you need alien:

**sudo apt-get install alien**

then convert the *.rpm to a deb:

**alien xfe-1.19.2-1.1.x86_64.rpm**

then install it:

**sudo dpkg -i xfe-1.19.2-1.1.x86_64.deb**

---

### Post by Markstar on 2008-10-24
> **kerry_s said:**
> okay, so you want 64bit.

grab this 1:
[ftp://ftp.pbone.net/mirror/ftp5.gwdg.de/pub/opensuse/repositories/X11:/FOX/SLE_10/x86_64/xfe-1.19.2-1.1.x86_64.rpm](ftp://ftp.pbone.net/mirror/ftp5.gwdg.de/pub/opensuse/repositories/X11:/FOX/SLE_10/x86_64/xfe-1.19.2-1.1.x86_64.rpm)

your going to convert it for a debian system, so first you need alien:

**sudo apt-get install alien**Alright, I installed some alien on my PC. :)

> then convert the *.rpm to a deb:

**alien xfe-1.19.2-1.1.x86_64.rpm**This part did not work - I get the following output when running this as root:
```
alien xfe-1.19.2-1.1.x86_64.rpm 
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
mkdir: cannot create directory `xfe-1.19.2': File exists
unable to mkdir xfe-1.19.2:  at /usr/share/perl5/Alien/Package.pm line 257.
``` :(

---

### Post by kerry_s on 2008-10-24
> **Markstar said:**
> Alright, I installed some alien on my PC. :)

This part did not work - I get the following output when running this as root:
```
alien xfe-1.19.2-1.1.x86_64.rpm 
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
warning: xfe-1.19.2-1.1.x86_64.rpm: Header V3 DSA signature: NOKEY, key ID 0f2672c8
mkdir: cannot create directory `xfe-1.19.2': File exists
unable to mkdir xfe-1.19.2:  at /usr/share/perl5/Alien/Package.pm line 257.
``` :(



looks like a permission thing

try:

**sudo alien xfe-1.19.2-1.1.x86_64.rpm**

if that don't work, i give up. :(

---

### Post by Markstar on 2008-10-25
> **kerry_s said:**
> looks like a permission thing

try:

**sudo alien xfe-1.19.2-1.1.x86_64.rpm**

if that don't work, i give up. :(No, I had tried this already before posting the last time ... with the same result. :(

I think I would like to start over:
1) clean up Xfe (in Synaptic it is already gone, but the compile version is still there...**but where???**)
2) download the newest libfox version from their homepage and try again.

So...removing the manually compiled program is a general question for me:
In Windows, I know where the programs are installed and how to uninstall them - but how do I do that in Ubuntu? Where to the programs go after I ran "*make install*"?

Again, thank you for your time!

---

### Post by kerry_s on 2008-10-25
> **Markstar said:**
> No, I had tried this already before posting the last time ... with the same result. :(

I think I would like to start over:
1) clean up Xfe (in Synaptic it is already gone, but the compile version is still there...**but where???**)
2) download the newest libfox version from their homepage and try again.

So...removing the manually compiled program is a general question for me:
In Windows, I know where the programs are installed and how to uninstall them - but how do I do that in Ubuntu? Where to the programs go after I ran "*make install*"?

Again, thank you for your time!

sounds like a good idea, sorry i couldn't help.

in term:

sudo updatedb
locate xfe

might help you find things.

---

### Post by Markstar on 2008-10-25
Alright, I located the files, they seem to be in these places```
/usr/local/bin/xfe
/usr/local/share/xfe
/usr/local/share/locale/ca/LC_MESSAGES/xfe.mo
/usr/local/share/locale/cs/LC_MESSAGES/xfe.mo

```Again, sorry for the stupid question...but is it okay for me to just delete them or is there something else I need to clean up (like a registry-like file). I'm just asking because I can still execute Xfe from anywhere which would lead me to believe that something must still be connected to it (or is it just because there is one(!) xfe file is in /usr/local/bin/ ?).

---

### Post by kerry_s on 2008-10-25
> **Markstar said:**
> Alright, I located the files, they seem to be in these places```
/usr/local/bin/xfe
/usr/local/share/xfe
/usr/local/share/locale/ca/LC_MESSAGES/xfe.mo
/usr/local/share/locale/cs/LC_MESSAGES/xfe.mo

```Again, sorry for the stupid question...but is it okay for me to just delete them or is there something else I need to clean up (like a registry-like file). I'm just asking because I can still execute Xfe from anywhere which would lead me to believe that something must still be connected to it (or is it just because there is one(!) xfe file is in /usr/local/bin/ ?).

yes, you can delete them
yes, /usr/local/bin/xfe is the executable

---

### Post by Markstar on 2008-10-26
> **kerry_s said:**
> yes, you can delete them
yes, /usr/local/bin/xfe is the executableFrom your answer I derived that there is nothing else to take care of, so I proceeded with the plan (download and compile newest libfox, then compile newest Xfe).

In the INSTALL file, I read this section:
> Building 64-bit code on Linux for x86-64 (AMD Opteron, Athlon64)
================================================================

Linux for AMD Opteron supports execution of both 32 and 64 bit code
on the same system; consequenly, two sets of libraries are installed.
To configure properly, you will need to let ld search the right set
of directories.  Here's how:


        export LDFLAGS="-L/usr/lib64 -L/usr/X11R6/lib64 -L/lib64"
        ./configure <other options>


No other issues are known at this time.Don't know what the command means but I did the export-command prior to ./configure. 
Here is what I got when I ran ./configure with fox-1.6.34:
```
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating utils/Makefile
config.status: WARNING:  utils/Makefile.in seems to ignore the --datarootdir setting
config.status: creating include/Makefile
config.status: WARNING:  include/Makefile.in seems to ignore the --datarootdir setting
config.status: creating include/fxver.h
config.status: creating src/Makefile
config.status: WARNING:  src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating src/version.rc
config.status: creating chart/Makefile
config.status: WARNING:  chart/Makefile.in seems to ignore the --datarootdir setting
config.status: creating doc/Makefile
config.status: WARNING:  doc/Makefile.in seems to ignore the --datarootdir setting
config.status: creating doc/art/Makefile
config.status: WARNING:  doc/art/Makefile.in seems to ignore the --datarootdir setting
config.status: creating doc/screenshots/Makefile
config.status: WARNING:  doc/screenshots/Makefile.in seems to ignore the --datarootdir setting
config.status: creating tests/Makefile
config.status: WARNING:  tests/Makefile.in seems to ignore the --datarootdir setting
config.status: creating adie/Makefile
config.status: WARNING:  adie/Makefile.in seems to ignore the --datarootdir setting
config.status: creating shutterbug/Makefile
config.status: WARNING:  shutterbug/Makefile.in seems to ignore the --datarootdir setting
config.status: creating pathfinder/Makefile
config.status: WARNING:  pathfinder/Makefile.in seems to ignore the --datarootdir setting
config.status: creating calculator/Makefile
config.status: WARNING:  calculator/Makefile.in seems to ignore the --datarootdir setting
config.status: creating windows/Makefile
config.status: WARNING:  windows/Makefile.in seems to ignore the --datarootdir setting
config.status: creating fox.spec
config.status: creating fox-config
config.status: creating fox.pc

```
*make* finished without any problems, though I did see some warnings flashing by from time to time.** I was also wondering about the fact that in Synaptic, there is libfox and libfox-dev, while on their homepage I can only download one version.** :confused:

Anyways, I proceeded to *sudo make install*, which also finished without any errors. :)

**_Then on to Xfe:_**
Even though I had downloaded and unpacked the archive as normal user, it seems I could only write and execute the files as super user and I got an error message when I ran *./configure*. So I ran *sudo ./configure*, which ran without any errors. Next was *sudo make* (again, running it as normal user wouldn't work), but there were a bunch of warnings like:
```
CommandWindow.cpp: In member function ‘FX::FXint CommandWindow::execCmd(FX::FXString)’:
CommandWindow.cpp:160: warning: ignoring return value of ‘int dup(int)’, declared with attribute warn_unused_result
CommandWindow.cpp:161: warning: ignoring return value of ‘int dup(int)’, declared with attribute warn_unused_result
CommandWindow.cpp:162: warning: ignoring return value of ‘int dup(int)’, declared with attribute warn_unused_result
```, but it finished without errors, only telling me that the compiler was leaving some directories. So final step was *sudo make install*, which also finished without errors. These were the final lines:
```
ln -s -f ../xfe-theme/zoomwin.png /usr/local/share/xfe/icons/windows-theme/zoomwin.png
ln -s -f ../xfe-theme/zoomwin.png /usr/local/share/xfe/icons/windows-theme/zoomwin.png
ln -s -f ../xfe-theme/zoomwin.png /usr/local/share/xfe/icons/windows-theme/zoomwin.png
ln -s -f ../xfe-theme/zoomwin.png /usr/local/share/xfe/icons/windows-theme/zoomwin.png
make[3]: Leaving directory `/home/markstar/Progs/xfe-1.19.2'
make[2]: Leaving directory `/home/markstar/Progs/xfe-1.19.2'
make[1]: Leaving directory `/home/markstar/Progs/xfe-1.19.2'
```
No errors - great, but when I ran xfe, I got this:
```
s$ xfe
xfe: error while loading shared libraries: libFOX-1.6.so.0: cannot open shared object file: No such file or directory
```]:cry:

Why, oh, why???? :(

---

### Post by gesy on 2009-05-27
Hi,

in your Home directory, you'll find the hidden one ".xfe". Enter in it and edit the config's file "xferc". Change the path for the icons (For me, it is: "/usr/local/share/xfe/icons/xfe-theme/").

That's all and will work!

---

