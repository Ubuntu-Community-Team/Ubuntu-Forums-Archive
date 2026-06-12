---
title: "Installing into prepared partitions"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by DrTeddy on 2007-12-18
I have Windows XP in hda1, linux swap in hda5, Suse linux in hda6, and an hda7  partition I want to load 7.04 into already prepared with ext3 filesystem. But installer CD sees none of these partitions, so I can't select the target partitions in the usual way. Is there an obvious way to direct the installer to the prepared partitions hda5 and hda7?

Thanks.

---

### Post by src2206 on 2007-12-18
I have faced this type of issue and weirdly enough, I found that Ubuntu installation CD generally do not prefer pre-made ext3. What I would suggest that as hda7 of your does not contain any data, just delete this partitions using Windows Disk Management feature and then ask Ubuntu installer to mount "/" in this partition and format it likewise.

This should solve your problem.

---

### Post by erginemr on 2007-12-18
> **DrTeddy said:**
> I have Windows XP in hda1, linux swap in hda5, Suse linux in hda6, and an hda7  partition I want to load 7.04 into already prepared with ext3 filesystem. But installer CD sees none of these partitions, so I can't select the target partitions in the usual way. Is there an obvious way to direct the installer to the prepared partitions hda5 and hda7?

Thanks.

I am not sure if this is the right direction, but are you sure that this is not because the live CD has not automatically mounted them and listing their content in Nautilus? Maybe for this reason, the installler (GParted) cannot select them as candidates for a new installation. And you may need to unmount them first.

Again, I may be wrong...

---

