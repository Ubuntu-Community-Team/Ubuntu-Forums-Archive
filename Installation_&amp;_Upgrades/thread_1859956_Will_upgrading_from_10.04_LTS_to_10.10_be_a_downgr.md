---
title: "Will upgrading from 10.04 LTS to 10.10 be a downgrade?"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by KonfuseKitty on 2011-10-14
If support for 10.04 LTS ends in April 2013, but support for 10.10 ends a year earlier, would that mean that if I upgrade from 10.04 to 10.10 inbetween, say in August 2012, that I would in fact be downgrading? Would I be going from a system with the latest updates, to one for which updates have stopped?

---

### Post by snowpine on 2011-10-14
In April 2012, you will be able to upgrade directly from 10.04 to the next LTS, 12.04.

---

### Post by uRock on 2011-10-14
Support for 10.10 will be dropped in April 2012. The non-LTS releases are supported for 18 months, whereas the LTS is supported for 36 months.

---

### Post by KonfuseKitty on 2011-10-14
But does that mean that I will lose the ability to upgrade to 10.10? I'm trying to understand my options...

---

### Post by uRock on 2011-10-14
> **KonfuseKitty said:**
> But does that mean that I will lose the ability to upgrade to 10.10? I'm trying to understand my options...

You can upgrade to it now, but the upgrade will be useless in Aug. 2012, since it will not receive any security updates. I would suggest doing as mentioned by snowpine and upgrade to 12.04 when it is released, unless there is a certain program you need updated. If that is the case then feel free to ask how to upgrade the program without having to upgrade the OS.

---

### Post by KonfuseKitty on 2011-10-14
The reason I asked the question was that I couldn't find an ISO image for 10.10 by going to Ubuntu.com and following the download links. So I thought the only way to go from 10.04 to 10.10 is now by upgrading. However, I've since found releases.ubuntu.com, where the ISO is still available. I note that 9.04 and 9.10 aren't available though, and that tells me that after April 2012 10.10 ISO won't be available either. I'll download it now, but the ISO is old, from October 2010, so after install I will need to update it. The snag is that I won't be able to obtain the last updates after 12.04 is released. I wish there was some overlap between the stopping of support of 10.10 and release of 12.04, so I could choose between the two and still get 10.10 updated to its last updates. (10.10 works best on my machine, 10.04 has some issues, 11.04 is close to unuseable, 11.10 I won't even bother.)

---

### Post by snowpine on 2011-10-14
Unsupported releases are available here: [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)

Honestly you are not the first user to have a bad experience with 11.04. If you look around the forums you'll read a lot of "don't know what I'm going to do when 10.10 reaches end-of-life" laments. Let's reserve judgment until we see what 12.04 looks like. ;)

---

### Post by KonfuseKitty on 2011-10-14
Hey, thanks for the link! And yes, I'm happy to reserve judgement and will try 12.04, but I need to be ready for the worst. If I can't use 12.04, the dilemma is going to be how to get last updates for 10.10, as I assume 10.10 support will have ceased by then. Thinking about it, I will probably need to create an image of my hard drive with the fresh and up-to-date install of 10.10 before I try 12.04.

---

### Post by uRock on 2011-10-14
If Unity is your downfall, then you may want to give the following a try [http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961) in ubuntu 11.10.

You may also want to check out Xubuntu or Kubuntu.

---

### Post by snowpine on 2011-10-14
NOT RECOMMENDED OR SUPPORTED but I offer the following for educational purposes.

When an Ubuntu release goes "end of life" its repositories move to old-releases.ubuntu.com. 

So if you edit your software sources:

```
gksu gedit /etc/apt/sources.list
```

You can then change all of the URL's to old-releases. For example change this:

```
deb http://us.archive.ubuntu.com/ubuntu/ maverick main 
```

to this:

```
deb http://old-releases.ubuntu.com/ubuntu/ maverick main 
```

This will allow you to apply all updates as of the end-of-life date (April 2012). Any bugs or security flaws discovered after this date will never get fixed.

---

### Post by KonfuseKitty on 2011-10-14
@snowpine: That looks like exactly what I was seeking, thanks a lot!
 
@uRock: Thanks for trying, but I've tested all the options you suggest and none of them match what plain Ubuntu 10.10 gives me. That said, I tried the two Gnome Classic options in 11.04, not 11.10, so there may have been an improvement since then. I'm not willing to find out though, as I recently spent a whole week installing and testing various OSs. Not doing that again till April 2012.
 
Marking this as solved, thanks to snowpine's education. ;-)

---

### Post by uRock on 2011-10-14
How can you say you've tested the options, when you haven't? The gnome fallback is for 11.10, not 11.04. Use whichever makes you happy, even if it is insecure.

---

