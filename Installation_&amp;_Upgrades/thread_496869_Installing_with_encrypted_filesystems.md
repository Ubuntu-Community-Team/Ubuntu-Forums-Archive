---
title: "Installing with encrypted filesystems"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by sy1234 on 2007-07-09
Hello,

I tried to install via debian-installer. I first setup three physical drives in a RAID5 sw configuration. On top of this I installed LVM to use the RAID'ed partition in a volume group, and I setup various logical volumes on this. All this according to the pretty good [installation guide]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/amd64/index.html") (for 6.10, even though I am actually installing 7.04 for AMD64) and everything works like a charm. But then I am stumped. I would like to have the logical volumes be encrypted. According to the same installation manual, this shouldn't be a problem. From reading it appears I should just select a logical volume in the partition menu, and then just select "physical volume for encryption" in the "use as:" option. But...there is no "physical volume for encryption" for me?! ;_;
I can only select the usual "ext3", "jfs" etc filesystems...

Anyone have any idea what's going on here? Am I missing something?

Thankful for any help...

EDIT: I realized I should try without the RAID and LVM stuff, and even for a completely raw harddrive, I still don't get any "physical volume for encryption" option?!

---

### Post by sy1234 on 2007-07-10
Does the 7.04 installer in fact not have support for encrypted filesystems?

Can I enable encryption after the installation some how? Or can I setup the partitions before I start the installation?

Thankful for ANY answers here...

---

