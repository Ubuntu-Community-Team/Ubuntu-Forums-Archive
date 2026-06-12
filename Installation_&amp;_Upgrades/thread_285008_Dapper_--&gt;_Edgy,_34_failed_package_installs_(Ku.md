---
title: "Dapper --&gt; Edgy, 34 failed package installs (Kubuntu)"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by SickIcarus on 2006-10-26
Hello All,
So I upgraded from Dapper to the Edgy RC last week, but have a bunch of packages held back for broken dependencies. Details below:

> 
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  hpijs libggi2 mplayer python-adns python-clientcookie python-crypto
  python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools
  python-egenix-mxtools python-gadfly python-htmlgen python-htmltmpl
  python-imaging python-imaging-sane python-jabber python-kjbuckets
  python-ldap python-mysqldb python-pam python-pexpect python-pgsql
  python-pylibacl python-pyopenssl python-pyxattr python-reportlab
  python-simpletal python-soappy python-sqlite python-syck python-xml
  python-xmpp vmware-player x-window-system-core
The following packages will be upgraded:
  dvd+rw-tools
1 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
Need to get 0B/142kB of archives.
After unpacking 8192B disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


> 
sudo apt-get install kubuntu-desktop python-qt3 python-kde3 ubuntu-minimal
Reading package lists... Done
Building dependency tree
Reading state information... Done
python-qt3 is already the newest version.
python-kde3 is already the newest version.
ubuntu-minimal is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: xorg but it is not going to be installed
E: Broken packages


Help?

---

### Post by SickIcarus on 2006-10-26
Oh, and as for dvd+rw-tools - I found that the version Ubuntu uses breaks my burners, has since Dapper, so I've been using the one from the Debian repos - same version as the one Edgy installs, just without the -ubuntu1 tag. Dunno why the generic Debian one works and ubuntu's doesnt, but that's neither here nor there :-)

---

### Post by library.ninja on 2006-10-26
Have you tried the steps listed here?

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Specifically,

> sudo apt-get install kubuntu-desktop python-qt3 python-kde3 ubuntu-minimal

I ask b/c I ran into the same problem last night / this morning and I don't have the system with me to try this out as a solution.

---

### Post by SickIcarus on 2006-10-26
Yes, I followed those steps:

> #

In the console run:

    *

        sudo apt-get update 

#

In the console run:

    *

        sudo apt-get dist-upgrade 

      Follow the prompts to upgrade

#

In the console run:

    *

        sudo apt-get install kubuntu-desktop python-qt3 python-kde3 ubuntu-minimal 

And the results I got are posted above.

---

### Post by SickIcarus on 2006-10-26
Any thoughts?

---

### Post by spaceghoti on 2006-10-26
I have much the same thing dealing with python upgrades.  The Adept package manager allows me to try to force the installation, but I don't know what it's going to do to my installation if I try.  I confess I'm a bit leery about it, but I'm not sure what else I need to do to ensure that I have a full upgrade from Knot Three to the final release.

---

### Post by library.ninja on 2006-10-27
The only method I've found that will work is to go through Adept and manually update each package.  It's never said anything about having to force anything.  I've gone through all of the programs this way and it's worked out fine.

---

### Post by SickIcarus on 2006-10-27
> **library.ninja said:**
> The only method I've found that will work is to go through Adept and manually update each package.  It's never said anything about having to force anything.  I've gone through all of the programs this way and it's worked out fine.

When I try that it does the following:

1) Each package selected to force upgrade sets other packages to be removed - kindof scary, but when I press on...

2) It still fails to install them, saying it will break.

I've also tried firing up Synaptic to repair broken dependencies, but that reports none broken.

---

### Post by Omegatron on 2006-10-29
I have the exact same problem.  Any solutions?

Are you using Automatix?  I tried that the other day and was very happy to see it install everything and make it work, but now I'm afraid it's the reason for my problems.

I was able to get these installed:

sudo apt-get install kubuntu-desktop python-qt3 python-kde3 ubuntu-minimal

by installing libgl1-mesa-glx and xorg, but I still have a list of kept back packages.  Is that bad?

---

### Post by ceros on 2006-10-29
> kubuntu-desktop: Depends: xorg but it is not going to be installed

That's strange, I have xorg installed. Everything's working for me. For some reason when I upgraded, it took out xserver-xorg. I had to put it back in. Try these two things.

```
sudo apt-get install xorg
```
```
sudo apt-get install xserver-xorg
```
and in case you need to configure your video card.
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ceros on 2006-10-29
For all those packages that are held back, they're held back because they will replace other packages. I've installed every held back package anyways, except for vmware-player and x-windows-system-core. I never had those two packages installed. hpijs replaces hplip and some other packages I can't recall. libggi2 replaces libggi1. All the python packages replace another python package with a similar name, (python-adns replaces python-2.4-adns, etc.). I don't remember exactly what mplayer replaces.

---

### Post by Omegatron on 2006-10-29
> **ceros said:**
> For all those packages that are held back, they're held back because they will replace other packages. I've installed every held back package anyways, except for vmware-player and x-windows-system-core. I never had those two packages installed. hpijs replaces hplip and some other packages I can't recall. libggi2 replaces libggi1. All the python packages replace another python package with a similar name, (python-adns replaces python-2.4-adns, etc.). I don't remember exactly what mplayer replaces.

So we should force it to install those held back packages?  How do we do that?  Just tell it to install each one separately?

---

### Post by ceros on 2006-10-29
That's right.
```
sudo apt-get install *individual-package*
```

Or use adept_updater, highlight every held back package, right-click and select upgrade.

---

### Post by Omegatron on 2006-10-29
> **ceros said:**
> Or use adept_updater, highlight every held back package, right-click and select upgrade.

gives:

> There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.

Doing it with apt-get is working mostly, though some have unmet dependencies.  I'll post again when I've whittled it down to ones I don't know how to handle.

---

### Post by Omegatron on 2006-10-29
Ok.  I got it down to just libarts1-audiofile held back.  I tried to install that and it needed something else-dev.   I tried to install that and it needed three other -dev things.  So I just did apt-get remove libarts1-audiofile.  :-)  Now adept-updater says it's all up to date.

Too bad Firefox crashes...

---

### Post by georgeav on 2006-10-29
> **SickIcarus said:**
> Yes, I followed those steps:



And the results I got are posted above.

I got the same error because I had a repo from beerorkid.com also setup; and there were some problems with the packages. You might check what repos you have setup and leave only the ubuntu ones.

---

### Post by Detox Genie on 2006-12-30
```
The following packages have been kept back:
  hpijs python-clientcookie python-crypto python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-gadfly python-htmlgen python-htmltmpl python-jabber python-kde3
  python-kjbuckets python-ldap python-mysqldb python-opengl python-pam
  python-pexpect python-pgsql python-pylibacl python-pyopenssl python-pyorbit
  python-pyxattr python-qt3 python-reportlab python-simpletal python-soappy
  python-sqlite python-syck python-xml python-xmpp x-window-system-core
```

Getting rid of this mess was a multi-step process.
[LIST=1]
[*]Make sure that there are no non-offical repositories in your sources.list.  Comment them out if necessary, just for now.
[*]Make sure your local repository is up to date. ;)
```
sudo apt-get update
```
[*]Update hpijs.  Apt-get complained a bit, but it removed and reinstalled everything successfully anyway.
```
sudo apt-get install hpijs hpijs-ppd hpijs-doc
```
[*]Get rid of x-window-system-core, trusting the "safe to remove" description aptitude gives.  It looks like it is only a dummy compatibility package.
```
sudo apt-get remove x-window-system-core
```
[*]Deal with the python mess.
```
sudo apt-get upgrade
```
This will produce a list of all the python packages being held back on the system.  Highlight it and paste it into your text editor of choice.  Delete the line breaks and extra spaces, leaving each package name separated by only a single space.  This format is so that it can all go on one command line after an "sudo apt-get install".
```
sudo apt-get install python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-gadfly python-htmlgen python-htmltmpl python-jabber python-kde3 python-kjbuckets python-ldap python-mysqldb python-opengl python-pam python-pexpect python-pgsql python-pylibacl python-pyopenssl python-pyorbit python-pyxattr python-qt3 python-reportlab python-simpletal python-soappy python-sqlite python-syck python-xml python-xmpp
```
Make sure to use your own list of python packages.  I don't think the above list quite covers them all, but is should be very close.  Apt-get will complain a lot during the install, but everything seems to work afterwards.  Future upgrades won't show any packages being held back anymore.
[/LIST]
This can all be done with a gui as well, using a similar process, but the command line gives more info about whats actually going on.

---

