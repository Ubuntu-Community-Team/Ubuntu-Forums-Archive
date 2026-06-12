---
title: "apt-get wine"
date: 2005-06-01
forum: Installation &amp; Upgrades
---

### Post by coriolan on 2005-06-01
I am a new Ubuntu user (just installed), I would need to install wine on an AMD64 machine, but *apt-cache search wine* only contains the documentation. :???:

---

### Post by Rodrigo on 2005-06-01
add the repositories to your sources.list

then do a:  sudo apt-get install wine

and thats it.

any problems?... read the ubuntu guide "http://ubuntuguide.org/#gettingstarted"

any wine problems?.... google is your friend...   wine hq

---

### Post by az on 2005-06-01
Does wine run in 64-bit?

---

### Post by coriolan on 2005-06-02
[QUOTE=Rodrigo]add the repositories to your sources.list

then do a:  sudo apt-get install wine

and thats it.

any problems?... read the ubuntu guide "http://ubuntuguide.org/#gettingstarted"
[/QUOTE]

Yes, I followed the instructions in [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) to the letter but
# sudo apt-get install wine
says:
```
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list ftp://ftp.nerim.net testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package wine has no installation candidate

```

---

### Post by coriolan on 2005-06-02
Well, I bought the Crossover Office now and it seems to work just fine here, but I am still curious of why did apt-get failed.  :confused:

---

### Post by shof2k on 2005-06-02
[QUOTE=coriolan]Well, I bought the Crossover Office now and it seems to work just fine here, but I am still curious of why did apt-get failed.  :confused:[/QUOTE]
 Post a list of your /etc/apt/sources.list file and we'll take a look.  Crossover office is essentially a souped up version of wine, so you've got everything sorted there :)

Just on a side note, I've only managed to get wine 20041019 working at the moment.  Any later version causes winetools to fail and stop my office installation.  Anyone else had this?

---

### Post by mingus on 2005-06-02
It is in the backports repository . . . I had no problem installing

---

### Post by AndyAWS on 2005-06-02
[QUOTE=coriolan]Yes, I followed the instructions in [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) to the letter [/QUOTE]

Do not use the merillat repos...use the Backports instead...as I understand it the ubuntuguide is currently being rewritten to that effect. New packages from the merillat repo may break your box.

---

### Post by coriolan on 2005-06-04
My sources.list is as follows:

```
deb http://fi.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://fi.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fi.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://fi.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://fi.archive.ubuntu.com/ubuntu hoary universe
deb-src http://fi.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
``` 

I removed the merillat from the end.

---

### Post by mingus on 2005-06-04
So did you get it from backports?

Sor what it's worth, because I have many different repositories in my sources.list, I prefer to use Synaptic.  If you are going to install from outside of the standard supported Ubuntu repository, it may be important to know what other versions there are, compare them, and prioritize (or if necessary, force) which version to install.

---

### Post by coriolan on 2005-06-05
No, with that source.list running
# sudo apt-get -s install wine
still says:
E: Package wine has no installation candidate

---

### Post by mingus on 2005-06-05
Run Synaptic
Settings/Preferences/General/Appearance:  Show properties in main window
Search "wine" and click on it
click on Versions tab below - should show Hoary + 2 backports versions
click on the version you want, then Package/Force Version
Apply

---

### Post by coriolan on 2005-06-05
Searching for wine (in *Synaptic* or with *apt-cache)* shows only the *wine-doc* package.

---

### Post by mingus on 2005-06-05
And in Synaptic under Settings/Repositories does it show Backports?

---

### Post by coriolan on 2005-06-05
Well, it shows the same things that in the source.list, which I pasted earlier. There are items for backports and extras from [http://ubunutu-backports.mirrormax.net/](http://ubunutu-backports.mirrormax.net/). Both are binary. Do you mean these?

---

### Post by mingus on 2005-06-05
Yes.  Just one more quick one, you said earlier that the search does return "wine-doc".  When you look at the Versions tab for wine-doc, does it show a version from Backports?

---

### Post by coriolan on 2005-06-05
No, it does not.

---

### Post by mingus on 2005-06-05
OK.  So let's see if apt-get is broken . . .

In the browser go to:

[http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/)

navigate down thru /dists to /hoary-backports.  There you should find a /main directory and a /universe directory.  Under /main/*i386 is where the 3-10 version of the wine deb is, and under /universe/*i386 you'll find the 4-19 version.

If you are able to navigate to these files, then for some reason when you Reload in Synpatic or do apt-get update, your package directory is not getting this site added.

---

### Post by coriolan on 2005-06-05
Aha, but this machine is AMD64! There is nothing much in 
/dists/hoary-backports/main/binary-amd64 or
/dists/hoary-backports/universe/binary-amd64.

---

### Post by az on 2005-06-05
Windows is 32 bit.  Wine is 32 bit.  I brought this up five days ago.  There is no 64 bit version of wine!

---

### Post by coriolan on 2005-06-05
Indeed, but now I know why apt-get cannot find wine: it's looking for it from amd64 directories. Since I now have Crossover Office and it's working, the problem is solved!  :)

---

### Post by mingus on 2005-06-05
[QUOTE=azz]Windows is 32 bit.  Wine is 32 bit.  I brought this up five days ago.  There is no 64 bit version of wine![/QUOTE]


good grief!!!  thx, azz

---

