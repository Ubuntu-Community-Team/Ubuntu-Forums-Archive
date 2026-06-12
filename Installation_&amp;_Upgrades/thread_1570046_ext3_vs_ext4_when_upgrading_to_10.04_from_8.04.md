---
title: "ext3 vs ext4 when upgrading to 10.04 from 8.04"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by emakarov on 2010-09-07
Hello,

I am going to do network upgrade of my 8.04 to 10.04 LTS. I have a dual boot with Vista, and currently I can read Ubuntu partition from Vista using Ext2fsd. However, I read that using Ext2fsd with ext4 (default in 10.04) is problematic because of "extents".

My questions: Will the upgrade convert my current ext3 partition into an ext4 one? How can I keep the ext3 partition? The release notes for 10.04 say:
> The simplest way to select a different file system such as ext3 at installation time is to add the partman/default_filesystem=ext3 boot parameter when starting the installer.How do I do this, in particular, during an *upgrade*?

Also, if anyone has the latest news on Ext2fsd working with ext4 with extents, this would be appreciated.

Thank you,
Evgeny

---

### Post by plucky on 2010-09-09
If you do an upgrade from 8.04 to 10.04,it doesn't format you partitions to ext4,it will stay as ext3.

If you want ext4,you will have to do a clean install and select ext4 when it comes to partitioning question.

Good Luck

---

