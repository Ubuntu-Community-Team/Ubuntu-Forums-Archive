---
title: "creating virtual Ubuntu packages"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by abbas.sadat on 2010-02-09
Hi,
I need to somehow create a package which is composed of other already existing packages. This is useful when you want to provide other people (like first year students) with a set of libraries which otherwise it would be difficult for them to install then one by one.
I'm not really sure about how to do this. One way can be to create an empty package with dependency on the desired packages so that when this empty package is being installed, other required packages are installed automatically before.

Does any one have an idea about how to do this? or any other solution to this problem?

Thanks,
Abbas

---

### Post by SaintDanBert on 2010-02-09
For *-buntu, we use the Debian "deb" style of package and the **apt** or **aptitude** or **synaptic** package manager. There are numerous packages that are collections of other packages for a variety of reasons. We call these "Meta-Packages."

Look here [ https://help.ubuntu.com/community/MetaPackages ]( https://help.ubuntu.com/community/MetaPackages ) for details about Ubuntu MetaPackages in general and several existing packages in specific.

You sound like an educator using linux. I'd be interested in hearing more about what you are doing.

Cheers,
~~~ 0;-Dan

---

