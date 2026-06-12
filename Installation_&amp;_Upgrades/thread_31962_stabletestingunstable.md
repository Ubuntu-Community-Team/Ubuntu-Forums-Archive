---
title: "stable/testing/unstable"
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by sprucio on 2005-05-05
Does Ubuntu have three different states like Debian? If so, what are they?

---

### Post by kvidell on 2005-05-05
[QUOTE=sprucio]Does Ubuntu have three different states like Debian? If so, what are they?[/QUOTE]
 Stable and Development.
Hoary and Breezy, respectively.
[http://www.ubuntulinux.org/wiki/BreezyBadger](http://www.ubuntulinux.org/wiki/BreezyBadger)

---

### Post by sprucio on 2005-05-05
In Debian there was a way to use both repositories. Does Ubuntu have this feature. Furthermore, how do you manipulate this through /etc/apt/sources.list?

---

### Post by bored2k on 2005-05-05
[QUOTE=sprucio]In Debian there was a way to use both repositories. Does Ubuntu have this feature. Furthermore, how do you manipulate this through /etc/apt/sources.list?[/QUOTE]
 [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

I wouldn't suggest mixing Breezy and HOary repositories..

---

### Post by sprucio on 2005-05-05
Heh, I was actually reading that page.

Questions ...

What do those keywords main, restricted, universe and multiverse mean? I know Debian has it structured like this but don't really know what they mean.

---

### Post by bored2k on 2005-05-05
[QUOTE=sprucio]Heh, I was actually reading that page.

Questions ...

What do those keywords main, restricted, universe and multiverse mean? I know Debian has it structured like this but don't really know what they mean.[/QUOTE]
 [http://www.ubuntulinux.org/ubuntu/components/document_view](http://www.ubuntulinux.org/ubuntu/components/document_view)

> The main distribution component contains applications that are free software, can freely be redistributed and are fully supported by the Ubuntu team. This includes the most popular and most reliable open source applications available, much of which is installed by default when you install Ubuntu.
> The restricted component is reserved for software that is very commonly used, and which is supported by the Ubuntu team even though it is not available under a completely free licence. Please note that it may not be possible to provide complete support for this software since we are unable to fix the software ourselves, but can only forward problem reports to the actual authors.
> The universe component is a snapshot of the free, open source, and Linux world. In universe you can find almost every piece of open source software, and software available under a variety of less open licences, all built automatically from a variety of public sources. All of this software is compiled against the libraries and using the tools that form part of main, so it should install and work well with the software in main, but it comes with no guarantee of security fixes and support. The universe component includes thousands of pieces of software. Through universe, users are able to have the diversity and flexibility offered by the vast open source world on top of a stable Ubuntu core.
> The "multiverse" component contains software that is "not free", which means the licensing requirements of this software do not meet the Ubuntu "main" Component Licence Policy.

The onus is on you to verify your rights to use this software and comply with the licensing terms of the copyright holder.

This software is not supported and usually cannot be fixed or updated. Use it at your own risk.
> About Ubuntu Backports
Ubuntu Linux is a great distribution, but falls short in the desktop realm to Gentoo and Fedora Core. Why? Once a stable version is released, no new software updates are accepted. I subscribe to the view that a distribution can be both stable and up-to-date, so I've taken it into my own hands to recompile newer packages from Hoary and Debian Sid for Warty.
[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)


Debian is just Stable, Testing and Unstable with Toy Story character names [woody, sarge & sid].

---

### Post by sprucio on 2005-05-05
Well, I'm at work so I'm reading off the Knoppix list but it's

main, contrib, non-free thus far.

Thanks for all that info. It really helped.

That last thing about backports, can you elaborate on that? Does software updates refer to newer versions or does it mean security updates?

---

### Post by bored2k on 2005-05-05
[QUOTE=sprucio]Well, I'm at work so I'm reading off the Knoppix list but it's

main, contrib, non-free thus far.

Thanks for all that info. It really helped.

That last thing about backports, can you elaborate on that? Does software updates refer to newer versions or does it mean security updates?[/QUOTE]
 Whatever you do, don't mix hoary with warty with breezy repositories .. **ever**

---

### Post by bored2k on 2005-05-05
[QUOTE=sprucio]That last thing about backports, can you elaborate on that? Does software updates refer to newer versions or does it mean security updates?[/QUOTE]

Backports are mostly newer versions of software ported by [Jdong](http://ubuntuforums.org/member.php?find=lastposter&t=31774). There you'll find things like newer Gaim, Firefox and some packages that probably will never reach main/universe/multiverse. If you want to dist-upgrade in the future, you would have to --downgrade these files though.. In conclusion, these are mainly faster updates.

---

### Post by sprucio on 2005-05-05
Well, let's say Mozilla-Firefox v1.2 was released with Hoary. Now, that v1.3 is released, does that mean that I have to wait for the next major release (in this case breezy) for it to upgrade to v1.3?

It would be annoying to downgrade also.

What would be the downfall of adding this to the file?

---

### Post by sprucio on 2005-05-05
Anyone?

---

### Post by bored2k on 2005-05-05
[QUOTE=sprucio]Well, let's say Mozilla-Firefox v1.2 was released with Hoary. Now, that v1.3 is released, does that mean that I have to wait for the next major release (in this case breezy) for it to upgrade to v1.3?

It would be annoying to downgrade also.

What would be the downfall of adding this to the file?[/QUOTE]
 No you don't have to wait for breezy. Backports just get a faster upgrade. Since Hoary is supposed to be stable, it needs a lot more testing, wich is way we don't get it instantly. Point is, you want bleeding edge, while sacrificing a bit of stability? add backports, you want complete stability with not really old packages constantly being upgraind? dont add them.

---

### Post by 23meg on 2005-05-05
another thing is, since Hoary is quite young, distro packaged versions of apps that come with Hoary already have many of the updates included in post-Hoary versions. for example, the firefox 1.0.2-ubuntu5  that comes with Hoary has most of the fixes that come in the default installation of 1.0.3.

---

