---
title: "Unison not up-to-date in Lucid"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hajk on 2010-04-08
I'm using Unison on various computers, with various OS-es, to synchronize and backup personal files. The current stable version of Unison is 2.32 (and has been stable for quite a while); the previous stable version was 2.27.

Unfortunately, Unison archives made with these different versions don't mix. Equally unfortunately, Ubuntu Lucid repositories only carry the older 2.27 version of the unison package (there's also a parallel -gtk version), whereas I use the 2.32 version on all my other computers running Mac OS X, Debian GNU/Linux (testing) and FreeBSD. There is an older bug in Launchpad requesting an upgrade to 2.32 in the Karmic repositories; I've added a note urging that this be done before Lucid release.

That was more than a month ago, and it now looks that Lucid will be released with the obsolete previous version of Unison. All is not lost, however, since the version in the Debian testing repository can be installed and works beautifully in Lucid. Here's how: 

1. Download the package from [http://packages.debian.org/squeeze/unison](http://packages.debian.org/squeeze/unison) for your architecture (there's no problem with the dependencies).

2. Install the package in a terminal with the command```
  
sudo dpkg -i unison<Tab>
```using the Tab-key to complete the full package name.

3. If the "apt-show-versions" package is installed, then verify with the```

apt-show-versions |grep unison
```command that the newly installed version supersedes the older version in Lucid.

It works for me.

Have fun!

---

### Post by dcstar on 2010-04-08
> **hajk said:**
> I'm using Unison on various computers, with various OS-es, to synchronize and backup personal files. The current stable version of Unison is 2.32 (and has been stable for quite a while); the previous stable version was 2.27.

Unfortunately, Unison archives made with these different versions don't mix. Equally unfortunately, Ubuntu Lucid repositories only carry the older 2.27 version of the unison package (there's also a parallel -gtk version), whereas I use the 2.32 version on all my other computers running Mac OS X, Debian GNU/Linux (testing) and FreeBSD. There is an older bug in Launchpad requesting an upgrade to 2.32 in the Karmic repositories; I've added a note urging that this be done before Lucid release.
........

I don't know how a "Stable" version is in the Debian "Testing" repository.

10.04 is a release based on stable apps, so I seriously doubt that anything not in that category will be made available.

Wait until 10.10 development is started and backported versions of things are made available for 10.04.

---

### Post by hajk on 2010-04-08
Ah, I see... the "stable" moniker refers to Unison itself. For example, when downloading a binary version of Unison for Mac OS X via a link on the Unison website, the "stable" version 2.32 is supplied. Or, when the Unison source code is needed from the Unison site, the version 2.32 is offered as the "stable" version.

Debian is always a bit slow in following upstream, and Ubuntu (derived as it is from Debian) is slower still because of the semi-annual package freeze. I've merely given a work-around, so that my Ubuntu installation does not impose the use of an obsolete version of Unison on my other computers/OS-es. The alternative would be not using Ubuntu, now where would that leave us... ;)

---

