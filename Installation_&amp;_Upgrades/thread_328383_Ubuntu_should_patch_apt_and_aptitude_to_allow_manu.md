---
title: "Ubuntu should patch apt and aptitude to allow manual ignoring of dependencies"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by gabba on 2006-12-30
I'm using Ubuntu Dapper (which I will stick with, for many reasons, until the next LTS release), and I recently realized that apt-get and aptitude leave you *absolutely no freedom* with managing some packages manually. I downloaded Battle for Wesnoth .deb's from the Debian testing ftp, and forced their install with dpkg. It gave me many warnings about dependencies, but the SDL versions were very close, and as I expected the game works like a charm.

The problem is that now, the update-manager, synaptic and apt-get and aptitude all complain that my system is broken, AND refuse to install or upgrade anything else because of this. I don't want to recompile these packages from source (waste of time and bandwidth), nor do I want to wait on someone to backport them to Dapper. After all, now it just works.

_I thought GNU/Linux was all about freedom?_ And what about the "just works" philosophy of Ubuntu? And here am I stuck with a restriction that even Microsoft has never imagined. I searched a lot on the internet and there is no alternative but to sacrifice to the whims of apt-get! Because of one single package that has zero chance of causing a conflict! If I want to manually manage a part of my softwares it's my business, I do it a lot on windows and I remember perfectly where all my stuff is.

So, conclusion, for apt-get to become a useful tool in the ubuntu spirit, **it should be patched by the Ubuntu team to accept a config file which tells it to ignore certain packages for dependency purposes**. The file could have several other options, such as assuming a package is always present for dependency checking, even though it was never installed through apt-get. This way you can clearly outline what you manage manually, and still take advantage of the power of apt-get to install stuff and update the rest of your system. Plus, manually installed software will still be easier to uninstall than if you do it with *make install* or unpacking tarballs.

Please, exclude any zealotry from this thread. This modification would be made with _advanced users_ in mind, who know what they are doing and are already careful with their systems.

---

### Post by az on 2006-12-30
> **gabba said:**
> 
_I thought GNU/Linux was all about freedom?_  ...

Please, exclude any zealotry from this thread. This modification would be made with _advanced users_ in mind, who know what they are doing and are already careful with their systems.

The package manager is the package manager.  It can only do so much.  The software is meant to work together at the source level.  The distro you pick does your the service of providing binaries.  the software is not binary compatible for  alot of reasons.  That being said, the package management system does have shortcomings and they are being addressed.  It will take some time, though.  For the moment, to be fair, it does do what it's supposed to do....

You are completely free to compile from source.  Nobody will ever take away your right to do that (notwithstanding software patents)

As for circumventing the dependencies, there are two things you should know:

1-  Using a packages compiled with a higher version of libc6 than you are running *will* eventually crash.  Circumventing that dependency would be suicide.

Other than that:

2- 

emma@ubuntu:~$ apt-cache show equivs
Package: equivs
Priority: extra
Section: universe/admin
Installed-Size: 132
Maintainer: Fabio Rafael da Rosa <f2r@users.sourceforge.net>
Architecture: all
Version: 2.0.6-0.1
Depends: perl | perl5, debhelper, dpkg-dev, devscripts, make, fakeroot
Filename: pool/universe/e/equivs/equivs_2.0.6-0.1_all.deb
Size: 18050
MD5sum: 86579c8b444254595062aeb90c631c98
Description: Circumvent Debian package dependencies
 This package provides a tool to create Debian
 packages that only contain dependency information.
 .
 If a package P is not installed on the system, packages
 that depend on P cannot normally be installed.  However,
 if equivalent functionality to P is known to be installed,
 this tool can be used to trick the Debian package management
 system into believing that package P is actually installed.
 .
 Another possibility is creation of a meta package. When this
 package contains a dependency as "Depends: a, b, c", then
 installing this package will also select packages a, b and c.
 Instead of "Depends", you can also use "Recommends:" or
 "Suggests:" for less demanding dependency.
 .
 Please note that this is a crude hack and if thoughtlessly used,
 it might possibly do damage to your packaging system. And please
 note as well that using it is not the recommended way of dealing
 with broken dependencies. Better file a bug report instead.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by gabba on 2006-12-31
> **azz said:**
> The package manager is the package manager.  It can only do so much.  ...  

Thanks for your reply. I understand that the package manager is good at managing the dependency system, and that **apt-get** was already a revolution in package managing when it came out.

But right now it is also our main tool to install programs on Ubuntu, and most of us users only install software that way. I'm just advocating extending a bit the functionality to give the user more freedom.

I read about **equivs**, and frankly it doesn't appear to me like a solution (even though it does one of the things I was suggesting). First, it's kind of annoying to have to create a fake package for every single unmet dependency. Which means in this case all the SDL dependencies of Battle for Wesnoth, about 8. Plus, I don't want my whole dependency system to believe it has those (fake) packages, because sooner or later it's gonna make upgrades complicated, or some other (important this time) programs will install without a warning, I'll have to remember what fakes I created when, and delete some of them, and so on.

The only thing I want is to be able to tell apt-get: look, this package (game) is not essential for my system, I don't care if it's broken, and/or I don't want to install 50 libraries just because it thinks it needs them, so please ignore any dependencies it asks for (or some of them). Just for this package. And right now as far as I know, it's impossible.

This makes me think as well about a book that should be written: "How to avoid installing Mozilla as a dependency of something, for Dummies". You know, you just need to install some small useful package for a quick job, just to find out that the packager in his wisdom has decided that you need to download a 30 MBs monster just to get going. A quick way to tell apt-get: "I don't care about this dependency for now, keep reminding me about it without pretending the whole thing is broken" would just be amazing. Sometimes it's better to leave some program in a bad state, and finish your job, than to be forced to fix everything right away. Not all of us are running a mission-critical server with Ubuntu.

In an ideal world every package would be perfect, and we'd find and download instantly what we need, but the truth is, sometimes you are in a hurry or you don't want to spend hours doing some dark sacrifice to apt-get just so it will let you play a game. Yes, I agree that we should do bug reports whenever we are able to.

Lastly, thanks for the reminder about the version of libc6, I'll check. But as I told you, the game was working fine, and even if it crashes it's not a disaster. I might finally get to compile it from source -  but even then I'll use checkinstall to install it as a .deb, for easy uninstall, so we're back to the same package manager discussion.

---

### Post by az on 2006-12-31
> **gabba said:**
>  I might finally get to compile it from source -  but even then I'll use checkinstall to install it as a .deb, for easy uninstall, so we're back to the same package manager discussion.

No, if you compile it yourself, the libc6 problem goes away.  If you don't have the dependent libraries, it won't run.  So the package manager discussion does go away.

---

### Post by gabba on 2007-01-07
Well, some other opinions on this? Even though my problem with this particular package is solved, I still consider this a worthy feature request.

---

