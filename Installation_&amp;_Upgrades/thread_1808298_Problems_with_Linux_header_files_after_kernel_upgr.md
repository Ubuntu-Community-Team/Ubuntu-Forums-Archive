---
title: "Problems with Linux header files after kernel upgrade"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by DrDaveyAtoms on 2011-07-20
I have been experiencing a non-critical problem for some time now and I am interested in finding out if there is a solution.

Whenever I upgrade the kernel I am not able to immediately boot into Ubuntu when I select the upgraded kernel from the GRUB menu. The problem can be solved by booting into a previous version of the kernel and installing the most up-to-date kernel linux header files. Prior to this, the most recent header files are not listed as being installed in Synaptic. Upon restarting, it is then possible to boot into the most recent version of the kernel.

As I said above, this is non-critical and I have found a work around for this but it would be convenient if someone has a permanent solution which would allow the kernel to be updated and work first time.

Thanks for your time.

---

### Post by MAFoElffen on 2011-07-20
> **DrDaveyAtoms said:**
> I have been experiencing a non-critical problem for some time now and I am interested in finding out if there is a solution.

Whenever I upgrade the kernel I am not able to immediately boot into Ubuntu when I select the upgraded kernel from the GRUB menu. The problem can be solved by booting into a previous version of the kernel and installing the most up-to-date kernel linux header files. Prior to this, the most recent header files are not listed as being installed in Synaptic. Upon restarting, it is then possible to boot into the most recent version of the kernel.

As I said above, this is non-critical and I have found a work around for this but it would be convenient if someone has a permanent solution which would allow the kernel to be updated and work first time.

Thanks for your time.
Welcome to Ubuntu Forums.

This is NOT as "non-critical" as you refer.  The kernel header files should install with the kernel.  If not, as you've found on your own- the system doesn't want to boot up... or a little more obscure, the graphics doesn't want to boot (or other drivers) because it was updated with without the correct or missing header files.  You have figured out on your own what to do to correct this, but not all average users have figured this out on their own.  No, it is not normal and not exactly how things are supposed to update...

I've seen where this problem has been intermittent, happening "once" to some user... but it sounds like it has happened to you more than once(?)  I think you are really a good candidate to report this to Launchpad... Which will not only help you, but to help the dev's to help prevent this from happening to others.

You can do this from the command line via:[FONT=monospace]
[/FONT]```
ubuntu-bug -p linux

```

---

