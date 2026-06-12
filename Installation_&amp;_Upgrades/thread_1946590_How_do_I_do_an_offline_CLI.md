---
title: "How do I do an offline CLI?"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by Splooshie123 on 2012-03-25
How do I do an offline command line install?

My Internet connection is quite slow and occasionally disconnects. I would like to install an absolute minimal (64 bit) system ([http://packages.ubuntu.com/lucid/ubuntu-minimal](http://packages.ubuntu.com/lucid/ubuntu-minimal)) without the need for an Internet connection.

Do any of the available iso images offer this feature?

---

### Post by Cheesehead on 2012-03-25
There are three levels of complexity, each represented by a metapackage:

ubuntu-minimal - The basic bootable system. Bare bones, little real functionality.
ubuntu-standard - A fully-featured command-line system (ubuntu-minimal plus a bunch)
*buntu-desktop - A fully-featured GUI desktop system (ubuntu-standard plus a bunch)

If you dive into the dependencies, you'll see which packages and applications rely upon which metapackage.

The Alternate CD enables you to install just ubuntu-standard, which is probably the starting point for a fully-featured CLI you're looking for.

The minimal package you linked to is, of course, the ubuntu-minimal metapackage, and is available at [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) . Normally, minimal requires internet connection, because you want to add lots of packages to flesh out the minimal skeleton.

In addition, you may wish to install apt-offline, aptoncd, or apt-zip, or some other offline package management solution. Manually tracing dependencies and downloading and copying packages to /var/cache/apt can be a bit tedious. I've done it...ugh.

---

### Post by Splooshie123 on 2012-03-25
Thank you Cheesehead.

So apparently, I'm going to have to download the alternate cd.

Does the alternate cd offer a command line install option?

EDIT: Nevermind. I found out it does.

Just for fun (and partially as a fail-safe), I'll create a custom iso with only a basic command line system on it. The challenge: I have no CDs here and I'm on a mac (64 bit and won't boot from a USB).

---

