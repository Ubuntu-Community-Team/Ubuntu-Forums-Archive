---
title: "How to reformat and reinstall while preserving /home?"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by Kurtosis on 2010-03-07
I installed Mythbuntu, got some Wine apps up and running, then discovered my Nvidia DualTV MCE won't work with Myth.  So I'd like to try a different variant, either the plain vanilla Ubuntu or UbuntuStudio.

Can I just use Mythbuntu to create a new partition, move /home/* to it, and then reformat and install over the original Mythbuntu partition?  

When I reinstall the new version, how do I tell the installation process to use /home on the other partition (without overwriting it) instead of creating a new one from scratch?

Thanks!

---

### Post by woodmaster on 2010-03-07
[COLOR=#008000]Your answers should be here:[/COLOR]
[COLOR=#008000][/COLOR] 
[COLOR=#008000][www.**psychocats**.net/ubuntu/**separatehome]("http://www.psychocats.net/ubuntu/separatehome")**[/COLOR]

---

### Post by oldfred on 2010-03-07
If you use manual partitioning on the normal install it lets you specify which partitions to use for root (/), swap & /home if you want. You also specify format like ext3 or ext4 and for /home you must specify do not format.

---

### Post by Kurtosis on 2010-03-08
> **woodmaster said:**
> [COLOR=#008000]Your answers should be here:[/COLOR]
[COLOR=#008000][/COLOR] 
[COLOR=#008000][www.**psychocats**.net/ubuntu/**separatehome]("http://www.psychocats.net/ubuntu/separatehome")**[/COLOR]
Perfect, thanks.

---

### Post by Kurtosis on 2010-03-08
> **oldfred said:**
> If you use manual partitioning on the normal install it lets you specify which partitions to use for root (/), swap & /home if you want. You also specify format like ext3 or ext4 and for /home you must specify do not format.
Thanks, I'm aware of that, it just didn't occur to me to do that when I installed.  Now I wish I had.  Note to self - always install /home to its own partition.

---

