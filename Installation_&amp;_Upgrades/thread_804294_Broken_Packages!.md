---
title: "Broken Packages!"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2008-05-23
I'm trying to install build-essential but get the following output:
```

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

```
So I try to install libc6-dev:
```

311$ sudo apt-get install libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-10ubuntu3 is to be installed
E: Broken packages

```
and libc-dev:
```

$ sudo apt-get install libc-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libc-dev is a virtual package provided by:
  libc6-dev 2.6.1-1ubuntu10
You should explicitly select one to install.
E: Package libc-dev has no installation candidate

```

All software sources are enabled in sources.list.

A while back I tried to install the 2.6.24-16 kernel.  I followed [this thread]("http://ubuntuforums.org/showthread.php?t=511974") and I didn't like it so I followed the directions to revert back to the 2.6.22-14 kernel.  I think that's where this all started.

Can you help me install build-essential?  Can you explain the difference between 2.6.1-1ubuntu10 and 2.7-10ubuntu3?

---

### Post by iaculallad on 2008-05-23
**sudo apt-get -f install**

then try reinstalling your build-essentials

---

### Post by MaindotC on 2008-05-23
Thanks for the reply.  I'm still getting the same set of errors.

---

### Post by iaculallad on 2008-05-23
> **strAlan said:**
> Thanks for the reply.  I'm still getting the same set of errors.

Try:

sudo apt-get remove build-essential
sudo apt-get install build-essential
sudo apt-get -f install

in that order.

---

### Post by MaindotC on 2008-05-23
It wasn't installed so it didn't work :(  Thanks for your suggestions and keep 'em coming.

---

### Post by iaculallad on 2008-05-23
If it's file dependency error, Try installing it using the Synaptics Package Manager. (type build-essential in the search-box)

System->Administration->Synaptics Package Manager. Hope that will work.

---

### Post by PmDematagoda on 2008-05-23
Please post the outputs of:-
```
cat /etc/apt/sources.list
```
and
```
cat /etc/lsb-release
```

---

### Post by MaindotC on 2008-05-23
Yep tried that too.  Here's the output - sorry I should have posted it before.

```

build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed

```
And of course I know I can't install libc-dev so I tried g++:
```

g++:
 Depends: g++-4.1 but it is not going to be installed

```
Tried g++-4.1:
```

g++-4.1:
 Depends: libstdc++6-4.1-dev but it is not going to be installed

```
Tried libstdc++6-4.1-dev:
```

libstdc++6-4.1-dev:
 Depends: g++-4.1 but it is not going to be installed
 Depends: libc6-dev but it is not going to be installed

```

Which loops me back around to the beginning :)

---

### Post by MaindotC on 2008-05-23
Sources.list:
```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy universe multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy restricted

```
Sorry I know I have some duplicate sources in there - just haven't gotten around to fixing them.  And the release:
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

```

---

### Post by iaculallad on 2008-05-23
Open your System->Administration->Software Sources, on  the "Ubuntu Software" tab, check the Main, Universe, Restricted, and Multiverse. Be sure that the "Installable from CD-ROM/DVD" is uncheck. Close the window and try re-installing the build-essential.

---

### Post by MaindotC on 2008-05-23
I've already had the cd-rom removed as you can see the sources.list :(

---

### Post by PmDematagoda on 2008-05-23
Your sources file looks fine, did you try doing a:-
```
sudo apt-get update
```
and then trying again?

---

### Post by MaindotC on 2008-05-23
Yeah I've done an update and an upgrade - several times and after any changes I've tried - nothing really coming from that :(

---

### Post by iaculallad on 2008-05-23
Try this:
[B]
sudo apt-get install g++-3.3[/B]

if it will make a difference.

---

### Post by PmDematagoda on 2008-05-23
> **strAlan said:**
> Yeah I've done an update and an upgrade - several times and after any changes I've tried - nothing really coming from that :(

Hmm, as a long shot, try going to [Ubuntu Packages]("http://packages.ubuntu.com/") to manually download and install the dependencies.

---

### Post by MaindotC on 2008-05-23
```

The following packages have unmet dependencies:
  g++-3.3: Depends: libstdc++5-3.3-dev (= 1:3.3.6-15ubuntu2) but it is not going to be installed
E: Broken packages

```

I did the same procedure for apt-get install and via Synaptic. It eventually leads me back to libc6-dev :(

---

### Post by MaindotC on 2008-05-23
> **PmDematagoda said:**
> Hmm, as a long shot, try going to [Ubuntu Packages]("http://packages.ubuntu.com/") to manually download and install the dependencies.

I tried this as well.  The package manager gives the same error messages as if I were installing them via Synaptic or apt-get install.

---

### Post by PmDematagoda on 2008-05-23
> **strAlan said:**
> I tried this as well.  The package manager gives the same error messages as if I were installing them via Synaptic or apt-get install.

Disable all the repos, update the sources and once that is done re-enable all the repos again and update the sources once again. See if that solves your problem.

---

### Post by iaculallad on 2008-05-23
You could give this command a try:


**sudo apt-get install g++-3.3**

---

### Post by MaindotC on 2008-05-23
> **PmDematagoda said:**
> Disable all the repos, update the sources and once that is done re-enable all the repos again and update the sources once again. See if that solves your problem.

You do realize that when I disable all the repos, there are no updates to be applied to the pacakges, correct?  I did as you suggested via Synaptic and via sources.list, plugging in reloads and apt-get update after each change.  Still getting the same errors :(

---

### Post by MaindotC on 2008-05-23
> **iaculallad said:**
> You could give this command a try:


**sudo apt-get install g++-3.3**

You already suggested this.  Thanks for your continued suggestions.

---

### Post by PmDematagoda on 2008-05-23
> **strAlan said:**
> You do realize that when I disable all the repos, there are no updates to be applied to the pacakges, correct?  I did as you suggested via Synaptic and via sources.list, plugging in reloads and apt-get update after each change.  Still getting the same errors :(

I was hoping for a complete repository refresh, but it seems to not have worked. Well, as a last ditch attempt(that's all I can think of), try changing the location of the servers and see if that would do any good.

---

### Post by MaindotC on 2008-05-23
I tried different servers in a previous attempt.  I'm sorry for all these needless posts but I didn't document the troubleshooting that I already did.  Dematagoda thank you for your help and if you can't help me anymore I hope you can talk to one of your gosu mods and help me out.  You get a star for effort.

---

### Post by MaindotC on 2008-05-23
It seems to me that 2.7-10ubuntu3 refers to Hardy packages, and 2.6.1-1ubuntu10 refers to Gutsy packages.  Per the first post I made, when it says:
```

libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-10ubuntu3 is to be installed

```
that translates to "you need the package for Gutsy but for some reason the package that apt is going to install will be for Hardy so f that".  Do you agree with me?

---

### Post by PmDematagoda on 2008-05-23
> **strAlan said:**
> It seems to me that 2.7-10ubuntu3 refers to Hardy packages, and 2.6.1-1ubuntu10 refers to Gutsy packages.  Per the first post I made, when it says:
```

libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-10ubuntu3 is to be installed

```
that translates to "you need the package for Gutsy but for some reason the package that apt is going to install will be for Hardy so f that".  Do you agree with me?

That seems to be the case. Try downloading the libc6 package from Ubuntu Packages and this time, install it using dpkg with:-
```
sudo dpkg -i name-of-file.deb
```
dpkg is more forceful and will install the package regardless of dependency problems, this can be bad as well so do it with caution. Once the package is installed try doing:-
```
sudo apt-get install -f
```

---

### Post by MaindotC on 2008-05-23
I tried using "aptitude" instead of apt - didn't even know these were different.  Here's the output:
```

$ sudo aptitude install libc6-dev
[sudo] password for a34lkj2348dsf311:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libc6-dev 
The following NEW packages will be automatically installed:
  linux-libc-dev 
The following NEW packages will be installed:
  linux-libc-dev 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 3940kB of archives. After unpacking 17.3MB will be used.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-10ubuntu3 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libc6 [2.7-10ubuntu3 (now) -> 2.6.1-1ubuntu10 (gutsy-updates)]
libc6-i686 [2.7-10ubuntu3 (now) -> 2.6.1-1ubuntu10 (gutsy-updates)]
module-init-tools [3.3-pre11-4ubuntu5 (now) -> 3.3-pre4-2ubuntu4 (gutsy)]

Score is 146

Accept this solution? [Y/n/q/?]
```

Holding my breath, I accepted "yes" and the following output ensued:
```

The following NEW packages will be automatically installed:
  linux-libc-dev 
The following packages will be DOWNGRADED:
  libc6 libc6-i686 module-init-tools 
The following NEW packages will be installed:
  libc6-dev linux-libc-dev 
0 packages upgraded, 2 newly installed, 3 downgraded, 0 to remove and 0 not upgraded.
Need to get 9359kB of archives. After unpacking 16.8MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://security.ubuntu.com gutsy-security/main linux-libc-dev 2.6.22-14.52 [653kB]
Get:2 http://archive.ubuntu.com gutsy/main module-init-tools 3.3-pre4-2ubuntu4 [87.4kB]
Get:3 http://archive.ubuntu.com gutsy-updates/main libc6 2.6.1-1ubuntu10 [4184kB]
Get:4 http://archive.ubuntu.com gutsy-updates/main libc6-i686 2.6.1-1ubuntu10 [1148kB]
Get:5 http://archive.ubuntu.com gutsy-updates/main libc6-dev 2.6.1-1ubuntu10 [3287kB]
Fetched 9359kB in 3s (2749kB/s)     
dpkg - warning: downgrading module-init-tools from 3.3-pre11-4ubuntu5 to 3.3-pre4-2ubuntu4.
(Reading database ... 112252 files and directories currently installed.)
Preparing to replace module-init-tools 3.3-pre11-4ubuntu5 (using .../module-init-tools_3.3-pre4-2ubuntu4_i386.deb) ...
Unpacking replacement module-init-tools ...
dpkg: warning - unable to delete old directory `/etc/depmod.d': Directory not empty
dpkg - warning: downgrading libc6 from 2.7-10ubuntu3 to 2.6.1-1ubuntu10.
Preparing to replace libc6 2.7-10ubuntu3 (using .../libc6_2.6.1-1ubuntu10_i386.deb) ...
Unpacking replacement libc6 ...
Setting up libc6 (2.6.1-1ubuntu10) ...
Installing new version of config file /etc/init.d/glibc.sh ...
Installing new version of config file /etc/gai.conf ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg - warning: downgrading libc6-i686 from 2.7-10ubuntu3 to 2.6.1-1ubuntu10.
(Reading database ... 112286 files and directories currently installed.)
Preparing to replace libc6-i686 2.7-10ubuntu3 (using .../libc6-i686_2.6.1-1ubuntu10_i386.deb) ...
Unpacking replacement libc6-i686 ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.22-14.52_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.6.1-1ubuntu10_i386.deb) ...
Setting up module-init-tools (3.3-pre4-2ubuntu4) ...
Installing new version of config file /etc/modprobe.d/arch/i386 ...
Installing new version of config file /etc/modprobe.d/blacklist ...

Setting up libc6-i686 (2.6.1-1ubuntu10) ...

Setting up linux-libc-dev (2.6.22-14.52) ...
Setting up libc6-dev (2.6.1-1ubuntu10) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done 

```
Then I ran apt-get install build-essential and it worked.  So apparently aptitude was a little better at resolving the issue than apt, eh?  I'm going to have to research this "aptitude" business.  I knew there was something up with the different types of ubuntu names in the packages - it was all b/c of that blasted kernel upgrade I did.  The packages had to be DOWNGRADED.  Thanks for all of your suggestions.

---

### Post by PmDematagoda on 2008-05-23
Glad it worked out, it may be that you installed the libc6 package for Hardy by accident, in any case the repositories were not at fault at all.

---

### Post by MaindotC on 2008-05-23
Btw, this was all so I could install the latest version of wine via source.

---

### Post by PmDematagoda on 2008-05-23
> **strAlan said:**
> Btw, this was all so I could install the latest version of wine via source.

Why are you building it via source? Just download the latest deb package for Ubuntu or add the Wine repository, that would have simplified things so much.

But anyway it was good that you solved the problem now instead of later.

---

### Post by MaindotC on 2008-05-23
I don't like using package managers as you can tell by the 29 posts above you :)

Actually - that's not true - I like using apt.  The reason is that the version in the repos was .9.59 or something like that and I didn't research the means for downloading the latest deb or whatever.  What concerns me is that I always have difficulty running programs in wine, and I've always been advised that one of the reasons for installing via source instead of a package manager is that the source installation provides a better configuration to interact with the system.  I'm not 100% sure how to prove that, but it's just something I'm trying.  So many of my friends can play Broodwar on their Ubuntu T60's and I've always been left out, so I've been eagerly awaiting the latest version of wine.

Maybe this time it'll work, maybe it won't.  I've also googled several threads regarding wine + starcraft.

---

### Post by PmDematagoda on 2008-05-23
> **strAlan said:**
> I don't like using package managers as you can tell by the 29 posts above you :)

Good luck with the compiling then, you may need it;).

---

### Post by MaindotC on 2008-05-23
> **PmDematagoda said:**
> Good luck with the compiling then, you may need it;).

Just out of curiosity - if I were so inclined to use the debian package - is it a problem to follow these directions even though I'm using Gutsy:

From winehq.org:
```

First, open a terminal window (Applications->Accessories->Terminal). Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list

```

Thanks!

---

### Post by PmDematagoda on 2008-05-23
By doing that you are adding a Hardy repository, now if the dependencies of Wine have Hardy ones, then you may face some dependency errors similar to what you faced previously(heavy emphasis on **may**, I haven't used Wine in quite a while and I can't really remember it's dependencies).

---

### Post by MaindotC on 2008-05-23
I followed those instructions but replaced "hardy" with "gutsy".  It still shows that if I installed, it woule be 0.9.46 boooo!  I'm going to continue with the source installation.

---

