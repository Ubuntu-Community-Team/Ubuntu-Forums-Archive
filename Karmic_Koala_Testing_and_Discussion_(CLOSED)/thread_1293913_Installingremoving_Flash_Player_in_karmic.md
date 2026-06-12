---
title: "Installing/removing Flash Player in karmic"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Gonchos on 2009-10-17
After a smooth clean installation of Karmic in my laptop I tried to install Flash player to view some utube videos. I tried both  .deb installer and tar.gz file, and both failed. Now I have an error message in my top panel that reads : "An error ocurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error was : "Error: BrokenCount > 0" This usually means that your installed packages have unmet dependencies".

If I run the PM and fix the broken packages, ubuntu tries to upgrade "flashplugin-nonfree" and install "flashplugin-installer". It fails to do so with this error message "E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal."

Any ideas?

PS: I'm a total newbie around here, go easy on me :)

---

### Post by psyke83 on 2009-10-17
Try this:

```
$ sudo apt-get remove --purge adobe-flashplugin flashplugin-nonfree flashplugin-installer
$ sudo apt-get install flashplugin-installer
```

If you received warnings or errors from the above, post them here.

---

### Post by Carl Roberson on 2009-10-17
Maybe

[COLOR=Black]robersonfox@ubuntu:~$ sudo dpkg-reconfigure flashplugin-installer [/COLOR]

---

### Post by Gonchos on 2009-10-18
> $ sudo apt-get remove --purge adobe-flashplugin flashplugin-nonfree flashplugin-installerdpkg: error processing flashplugin-nonfree (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
> $ sudo apt-get install flashplugin-installersame error

> [COLOR=Black]sudo dpkg-reconfigure flashplugin-installer [/COLOR]Package `flashplugin-installer' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: flashplugin-installer is not installed


[COLOR=Black]
[/COLOR]:confused:

---

### Post by ronacc on 2009-10-18
open synaptic , at the lower left select "status" . if there are broken packages there will be a selection above saying broken select that and it will show you which packages are broken . try manualy selecting them for reinstallation .

---

### Post by Gonchos on 2009-10-18
> **ronacc said:**
> open synaptic , at the lower left select "status" . if there are broken packages there will be a selection above saying broken select that and it will show you which packages are broken . try manualy selecting them for reinstallation .

I had to select "Custom Filter" in order to see the broken packages and got this error: 

E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

---

### Post by ronacc on 2009-10-18
did you reinstall it ?

---

### Post by psyke83 on 2009-10-18
Try this:

```
$ sudo apt-get install --reinstall adobe-flashplugin
$ sudo apt-get install --reinstall flashplugin-nonfree
$ sudo apt-get remove --purge adobe-flashplugin
```

---

### Post by Gonchos on 2009-10-18
> did you reinstall it ? 	

I tried but got this error: 

E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal. 	

> $ sudo apt-get install --reinstall adobe-flashplugin


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package adobe-flashplugin has no installation candidate

> $ sudo apt-get install --reinstall flashplugin-nonfree

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

> sudo apt-get remove --purge adobe-flashplugin

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by ronacc on 2009-10-18
remove flashplugin-nonfree .

---

### Post by Gonchos on 2009-10-18
Same error ronacc

---

### Post by ronacc on 2009-10-18
do you have anything else flash related installed ? if so try removing that , use "remove completely' in synaptic .

---

### Post by Gonchos on 2009-10-18
Nothing else, just flashplugin-nonfree left

---

### Post by Vanishing on 2009-10-18
this is rather a risky attempt in solving your problem:
> sudo vim /var/lib/dpkg/status
or
> sudo gedit /var/lib/dpkg/status
or
> sudo kate /var/lib/dpkg/status

find the broken package, delete the paragraphs from "Package:" to "Description: "
save
fire up synaptic, reinstall the packages.

it WILL solve the problem:guitar:

---

### Post by ronacc on 2009-10-18
using nautilus go to /var/cache/apt/archives/  and see if the flashplugin-nonfree is there . If it is , open a terminal there and run ```
 sudo dpkg --force-all --purge ./<package name> 
```

---

### Post by Gonchos on 2009-10-18
> **Vanishing said:**
> this is rather a risky attempt in solving your problem:

or

or


find the broken package, delete the paragraphs from "Package:" to "Description: "
save
fire up synaptic, reinstall the packages.

it WILL solve the problem:guitar:
this did indeed solve it! thanks :)

No flash player, but I guess I will wait till Karmic is officially released and maybe this bug will be gone.

Thank you all!

---

### Post by Vanishing on 2009-10-18
> **Gonchos said:**
> this did indeed solve it! thanks :)

No flash player, but I guess I will wait till Karmic is officially released and maybe this bug will be gone.

Thank you all!

no problem.
but if you install the following 2 packages, youtube videos should work:
> sudo apt-get install flashplugin-installer adobe-flashplugin
try it..:guitar:

---

### Post by psyke83 on 2009-10-18
> **Vanishing said:**
> no problem.
but if you install the following 2 packages, youtube videos should work:

try it..:guitar:

Please, don't. The adobe-flashplugin and flashplugin-installer packages provide the same functionality. They *should* conflict, but they don't.

Here is a quick overview:
[LIST]
[*]flashplugin-installer - recommended package, fetches latest .tar.gz from Canonical server.
[*]flashplugin-nonfree - dummy package intended to ease upgrades, whose functionality is replaced by flashplugin-installer.
[*]adobe-flashplugin - provided either by Adobe's website or Canonical's partner repository. Currently seems to have buggy scripts which is causing problems for users.
[/LIST]

I recommend that you only install flashplugin-installer.

---

### Post by Gonchos on 2009-10-18
> $ sudo apt-get install flashplugin-installer

And everything runs nicely!

Thank you!

---

