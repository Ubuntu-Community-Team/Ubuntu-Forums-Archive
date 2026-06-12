---
title: "Continued upgrades, where do old replaced file go ?"
date: 2023-07-11
forum: Installation &amp; Upgrades
---

### Post by BrassCat on 2023-07-11
Hello the forum. 4 months into ubuntu. I do perform suggested upgrades,
adds up to a lot of file space. Do these upgrades remove the older file it
is replacing ? Else, how to I clean up the older unused files ?

Thanks, Stan

---

### Post by TheFu on 2023-07-11
Most upgrades remove the installed versions, but there are also cached versions of packages retained for some period.  Whether they are removed or not depends on the front-end you use and the specific command for the package manager.

If you want to clean everything for the same OS release, after running your patching, run
```
sudo apt autoremove
sudo apt clean
```

I find this is to be a bit agreesive and prefer to have some packaged cached which are still reference, and have the older versions removed.  That's these to commands:
```
sudo apt autoremove
sudo apt autoclean
```

If you want more details, the manpage (i.e. command documentation) on your system spells out which options exist for every command and what they are supposed to do. It is generally correct.

apt is a little different than most commands. Some of the documentation is placed into the apt-get manpage.
```
$ man apt-get
....
       autoclean (and the auto-clean alias since 1.1)
           Like clean, autoclean clears out the local repository of retrieved package files. The difference is
           that it only removes package files that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it growing out of control. The
           configuration option APT::Clean-Installed will prevent installed packages from being erased if it is
           set to off.

       autoremove (and the auto-remove alias since 1.1)
           autoremove is used to remove packages that were automatically installed to satisfy dependencies for
           other packages and are now no longer needed.
...
```
that's for the version of the software on my system. Your system might be different. It is always best to check the local manpages, since those are tied to the exact version of the command you have installed - not the version I have installed.  Commands can change from release to release. I'll leave looking up the "clean" option in the manpage to you.

As the manpage says above, it is possible to have a system-specific setup for the behavior of the entire APT subsystem. Sometimes this is good, but most users don't bother and stick with the defaults.  I've only screwed with the defaults for APT when the system was extremely limited for total storage or it was running entire without any local storage at all.

---

### Post by guiverc on 2023-07-11
I'll recommend reading and taking in what TheFu has written; it's excellent.

I'm using a *development* release, and use this system to look for issues with any new packages that are received (*checking for upgrades at least three times per day*), so my usage is more aggressive than I'd expect from most users, however my upgrade command is 

```

sudo snap refresh; sudo apt update; sudo apt full-upgrade ; sudo apt autoclean; sudo apt autoremove; neofetch

```

You'll note it includes both *autoclean* & *autoremove* as suggested by TheFu, though including it every time I check for upgrades would be uncommon I suspect for normal users. FYI: The use of `neofetch` is only as I find the final color squares that will remain in my window a useful visual reminder of why the command was run (I wouldn't type neofetch if I actually did an apt install/remove etc)

---

### Post by TheFu on 2023-07-11
BTW, some years ago, I wrote an article about maintaining Ubuntu Desktop systems that was picked up by a popular tech/life blog.  I've updated it over the years: 
[https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) is my updated 2021 version.  

For most users, it comes down to 2 things:
* have backups, at least weekly and at least 4 versions
* patch the system weekly

Most of the rest in the article isn't really needed with a current Ubuntu Release. Standard stuff should clean it well enough unless you have a limited storage system, say under 100GB total for everything, not counting media files.  For older releases and certain advanced storage layouts, cleaning out kernels needed to be done much more often. A fresh install will make sufficient space for these areas so it isn't an issue like it was previously. Upgraded releases often run into issues with limited space in these smaller areas. Bad things happen if the user isn't very, very, careful.

Here's a link to the version they grabbed initially: [https://lifehacker.com/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc-5817282](https://lifehacker.com/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc-5817282)

---

