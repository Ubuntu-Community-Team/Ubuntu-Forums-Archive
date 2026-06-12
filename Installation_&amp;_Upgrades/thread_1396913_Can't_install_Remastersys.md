---
title: "Can't install Remastersys"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by nabilalk on 2010-02-02
When attempting to install Remastersys with Ubuntu Karmic (9.10) I get this error:

   

  >   Could not mark all packages for installation or upgrade:

        The following packages have unresolved dependencies. Make sure that all required repositories are added and enabled in the preferences

        Remastersys:
        Depends: casper but it is not going to be installed
        Depends: ubiquity but it is not going to be installed

Apparently the issue is with a lack of "casper" and "ubiquity" install. When I try to install casper from Synaptic (package manager) I get this error:

    > casper:

    Depends: initramfs-tools but it is not going to be installed
    Depends: dmsetup but it is not going to be installed

When I try to reinstall initramfs-tools and dmsetup, I am told that both are the latest versions.

Any ideas? Thanks.

---

