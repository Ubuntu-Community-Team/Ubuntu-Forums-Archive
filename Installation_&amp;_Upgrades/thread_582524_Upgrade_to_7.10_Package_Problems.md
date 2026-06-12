---
title: "Upgrade to 7.10 Package Problems"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Phonan on 2007-10-19
Hey everybody. This happens to be my first post on the forums, and I made an account for a rather specific reason.

I've been using Ubuntu since this summer, and I just upgraded to 7.10 "Gutsy." However, while installing, I had quite a few problems. First, the download speed was horrible. This was expected though, as it was the first official release date. However, I had a much bigger problem with packages.

While installing the latest upgrade to Ubuntu, the Update application had problems with a large number of the packages it installed, these being:
[LIST]
[*]tzdata
[*]util-linux
[*]locales
[*]sun-java-6-jre
[*]util-linux-locales
[*]language-pack-en
[*]language-pack-gnome-en-base
[*]language-pack-gnome-en
[*]ubuntu-minimal
[*]sun-java-6-fonts
[*]sun-java-6-bin
[*]sun-java-6-plugin
[*]ubuntu-minimal (I guess I got this problem twice)
[*]update-manager
[/LIST]
In Synaptic, all the packages are checked as installed. If I try reinstalling one of them, it says it can't because of problems with other packages, which happen to be the others that I had problems with. I believe these programs are quite essential, and I really can't install anything new without them. Any help would be greatly appreciated.

Information on my (rather low-end) system, if needed-
AMD Sempron 1.6 GHz processor, now 1.8 GHz; 512 megs of Kingston RAM at I believe 667 MHz; Nvidia Geforce 7300; Western Digital 160 GB Hard Drive. I'm running (obviously) Ubuntu 7.10 "Gutsy" and I don't have any other OS's on here right now.

Thank you very much for any help people can offer me. I love Ubuntu, and I'm really excited about this update. However, seeing as I don't really seem to know enough to fix this problem, I've thought about backing up my data and reinstalling Gutsy after formatting my hard drive. Any advice on keeping some of my non-free (sorry) applications would be helpful too, if this is possible (and legal!)

Once again, thank you all very much.

Phonan

---

### Post by Hoppiesbox on 2007-10-20
Having a similar problem myself, with a slightly different(many the same) list of packages affected. One of the packages affected on my sytem is the gnome-common, and one other gnome  package - which I'm guessing is why I can't get X started. Can you have a look at my thread:
[http://ubuntuforums.org/showthread.php?t=582616](http://ubuntuforums.org/showthread.php?t=582616)
and this post from Doug:
[http://ubuntuforums.org/showthread.php?p=3579154#post3579154](http://ubuntuforums.org/showthread.php?p=3579154#post3579154)

Maybe you, or someone reading these can offer some suggestions on fixing these problems. Personally everytime I try **anything** related to package management (apt, synaptic, aptitude, dpkg, dselect) it tells me dpkg --configure -a needs to be run to fix my packages....which naturally does nothing except spit out errors like:

```
gconftool-2: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error processing libgnomekbd-common (--configure):
 subprocess post-installation script returned error exit status 127
Setting up bsdmainutils (6.1.6ubuntu1) ...
Setting up util-linux-locales (2.13-8ubuntu1) ...
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
Setting up discover1-data (2.2007.05.11ubuntu4) ...
Setting up dmz-cursor-theme (0.4.1) ...
Setting up libxfce4util4 (4.4.1-1ubuntu1) ...
Setting up screen (4.0.3-0.4ubuntu2) ...
Installing new version of config file /etc/init.d/screen ...
 Removing any system startup links for /etc/init.d/screen-cleanup ...
dpkg: dependency problems prevent configuration of libgdl-gnome-1-0:
 libgdl-gnome-1-0 depends on libgnomeui-0 (>= 2.17.1); however:
dpkg: error processing libgdl-gnome-1-0 (--configure):
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:251: process_queue: Assertion `!queuelen' failed.
```

So, yeah....what a pain - Been loving Ubuntu, and linux in general - since about the time you started - and this is the first problem I've had to post about. As of last night it seemed that nobody was having my(our) problem...but this morning I've seen a few similar posts.

Hopefully we can figure this out!

Thanks all!

---

### Post by Phonan on 2008-03-08
Sorry, it's been forever, but I just thought I'd say I solved this a while ago by just running around it and reinstalling Ubuntu. Good luck to anyone who comes up against this, and I hope it gets fixed in 8.04!

---

