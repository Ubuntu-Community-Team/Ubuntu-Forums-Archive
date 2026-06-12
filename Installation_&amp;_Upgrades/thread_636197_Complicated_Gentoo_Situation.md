---
title: "Complicated Gentoo Situation"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by 1337455 10534 on 2007-12-09
[SIZE="2"]I am currently in single-boot with the latest Gutsy, but I want to double-boot with the latest Gentoo. Several issues pop up. Firstly, I am not positive, but my dad says that my HP is an i586, since it is P4. It's about 3 years old, and it was really good then. In any case, its got 1 GB of RAM and handles Compiz Fusion very well, and ALSA works. Oh, and GNOME is awesome.

Being an i586 means that the Gentoo LiveCD wont work, not to mention the LiveDVD, which I have already burned (grr!). There is no way I am going to get Sabayon. Sorry.[/SIZE]

[COLOR="Red"]**_Does anyone here know of a way to download the stage3 tarball and other packages and put it on the minimal CD (which supports i486 and later) and install from that? Much appreciated. _**[/COLOR]

And yes, I've read the Gentoo Handbook, and the Alternate Install Methods. If this method is possible, I much rather would do it than slaving for hours with alternate methods..
If this is not possible, can someone explain Catalyst or GLI? I really want to give an other distro a serious try..

I know Gentoo will be on a different partition, but will it change any of my Ubuntu settings? Should this thread be moved to other OS talk? (Well, it's sorta about Ubuntu...)

---

### Post by rsambuca on 2007-12-09
If you are going to install gentoo to another partition, then do it from within your Ubuntu installation via a chroot.  The huge benefit of this is that you have no computer downtime, so you can access the internent and the handbook while everything is installing and compiling.  It is very easy to do.  The live CD frankly is not recommended and doesn't work very well.

Instructions on [how to install from within ubuntu are here]("http://www.gentoo.org/doc/en/altinstall.xml#doc_chap5").

---

### Post by 1337455 10534 on 2007-12-09
Thank you so much!
Another quick noob question; say I have a LiveDVD.iso, and I follow this guide, will it work on my lesser than i686 computer? Really I don't see why not, since I don't want to run it Live, all I need are the Gentoo pizazz. 
Say.... Why can Ubuntu run Live on my computer, but not Gentoo? :confused:

---

### Post by 1337455 10534 on 2007-12-10
ehh, bump? I've registered and asked the Gentoo forums people about this too..

---

### Post by rsambuca on 2007-12-10
Which method are you going to be using to install?  If you are doing it via chroot, you don't need any .iso files.

---

### Post by 1337455 10534 on 2007-12-10
> 
In order to install Gentoo from your existing Linux distribution you need to have chroot command installed, and have a copy of the Gentoo installation tarball or ISO you want to install.

I just torrented 3.7 GB worth of Gentoo, I hope I'll be able to use at least the ISO, considering the DVD's already wasted..

Is there any way I can use the ISO? Perhaps use ISO master to extract all of the files in there?
> 
We want to resize our Linux root partition, therefore we must boot from a floppy disk a minimal linux system and use previously-compiled parted copied to a diskette in order to resize /. However, if you can unmount the partition while still in Linux you are lucky, you don't need to do what follows. Just compile parted and run it on an unmounted partition you chose to resize.

More importantly, can Ubuntu unmount and resize /?  I.e can I avoid using Mininux?

Normally I'm this hesitant, but this is all almost completely new to me..

---

### Post by rsambuca on 2007-12-10
To be honest, I have no idea if you can use the iso for the required files.  The stage3 tarball is only 103MB, though.  Small potatoes compared to what you just did!

---

### Post by rsambuca on 2007-12-10
For the partitioning, I used gParted to make the partitions ahead of time.  That way you can skip most of the early steps.

---

### Post by 1337455 10534 on 2007-12-10
Ok, thank-you!

---

