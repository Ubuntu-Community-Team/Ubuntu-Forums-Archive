---
title: "Moving Ubuntu Partition and Grub"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by RMOP on 2011-06-03
I've got XP installed on one physical HD, and Ubuntu on another. Pre-2.0 Grub is installed on the Ubuntu partition (/dev/sdb5).

I used the following command to clone my Ubuntu partition:

**sudo dd if=/dev/sdb5 of=/dev/sdb3**

This command ran as expected and created a new partition at the beginning of the drive where Ubuntu was already installed.

I want to:

1) Update grub (currently on dev/sdb5) to include the cloned partition in the boot menu.

2) Ensure that I can boot to the new partition and that the environment is identical to the one from which it was cloned

3) Move grub to /dev/sda3 and delete it from /dev/sda5

4) After checking that I can boot to the new Ubuntu partition, DELETE the original Ubuntu partition

5) Re-size the remaining Ubuntu partition to include the newly-deleted partition.

I think this is as easy as it sounds, but would appreciate any comments and gotcha notices! Thanks.

---

### Post by oldfred on 2011-06-04
Best to document where everything is at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

