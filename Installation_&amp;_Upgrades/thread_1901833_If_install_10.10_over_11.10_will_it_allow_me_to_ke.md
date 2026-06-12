---
title: "If install 10.10 over 11.10 will it allow me to keep my files?"
date: 2011-12-29
forum: Installation &amp; Upgrades
---

### Post by Shvesley on 2011-12-29
If install 10.10 over 11.10 will it allow me to keep my files? Or will I have to back them up and start a new?

---

### Post by squenson on 2011-12-29
Always do a backup before an upgrade or a downgrade!!!

---

### Post by jerrrys on 2011-12-29
Yes, you need to backup and reinstall.

---

### Post by MARP1961 on 2011-12-29
Although it is always sensible to back up important files it is possible to avoid having to reinstate all your files and redo all your settings if you have your Home Folder on a separate partition.

**When you reinstall in future** you can choose the manual partitioning option by selecting 'Do Something Else' during installation. You will need a system partition for Ubuntu of around 12GB (Ext 4 Journaling File System , Mount Point:  /). Then you create a separate home partition, with as much space as you can afford (Ext 4 Journaling File System, Mount Point: /Home). Finally allow around 2GB for a SWAP partition. If you install like this it is easy to keep all your settings and files. 

When you eventually want a new install you go back to the manual partitioning and make sure you only allow the 'new' Ubuntu to format and install over the old one on the **/ partition.** Make sure you set all the mount points and ext4 file system options as before but** do not format** the** /Home** partition (or any ntfs Windows partitions you want to keep).

I understand that this doesn't help you this time around, particularly as the 10.10 installer doesn't give you the option of retaining the settings and files. Interestingly I think 11.10 does give the option of 'Upgrading' in the installer. Short of copying all your files to a spare USB, Hard Drive or DVDs I'm not sure what else you can do.

---

### Post by MARP1961 on 2011-12-29
Why do you want to go back to 10.10 anyway? If you don't like the new Unity interface then try installing Gnome Shell via the Software Centre or perhaps Xubuntu or Lubuntu desktop environments. There are options to try before giving up and downgrading to versions that will soon be unsupported.

---

