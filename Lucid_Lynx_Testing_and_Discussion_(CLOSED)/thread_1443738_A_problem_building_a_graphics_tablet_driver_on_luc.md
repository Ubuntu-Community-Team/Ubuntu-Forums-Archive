---
title: "A problem building a graphics tablet driver on lucid"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by techno-mole on 2010-03-31
Can anyone give me a pointer as to why when I run this - 

```
dpkg-buildpackage -rfakeroot
```

I get this error in terminal - 

```
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: error: tail of debian/changelog gave error exit status 1

```

What I am trying to do is install a driver for my graphics tablet, which was fine until I borked the system and had to start again, the last time I ran the steps to build the driver etc everything went fine.

Here are the steps I am using to build/install the driver (these are the steps as I was told on launchpads wizardpen section)

```
bzr branch lp:wizardpen (yes I have bzr installed)

Then I cd to the folder that downloads to my home directory (named wizardpen)

Then I run this - sudo ./autogen.sh and if all goes well, which it does.

Then I am meant to run this - dpkg-buildpackage -rfakeroot and in theory a .deb package for my system should be built, but it doesn't happen because of this error - 

dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: error: tail of debian/changelog gave error exit status 1

```

Any ideas as to why this has happened ? especially as it worked previously.

Thanks in advance for any advice.

---

### Post by techno-mole on 2010-04-01
*BUMP*

me again.

I get that it's looking for a specific folder and file, so is there a way it can be created ? there is a changelog file in the source folder, I have tried creating folder and placing the changelog into it, but it still moans about it not being there.

Is it a problem with the system or the driver files, eg they aren't complete ? or such like.

thanks in advance for any help.

---

### Post by EseNoy on 2010-04-07
Same problem here...

---

### Post by techno-mole on 2010-04-08
have you tried this - [launchpad installation instructions]("https://answers.launchpad.net/wizardpen/+faq/1021")

I am currently having an issue with this as it fails to build on my system (lucid beta) but you may have more luck, I would be interested to see if you encounter the same error as me.

cheers

---

### Post by SevenMachines on 2010-04-08
[FONT=monospace]the short answer is that you are trying to build a debian package (.deb) of code that has no packaging (the missing debian/directory). You can either,
* [Package it!]("https://wiki.ubuntu.com/PackagingGuide/Complete") - often easier than you might think :)
* Use someone elses packaging if its available!
* Use checkinstall to wrap around a manual install and generate a pseudo-debian package that way
* Ignore using the package managing system and compile and install manually, usually something like
$./autogen.sh
$./configure
$make
$sudo make install
[/FONT]

---

### Post by SevenMachines on 2010-04-08
ah, i think your missing the 'bzr get packaging' stage, try
$bzr branch [lp:~doctormo/wizardpen/debian-packing]("https://answers.launchpad.net/+branch/%7Edoctormo/wizardpen/debian-packing")  debian

after
$bzr branch [lp:wizardpen]("https://answers.launchpad.net/+branch/wizardpen")

(see [https://answers.launchpad.net/wizardpen/+faq/1021](https://answers.launchpad.net/wizardpen/+faq/1021))

{EDIT} as mentioned above by techno-mole!

---

### Post by techno-mole on 2010-04-08
this is what I end up with on lucid beta 1 when trying to build the driver packages, using the current faq on launchpad - 
```
make[3]: Entering directory `/home/techno-mole/wizardpen/man'
make[3]: *** No rule to make target `wizardpen.@DRIVER_MAN_SUFFIX@', needed by `all-am'. Stop.
make[3]: Leaving directory `/home/techno-mole/wizardpen/man'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/techno-mole/wizardpen'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/techno-mole/wizardpen'
make: *** [build-stamp] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
```

I get the above after running the ```
dpkg-buildpackage -rfakeroot
```

I have filed a bug report, and I've been trying to fix it myself, not that I have any idea what I'm doing, needless to say I haven't solved it yet :)

---

### Post by SevenMachines on 2010-04-08
sadly no such problem here but i'm guessing its autogen related, have you tried

$autoreconf

before running ./autogen.sh ?

do you get any related DRIVER_MAN_SUFFIX information when you run autogen?

---

### Post by SevenMachines on 2010-04-08
perhaps even
$autoreconf -if

---

### Post by techno-mole on 2010-04-08
I get the same result whether I run autoreconf or autoreconf -if the out put is exactly the same.

---

### Post by SevenMachines on 2010-04-08
hmm, does aclocal.m4 contain something like 'AC_SUBST([DRIVER_MAN_SUFFIX])' somewhere after autogen? there should also be something in configure and Makefile

are you up-to-date on wizardpen?
$bzr pull

i'm guessing you may need to update autotools though. i'll give it a quick try on an older ubuntu vm

---

### Post by SevenMachines on 2010-04-08
oops, 'wood for the trees' :) just a thought, techno-mole, do you have xutils-dev installed? Thats where those missing macros come from, it'll need to be installed, i'm not sure how up to date it needs to be

---

### Post by techno-mole on 2010-04-08
I have downloaded the files from bzr today, so I assume they are the most recent.

as for the " AC_SUBST([DRIVER_MAN_SUFFIX]) " I found nothing exactly like that in any of the files you mentioned, or anything that had that in it either, I searched through the files a couple of ties using gedit and it didn't find anything that mentions DRIVER_MAN_SUFFIX ?

if it's any help I don't seem to have a package called autotools specifically, I have autotools-dev - 20090611.1 ?

cheers

---

### Post by SevenMachines on 2010-04-08
yep, its certainly a missing xutils-dev problem, i'm not sure whether it should be a build-dep or not, i guess so but better to see what the good doctormo thinks.

---

### Post by techno-mole on 2010-04-08
well I have good news and bad news, I re-installed lucid last night, so I decided to remove everything (after trying to get this driver package to build) and start again, the good news is that I have managed to build a .deb package of the driver, the bad news is that it doesn't work, I'm back to the cursor going to the top left of the screen if I try and use the tablet.

It seems that for some reason there was something wrong with xutils-dev, but I don't know what.

The only error/issue I can see is this - dpkg-buildpackage: warning: Failed to sign .dsc and .changes file
 Don't know how important this is ?

cheers

---

### Post by SevenMachines on 2010-04-08
> **techno-mole said:**
> The only error/issue I can see is this - dpkg-buildpackage: warning: Failed to sign .dsc and .changes file
 Don't know how important this is ?
The signing stuff is important for uploading to repositories/ppa's etc and wouldnt cause the sort of problem your having, theres more on setting up name/gpg keys in the packaging guide.
i'm guessing dmesg and /var/log/Xorg.0.log will tell you more about the actual driver issues. i know nothing of tablets though!

---

