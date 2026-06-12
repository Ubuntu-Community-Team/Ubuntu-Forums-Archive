---
title: "Downgrading a package?"
date: 2014-05-12
forum: Installation &amp; Upgrades
---

### Post by cogset on 2014-05-12
I've tried to downgrade a package (using first the -s option,just to be sure I wasn't going to break anything) with ```
apt-get install <package-name>=<package-version-number>
```and I was surprised to see that it doesn't actually  work the way I was expecting.
If I pick for instance gedit, I can see just two version numbers available with apt-cache show,which are 2.30.3-0ubuntu0.1 and 2.30.0git20100413-0ubuntu1 : with the command listed above,I can indeed simulate installing the oldest available version of the two,which is 2.30.0git20100413-0ubuntu but then  any other version that I can see in the changelogs isn't available,trying to install 2.30.0-0ubuntu1 results in this error
 ```
E: Version '2.30.0-0ubuntu1' for 'gedit' was not found
```
As far as I can tell,this applies to every package I've tried so far:the available versions seem to be the current installed and the oldest one for a given release,all other intermediate versions that I can see with **aptitude changelog** are not available.

Looking at it,there's no way I can eventually roll back to just the previous version of a package,because it won't be available-is this the normal situation,and if so,which options do I have to downgrade a package if I wish so?

---

### Post by vasa1 on 2014-05-12
> **cogset said:**
> ...
If I pick for instance gedit, I can see just two version numbers available with apt-cache show,which are 2.30.3-0ubuntu0.1 and 2.30.0git20100413-0ubuntu1 : with the command listed above,I can indeed simulate installing the oldest available version of the two,which is 2.30.0git20100413-0ubuntu but then  any other version that I can see in the changelogs isn't available,trying to install 2.30.0-0ubuntu1 results in this error
 ```
E: Version '2.30.0-0ubuntu1' for 'gedit' was not found
```...
Can you please explain?
To my mind, it is more like *apt-cache policy* rather than *apt-cache show* and when I run *apt-cache policy gedit*, I get
```
[01:28 PM] ~ $ apt-cache policy gedit
gedit:
  Installed: (none)
  Candidate: 3.10.4-0ubuntu4
  Version table:
     3.10.4-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
[01:29 PM] ~ $ 

```This is with Ubuntu 14.04. What version of Ubuntu are you using?

---

### Post by cogset on 2014-05-12
I'll try to explain:as a proof of concept,in case I may want to downgrade a package,I've picked some random packages (the example was from Lucid using gedit,but I've also tried in Quantal using firefox and other packages),first checked the installed version with **apt-cache policy**,then the available versions with **apt-cache show**,then the changelogs with **aptitude changelog**:what I've seen is that I don't really have the option to downgrade/roll back to a previous version of choice using ```
apt-get install <package-name>=<package-version-number>
```,because for any given package there are only two versions available,the current and what appears to be the oldest one.
When trying to downgrade to any other version listed in the changelogs using the command above,it fails with 
```
E: Version 'xxxxx' for 'package' was not found
```
What I've seen is that actually on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) there are indeed no older packages,they are in [http://archive.ubuntu.com](http://archive.ubuntu.com) :so maybe the only way to downgrade a package if one really wishes so,is to download the .deb package from there and manually install it?

---

### Post by vasa1 on 2014-05-12
I've never tried to downgrade but wouldn't you (or APT) need to have access to the repository for the older software? So if you're on 14.04 and you want something from 10.04, won't you need to somehow add that to sources.list (or wherever)?

---

### Post by slickymaster on 2014-05-12
The process of reverting to a previous version of a package on Ubuntu is normally:```
sudo apt-get remove package_name
gksudo gedit /etc/apt/sources.list -> comment out the ppa providing the new package
sudo apt-get update
sudo apt-get install package_name
```
Or using Synaptic
[LIST=1]
[*]start Synaptic Package Manager
[*]search for your package, click on it and select mark for removal
[*]click apply
[*]go to Settings > Repositories > Third Party Software and uncheck the PPA providing the new packge
[*]Click Close, and then Reload
[*]search for the package and reinstall it.
[/LIST]
Optionally, you can re-enable the PPA after reverting to the Ubuntu default package

---

### Post by cogset on 2014-05-12
OK,let me try again:this has nothing to do with PPAs as far as I'm concerned,neither with installing packages from a previous release,in which case I can see how editing sources.list would be necessary.
The assumption is something like that:
[LIST]
[*]I'm using Firefox 28 in Quantal 
[*]an update to Firefox 29 is installed 
[*]I don't like Firefox 29,or something doesn't work,I decide to roll back to Firefox 28 
[*]Firefox 28 is not available at this point:I can only install,and I know because I've simulated this with ```
apt-get -s install Firefox=<firefox version>
```version 11,which is exactly the only other version,aside of the current one,I can see with **apt-cache show firefox** 
[*]Firefox 28,or any other intermediate version,can't be installed with the command ```
apt-get -s install Firefox=<firefox version>
``` because it throws an error saying "package not found" 
[*]Upon checking,Firefox 28 and previous versions are indeed not available in [http://packages.ubuntu.com](http://packages.ubuntu.com) but they are in [http://archive.ubuntu.com](http://archive.ubuntu.com) ,so I maybe should add this line to my sources to eventually perform a downgrade? 
[/LIST]

---

### Post by vasa1 on 2014-05-12
> **cogset said:**
> ... so I maybe should add this line to my sources to eventually perform a downgrade? ...
That's my guess.

With specific reference to Firefox 29, I don't have too many extensions and so installing [CTR]("http://forums.mozillazine.org/viewtopic.php?f=48&t=2827985") helped me get back what I wanted.

Also see [http://ubuntuforums.org/showthread.php?t=1036360](http://ubuntuforums.org/showthread.php?t=1036360) which suggests you can pick up a .deb from 
[http://archive.ubuntu.com/ubuntu/pool/main/](http://archive.ubuntu.com/ubuntu/pool/main/). You may need to uninstall the existing version before installing the .deb. That would avoid modifying your sources file. Again, just a guess.

---

### Post by cogset on 2014-05-13
Thinking of it,you can't really add [http://archive.ubuntu.com/](http://archive.ubuntu.com/) nor [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to your sources,as the first one you have already and the second isn't a proper source-so it seems that in my case the possibility to downgrade a package using apt is just theoretical,the only way to actually accomplish this would be to manually download and install the .deb package of choice from [http://archive.ubuntu.com/ubuntu/pool/main/](http://archive.ubuntu.com/ubuntu/pool/main/) as we've concluded.
That is,unless some apt guru doesn't chime in and say otherwise.

---

### Post by Dennis N on 2014-05-13
Regarding Firefox versions, you can install another version of Firefox without removing Firefox 29. You would download the .tar.bz archive file from Mozilla for the version you want, create a different profile for it (important), and make a separate launcher. You can then run either one.

---

### Post by cogset on 2014-05-13
Yes,I've done that several times:it was really a question about apt,I've used Firefox just as an example.

---

### Post by bapoumba on 2014-05-13
I may be wrong here, but that is how I see it.

A distribution, ie trusty for ex, is a set of packages where all dependencies are satisfied. Some packages are tied up together with metapackages (packages with no code in them, but with a dependency list) or with dependencies, recommends and conflicts.
Repositories where the package manager knows where to get the packages are maintained by people who do some housekeeping.

Say you want package A version n-10 below the distribution version, I'm not sure it will be possible with any package manager, or that would be some kind of luck.

Say package A n-10 requires package B n-5 wich in turn depends on package C n-10, but package C-10 conflicts with package C n you currently have installed. This happens a lot with libraries. How would the package manager resolve that ? This is its role, ensure all installed packages have homogeneous versions.

Conflicts are used to prevent installing conflicting packages that would break things if installed together. Of course, a user can always manually override the package manager and install other package versions anyway, but not without consequences. You can browse this sub-forum and look at threads where people get stuck installing different packages versions from their own distribution. It usually happens using ppas where devs label version number higher than distribution numbers so that the package manager can update/upgrade. Thinking of it, there is no "downgrade" option to apt-get :)
[quote=man apt-get]Both of the version selection mechanisms can downgrade packages and must be used with care.
[/quote]
[http://debian-handbook.info/browse/stable/sect.package-meta-information.html](http://debian-handbook.info/browse/stable/sect.package-meta-information.html)

You cannot just mix up different releases in the source.list or you'll be soon into trouble. If not, then that would again be out of luck imho.

All in all, you could use the pin version option to keep an installed package at its current version and prevent any upgrade process. Or work with the /etc/apt/preferences.d files, both have their limits and risks.
[http://debian-handbook.info/browse/stable/sect.apt-get.html#sect.apt.priorities](http://debian-handbook.info/browse/stable/sect.apt-get.html#sect.apt.priorities)
[http://manpages.ubuntu.com/manpages/lucid/fr/man5/apt_preferences.5.html](http://manpages.ubuntu.com/manpages/lucid/fr/man5/apt_preferences.5.html)

---

### Post by cogset on 2014-05-28
I'm not sure I've fully understood your explanation,I do reckon that attempting to mix different sources or adding PPAs can/will eventually lead to troubles, my original question however was about the theoretical possibility of rolling back just to the previous version of a given package,using apt-get with the command ```
install <package-name>=<package-version-number>
```which as you point out should be used with care,but nonetheless should work in principle.
In reality,it doesn't:I've tried some random packages with the --simulate option  and some can  apparently be downgraded to some specific version numbers but not to other versions (E: Version 'xxx' for 'package' was not found),some can't be downgraded at all.
Maybe it has do do with dependencies,maybe for security reasons packages such as web browsers can't be downgraded.

Pinning of course will work,but you have to do this before upgrading the system-unfortunately you won't know if a program won't work as you expect until you've actually upgraded it,and at that stage you can't actually undo the last update,which is what I was theoretically after.

---

### Post by bapoumba on 2014-05-28
> **cogset said:**
> I'm not sure I've fully understood your explanation,
Reading over, I may have not been very clear either :)
> **cogset said:**
> 
I do reckon that attempting to mix different sources or adding PPAs can/will eventually lead to troubles, my original question however was about the theoretical possibility of rolling back just to the previous version of a given package,using apt-get with the command ```
install <package-name>=<package-version-number>
```which as you point out should be used with care,but nonetheless should work in principle.
In principle. When I mentioned "housekeeping", that was regarding the maintaining of the repos, where, for a given release, not all packages versions are kept. From memory, previous versions are removed after 24h (or the repos would grow out gigantic when you think of all the updates coming in, mostly from resolved bugs or new application packages).

If we get back to your Firefox example, Utopic, Trusty and Saucy have the latest FF 29 and Raring has FF 26. I have not checked, but I guess this situation is a combination of 2 things : 1- dependencies and 2- what the Mozzila Foundation offers, in particular regarding security updates. If they do maintain 26 and 29 for security (this is the point I have not checked) then Ubuntu will only offer these versions and no intermediates that would not get the security patches.
> **cogset said:**
> 
In reality,it doesn't:I've tried some random packages with the --simulate option  and some can  apparently be downgraded to some specific version numbers but not to other versions (E: Version 'xxx' for 'package' was not found),some can't be downgraded at all.
Maybe it has do do with dependencies,maybe for security reasons packages such as web browsers can't be downgraded.

Pinning of course will work,but you have to do this before upgrading the system-unfortunately you won't know if a program won't work as you expect until you've actually upgraded it,and at that stage you can't actually undo the last update,which is what I was theoretically after.
Yes, pinning needs to be decided before upgrading. All in all, I think packages managers are not the tools you'd be looking for, and compiling a specific package from sources (provided you can find them) is the only way to achieve what you are exactly looking for.

---

### Post by ian-weisser on 2014-05-28
Older versions are not kept in the Ubuntu repositories. So downgrading by apt is not supported...and the system will promptly try to upgrade to the newest version again.

Generally, you must downgrade by finding the desired version of the package on your own, and then downgrading using dpkg instead of apt.

The dpkg manpage is very clear that downgrading does not include dependency checking, and is at-your-own-risk.

---

