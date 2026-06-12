---
title: "can I upgrade from my H.Heron to the new release?"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ieBrazil on 2008-10-23
I don't know... I'm a new user and I'm not sure about upgrading ...

My quest: is it possible (and do you advice my to) upgrading from my Hardy Heron to the new release? My LTS version is amongst the ones that are possible to be upgraded?

Tnx!



ieBrazil

---

### Post by geirha on 2008-10-23
Yes, though I recommend you wait till it is out of beta and officially released. This page should be completed by then, and provide the necessary instructions on how to upgrade to Intrepid from Hardy: [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

---

### Post by evilkastel on 2008-10-23
I'll wait a few days yet, and keep in mind that a few times, there are problems upgrading. So is unlikely but possible. If you have your /home in the same partition than /, proceed with caution.

---

### Post by Comhra on 2008-10-23
> **geirha said:**
> Yes, though I recommend you wait till it is out of beta and officially released. This page should be completed by then, and provide the necessary instructions on how to upgrade to Intrepid from Hardy: [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

I thought the RC was released today?

---

### Post by geirha on 2008-10-23
> **Comhra said:**
> I thought the RC was released today?
Ah, yes, it's scheduled for today. I should rather have said to wait for the final release. I consider a release candidate a sort of beta version.

---

### Post by ieBrazil on 2008-10-23
oh yea, I'll wait some months ... after I up grade. Sure!

Thank you all.

---

### Post by Daimoneze on 2008-10-23
> **ieBrazil said:**
> oh yea, I'll wait some months ... after I up grade. Sure!

Thank you all.

Months won't be necessary. Final will probably be released in the next few days. Likely to still have a few bugs, but final none-the-less.

---

### Post by tubezninja on 2008-10-23
Even once the final release is out there, I would **still** wait a couple of days to a week to upgrade.  The mirrors and package distribution servers are typically *hammered* just as a new release comes out, and it can take several tried to get the upgrade to work successfully.

Once the furor over the release dies down in a week or two, then contacting the servers for upgrades will be much less trouble prone.

---

### Post by henwyn on 2008-10-23
I have upgraded H.H. to testing versions of Ibex with mixed results; the problems show up in video and sound and occasionally in networking. They seem to be caused by old versions of some programs or unnecessary programs being left in place. If it isn't too much trouble a new installation is usually less trouble and often faster.

If your home directory is not on a separate partition, I would prepare for installing by creating a new (large) partition, (because your /home directory with all your files and the /var directory with the log files are the two things that grow and can fill up a partition, making it impossible to boot). Then copy your current /home directory to the new partition. When you install the new distribution, choose custom partitioning, choose that directory as your /home directory and do **_NOT_** format it. 

Depending on how much space you have, you can then either make a new partition for your root file system or install over the top of your current partition. In either case, the partition you install / to has to be formatted, erasing any data on it.

The main point of this is that it is a lot easier to upgrade if your /home directory is on a seperate partition. I have four different installations of Ubuntu/Kubuntu on this box, all sharing the same /home directory. HTH

---

### Post by forumache on 2008-10-24
> **ieBrazil said:**
> oh yea, I'll wait some months ... after I up grade. Sure!

Thank you all.

Wait six months... and you can upgrade to Jaunty Jackalope (Ubuntu 9.04) or one year to upgrade to Kicking Kangaroo (or whatever name release 9.10 will get) ;)

P.S. Karmic Kookaburra anyone?

---

