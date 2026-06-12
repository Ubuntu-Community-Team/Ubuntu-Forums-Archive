---
title: "Installaing packages from CD on a command-line system"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by minus24 on 2008-08-07
Following the [Installation Low Memory Systems]("https://help.ubuntu.com/community/Installation/LowMemorySystems") guide, I've installed an Ubuntu command-line system on a friend's old laptop, using the Xubuntu 8.04.1 alternate CD.  The laptop has 128 MB of RAM and 2.1 GB of available hard disk space, of which I've allocated 256 MB for the swap partition.

The command-line system installed just fine, and only took just over an hour!  I then installed xorg from the alternate CD -- the laptop has no internet access -- and that also works fine.

I don't want to install the full xubuntu desktop, so next I tried installing xfce4.  However, "sudo aptitude install xfce4" finds no matching packages.  "sudo aptitude install xfce" finds about 50 packages on the CD with "xfce" in their name.  I don't really want to install all of those and just hope that XFCE works.  Is there an XFCE meta package I can install from the alternate CD?

I also want to install openbox and pypanel, which are not on the alternate CD.  So I need to create a CD containing those packages (and others) to load on the laptop.  Is APTonCD the best way to do this?

---

### Post by MaddMatt on 2008-08-15
Good question. I'm installing from an alternate cd right now to dm-crypt my harddrive and for some reason it didn't install a display manager, so I'm also working on installing things from command line. Apparently (according to [this]("http://people.debian.org/~psg/ddg/node108.html")) a simple 'apt-get install' will search the CD for the packages you're looking for. (I think). So, I guess 'yes' if you burn a cd with the packages you want you can probably install them. The other option is downloading packages in a .deb format and installing them with gdebi from the command line, which should be already installed on your system. 

Hope you figured it out!
-M

---

