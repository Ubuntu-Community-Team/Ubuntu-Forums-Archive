---
title: "new packagekit!!!"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-03-31
i want to share with you new version of packagekit: simple, powerful and fast.

* New Features:
 - Switch gnome-packagekit to the GNOME release guidelines and version numbers 
 - Provide tooltips for the icons in the new update viewer 
 - Add a new menu item 'Select security updates' to the new update viewer. 
 - Hide the update icon notification when the update viewer is opened 
 - Switch the default update viewer to gpk-update-viewer2

---

### Post by ghindo on 2009-03-31
This isn't from the repos, is it?

---

### Post by taavikko on 2009-03-31
> **ghindo said:**
> This isn't from the repos, is it?

It is available, if you want to install it.

```
aptitude show packagekit-gnome
Package: packagekit-gnome
New: yes
State: not installed
Version: 0.3.13-0ubuntu1
Priority: extra
Section: universe/gnome
Maintainer: Sebastian Heinlein <glatzor@ubuntu.com>
Uncompressed Size: 11.2M
Depends:
<snip>
</snip>
Description: graphical distribution neutral software management tools
 PackageKit allows to perform simple software management tasks over a DBus interface  e.g. refreshing the cache,
 updating, installing and removing software packages or searching for multimedia codecs and file handlers.

 This package contains a set of GTK based applications for PackageKit:
 * Status icon for PackageKit transactions (gpk-update-icon)
 * System update tool (gpk-update-viewer)
 * Software installation and removal tool (gpk-applications)
 * Repository editor (gpk-repo)
 * Several small helpers and prototype implementations
Homepage: [http://www.packagekit.org](http://www.packagekit.org)
```

---

### Post by gnomeuser on 2009-03-31
> **ghindo said:**
> This isn't from the repos, is it?

No, unfortunately. Also it doesn't seem that Ubuntu really cares about PackageKit which is a damn shame.

---

### Post by ghindo on 2009-03-31
> **taavikko said:**
> It is available, if you want to install it.I've installed it (even the PPA version!) but it doesn't look a think like the OP's picture.

---

### Post by taavikko on 2009-03-31
> **gnomeuser said:**
> No, unfortunately. Also it doesn't seem that Ubuntu really cares about PackageKit which is a damn shame.

> **ghindo said:**
> This isn't from the repos, is it?

It is available through apt/dpkg in universe repos

```
devil@elite:~$ apt-cache policy packagekit-gnome
packagekit-gnome:
  Installed: (none)
  Candidate: 0.3.13-0ubuntu1
  Version table:
     0.3.13-0ubuntu1 0
        500 http://archive.ubuntu.com jaunty/universe Packages

```

---

### Post by gnomeuser on 2009-03-31
> **taavikko said:**
> It is available, if you want to install it.

```
aptitude show packagekit-gnome
Package: packagekit-gnome
New: yes
State: not installed
Version: 0.3.13-0ubuntu1
Priority: extra
Section: universe/gnome
Maintainer: Sebastian Heinlein <glatzor@ubuntu.com>
Uncompressed Size: 11.2M
Depends:
<snip>
</snip>
Description: graphical distribution neutral software management tools
 PackageKit allows to perform simple software management tasks over a DBus interface  e.g. refreshing the cache,
 updating, installing and removing software packages or searching for multimedia codecs and file handlers.

 This package contains a set of GTK based applications for PackageKit:
 * Status icon for PackageKit transactions (gpk-update-icon)
 * System update tool (gpk-update-viewer)
 * Software installation and removal tool (gpk-applications)
 * Repository editor (gpk-repo)
 * Several small helpers and prototype implementations
Homepage: [http://www.packagekit.org](http://www.packagekit.org)
```

The rest of the world is on PackageKit 0.4.6. As this posting was about the new PackageKit, no it is not in the repos. Aside that the Debian/Ubuntu guys have all but forked PackageKit into something apt specific called aptdeamon.. totally defeating the purpose of PackageKit.

---

### Post by taavikko on 2009-03-31
> **gnomeuser said:**
> The rest of the world is on PackageKit 0.4.6. As this posting was about the new PackageKit, no it is not in the repos. Aside that the Debian/Ubuntu guys have all but forked PackageKit into something apt specific called aptdeamon.. totally defeating the purpose of PackageKit.

Whups, so it was, version or two left behind.. My bad!

Just getting to know pkg-kit as in KDE enviroment

Although I prefer the CLI for installing and updating.

---

### Post by philinux on 2009-03-31
According to synaptic. version 0.3.13
PackageKit allows to perform simple software management tasks over a DBus
interface e.g. refreshing the cache, updating, installing and removing
software packages or searching for multimedia codecs and file handlers.

The work is done by backends which make use of the package manager shipped by
the corresponding distribution. [B]PackageKit is not meant to replace
advanced tools like Synaptic.[/B]

So whats it for then? I use apt-get and synaptic.

---

### Post by hanzomon4 on 2009-03-31
This pk thing is confusing me

---

### Post by biasquez on 2009-03-31
this version is compiled from git (0.4.7 called now 2.27.x).
is it very stable and bug fixed instead of packagekit 0.3.x

---

### Post by gnomeuser on 2009-03-31
How so? It seems easy enough to me.

If you the application developer want to say add some functionality that is installed on demand, say you are developing an instant messaging client. You may not want every protocol installed by default, instead you could use PackageKit' API to probe for the installed packages and if they are not present search for them and install them based on demand. This lowers the foot print of your install as a user. It also gives you a consistent experience across distributions as the same widgets are being used.

Another place where PackageKit benefits the user is the use of PolicyKit, it allows you to setup policy for what users can do without authentication, what they need to type in their password for and what you need additional permissions for. This is useful for having good defaults for single users machines e.g. where you might want the user to be allowed to install packages which are signed with a gpg key on the trusted list and update the packages, but not remove any packages e.g.

You get consistent experiences as a user regardless of which Linux distro you sit down in front, as a developer you now for the first time get to hook into the package manager without being tied to one specific distribution or packaging system. Given that there is one set of tools for every packaging system you should also get fewer bugs as there is only a limited set of code paths to test, your translations should be stronger as it is one set of strings instead of one for every distro. 

Another thing one could use PackageKit for would be to have a bit of JavaScript that calls PK over dbus. This could be used on review websites to have a little button that could tell the user that the application is available for installation. Bring a one click install experience to situations where one might want to try out a piece of software.

Finally as a distribution, if you start converting your installers and tools over to using PK calls instead of direct calls to your packaging system, should you ever need to replace the underlying packaging system the transition would be much smoother as the new backend would just need a PK backend.

PackageKit is a damn good thing, it's not perfect but it lets us do a bunch of interesting bits of integration that will work regardless of which distro you are on. It also does not replace what you have currently it compliments it.

---

### Post by biasquez on 2009-03-31
hi, i'm not developer but only an user that he's testing new packagekit.
packagekit use PolicyKit by default and it's compatible with gstreamer and firefox like application.

---

### Post by BGFG on 2009-03-31
> **gnomeuser said:**
> The rest of the world is on PackageKit 0.4.6. As this posting was about the new PackageKit, no it is not in the repos. Aside that the Debian/Ubuntu guys have all but forked PackageKit into something apt specific called aptdeamon.. totally defeating the purpose of PackageKit.

Could you give a little more detail on aptdaemon ?

---

### Post by biasquez on 2009-03-31
> **BGFG said:**
> Could you give a little more detail on aptdaemon ?

what do you want to know about it?

---

### Post by ghindo on 2009-03-31
How do I compile the newest PackageKit from git?  I've never used git before :(

---

### Post by BGFG on 2009-03-31
> **biasquez said:**
> what do you want to know about it?

The changes that they made to packagekit as it would relate to aptdaemon. Are they radical ? deleterious to packagekit ?

---

### Post by Simian Man on 2009-03-31
I love PackageKit on Fedora, it totally blows away Synaptic and other similar applications.  Having Totem prompt me when I am missing plugins and have PackageKit automatically install the correct ones is a beautiful thing.

---

### Post by Kow on 2009-03-31
Yea I don't know what Ubuntu and Debian's issues are with regard to PackageKit:

[http://brainstorm.ubuntu.com/idea/64/](http://brainstorm.ubuntu.com/idea/64/)

Notice how it was set for Jaunty? Obviously PackageKit integration is not going to occur in 9.04.

The official blueprint on launchpad is ancient:
[https://wiki.ubuntu.com/DesktopTeam/Specs/PackageKit](https://wiki.ubuntu.com/DesktopTeam/Specs/PackageKit)

Notice how 0.1 and 0.2 are the only mentioned versions.

---

### Post by plun on 2009-03-31
> **biasquez said:**
> this version is compiled from git (0.4.7 called now 2.27.x).
is it very stable and bug fixed instead of packagekit 0.3.x

Well, I tried to compile it but I am stucked at [packagekit-glib]("http://packages.ubuntu.com/jaunty/libpackagekit-glib-dev")

> ver 4.3 is needed.....  :confused:


a dev comment about PackageKit and why Ubuntu follows a debian "dead-end" would be appreciated....

---

### Post by biasquez on 2009-03-31
i attached changelog of recent releases

about install from git: [http://packagekit.org/pk-download.html](http://packagekit.org/pk-download.html)

---

### Post by plun on 2009-03-31
> **biasquez said:**
> i attached changelog of recent releases

about install from git: [http://packagekit.org/pk-download.html](http://packagekit.org/pk-download.html)

OK... I figured it out... PackageKit must be installed before packagekit-gnome can be compiled...  sorry ;)


Testing....:D

---

### Post by Flywaver on 2009-03-31
> **biasquez said:**
> i want to share with you new version of packagekit: simple, powerful and fast.

* New Features:
 - Switch gnome-packagekit to the GNOME release guidelines and version numbers 
 - Provide tooltips for the icons in the new update viewer 
 - Add a new menu item 'Select security updates' to the new update viewer. 
 - Hide the update icon notification when the update viewer is opened 
 - Switch the default update viewer to gpk-update-viewer2

biasquez, what is your desktop dock I love it!!! Do you use AWN and where can I get the same?
Thanks!

---

### Post by RAOF on 2009-03-31
> **Simian Man said:**
> I love PackageKit on Fedora, it totally blows away Synaptic and other similar applications.  Having Totem prompt me when I am missing plugins and have PackageKit automatically install the correct ones is a beautiful thing.

Last time I checked, that worked (and has worked for a couple of releases) in Ubuntu, too.  I don't check very often, though, because I'm only missing a plugin once per install ;).

---

### Post by Darkshade on 2009-03-31
> **Flywaver said:**
> biasquez, what is your desktop dock I love it!!! Do you use AWN and where can I get the same?
Thanks!

It's AWN.
```
sudo apt-get install avant-window-navigator
```

---

### Post by Flywaver on 2009-03-31
> **Darkshade said:**
> It's AWN.
```
sudo apt-get install avant-window-navigator
```

Thanks Darkshade. Yes I knew it was AWN...I was wondering where he got his icons/theme for it :)

Cheers!

---

### Post by hanzomon4 on 2009-03-31
> **gnomeuser said:**
> How so? It seems easy enough to me.

If you the application developer want to say add some functionality that is installed on demand, say you are developing an instant messaging client. You may not want every protocol installed by default, instead you could use PackageKit' API to probe for the installed packages and if they are not present search for them and install them based on demand. This lowers the foot print of your install as a user. It also gives you a consistent experience across distributions as the same widgets are being used.

Another place where PackageKit benefits the user is the use of PolicyKit, it allows you to setup policy for what users can do without authentication, what they need to type in their password for and what you need additional permissions for. This is useful for having good defaults for single users machines e.g. where you might want the user to be allowed to install packages which are signed with a gpg key on the trusted list and update the packages, but not remove any packages e.g.

You get consistent experiences as a user regardless of which Linux distro you sit down in front, as a developer you now for the first time get to hook into the package manager without being tied to one specific distribution or packaging system. Given that there is one set of tools for every packaging system you should also get fewer bugs as there is only a limited set of code paths to test, your translations should be stronger as it is one set of strings instead of one for every distro. 

Another thing one could use PackageKit for would be to have a bit of JavaScript that calls PK over dbus. This could be used on review websites to have a little button that could tell the user that the application is available for installation. Bring a one click install experience to situations where one might want to try out a piece of software.

Finally as a distribution, if you start converting your installers and tools over to using PK calls instead of direct calls to your packaging system, should you ever need to replace the underlying packaging system the transition would be much smoother as the new backend would just need a PK backend.

PackageKit is a damn good thing, it's not perfect but it lets us do a bunch of interesting bits of integration that will work regardless of which distro you are on. It also does not replace what you have currently it compliments it.

I guess this was aimed at me... I just keep getting different explanations as to what PK is. It's confusing.. What does it replace? Synaptic? Apt? or is it just another layer on top of everything else? Is it a gui program or some sort of daemon or both? As a user what will PK be to me I guess is the question...

---

### Post by Reiger on 2009-04-01
> **hanzomon4 said:**
> I guess this was aimed at me... I just keep getting different explanations as to what PK is. It's confusing.. What does it replace? Synaptic? Apt? or is it just another layer on top of everything else? Is it a gui program or some sort of daemon or both? As a user what will PK be to me I guess is the question...

Fundamentally it does not replace anything. In Linux land you have:
(a) RPM's.
(b) DEB's. 
(c) Various RPM-based packages that add automatic installation of dependencies and other convenient features. (Think: YUM, PET etc.)
(d) And whatever I forgot

Now suppose that you have some kind of tool that can act as a generic 'installation wizard' to manage the installation of whatever format you throw at it, provided that you have the underlying installer-backend (RPM, APT, YUM, YAST etc. etc.) installed....

... That is what Package Kit is. It is a wrapper around various formats, so that in theory you can use the same `interface' for all formats.

---

### Post by biasquez on 2009-04-01
> **Flywaver said:**
> Thanks Darkshade. Yes I knew it was AWN...I was wondering where he got his icons/theme for it :)

Cheers!

i'm using meliae-dust like icons, i love dust theme :p


about packagekit, according to me, it can replace synaptic because with packagekit, user can update/upgrade distro and add/remove all application.

---

