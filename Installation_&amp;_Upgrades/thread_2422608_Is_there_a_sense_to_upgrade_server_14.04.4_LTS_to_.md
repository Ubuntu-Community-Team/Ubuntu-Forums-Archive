---
title: "Is there a sense to upgrade server 14.04.4 LTS to 16.04 LTS or even to 18.04 LTS ?"
date: 2019-07-10
forum: Installation &amp; Upgrades
---

### Post by cpservicespb on 2019-07-10
I have Ubuntu 14.04.4 x64 server noX working ages.
There are:
- asrerisk, built by myself from sources;
- freeradius / isc-dhcpserver, both built by myself from sources;
- Strongswan/Xl2tpd, built by myself from sources;
- samba4, built by myself from sources;
- ntpd, built by myself from sources;
- openssl 1.1.x and 1.0.2, built by myself from sources;
- plan to build vlc noX, by myself from sources;
- iptables, bind9, apache2, mysql, php7.3.3, installed from packages.

Filesystems are ext4 and ntfs.


Is there is a sense to upgrade to 16.04 LTS and all the more so to 18.04 LTS ?
Will it be necessary to rebuild all packets (built by me) and make global/local resettings ?
For example, as one of a global resetting is moving from iptables to nftables/bpfilter.
Will it be necessary to move from iptables to nftables/bpfilter ?

Are the new Ubuntu versons more reliable, faster and so on ?

---

### Post by uRock on 2019-07-10
Since your current version is no longer supported, I'd recommend upgrading. I m not sure if any of those applications will be effected. If they are likely to be effected, then I'd recommend going all the way to 18.04 so you don't have to deal with this again for the next few years.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Vinodh Moodley on 2019-07-10
With 10 years of support, 18.04 makes the most sense to upgrade to.

---

### Post by CatKiller on 2019-07-10
You should definitely upgrade. Since 2014 we've had Heartbleed, Spectre and Metldown. Even if 14.04 has mitigations for those, it won't get them for whatever the next class of discovered vulnerabilities turns out to be, since it's no longer supported. Upgrades aren't just for desktop machines.

You will need to back up your configurations and changes, but you should be doing that anyway.

---

### Post by cpservicespb on 2019-07-10
But what is about rebuilding appliction I mentioned and moving from iptables to nftalbes ?

---

### Post by cpservicespb on 2019-07-10
And what about stability on new version ?

---

### Post by #&amp;thj^% on 2019-07-10
> **cpservicespb said:**
>  moving from iptables to nftalbes ?
See Below
[https://wiki.nftables.org/wiki-nftables/index.php/Moving_from_iptables_to_nftables](https://wiki.nftables.org/wiki-nftables/index.php/Moving_from_iptables_to_nftables)
And all your questions are a per user case, so no one can tell you how it will affect your set-up.
With all the new changes from 14.04 to 18.04 there is bound to be a learning curve for you.

---

### Post by CatKiller on 2019-07-10
No Ubuntu release is universally more stable or less stable than any other.

18.04 will be supported till 2028. Support for 14.04 ended three months ago. It's not a difficult choice.

If you want to use software that you've compiled yourself rather than the versions in the repositories you'll need to do that yourself, of course. If you want to configure your software differently than  the versions in the repositories you'll need to do that yourself, of  course.

---

### Post by TheFu on 2019-07-10
14.04 server support ended a few months ago.  Doing anything except a fresh install will be very difficult at this point.
It is best to avoid installing anything outside the package manager.  When you build from sources, you've said that you will manually rebuild from sources again every few weeks to keep patched.  Whereas if you use the package manager versions, then Canonical will handle that for you.  Canonical will back-port any security issues for the version on your "supported" OS.

Why make things hard using sources? This isn't the 1990s anymore. We don't need to use the source to get the functionality or security anymore and haven't since 2002.  In the 1990s, I was always building stuff from source, because that was the only way to get required functionality.  These days, there are a few packages where I need newer versions than what the Canonical Repos provide, so I use the project's PPA instead.  Most of the larger projects have PPAs for their current stable releases that are built for each of the supported, LTS, Ubuntu releases.  Definitely use those.

The other questions cannot be answered. "It depends" is the only answer possible. I wouldn't run all those things on the same system. I've virtualize and put the things that need similar security/risks together and I'd keep the other things far, far, far away.  
Since 14.04, many core settings are very different.  The "interfaces" file isn't used anymore. The init system is gone.  Apache is a different version.  Best to embrace the Ubuntu packaging and use them.  I spend about 5 minutes patching my Ubuntu servers every week. When using source, each program would be 5 minutes by itself, minimum.

No way would I have Samba on an internet facing server. NO FREAKIN' WAY!  BTW, you don't need NTFS so share storage with Samba. Actually, it can cause problems using it. I wouldn't put NFSv3 near the internet either.

Same for bind - not on the internet.  Bind is hacked a bunch. If you need an internal name server, keep it away from the internet.

Most people have dumped mysql for mariaDB at this point - concerns about Oracle.

I'm running 16.04 on most of my systems for a variety of reasons.  Today, I'd have to think really long before deploying 16.04 on a new box. This is mainly a support question.  Always stay on supported and maintained versions of all software. OS, applications, and services.

Update:
All the advice here from the regulars is pretty great.  
Seeing how others see the question and provide their excellent answers helps not just this poster, but the other 50 who find it over then next 10 yrs with the same or nearly the same questions.

I do try to concentrate more on the "why" and less on the "what to type."

---

### Post by uRock on 2019-07-10
> **cpservicespb said:**
> And what about stability on new version ?

Being that it is an LTS and has been released for more than a year, it should be rock solid.

@TheFu You always have sound advice.

---

### Post by cpservicespb on 2019-07-10
The question about rebuilding soft built from sources is, will it be definetelly necessary to rebuild the soft or it will continue to work ?
As I understood it will be necessary.

---

### Post by #&amp;thj^% on 2019-07-10
Yep built from sources, will need to be re-built.

---

### Post by PaulW2U on 2019-07-10
> **Vinodh Moodley said:**
> With 10 years of support, 18.04 makes the most sense to upgrade to.
Just to clarify, as far as these forums are concerned Ubuntu 18.04 is supported for just **five** years.

For further support of up to **ten** years a paid subscription to [ESM]("https://ubuntu.com/esm") as per the [Releases]("https://wiki.ubuntu.com/Releases") wiki page is required.

---

### Post by 1clue on 2019-07-10
@cpservicespb,

You have everything built by you from sources, what's the reason for all that?

As everyone else is doing, I would strongly recommend that you get onto 18.04 especially if security is important, or even if your server could possibly see traffic from the Internet. That said, the "upgrade" path involving systemd is a huge problem, it's much easier to start with an 18.04, update it to latest bug fixes, install your software and then perform a manual migration of your data.

There's no need to use nftables right now, if you're familiar with iptables. They both use the same kernel code, but nftables isn't bug free yet IMO. Iptables has problems, but at least we know what those problems are.

The biggest difference you'll see between the 14.04 and 18.04 is systemd for your init manager. From the system admin point of view, systemd is easier to configure than the old way (which was upstart).

---

### Post by cpservicespb on 2019-07-10
[**[COLOR=#000000]1clue[/COLOR]**]("https://ubuntuforums.org/member.php?u=799622") and all answered, thanks.

---

### Post by Bruce H on 2019-07-16
All of the above, but do yourself a favor and buy a new hard drive if you can (or even better, an SSD) and install 18.04 on that. Then you can mount your old drive in a spare drive bay or external enclosure so you have it available for easy reference. All of your config files in /etc, for instance.

I also second using the packages from the software store instead of compiling yourself. It's easier and a lot less time consuming. But, hey, do as you see fit. It's your system.

---

