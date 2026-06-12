---
title: "Upgrading to 10.10 but 10.04's update manager thinks I don't have enough space?"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by laeg_ on 2011-01-13
I am trying to upgrade from 10.04 to 10.10 but the update manager reports that I do not have enough space although I have 14 GBs free, as per the screenshot.

How can I fix this?

[IMG]http://oi56.tinypic.com/24c9v9i.jpg[/IMG]

---

### Post by mikewhatever on 2011-01-13
You probably have a separate home partition which has enough free space, but the update manage complains about the root partition, which probably is nearly full. Can you post the output of the **df -h** command to verify the situation.

---

### Post by laeg_ on 2011-01-13
> **mikewhatever said:**
> You probably have a separate home partition which has enough free space, but the update manage complains about the root partition, which probably is nearly full. Can you post the output of the **df -h** command to verify the situation.

You are correct, and I realised shortly afterwards this was the case but unfortunately I was not a home.

Resized the / partition with GParted and I am upgrading at the moment.

Thanks.

---

### Post by mikewhatever on 2011-01-13
Cool. Thanks for updating.

---

