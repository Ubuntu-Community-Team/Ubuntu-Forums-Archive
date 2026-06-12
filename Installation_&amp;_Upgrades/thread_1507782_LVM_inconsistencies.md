---
title: "LVM inconsistencies?"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by pft42 on 2010-06-12
Hi,

after all I recently converted my home server from opensuse to ubuntu (10.04LTS).
I reinstalled system on root partition and then mounted exisiting LVM partitions for home and a couple of others.

What really scares me at the moment is that even with proper shutdown ("sudo reboot" - no crash) I get lots of transaction replays.
According to logs (mainly boot.log) it was only 3 partitions all with reiserfs and ~200 transactions replayed each but from what I saw during boot it was more partitions and more transactions.

So my qustions:
Where do these replays come from? From my understanding they should not be there after a clean shutdown.
Are there any issues with LVM partitions setup with opensuse and used with ubuntu?
Are there any dependencies with file systems used? I use ext3, reiser and XFS on various lvm partitions.
Where can I safely get the logs for all replayed transactions?

---

