---
title: "Partition size problem"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by typeadam on 2008-01-08
I've been reading several posts regarding the partitions that the installer does but I'm not clear about the resizing part of it. Can anyone help?
I'm installing Kubuntu 7.10 on my notebook, which already has Vista. I have a 120GB drive w/ about 60GB free. I want to designate only 20GB to Kubuntu and leave the rest for Vista. However I'm assuming I have to use option 3 in the installer during the partition option to do this, right?
So what do I set?
I'm attaching an image of the installer to show you what I mean.
If anyone can clarify this for me, I'd appreciate it. Thank you.
Adam

---

### Post by typeadam on 2008-01-08
Does anyone know? Or does everyone use the default partition size?

---

### Post by kshane on 2008-01-08
> **typeadam said:**
> I've been reading several posts regarding the partitions that the installer does but I'm not clear about the resizing part of it. Can anyone help?
I'm installing Kubuntu 7.10 on my notebook, which already has Vista. I have a 120GB drive w/ about 60GB free. I want to designate only 20GB to Kubuntu and leave the rest for Vista. However I'm assuming I have to use option 3 in the installer during the partition option to do this, right?
So what do I set?
I'm attaching an image of the installer to show you what I mean.
If anyone can clarify this for me, I'd appreciate it. Thank you.
Adam

Just do the manual setup and specify the size you want. You can also download the ISO for G-Parted and use it to set the partitions exactly as you want them at any time.  WARNING:  Windows (ANY Windows) does not take kindly to changes in it's own partition.

Kevin

---

### Post by tech9 on 2008-01-08
> **kshane said:**
> Just do the manual setup and specify the size you want. You can also download the ISO for G-Parted and use it to set the partitions exactly as you want them at any time.  WARNING:  Windows (ANY Windows) does not take kindly to changes in it's own partition.

Kevin

gparted works well +1

---

### Post by kshane on 2008-01-08
> **typeadam said:**
> Does anyone know? Or does everyone use the default partition size?

I don't use "default" anything!  :lolflag:

Kevin

---

### Post by typeadam on 2008-01-08
Well I want to do the manual but I'm just not sure how. In the pic I attached there are 3 things I can click on: /dev/sda, /dev/sda1, and /dev/sda2. The one that says sda2 seems to have the largest capacity but what do I click to allocate 20GBs of that for Ubuntu?
Thanks,

---

