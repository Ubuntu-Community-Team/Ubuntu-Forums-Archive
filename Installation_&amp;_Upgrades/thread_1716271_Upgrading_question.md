---
title: "Upgrading question"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by linuxn3wbie on 2011-03-28
I heard there's a new Ubuntu version coming out next month; Will I be able to upgrade from 10.10 to 11.04, or will I have to reinstall Ubuntu entirely? Seeing as I'm a new Ubuntu user, I don't know whether Ubuntu offers upgrades.

Thanks in advance!

---

### Post by ~Plue on 2011-03-28
the update manager would offer an upgrade option. however, i'm not sure how smooth it would be (gave me some trouble the last time i tried)

---

### Post by Sean Moran on 2011-03-28
> **linuxn3wbie said:**
> I heard there's a new Ubuntu version coming out next month; Will I be able to upgrade from 10.10 to 11.04, or will I have to reinstall Ubuntu entirely? Seeing as I'm a new Ubuntu user, I don't know whether Ubuntu offers upgrades.

Thanks in advance!
I've never tried it.  I just install every distro from fresh because I have lots of time to spare and like to keep up the practice, but whenever I open System->Administration->Update Manager, I get a message at the top telling me:

New Ubuntu release 10.04.1 LTS is available  [Upgrade]

I don't think it would hurt, but my computer would be upset with me if I ever gave her so much disrespect as to not install a new distro fresh and clean, but only an upgrade.  If I treated her like that, she'd probably have an hard disk failure, or worse, just to spite me.

---

### Post by Pumalite on 2011-03-28
You can; but I'd prefer a new install. If you choose the former; update your system to the last minute and then leave your sources.lst as simple as you can. No Partner, Medibunto, etc. No third sources

---

### Post by PSBTornado on 2011-03-28
You will be offered the update at the end of April at this stage in Update Manager. I tend to hang back at least a week or two and read on here if peeps are having issues. The more knowledgeable Ubuntu users normally work around the issues quickly and offer suggested fixes.

You can Press Alt+F2 and type
 > update-manager -d 
in the box to get the update in update manager early. But I don't due to reasons stated above

---

### Post by Frogs Hair on 2011-03-28
I like a clean installation . I don't know how well  upgrades work because only the problems are reported here. I would rather deal with one operating system at a time rather than a mix of two.

---

### Post by linuxn3wbie on 2011-03-31
Thanks for the answers.
I'll wait a month or two months after the new version gets released, and then go for a clean install. :)

On an entirely different kind of note (just so I don't have to open another topic, I don't like spamming the forums with my newbie questions but I tend to have a lot of them :D ): Linux just checked my hard drives for errors upon booting. I shut it down correctly yesterday. Does Ubuntu do this on a weekly basis, or did I do something wrong?

---

### Post by ssulaco on 2011-03-31
> **linuxn3wbie said:**
> I heard there's a new Ubuntu version coming out next month; Will I be able to upgrade from 10.10 to 11.04, or will I have to reinstall Ubuntu entirely? Seeing as I'm a new Ubuntu user, I don't know whether Ubuntu offers upgrades.

Here is some info on upgrades:       [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
I recently upgraded from 8.04 to 10.04,it was smooth,no problem,I did disable proprietary drivers and PPA's.

---

### Post by ssulaco on 2011-03-31
> **linuxn3wbie said:**
>  Linux just checked my hard drives for errors upon booting. I shut it down correctly yesterday. Does Ubuntu do this on a weekly basis, or did I do something wrong?
its called "fsck". equivalent to MS "chkdsk"
[http://manpages.ubuntu.com/manpages/intrepid/man8/fsck.8.html](http://manpages.ubuntu.com/manpages/intrepid/man8/fsck.8.html)
I believe fhe fsck is set to run every 30 boots and or will also run if it detects file system corruption due to non-graceful shutdown, such as a crash or power loss.

---

