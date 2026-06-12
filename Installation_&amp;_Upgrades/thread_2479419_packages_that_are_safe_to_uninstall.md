---
title: "packages that are safe to uninstall"
date: 2022-09-23
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2022-09-23
is there a list of packages that are critically unsafe to uninstall, as opposed to the *much* larger list that are safe to uninstall?  i can imagine several such packages, but i would want to be sure i have an absolutely complete list.

i once had such a list but i can recall very little about it like what distribution it was for and such.  i know bash was on the list.  i assume apt was on the list.  back then i was trying to make a very tiny system (which did succeed installing other packages back into the system).  today i have a different reason (putting a hard restriction in a script that otherwise might uninstall packages).

---

### Post by mikewhatever on 2022-09-24
No. There isn't a definitive list. It also depends on what one considers safe and unsafe. In my pond, very little is critical or dramatic, as it is easy to reinstall or restore from a backup.

---

### Post by ajgreeny on 2022-09-24
Just bear in mind that when you uninstall anything either using terminal or a GUI app, such as synaptic, you will get a list of all other packges that will be removed.

That list may be very long or could be empty but it gives you a chance to look through the list to see if anything is obviously dangerous looking, not always easy to know as there may be many library packages and it's not easy to know what else they may be needed for.

If in doubt, don't remove packages!

---

### Post by guiverc on 2022-09-24
If I wanted a minimal system, I'd likely examine Xubuntu Core

[https://xubuntu.org/news/introducing-xubuntu-core/](https://xubuntu.org/news/introducing-xubuntu-core/)

I don't see a release being mentioned (*and what is minimal can vary on release*), so assuming it was *jammy*, why not look at the *jammy* Xubuntu Core manifest, ie. [https://unit193.net/xubuntu/core/xubuntu-22.04-core-amd64.iso.manifest](https://unit193.net/xubuntu/core/xubuntu-22.04-core-amd64.iso.manifest)

Yeah it's mostly one person's opinion (unit193), but I've seen discussion on what to include/exclude in #xubuntu-devel I'm positive, so it contains other Xubuntu *developer/members* input too.

Note:   This isn't authoritative;  I'm only providing this in the hopes that's its of use to you, as it's likely something I would explore *IF I WANTED TO EXPLORE PACKAGES SAFE TO UNINSTALL*   (*and my boxes have `xubuntu-desktop` installed** so that's for sure not me!*)

---

### Post by TheFu on 2022-09-24
Packages are changing dependencies all the time, so there isn't any maintained list that is 100% correct.
If you have a system that supports snapshots (LVM, BRTFS, ZFS), then you could make a snapshot, remove a package and see if any ill effects occur.  If there are some, restore from the named snapshot and move on.

I'd probably start with a list of packages created from an lxd ubuntu server for the release I want.  This is about 500MB.  Then I'd create a list of packages from a minimal server install.  Compare those two and see what changed.  A minimal server is less than 2GB.

That's how I'd do it.  I don't know of any easier way. Perhaps someone else does?

If I really wanted 'minimal', I'd start with Alpine Linux.  Think that is 20MB total, but it is painful to use because so many things aren't installed as to make working in bash less than great.  bash-completion is a package worth it to me. I'll accept that bloat.

---

### Post by Skaperen on 2022-09-26
to be safe, it must leave the system in a *rebootable* and *runnable* state.  it must be able to connect to the network to access packages.  it must be able to run a package install tool (GUI or CLI).  it would be a mostly minimal system configuration with possibly more that can be removed.  for example, if the "rm" command were in its own package (it is not) then it could be safely removed.  while the lack of "rm" would be troublesome, it could be re-installed back into the system.  OTOH, removing "bash" could be unsafe even though other shells exist (too much expects it to be there).  removing all the editors could be an interesting issue.

---

### Post by Skaperen on 2022-09-26
> **TheFu said:**
> If I really wanted 'minimal', I'd start with Alpine Linux.  Think that is 20MB total, but it is painful to use because so many things aren't installed as to make working in bash less than great.  bash-completion is a package worth it to me. I'll accept that bloat.i'd want something that can get me to a normal Xubuntu or Ubuntu system by just installing the necessary packages.  e.g. it would need to be using the Ubuntu repository.  it needs to be able to boot up, so it probably needs bash.  i personally can get by with a lesser shell but it would need to let me login.

---

### Post by TheFu on 2022-09-26
I don't think bash is mandatory.  dash is, but not bash.  If it is, that's a huge mistake by the dependency and packaging team.  You can try it by modifying the root passwd entry to use dash instead of bash.  Have a Try Ubuntu environment ready to put it back, should that fail. Really, it shouldn't.  In theory all programs in /usr/ are optional.  Only /sbin/ and /bin/ should be mandated for a booting system.

Sort like how bluetooth became a mandatory dependency for qemu-kvm - makes no sense to me, as I don't use BT anything, but I suppose if your keyboard and mouse are BT, you'd consider it mandatory.  I purged the BT stuff multiple times and it kept being reinstalled.  I didn't purge it and place a hold on the package status. BTW, I removed the BT kernel driver and disabled any BT radios in the BIOS, so reinstalling wasn't going to actually do anything.

If you create an lxd ubuntu-22.04 container, you can use that list of minimal packages as the small number to start.  I think the ubuntu container download is under 80MB, but post install, it becomes around 500MB.  Once made useful, I think my smallest container based on Ubuntu is 932MB.

---

### Post by ian-weisser on 2022-09-27
One old trick is to pick a package and simulate removing it.

```

apt autoremove --simulate <package_name>

```

- No sudo (extra protection)
- Read the output carefully. If the result looks catastrophic, then don't do it for real.

---

### Post by ajgreeny on 2022-09-28
> **ian-weisser said:**
> One old trick is to pick a package and simulate removing it.

```

apt autoremove --simulate <package_name>

```

- No sudo (extra protection)
- Read the output carefully. If the result looks catastrophic, then don't do it for real.
A good idea but it doesn't add anything to what you see without the -s option which tells you what will happen if other packages are to be removed along with the one you specifically asked to remove.

---

### Post by ActionParsnip on 2022-09-28
You could install Ubuntu server then install just the desktop environment you like, but not via the metapackage. You can then install the he login manager (if one isn't installed but is likely to do so) then be fine. This is how I install. Instead of hacking out the fluff I install Ubuntu Server then install openbox, slim and tilda then run from there. Building up rather than down

---

### Post by poorguy on 2022-09-28
I just installed Xubuntu 22.04.1 and chose the minimal install and then removed all of the what I don't need and don't want using Synaptic.

I just take a screenshot of what all packages are being removed prior to cautiously removing them so I can reinstall them if necessary.

I haven't had any problems or issues by doing so however I'm cautious about what I remove and anything I'm uncertain of I leave.

Bottom line for me if I Bork my install not a big deal I'll just reinstall as anything important is already saved to backup drives.

---

