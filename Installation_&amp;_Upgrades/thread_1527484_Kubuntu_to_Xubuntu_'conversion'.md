---
title: "Kubuntu to Xubuntu 'conversion' ?"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by neptune on 2010-07-09
Hi,

Is there a simple / easy way to go from Kubuntu Lucid 64bit to Xubuntu Lucid 64bit without formatting or re-installing?

I've installed Kubuntu on an older desktop and want to see how Xubuntu would run instead.

Thanks!

---

### Post by ks07 on 2010-07-09
> **neptune said:**
> Hi,

Is there a simple / easy way to go from Kubuntu Lucid 64bit to Xubuntu Lucid 64bit without formatting or re-installing?

I've installed Kubuntu on an older desktop and want to see how Xubuntu would run instead.

Thanks!
Hi,
[Have a look at the guides here.]("http://www.psychocats.net/ubuntu/xfce") They are very detailed and should do everything you want. Just note that the guides presume you are using Ubuntu (GNOME), not Kubuntu to begin with.

A quick way of doing what you want would be to go to synaptic and install 'xubuntu-desktop'. You may also want to install 'xubuntu-gdm-theme' and 'xubuntu-default-settings'. Then, if it worked correctly, you can go to synaptic in Xubuntu and uninstall 'kubuntu-desktop' to remove Kubuntu.

The only problem with following these instructions is that some HDD space can be wasted on leftover shared libraries (e.g. the qt libs). Most of these should be removed when you remove kubuntu-desktop, however. :p

---

### Post by neptune on 2010-07-09
Hey thanks very much! Looks like that site has all the details I need.

---

