---
title: "Held Broken Packages"
date: 2013-11-21
forum: Installation &amp; Upgrades
---

### Post by norvans on 2013-11-21
Using Ubuntu 13.04 (gnome version)
Whenever I try install an application using the terminal:

[COLOR=#222222][FONT=Verdana]sudo apt-get install <some program>[/FONT][/COLOR]
I have error messages such as:

[COLOR=#222222][FONT=Verdana]E: Unable to correct problems, you have held broken package.[/FONT][/COLOR]

I have tried, as suggested in many different posts to check what were the broken packages by using:

dpkg --get-selections | grep hold
But I have no results. I have also tried this, but was pointless:

[FONT=Ubuntu Mono, monospace][COLOR=#000000]sudo apt-mark showhold[/COLOR][/FONT]
Please help me fix this package problem, I cannot install anything new from both the terminal and Software Center... I have also tried using synaptic in edit > fix packages, but still the problem goes on...

---

### Post by ibjsb4 on 2013-11-21
```
sudo apt-get clean
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
```

Get any errors?

---

### Post by norvans on 2013-11-21
After typing:


```
sudo apt-get clean
sudo dpkg --configure -a
sudo apt-get -f install 
```


I got nothing from the 2 first commands and for the third one:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  p7zip
Use 'apt-get autoremove' to remove it. 
```

So I did the autoremove with no errors.
I did the apt-get update with no errors.

Tried installing a program, and still got the same problem:
```
sudo apt-get install mysql-server mysql-client 
```

Received:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 mysql-client : Depends: mysql-client-5.5 but it is not going to be installed
 mysql-server : Depends: mysql-server-5.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages. 
```

It might be a problem the Ubuntu Gnome 13.04 version, but I doubt it since no one seemed to have complained about it...
Could it be a problem in the repositories?

---

### Post by ian-weisser on 2013-11-21
What happens when you try:
```
sudo apt-get install mysql-client-5.5 mysql-server-5.5
```

---

### Post by norvans on 2013-11-21
Well, pretty much the same thing as previously. With a little more info on broken packages. I have had the problem when trying to install a few other programs but never took the time to try and fix it.

```
 Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 mysql-client-5.5 : Depends: libdbi-perl but it is not installable
                    Depends: libdbd-mysql-perl (>= 1.2202) but it is not installable
                    Depends: libterm-readkey-perl but it is not installable
 mysql-server-5.5 : Depends: libdbi-perl but it is not installable
                    Depends: mysql-server-core-5.5 (= 5.5.34-0ubuntu0.13.04.1) but it is not going to be installed
                    Recommends: libhtml-template-perl but it is not installable
E: Unable to correct problems, you have held broken packages.
```

---

### Post by ian-weisser on 2013-11-21
What version of Ubuntu are you running?

Do you remember what you installed or did right before your package manager stopped working?

Have you installed a SQL client and/or server before?

Please post your etc/apt/sources.list file.

Please list the contents of your /etc/apt/sources.list.d directory.

---

### Post by linusti on 2013-11-22
It's not a Gnome issue...  It's busted in the main repository.  Seems someone fubared a dependency in the packaging in libdbi-perl.  Breaks all to H*LL things for anyone needing DB access with Perl- and I'm surprised that this slipped through the cracks like this.

To Canonical and the Ubuntu Team: If you've got the aspirations you do on this stuff, you can ILL AFFORD to have this kind of stuff going out on ANY of your releases- PERIOD.

It's nothing to do with the SQL server or anything like that.  Look CAREFULLY at what was highlighed in the fail from the unmet dependencies.  libdbi-perl refers to perlapi-5.14.2 which is a metapackage of perl-base- and perl-base is on version 5.18.

At least part of the screwups are being tracked with [https://bugs.launchpad.net/ubuntu/+s...l/+bug/1254144]("https://bugs.launchpad.net/ubuntu/+source/libdbi-perl/+bug/1254144")  You might want to go over to the bug to raise it's heat and get them to pay attention.

[Update]

You can't easily just simply downgrade Perl, either.  It pitches a fit:

```

fearl@fearl-Precision-M6600:~$ sudo apt-get install perl-base=5.14.2-21build1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cli-common : Depends: perl-modules but it is not going to be installed
 libwebkitgtk-1.0-0 : Depends: libenchant1c2a (>= 1.6.0) but it is not going to be installed
 update-notifier : Depends: update-manager-gnome but it is not installable or
                            update-manager (>= 1:0.165) but it is not going to be installed
                   Depends: ubuntu-release-upgrader-gtk but it is not going to be installed
 xemacs21 : Depends: xemacs21-mule (>= 21.4.22-4ubuntu1) but it is not going to be installed or
                     xemacs21-mule-canna-wnn (>= 21.4.22-4ubuntu1) but it is not going to be installed or
                     xemacs21-nomule (>= 21.4.22-4ubuntu1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
fearl@fearl-Precision-M6600:~$ 

```

Looking in the repos...someone did an update to the Perl ecosystem in the repos on November 2- but Ubuntu's web info on the packaging shows to be with 5.14.2...  Don't know where the disconnect was on this one, but I hope they get on it and sort it quickly.

[Update - 2]

Oh, this is ***_REALLY _***messed up.  Bigger problem.  They oopsed a lot more...  New combined bug:

[https://bugs.launchpad.net/ubuntu/+source/perl/+bug/1254180](https://bugs.launchpad.net/ubuntu/+source/perl/+bug/1254180)

For those finding this or any of the other Perl packaging related issues, please go over to the new bug and subscribe so it gets maximal visibility.

---

### Post by ian-weisser on 2013-11-22
linusti,

Thanks for doing so much research on this, and opening bug reports.
Looking through those bug reports, seems like a PPA was part of the issue.
Have you any insight on which elements were Ubuntu Repo problem, and which were PPA?

---

