---
title: "Will update wipe out all my data?"
date: 2020-01-21
forum: Installation &amp; Upgrades
---

### Post by Donnie Love on 2020-01-21
I want to update to the latest version, but I don't know if that will completely wipe the hard drive or is my data safe?

---

### Post by kurt18947 on 2020-01-22
Upgrading shouldn't wipe out your data but I would certainly have at least one backup that I knew would restore before beginning an upgrade. I don't usually back up my entire install, I just backup Thunderbird and /home, documents, pictures etc. I use Firefox sync so there's bookmarks & add-ons. One recommendation before starting an in-place upgrade, uninstall any 3rd party drivers such as Nvidia video and disable/purge any ppa's.

Experienced types sometimes have a separate /home partition so the O.S. can be deleted and reinstalled without having to touch the data. I've not tried it so can't say if it's a good idea or not. I did do something similar when using Windows, keeping my data in a separate partition and that did save significant data loss when Windows got corrupted. Some experienced types are also skeptical of in-place upgrades, preferring to wipe & re-install. I hope others will be along to add their experiences and recommendations.

---

### Post by tea for one on 2020-01-22
> **Donnie Love said:**
> I want to update to the latest version, but I don't know if that will completely wipe the hard drive or is my data safe?

Which version and flavour of Ubuntu are you using?

Your machine details would also be relevant?

---

### Post by ajgreeny on 2020-01-22
> **tea for one said:**
> Which version and flavour of Ubuntu are you using?

Your machine details would also be relevant?
Agreed!

From which version to which new one?

I would also suggest that you ***MUST*** make a backup of all your personal files before trying a reinstall, upgrade, or clean install of a newer version; in fact you ought to be sure to keep backups all the time (see my next paragraph).  I am one of those users who for many years has used a separate partition for /home and it does save a great deal of potential trouble when moving from version to version.

However, it is possible to wipe out files and folders from your personal data simply by inadvertently hitting the wrong key or a bad terminal command, (I've done it myself once only, thank goodness but it was easily recovered as I always have regular backups of everything in my home), so if you don't have backups which are up to date, do it now before anything else.

---

### Post by Donnie Love on 2020-01-22
I'll be upgrading from Lubuntu 14.04.5 LTS to the latest version of the same.

You've all expressed the same concern I have. Believe me, I want to back up my data. If I could do that, I wouldn't have even asked this question. But there's about 400 gigabytes and I have nowhere to put it. I'd like to start with a fresh clean hard drive, but budgetary constraints prevent it. I need to update right away because the old version just doesn't work anymore.

I should also mention I'm not a tech guy and I have no one to help me. I have no idea what I'm doing. I like the partition idea, but I'm definitely not the experienced type.

---

### Post by tea for one on 2020-01-22
> **Donnie Love said:**
> I'll be upgrading from Lubuntu 14.04.5 LTS to the latest version of the same.

You've all expressed the same concern I have. Believe me, I want to back up my data. If I could do that, I wouldn't have even asked this question. But there's about 400 gigabytes and I have nowhere to put it. I'd like to start with a fresh clean hard drive, but budgetary constraints prevent it. I need to update right away because the old version just doesn't work anymore.

I should also mention I'm not a tech guy and I have no one to help me. I have no idea what I'm doing. I like the partition idea, but I'm definitely not the experienced type.

Lubuntu 14.04 is unsupported now, so you will not be able to upgrade to a newer version in situ.

Without a **backup**, anything you attempt will run the risk of losing all **your personal data**.

If your budget constraints do not allow you to purchase a suitable backup device, then you may have to resign yourself to losing your data.

Even if you are unable to backup now, clearly you will want to do this in the future, therefore consider everything carefully.

I would be very reluctant to offer suggestions with the knowledge that my help could inadvertently remove your personal files.

---

### Post by dragonfly41 on 2020-01-22
[COLOR=#000000]> But there's about 400 gigabytes and I have nowhere to put it. I'd like to start with a fresh clean hard drive, but budgetary constraints prevent it.

Do you have any old computers lying around where a drive can be pulled out to use that drive in a USB container (after formatting)?
You can go to a PC recycling base and pickup some old drives until you can afford to buy some new (and more reliable) devices.[/COLOR]

---

### Post by Donnie Love on 2020-01-22
Yes, I tried to use one of my old hard drives. Unfortunately they are all very old and none of them have the SATA connection, except one and for some reason my monitor won't work with it.

I think my only option is to wait and hope that someday I can afford to buy a new hard drive.

---

### Post by TheFu on 2020-01-22
This is a high-risk operation.  Non-experts are likely to wipe all their data by making a mistake.  

If it was me in your shoes, I wouldn't attempt it until I had gotten the data I need to keep backed up.  500G disks are $25 around here.

In the next install, split off /home/ into a separate partition so upgrading isn't as risky.  However, great care must be taken even then to ensure an accidental toggle to "format" the partition isn't selected/defaulted and all the data gets wiped.

Heck, you've been on 14.04 over 3 years support ended. What's another month if you need to save $20 for a backup disk?

The safest way to move to a new release that I know is to swap disks. Leave the old disk disconnected. Do a fresh install on the newly installed disk, then copy over data from the old one.

The way I do a new release install is to use my existing backups.  I do a fresh install, then follow my normal restore process for previously taken versioned backups.  This does 2 things.  I get a fresh install without any cruft left over and I get to validate the restore process is working at my leisure, not when it is critical that the system be available for work.

The move from 14.04 to 18.04 Lubuntu has huge changes. HUGE.  Someone like you shouldn't be using a non-LTS release. Those only have months of support.  In 3 months, 20.04 Lubuntu will be released.  That swaps LXDE for LXQt - a complete change in DE. Big change.  Not something I'd overlay - definitely want a fresh install.

But it is your system, your data, your risk.

---

### Post by Donnie Love on 2020-01-22
Yeah, I want to do as you've suggested, start with a new hard drive. I didn't know hard drives had come down in price. I thought they were still hundreds of dollars. That's good to know. Thanks.

---

### Post by TheFu on 2020-01-22
> **Donnie Love said:**
> Yeah, I want to do as you've suggested, start with a new hard drive. I din't know hard drives had come down in price. I thought they were still hundreds of dollars. That's good to know. Thanks.

A cheap 500GB SSD is $50. A quality one is $70. With SSDs, quality actually matters for longevity.  A Samsung 860 for $70 should last 8+ yrs for most people and make storage performance at least 3x faster than spinning disks.  It is the cheapest upgrade for any system that actually accomplishes the most performance gain for most situations.

I picked up a slightly used 250GB WD-Blue for $10 at Microcenter about 18 months ago. It was needed for a very specific need or I would have gotten a 2TB.  That's sorta my min these days.  Quality 2TB runs $60 on sale. I just searched and found a cheap 2.5inch (slow) 2TB HDD + enclosure for $31.  Fine for backups, but not good for running an OS.  External enclosures powered only by USB are really, really, really, slow.

---

### Post by Donnie Love on 2020-01-23
I kind of hate to say this, but I need longevity in an operating system. My hard drive is working perfectly. But it is old, so now is as good a time as any to replace it. And it will serve as a backup for my data, which I also need.

---

### Post by hurtstotalktoyou on 2020-01-23
> **Donnie Love said:**
> I want to update to the latest version, but I don't know if that will completely wipe the hard drive or is my data safe?

Not if you know what you're doing, no.  **However**, since you're asking, that means you're new at this, and had better take precautions.  So, definitely back up any important data.  Hopefully you won't need it.

If everything goes well, next time you can take fewer precautions, because you'll be experienced : )

---

### Post by hurtstotalktoyou on 2020-01-23
> **TheFu said:**
> A cheap 500GB SSD is $50. A quality one is $70. With SSDs, quality actually matters for longevity.  A Samsung 860 for $70 should last 8+ yrs for most people and make storage performance at least 3x faster than spinning disks.  It is the cheapest upgrade for any system that actually accomplishes the most performance gain for most situations.

I picked up a slightly used 250GB WD-Blue for $10 at Microcenter about 18 months ago. It was needed for a very specific need or I would have gotten a 2TB.  That's sorta my min these days.  Quality 2TB runs $60 on sale. I just searched and found a cheap 2.5inch (slow) 2TB HDD + enclosure for $31.  Fine for backups, but not good for running an OS.  External enclosures powered only by USB are really, really, really, slow.

Last I checked, Hitachi made the most reliable HDDs, whereas Western Digital and other mfctrs had seriously high failure rates.  Not sure if that's still the case.

Also, I wouldn't buy a used HDD since they're not all that cheaper but you don't know how they've been used/abused.

---

### Post by TheFu on 2020-01-23
> **hurtstotalktoyou said:**
> Last I checked, Hitachi made the most reliable HDDs, whereas Western Digital and other mfctrs had seriously high failure rates.  Not sure if that's still the case.

Also, I wouldn't buy a used HDD since they're not all that cheaper but you don't know how they've been used/abused.

That was 5+ yrs ago when Hitachi was noticeably better and data is really only available for huge disks currently - 8TB and larger.  I've had 2 Hitachi 4TB disks fail in the last 5 yrs.  All my Seagate 2TB disks (over 320G) in size have failed, usually just after the 1 yr warranty expired.  I have about 6 Seagate 320G disks from 2005-ish which are all going strong. All we can really do for storage is 
a) monitor SMART data weekly (look for any changes), but know that 22% of the time a disk fails, nothing is shown in the SMART data.
b) have excellent, automatic, daily, versioned, backups <---- this should go without any need to say.
c) storage of all types fail all-the-time.  Having backups means it is a slight inconvenience instead of massive data loss. It doesn't matter if the storage is MicroSD, USB3 Flash, typical SATA HDD, or SSD - they all fail.  I've seen cheap SSDs fail in a little over 18 months. Not all SSDs are the same.  Look at the published endurance specs. Any vendor who doesn't publish those is hiding something. Beware.

Spinning disks smaller than 1TB are getting harder to find because SSDs have taken over that market segment.
The HDD data is published quarterly by Backblaze. Since they are a cloudy storage company, they don't want tiny HDDs. They need huge storage drives.  [https://www.backblaze.com/b2/hard-drive-test-data.html](https://www.backblaze.com/b2/hard-drive-test-data.html)

---

