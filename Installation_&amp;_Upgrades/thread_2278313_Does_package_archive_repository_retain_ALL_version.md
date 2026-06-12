---
title: "Does package archive repository retain ALL versions of packages?"
date: 2015-05-15
forum: Installation &amp; Upgrades
---

### Post by nneul-0 on 2015-05-15
If there are for example 5 updates of openssl issued over some period of time for a particular distro version - are each of those packages retained indefinitely in the archive, or are older versions discarded?

I'm interested from the perspective of being able to take a snapshot of the repository metadata - so that I can apply a set of patches to a development/test environment, and then know that a week or so later, know that I can apply the exact same set of updates to my production machines. 

If I can rely on the archive retaining all versions of the packages (at least for some determined window of time) - then I only need to snapshot the metadata. Otherwise I'll need to snapshot all of the packages as well. 

(And yes, I'm aware of Landscape, just not practical from a cost perspective.)

---

### Post by ian-weisser on 2015-05-15
> **nneul-0 said:**
> If there are for example 5 updates of openssl issued over some period of time for a particular distro version - are each of those packages retained indefinitely in the archive, or are older versions discarded?

Older versions are discarded from the repository. Apt expects a repository to have only one version of a package.

Older versions are retained on the package's Launchpad page. [Example]("https://launchpad.net/ubuntu/precise/+package/openssh-client")

---

### Post by nneul-0 on 2015-05-15
Are they removed immediately upon publication of the newer version, or is there an overlap period?

---

### Post by ian-weisser on 2015-05-15
Both.
To you, it seems immediate. Apt expects a repository to have only one version of a package.
However, *phased updates* were implemented several years ago for users of Software Updater (not Synaptic or apt-get). That means some users may see an update several days before other users. Phased updates is another layer of protection - a catastrophic update can be detected and reverted before it affects everybody.

---

### Post by nneul-0 on 2015-05-15
Thank you!

---

