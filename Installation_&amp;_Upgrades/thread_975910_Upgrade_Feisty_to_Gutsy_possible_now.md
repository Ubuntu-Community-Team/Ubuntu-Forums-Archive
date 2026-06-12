---
title: "Upgrade Feisty to Gutsy possible now?"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by dwiedenfeld on 2008-11-08
OK, so I've been using Feisty since about when it came out--my first experience with Linux. HAve been happy with it.

Last week I heard that support would be ended for Feisty. I knew it wasn't an LTS version, but that didn't mean much to me before. But now I decided I had better upgrade to Hardy.

Tried it now, and it doesn't seem to work. First problem seems to be that medibuntu has changed its name. I think I got that fixed (?).

But when I looked in the packages archive at medibuntu, it says Feisty has been removed. Gone! 

Does that mean that I can't upgrade to Gutsy at all? Will I have to do a clean install?  I don't want to do that. I have a dual boot system that I'm not confident of not losing something.

---

### Post by Partyboi2 on 2008-11-11
Medibuntu is only a 3rd party repo  and should not effect your upgrade to gusty as long as it is disabled. You will need to go into Software Sources and disable all 3rd part repos before upgrading.

---

### Post by tommcd on 2008-11-11
> **dwiedenfeld said:**
> 
Last week I heard that support would be ended for Feisty. I knew it wasn't an LTS version, but that didn't mean much to me before. But now I decided I had better upgrade to Hardy.

The title of your thread is upgrading Fiesty to Gutsy, but here you say Fiesty to Hardy. Is this a typo, or are you trying to go from Fiesty --> Hardy?
Upgrading from Fiesty to Hardy, while skipping Gutsy, may cause problems. It is recommended that you only upgrade in sequence. That is Fiesty > Gutsy > Hardy. See this:
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)
Personally, I would just do a clean install. It will likely be faster, and with much less chance for breakage. 
If you do a clean install, choose manual partitioning. Pick your root and swap partitions. Choose to format root and swap, and install Ubuntu to the root partition. Just don't format your Windows partition. If you have a separate /home partition, set the mount point for that as /home, but do not format it. The rest is all automatic.

---

