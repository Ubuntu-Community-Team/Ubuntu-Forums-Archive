---
title: "REAL Java support in Ubuntu 9.10"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by wirah on 2009-11-17
Hi,

Have recently upgraded to Ubuntu 9.10 to find something very annoying. The previous release's ~9.04 packages for SUN Java are stuck, as the karmic ones have a lesser version number. This is a problem for many reasons:

1. It's very confusing.
2. Certain apps (namely eclipse) don't work properly with the 9.04 package and require the upgrade, which I am prevented from doing via Synaptic.
3. The karmic version is OLDER!

I read that this is because somebody has decided that "OpenJDK" is a better solution than Sun Java. It isn't, here's why:

1. Hosting providers use and are supporting only SUN Java.
2. Companies use and are providing and supporting only SUN Java.
3. There will never be 100% compatibility between SunJDK and OpenJDK
4. Ubuntu is now even more difficult to set up for my 200 user company, because we have to MANUALLY install Java, lest we use the inferior (sorry, but in a corporate environment it is inferior) OpenJDK and then have a risk of something which works locally, not work on our live servers. This introduces RISK.

Please can whoever has made this decision, whatever board, voting system, whatever, please re-think their decision. I do not use Ubuntu to have to manually install half of my software (Eclipse is already a big issue) like some windows user. I use Ubuntu because it's clean and easy. This OpenJDK stuff does not help.

Whatever happened to choice? If I install sun-java6-jdk I expect sun's JDK. If I install open-java6-jdk I expect the open one. I want my choice back!

---

### Post by Mighty_Joe on 2009-11-17
The forums are for community support.  If you want the attention of developers, use [Brainstorm]("http://brainstorm.ubuntu.com/") or [Lanuchpad]("https://launchpad.net/ubuntu")

---

### Post by Talon2 on 2009-11-26
Just discovered this today.  This doesn't work in an educational environment either.

I've tried OpenJDK.  It isn't compatible.

This is a very bad decision.

I wish I had the freedom to choose instead of some idiot at Canonical choosing for me!!!

I need to find a new distro because this is BS!

---

### Post by jamesstansell on 2009-11-30
It depends on what you're wanting to do and what 'part' of java you're talking about.

For the browser plugin, yes the one that comes with openjdk6 is not always compatible with the sun-java6 plugin.  This is probably the most critical difference.  (In a lot of cases, though, the applets with problems are just poorly written.)

For command line programs there is very little difference.  Especially for graphical programs like azureus which use the SWT library, there really shouldn't be an issue.  If a program claims to be incompatible or has a bug then it's probably really a bug in the program or possibly an external library.

For any programming or server work the openjdk should really be preferred.  It passes all the compatibility tests, and it gets bugfixes sooner than the sun-java packages do.  The license gives the devs the ability to address issues and get new versions out in a much more timely manner.

Now, there _is_ one curious thing about the sun-java6 packages.  Because they are actually compiled by sun to work on all linux systems, a matched set of debs will generally work in whatever ubuntu release you like.  Whereas because the openjdk packages are compiled for a specific ubuntu release, you really can't expect it to work for any other release.

All that said, especially for the browser plugin the sun-java6 packages will continue to be important for some time.  But there is currently a shortage of devs working on those packages.  If you know a MOTU or someone else with the time or interest to assemble the packages, then please encourage them to find out how they can get involved.

---

### Post by jamesstansell on 2009-12-01
When I read your direction to use launchpad it made me think about the bug tracking.  But actually the answers section would probably be a better place to document these concerns.

---

### Post by jocko on 2009-12-01
> **wirah said:**
> Hi,

Have recently upgraded to Ubuntu 9.10 to find something very annoying. The previous release's ~9.04 packages for SUN Java are stuck, as the karmic ones have a lesser version number. This is a problem for many reasons:

1. It's very confusing.
2. Certain apps (namely eclipse) don't work properly with the 9.04 package and require the upgrade, which I am prevented from doing via Synaptic.
3. The karmic version is OLDER!

I read that this is because somebody has decided that "OpenJDK" is a better solution than Sun Java. It isn't, here's why:

1. Hosting providers use and are supporting only SUN Java.
2. Companies use and are providing and supporting only SUN Java.
3. There will never be 100% compatibility between SunJDK and OpenJDK
4. Ubuntu is now even more difficult to set up for my 200 user company, because we have to MANUALLY install Java, lest we use the inferior (sorry, but in a corporate environment it is inferior) OpenJDK and then have a risk of something which works locally, not work on our live servers. This introduces RISK.

Please can whoever has made this decision, whatever board, voting system, whatever, please re-think their decision. I do not use Ubuntu to have to manually install half of my software (Eclipse is already a big issue) like some windows user. I use Ubuntu because it's clean and easy. This OpenJDK stuff does not help.

Whatever happened to choice? If I install sun-java6-jdk I expect sun's JDK. If I install open-java6-jdk I expect the open one. I want my choice back!

You still have the choice to use whichever java version you want.
And I don't get what your problem is. The package versions for sun-java6-bin, sun-java6-jre and sun-java6-plugin are all at 6-15-1, while in jaunty they were at 6-14-0, so they should upgrade cleanly. If they by some reason don't, just remove them and install the karmic versions.

**Edit:** I just checked the jaunty-updates repo and saw that the version there was 6-16, so I was wrong... Weird that they haven't added the 6-16 version to karmic yet (it came to intrepid in august, so it was probably too late to include in the release, but it could have gone into the update repo)...
**Edit2:** There are a couple of [bug reports]("https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/446304") on this already. Why don't you add "affects me too" to one of them...

---

