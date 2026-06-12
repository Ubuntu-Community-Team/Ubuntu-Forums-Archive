---
title: "Server vs. minimal install"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by Karl1982 on 2010-10-08
I recently set up a PXE boot system capable of dishing out Ubuntu's netboot installer.  Works fine.  But I may be using this to install servers... So my question is, is it against best practices for me to install server platforms starting with the minimal installation from netboot?

I don't know what the differences are between the regular and server kernels.  I did notice the server install comes with stuff like screen which is very handy and I would install anyway.  Am I just as well off with the minimal installation followed by using tasksel for basic Ubuntu server?

---

### Post by andrewthomas on 2010-10-08
> **Karl1982 said:**
> 
I don't know what the differences are between the regular and server kernels.
As far as I know, the only difference is between the configuration options.  You could install one of each and do a diff on the configs.

---

### Post by Karl1982 on 2010-10-09
There's a (minor) distinction made by landscape-common in /etc/update-motd.d where the text inserted into the MOTD is slightly different depending on whether a generic or server kernel is loaded.  If I remember correctly, it used the output of uname -r as the basis for that determination.  I don't have landscape-common on my laptop, so I'm not 100% on that, but I think that's what it was even on my most recent minimal alternate install.

I don't see anything kernel-related in the packages for the "server" task in tasksel.  It looks like it includes the packages like screen that I noticed were missing from minimal vs. server install.

Maybe I'll try a minimal installation over netboot and then switch out the generic kernel for the server kernel sometime and see how it goes.  It seems like between loading the server kernel and the "basic Ubuntu server" packages from tasksel, it would be pretty close to an Ubuntu Server CD installation.

I haven't played with the kernels too much yet.  Do you mean I should download the source from the same version of both kernels and diff that?

---

### Post by andrewthomas on 2010-10-09
You don't need to download the source.  When you install a kernel, the config is placed in your /boot folder (ie config-2.6.35-22-generic.)

---

