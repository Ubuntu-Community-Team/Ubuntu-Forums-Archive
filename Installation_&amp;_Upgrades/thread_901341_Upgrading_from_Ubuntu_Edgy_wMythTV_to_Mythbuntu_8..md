---
title: "Upgrading from Ubuntu Edgy w/MythTV to Mythbuntu 8.04..."
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by kpatz on 2008-08-26
I built a MythTV box a couple years ago that is (still) running Edgy 6.10.  On my to-do list is to upgrade this box to Hardy, and upgrade the MythTV to the latest version.

This box is already tweaked, and has programs recorded on it, which I don't want to lose.  So I'm debating whether to install Ubuntu Hardy and then install MythTV separately, or to start over using Mythbuntu.

I plan on backing everything up before doing the upgrade, including the MySQL databases.  Is it possible to load a database from MythTV 0.20.2 into a MythTV 0.21 or Mythbuntu 8.04 install?  According to the MythTV site, database updates are applied automatically, but I'm just wondering if anyone has tried it.

Basically, I would back up the database and media files (which are on a separate partition), install Mythbuntu, then restore the database over the one created on install.

Thoughts?  Has anyone done this?  Tips?

TIA...
KJP

---

### Post by .nedberg on 2008-08-26
I did a KnoppMyth -> Mythbuntu Feisty -> Mythbuntu Hardy update a while ago.

From KnoppMyth I did as you describe (backup data + database). I then installed Mythbuntu and loaded the database and recordings.

Here is a link to a thread I started when I changed from KnoppMyth to Mythbuntu.
[http://ubuntuforums.org/showthread.php?t=609564](http://ubuntuforums.org/showthread.php?t=609564)

Feisty -> Hardy was just a walk in the park with no problems.

You should be able to do a normal upgrade to Feisty, then to Hardy. But still backup everything!

A new install of Hardy would be a bit more work, but it might be worth it...

---

