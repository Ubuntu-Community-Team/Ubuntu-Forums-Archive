---
title: "Setting exact swap size in installer"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by latestversion on 2012-12-23
In order to ensure hibernation works I've read that swap partition needs to be at least the same size as physical RAM. I just installed Ubuntu 12.10 using the default install where I don't set up the partitions myself (LVM and full disk encryption enabled) and ran the 'free -m' command and saw the following:```

         total
Mem:     7985
Swap:    8087
```Why did it choose a higher number? Is there a certain amount by which swap partition must be higher than physical RAM for things like hibernate to work, or if I did manual partition setup could I have set swap partition to be exactly 7985 instead of 8087?

I ask because for future installations on a different machine where I need to set up partitions manually during the installation (to have more partitions under root partition), how can I know how much to set the swap size (without it being too much, i.e. I could have set swap to be 10GB even though I know my RAM is only 7-8GB).

---

### Post by darkod on 2012-12-23
Yeah, the only way to set exact size is to use the manual partitiong.

As for the size of swap for hibernation, I don't know the exact value (never really looked for it) but the usual recommendation on the forum is 1.5 x RAM which might be too much, especially if you have loads of ram.

Now, whether you actually need the 150% or you can do with 110-120%, I don't know. I have never really investigated since I don't use hibernation.

---

### Post by necromonger on 2012-12-23
I have 12 gigs of ram and use 4 gig swap.I think any thing over that is to much.

---

### Post by darkod on 2012-12-23
> **necromonger said:**
> I have 12 gigs of ram and use 4 gig swap.I think any thing over that is to much.

Not for hibernation, that the OP is talking about. When going into hibernation it saves everything from RAM to the swap partition on the hdd. That's why it has to be bigger than 100% of RAM.

Otherwise, with 12GB RAM you probably never even use swap but it's better that you have it just in case.

---

