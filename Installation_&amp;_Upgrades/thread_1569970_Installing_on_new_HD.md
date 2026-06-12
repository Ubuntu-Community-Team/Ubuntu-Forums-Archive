---
title: "Installing on new HD"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by MaxRift007 on 2010-09-07
Hello everyone,

I'm looking to install a new hard drive and will be loading ubuntu on it as the sole OS, I've done fresh installs on mac's (running Mac OSX) with new HD's but this will be the first time I try this out with ubuntu. I'm going to be doing a fresh install of ubuntu (don't have anything that I really need to back up, so I wont be loading any back up files).

I'll be installing the HD on my old **Dell Inspiron 6400** (which is currently running ubuntu with no issues). I'll be installing **ubuntu from a CD **(v9.10, I'll follow the appropriate upgrade steps from there), so I know I'll have to change the boot sequence in the BIOS, but the one question I can't seem to find the answer to on the net is, do I need to do anything to the HD to prepare it for ubuntu?

Can I just boot to the CD and let her rip, or is there any special formatting that I need to apply to the HD prior to running the install?

Any tips/suggestion would be appreciated.

---

### Post by pricetech on 2010-09-07
You shouldn't need to change your boot order.  Unless Dell did something unusual on your particular model, F12 will get you a boot menu.

Your BIOS should find and autoconfigure the new drive for you.  If not, enter the BIOS and make sure the proper controller is turned on.  If in doubt, just reset to defaults and the BIOS will autodetect which controllers have a drive connected.

No special partitioning ahead of time is needed.  Just let the installer create and format the partitions for you.

---

### Post by MaxRift007 on 2010-09-07
> **pricetech said:**
> You shouldn't need to change your boot order.  Unless Dell did something unusual on your particular model, F12 will get you a boot menu.

Your BIOS should find and autoconfigure the new drive for you.  If not, enter the BIOS and make sure the proper controller is turned on.  If in doubt, just reset to defaults and the BIOS will autodetect which controllers have a drive connected.

No special partitioning ahead of time is needed.  Just let the installer create and format the partitions for you.

Cool, just what I needed to know, thanks

---

### Post by ajgreeny on 2010-09-07
But don't accept the default partitioning as it is much better to have a separate /home partition, particularly in future when and if you perhaps need to do a new clean install of a new version of Ubuntu.

See [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome) for the details.  It is seamless when you are using Ubuntu, you will not notice the difference, but if you need to re-install ever, you will bless the day you made a separate /home.

---

