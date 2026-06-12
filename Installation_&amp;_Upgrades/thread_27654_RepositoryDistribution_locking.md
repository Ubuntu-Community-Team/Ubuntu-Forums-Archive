---
title: "Repository/Distribution locking?"
date: 2005-04-17
forum: Installation &amp; Upgrades
---

### Post by ionos on 2005-04-17
[SIZE=1]Forgive me for not being that familiar with the Ubuntu/Debian/apt terminology, I'm coming from a FreeBSD/Gentoo background; I only have Ubuntu running for a couple of days now (but me likes what me sees).[/SIZE]

Anyways, here it goes: In order to install some software, I had to add new external (= not directly related to Ubuntu) repositories to sources.list, namely some debian ones. Then I installed the software in question, everything worked great.

Now I'm facing the problem that the external repositories contain some newer versions of packages I had installed from the hoary-repositories, and the update mechanism tries to install the external versions. Of course, I'd rather had it use genuine Ubuntu packages whenever possible, even if that means not having the latest version installed. And sometimes, the name of the external packages (e.g. foobar-woody1) seems to confuse synaptic, but that a different issue.

**Question**: How can I ensure that synaptic uses the "right" repository for each package, that is
[list=1]
[*] the repository the software was originally installed from, or
[*] only use certain repositories (debian) if the package cannot be found in a specified set of repositories (eg. hoary & backports).
[/list]

Possible solutions (neither one is satisfactory):
[list=1]
[*] Just ignore the packages that would get an undesired upgrade, i.e. perform upgrades manually on a per-package basis - bad, as this would render the nice auto-update-features useless
[*] Disable the external repositories - bad, as packages not found in the Ubuntu repositories will not be upgraded
[*] Lock packages with a newer external version to the installed ubuntu version - bad, as ubuntu upgrades will be missed
[*] Tell synaptic to prefer the hoary repositories - bad, as this does not solve a backports-debian-rivalry, for example (I'd rather have the backport version)
[/list]

What could work (if it were supported):
[list=1]
[*] Lock packages to a distribution/repository
[*] Have not only one prefered source in the synaptic preferences, but a hierarchy of sources (first use hoary, if not found there use backports, ...)
[/list]

I might well be missing something, given my lack of Ubuntu-experience - sorry if I'm bothering folks with a maybe rather trivial question. Could a kind soul share some insight with me?

Cheers
 - i

---

### Post by erkki70 on 2005-04-17
[QUOTE=ionos]**Question**: How can I ensure that synaptic uses the "right" repository for each package, that is

[list=1]
[*] the repository the software was originally installed from, or
[*] only use certain repositories (debian) if the package cannot be found in a specified set of repositories (eg. hoary & backports).[/QUOTE]
[/list]Hi,
I would first recommend to use Synaptic as you'll get WYSIWIG view of the packages with better control than the automatic updater.
Even though you have a bunch of extra repositories, you'll always identify original Ubuntu package releases with the Ubuntu logo in front of them. Pretty easy to see what is what this way. Then, if you carefully read the version of a package, you can also easily spot where it comes from. Using the property button gives you even more details.
So far, I've done this way and haven't encounter any problem yet.

There might be another way though, I'm aware that my answer might not be satifsfaying...

Hope this helps anyway.

Cheers,
Erkki

---

### Post by speedman on 2005-04-17
Have a look here for simple instructions on using apt-pinning:

[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)


Regards,

SM

---

### Post by ionos on 2005-04-17
[QUOTE=speedman]Have a look here for simple instructions on using apt-pinning:
[/QUOTE]

Thanx speedman, that did the trick. And synaptic adheres to these preferences, too ... so sweet. I might actually start to like apt/deb ...

Cheers
 - i

---

