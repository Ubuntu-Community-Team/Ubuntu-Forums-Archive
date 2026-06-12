---
title: "Best practice for Compiling from source?"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by disabled_20220313 on 2007-01-09
Hi there,

I am about to compile rTorrent and libtorrent from source, whats the best way to have a go at this?

I've compile software before including the kernel, but usually just made a complete mess of it to get it working, files and directories all over the place.

Is there a "best method" or procedure I should follow to make sure its all nice and tidy? Like what directories to put the source in and where to put the binaries?

Also I've usually compiled programs rather than libraries that will be used. How does it work with the libtorrent compile?

Thanks for looking, hope you can help.

Ciarán

---

### Post by bruenig on 2007-01-09
One practice I tend to use is to set it to install into /opt
Since there is nothing in there by default you can keep all compiled stuff in there, seems more tidy to me.

---

### Post by simonn on 2007-01-09
See: [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

In a nutshell:

A prefix of / (e.g. /bin, /lib etc) is for any executables that are needed for the system to boot and before networking is started.

A prefix of /usr (/usr/bin, /usr/lib etc) is for distro repository installed files - in ubuntu's case anything installed using dpkg, apt-get, synaptic etc. 

The idea is that /usr could potentially be mounted from a network file system, so the root level contains only what is needed to to boot the system and perform maintenance without network access. Imagine an office which used Ubuntu. If client pcs /usr was mounted from a server then updates would only need to be done once for all the PCs. This would obviously have a huge impact on network performance, but that is another issue.

/usr/local level (/usr/local/bin. /usr/local/lib etc) is for locally installed files i.e. anything you compile yourself.

A prefix of /opt is for anything you install from specific manufactures e.g. Adobe Acrobat Reader .tar.gz downloaded from Adobe, Real Player downloaded drectly from real.com etc. The path is different to the {,/usr,/usr/local}/{bin,lib...} in that is is /opt/[package name]/[whatever distributor sees fit] e.g. /opt/RealPlayer.

In other words, stuff you compile yourself should have the prefix /usr/local. Scripts you write yourself should be in /usr/local/bin or /usr/local/sbin etc.

However, I have used /opt to put specific versions of libraries which clashed with the distro supplied version of the same libraries but were needed by some other application.

---

### Post by konsole on 2007-01-10
> **ciaran.mooney said:**
> Hi there,

I am about to compile rTorrent and libtorrent from source, whats the best way to have a go at this?

I've compile software before including the kernel, but usually just made a complete mess of it to get it working, files and directories all over the place.

Is there a "best method" or procedure I should follow to make sure its all nice and tidy? Like what directories to put the source in and where to put the binaries?

Also I've usually compiled programs rather than libraries that will be used. How does it work with the libtorrent compile?

Thanks for looking, hope you can help.

Ciarán

The process is simple. Follow the install instructions at [http://libtorrent.rakshasa.no](http://libtorrent.rakshasa.no) and you should be fine.

I suggest you grab the 0.7.1 and 0.11.1 tar.gz to use as source. Alternatively don't go past  rev 841 if you're going to use svn.

Compiling libraries is no different than compiling programs, both usually produce binaries. I compile from location: /home/src/rtorrent.

The only difference I suggest is the last step. Instead of issuing "make install" run "checkinstall" This will install and create debs for libtorrent and rtorrent, that you can later remove or reinstall. 

You can check where everythings installed by issuing "dpkg-deb -c libtorrent_0.11.1.deb"

Also compile and install libtorrent prior to rtorrent.

Have fun. rtorrent rocks.

k.

---

### Post by cshring on 2007-01-15
check out pbuilder if you want your system to remain clean of all the dev package mess.

More info in this post -
[http://www.ubuntuforums.org/showthread.php?t=206382](http://www.ubuntuforums.org/showthread.php?t=206382)

---

