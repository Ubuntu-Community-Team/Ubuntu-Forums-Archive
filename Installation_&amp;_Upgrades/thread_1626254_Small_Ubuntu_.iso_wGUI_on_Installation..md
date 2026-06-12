---
title: "Small Ubuntu .iso w/GUI on Installation."
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by Sean Moran on 2010-11-20
This is getting very frustrating for me now that I am confined to the on-and-off aircard sort of Internet connection, so I hope not nearly as frustrating to the reader.  After a year of building custom Ubuntu distros though, it is this confounded aircard that has taught me the need to build something small and light, for the simple purpose of reducing the time required to download the initial .iso file for a Live-CD.

I've looked at the Minimal-CD but it's a completely different system to the /casper/filesystem.squashfs setup that I'm used to.  I'm downloading (it will fail I assure you from a connection like this) Lubuntu, but alredy see that it is a 546Mb .iso, and I've already managed to pare down Ubuntu 9.10 to 496.1Mb for the .iso INCLUDING Firefox, so only time will tell if I can shave anymore off Lubuntu to reduce the size of the .iso file.

My objective is to try to get a nice little Live-CD w/GUI and look-n-feel of Ubuntu, but 100-200-300 Mb for the .iso file.  At this point, I have mounted the standard Ubuntu .iso and then removed --purged:

gnome-games, rhythmbox, tomboy notes, gimp, empathy, evolution, openoffice, and all the extra language packs.

I have attempted to swap Gnome for XFCE but that didn't work after a few tries, and it detraqcts from the full-blown Ubuntu authenticity.  I am using a method of mounting the .isos into a scratch directory, then chrooting to that dir to make the necessary remocals and installations, then I squashfs the filesystem up again and mkisofs to build the leaner version of a Live-CD .iso file.

Can anybody please advise me on what other possible applications I might remove to reduce the .iso a little bit more, without losing the main look-n-feel of the Ubuntu desktop?

---

### Post by Superluke on 2010-11-29
I'm a bit of a n00b and have no idea how to do what you're doing, but I'd certainly be interested in the final product - something to fit on a 256mb flash drive and help restore systems in particular.

---

### Post by schlichtblau on 2012-07-09
the smallest iso i found was this:
[http://www.ubuntu-mini-remix.org/](http://www.ubuntu-mini-remix.org/)

and i used universal usb installer on windows to generate my bootable pendrive (sorry, this one works only with the most common ubuntu distributions, excluding the above mentioned one. for the ubuntu mini remix, you rather need unetbootin) :
[http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/](http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/)

unetbootin:
[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by Cheesehead on 2012-07-09
You can see the list of packages included in the LiveCD with the command [FONT="Courier New"]apt-cache depends ubuntu-desktop[/FONT].

ubuntu-desktop is the metapackage (a package with no content, just a list of dependencies) used to create the LiveCD environment. Those dependencies include many of the applications and features. The list of dependencies is not complete - each dependent package has it's own dependencies that aren't listed.

For example, you can safely remove any of the (approximately) 112 'Recommends' packages that you don't want. You can remove any of the 'Depends' packages, too, but those are more likely to alter the system to a configuration you don't prefer.

---

