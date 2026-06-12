---
title: "Why does Ubuntu use an old FreeMind package?"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by PadreSol on 2008-07-11
Hey maintainers, why is Ubuntu delivering an old version of freemind??

freemind.sf.net has a new debian package, wondering why Ubuntu's out-of-sync

---

### Post by Zack McCool on 2008-07-11
Ubuntu will use the "old" versions of a lot of things.  They don't update to the newer packages until the new ones have been tested as stable with the OS.  Unless there is a problem with the old one, they might not even move to a new version until the next release...

---

### Post by PadreSol on 2008-07-12
> **Zack McCool said:**
> Ubuntu will use the "old" versions of a lot of things.  They don't update to the newer packages until the new ones have been tested as stable with the OS.  Unless there is a problem with the old one, they might not even move to a new version until the next release...

Where are the test results? Are they online somewhere?  I think your answer might apply partially but not completely.

Maybe it's waiting for a security audit? 

I downloaded a recent copy so I guess ubuntu can do whatever.

---

### Post by iaculallad on 2008-07-12
Try following up with this Freemind's [thread]("https://bugs.launchpad.net/ubuntu/+source/freemind/+bug/182927") located at answers.launchpad.net.

---

### Post by mcduck on 2008-07-12
The gemeral rule is that after Ubuntu verison is released all it's package versions are frozen to those available at the time of release. Updates are only provided for security reasons and to fix serious bugs.

So there is no group of people browsing around the web continuosly looking for latest program versions and testing if they'd work correctly with the already-released Ubuntu version (and all the other packages).

Sometimes after the new versions of some program has been included in the development version of Ubuntu it might be backported to the current released version, but only if the package has little or no dependencies that would require updating.

If you want a Linux distribution that always gives you the latest and greatest versions of all programs Ubuntu is not for you. Try Gentoo instead. Ubuntu has chosen a compromise between extreme stability and testing (Debian) and up-to-date software (Gentoo).

---

### Post by PadreSol on 2008-07-12
> **mcduck said:**
> The gemeral rule is that after Ubuntu verison is released all it's package versions are frozen to those available at the time of release. Updates are only provided for security reasons and to fix serious bugs.

So there is no group of people browsing around the web continuosly looking for latest program versions and testing if they'd work correctly with the already-released Ubuntu version (and all the other packages).

Sometimes after the new versions of some program has been included in the development version of Ubuntu it might be backported to the current released version, but only if the package has little or no dependencies that would require updating.

If you want a Linux distribution that always gives you the latest and greatest versions of all programs Ubuntu is not for you. Try Gentoo instead. Ubuntu has chosen a compromise between extreme stability and testing (Debian) and up-to-date software (Gentoo).

Thanks mcduck.  As for freemind it sounds like there was just some knowledge sharing that needed to happen.  Thanks to iaculallad for pointing me to that thread discussing packaging. In freemind's case the betas are pretty stable and new versions come slowly so low risk to take new software.

About stability look at the Xorg, we're using an unsupported xserver. But to be fair maybe there are fixes that were worth the risk to take now.  

Xorg -version

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)


Looks like current is 1.4.99.905.  Guess my point is that being conservative and being stable aren't the same.

---

### Post by faust99 on 2008-08-03
New freemind deb is here: [http://sourceforge.net/project/showfiles.php?group_id=7118&package_id=161831&release_id=574421]("http://sourceforge.net/project/showfiles.php?group_id=7118&package_id=161831&release_id=574421")

---

### Post by PadreSol on 2008-08-07
> **faust99 said:**
> New freemind deb is here: [http://sourceforge.net/project/showfiles.php?group_id=7118&package_id=161831&release_id=574421]("http://sourceforge.net/project/showfiles.php?group_id=7118&package_id=161831&release_id=574421")

Yep, better late than never. (^;

---

### Post by mckelly46 on 2008-10-18
There is a version 0.9.0. I've run it in a windows environment and love it ... I'm not sure its ready for linux yet (anyone tried it?).

In the meantime I've grown quite fond of kdissert. It's very much like freemind version 0.9.0. In fact I find it better than freemind.

Cheers,

Michael

---

