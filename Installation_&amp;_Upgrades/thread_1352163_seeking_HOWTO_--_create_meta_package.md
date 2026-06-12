---
title: "seeking HOWTO -- create meta package"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2009-12-11
Can someone tell me where to find instructions so that I might create my own "meta package"?  As I understand, a **meta package** looks like any other DEB file, but only contains a list of dependencies -- "... make sure all of these things are present ..." I know that I can use **dpkg --get-selections** and **dpkg --put-selections**, but that feels like "dump this mound of stuff." If I have meta packages, it feels like things get thought out better. 

There are a group of things that I always want to install. I have a script that says, "apt-get install ..." twenty times. It seems that this is a perfect situation for an apt meta package. I'd like to spin a distro install and then install my "meta package" to get all of my personal preference stuff. For example, I use emacs. [I'll wait for laughter to die down ...] There are a set of tools and toys that I always want to use with emacs. A dans-emacs-meta package would let me get all of those parts and also deal with the inevitable dependencies as my favorite parts evolve.

Also, I know that there is some technique to store all of the distro install answers so that you can repeat that install automatically.
I think that this is called "kick start". How easy is this to get working? Does it include saving all of the new install setup and config that a new distro usually requires?

I'm trying to build a collection of tools for getting mostly identical distro installs. The hardware is not identical so "cloning" is not an option. I thought that an automatic install would let the distro feel the hardware on hand and do good things. Kickstart would help each distro be mostly alike. Metapackages would help get my preferences for add-ons to be mostly alike.

Thanks,
~~~ 0;-Dan

---

### Post by lemming465 on 2009-12-12
You need to spend some quality time with the [Debian Policy Manual]("http://www.debian.org/doc/debian-policy/").  You can certainly build your own metapackage if you are persistant enough.  

It shouldn't be necessary to have 20 "apt-get install ..." lines; a single long one ought to suffice, and will do a better job of dependency resolution as well.  You might want to think about switching to *aptitude*; Debian is deprecating apt-get.

Kickstart is a RedHat-ism; while it can be used with Debian style installs the more native way to script answers is using preseed files for *debconf*.  You might look into packages such as *debconf-doc* and *ubiquity-frontend-debconf*.

---

### Post by SaintDanBert on 2010-01-07
Actually, I'm a very *-buntu instead of Debian kind of fellow.

Is "aptitude" displacing "apt-get" everywhere or is that a Debian specific trend?

~~~ 0;-Dan

---

### Post by gsmanners on 2010-01-07
In my experience "apt-get" is used about 10x more often than "aptitude" in a generic search through help or docs.

---

### Post by lemming465 on 2010-01-08
I'm naively assuming that since Debian is moving toward aptitude, Ubuntu will follow.  There are a few operations that apt-get does which aptitude does not, so apt-get is not completely obsolete yet in any case.  apt-get is both older and more familiar, so it's not surprising that the majority of the historical web help features it.

---

### Post by lemming465 on 2010-01-11
As for being more fond of Ubuntu that Debian; that's just fine - many of us are in that camp.  If you want to make your own metapackage, you probably do want to spend some time with the Debian policy manual; Ubuntu uses Debian style packages and that's the documentation for how they work.  Meanwhile, the other thing you really want is an example.  A rather gonzo case would be something like *apt-get source kubuntu-desktop*

---

