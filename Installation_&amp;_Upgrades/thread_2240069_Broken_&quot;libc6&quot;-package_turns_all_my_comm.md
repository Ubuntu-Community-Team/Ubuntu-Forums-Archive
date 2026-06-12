---
title: "Broken &quot;libc6&quot;-package turns all my commands for repair into a vicious circle"
date: 2014-08-17
forum: Installation &amp; Upgrades
---

### Post by Cheerz on 2014-08-17
[FONT=arial]In my attempt to install the wine1.7.24.deb from winehq.org with dpkg, which failed to complete it's install for reasons I cannot recover, the "libc6"-package has rendered my system at a paralyzing halt. Here is a conversation from #ubuntu in IRC which breaks it down. Bold is me, and what is not bold is my kind helper.

[code]

**Whenever I try to completely remove, reinstall or remove "libc6" which is causing broken packages, unabling me to install or remove other packages, it wants to remove a HUGE amount of other essentials, like alsa, ardour3 and all kinds of things which are out of the question. What's this all about?**[/FONT][B]
[FONT=arial]libc6 is currently at 2.17, when it should be at 2.15, but if I try to force the version down it tries to shred my system all the same[/FONT]
[/B][FONT=arial]**What the hell...**
[/FONT]
[FONT=arial]Why should it be 2.15?[/FONT]
[FONT=arial]Make sure you have the exact version for the package you want to install and do: sudo apt-get install lib6=<version>[/FONT]
[FONT=arial]Probably you added a PPA which updated it, and a bunch of other stuff
[/FONT]
[B][FONT=arial]2.17 is for ubuntu 14.04, I have 12.04[/FONT]
[FONT=arial]sirriffsalothp@HP:~$ sudo apt-get install libc6=2.15[/FONT]
[FONT=arial]Reading package lists... Done[/FONT]
[FONT=arial]Building dependency tree [/FONT]
[FONT=arial]Reading state information... Done[/FONT]
[FONT=arial]E: Version '2.15' for 'libc6' was not found[/FONT]
[FONT=arial]sirriffsalothp@HP:~$ sudo apt-get install libc6=2.17[/FONT]
[FONT=arial]Reading package lists... Done[/FONT]
[FONT=arial]Building dependency tree [/FONT]
[FONT=arial]Reading state information... Done[/FONT]
[FONT=arial]E: Version '2.17' for 'libc6' was not found[/FONT]
[FONT=arial]Long time no see zequence :)

[/FONT][/B]
[FONT=arial]I don't think those were the exact versions[/FONT]
[http://packages.ubuntu.com/precise/libc6](http://packages.ubuntu.com/precise/libc6)
[FONT=arial]seems to be 2.15-0ubuntu10.6[/FONT]
[FONT=arial]so: sudo apt-get install libc6=2.15-0ubuntu10.6[/FONT]
[FONT=arial]but, there will probably other packages that are the wrong version, dependencies, etc
[/FONT]
[B][FONT=arial]E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/FONT]
[FONT=arial]And sudo apt-get -f install gets me back where we were already[/FONT]
[FONT=arial]Namely, E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.[/FONT]
[FONT=arial]E: Unable to correct dependencies
[/FONT][/B]
[FONT=arial]What can I say. You've screwed it up somehow.[/FONT]
[FONT=arial]You could try aptitude. It can sometimes make a difference[/FONT]
[FONT=arial]sudo aptitude install -f
[/FONT]
[B][FONT=arial]Hmm[/FONT]
[FONT=arial]Running a .deb file should not screw my system up, that's all I did since this happened, and this is from winehq[/FONT]
[FONT=arial]I don't have aptitude, and can't install it, lol :)[/FONT]
[FONT=arial]Guess I'll ask in ubuntuforums, hopefully they can dig deeper


[/FONT][/B][FONT=arial][code/]

I'm at a total loss for what to do, and I really would not want to reinstall everything as this is a studio-laptop highly tailored to fit my needs, but if it is broken beyond repair, I guess the day had to come at some point. Any and all help would be greatly appreciated!

Thank you!

SirRiffsAlot

P.S. This is Ubuntu Studio 12.04, but I figured this really applies to Ubuntu at the end of the day, so. [/FONT]

---

### Post by grahammechanical on 2014-08-17
> [COLOR=#000000][FONT=arial]P.S. This is Ubuntu Studio 12.04, but I figured this really applies to Ubuntu at the end of the day, so.[/FONT][/COLOR]

Not really. A specialized Ubuntu like Studio will have libraries or versions of libraries that Ubuntu does not have. As you have 12.04 you should also have Synaptic Package Manager installed by default. Search for the library in Synaptic, select it and right click. A menu will appear that will give the option to Mark for Reinstallation or Removal or Complete Removal. Try it with wine first of all. You will get a list of packages that are also going to be removed.

Regards.

---

### Post by Cheerz on 2014-08-17
Did you even read the whole thing? I've already tried all of that, the first paragraph of my explanation tells you that it is a fruitless exercise. But yeah perhaps I was wrong about the Ubuntu Studio-part. In any case, whatever I use to attempt changing the broken packages, it ends up wanting to uninstall practically my whole system, from Ardour3, to desktop environments, a HUGE list of things that simply should not be removed. Complete removal, repair, removal, reinstallation, all of them result in the same thing: "Packages to be REMOVED: (huge list, no way)"

Cheers!

---

### Post by Cheerz on 2014-08-18
> **grahammechanical said:**
> Not really. A specialized Ubuntu like Studio will have libraries or versions of libraries that Ubuntu does not have. As you have 12.04 you should also have Synaptic Package Manager installed by default. Search for the library in Synaptic, select it and right click. A menu will appear that will give the option to Mark for Reinstallation or Removal or Complete Removal. Try it with wine first of all. You will get a list of packages that are also going to be removed.

Regards.

bump. Hope it's not too soon, but this really is getting in the way of everything :)

---

### Post by sotiris2 on 2014-08-18
Did you add any PPAs? If so can you remove them and try reinstalling libc6 again? If you had other PPAs before and disable them then that could be the problem as well since they may have provided the newer version of lib6 and newer versions of alsa, ardour etc that depend upon libc6's newer version.

---

### Post by Cheerz on 2014-08-20
I tried disabling all of my PPA's, updating and trying to reinstall, completely remove, install other software, et cetera, and the problem is still the same. I removed the Wine PPA, which was my latest addition right before this problem started, which didn't help either.

Any other suggestions?

---

### Post by steeldriver on 2014-08-20
I doubt I can help, but it may help others if you post your current libc6 package(s) status as provided by

```

dpkg -l | grep libc6

```

---

### Post by Cheerz on 2014-08-28
```

sirriffsalothp@HP:~$ dpkg -l |grep libc6
iU  libc6                                   2.17-0ubuntu5.1                                     Embedded GNU C  Library: Shared libraries
iF  libc6:i386                              2.15-0ubuntu10.6                                    Embedded GNU C  Library: Shared libraries
ii  libc6-dbg                               2.15-0ubuntu10.6                                    Embedded GNU C  Library: detached debugging symbols
ii  libc6-dev                               2.15-0ubuntu10.6                                    Embedded GNU C  Library: Development Libraries and Header Files
ii  libc6-dev-i386                          2.15-0ubuntu10.6                                    Embedded GNU C  Library: 32-bit development libraries for AMD64
ii  libc6-i386                              2.15-0ubuntu10.6                                    Embedded GNU C  Library: 32-bit shared libraries for AMD64
sirriffsalothp@HP:~$

         

```

There it is :) That 2.17 package is causing the issues I expect, but I have no idea how to handle it. Anything I try in the commandline returns the same error-message :(

---

