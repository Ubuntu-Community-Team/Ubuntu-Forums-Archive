---
title: "Resize error?"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by Neo2 on 2007-04-08
My first post, yo!
Well, I even have the book by Rick Grant (Ubunto for non geeks) and a cd with 6.0.6 on it si felt confident. Got as far as screen 'step 5 of 6' where according to everyone and their dogs the options should be: resize and use free space, erase ahrd disc, manually edit partition. BUT, being a newbie I wanted option 1 (have no idea about partitions) but would you believe it, it wasn't listed as an option!, just erase and manual were available!!! Help! I have no idea how to manually partition, and when I went that path had a long list of confusing /media/dev type thingies which means nothing to me.

Please help me as I WANT to dump Bill....

Neo

:confused:

---

### Post by spin2cool on 2007-04-08
What exactly are you trying to set up?  Are you deleting your windows installation and going Ubuntu-only?  If so, I'd set up three partitions.  

Partition 1:  ext3  (for your root filesystem - about 15 gigs)
Partition 2: linux-swap (size: about 2x your RAM - 1gb RAM -> 2GB swap, etc)
Partition 3: ext3 (all the remaining space on your HD)

Then mount it exactly where I said - set partition 1 to be your filesystem partition (/) 
Set partition 2 to be your swap partition, and set partition3 to be your /home/ partition.  

Technically, the home partition isn't necessary, but it's nice if you decide to change operating systems, or want to start over.  You'll be able to reinstall your OS to partition 1 without losing all your data on partition 3.

---

### Post by Neo2 on 2007-04-09
Thanks for this, I was brave and had another go anyway, well why not, I can always reinstall windows ;-)) It worked better this time, in fact it detected some free space I had created with Acronis earlier and installed automatically to that. Now I have a problem with the network card Intel 82566 Gigabit which apparently is not supported by Dapper... so back to XP for the time being methinks, unless you (or anyone) knows where to get Linux drivers for this card?

Neo

---

### Post by spin2cool on 2007-04-09
I would advise against running Dapper unless you have a compelling reason to do so.  Edgy is out and very stable, and Feisty is about to hit the stage.  You'll be better off with one of those, so you can take advantage of all the bugfixes, etc.

---

