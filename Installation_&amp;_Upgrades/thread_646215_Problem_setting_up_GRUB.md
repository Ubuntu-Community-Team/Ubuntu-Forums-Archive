---
title: "Problem setting up GRUB"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by Qooroo on 2007-12-20
Alright, so I installed Ubuntu. And it's great. Supporting my WoW addiction demanded installing Windows on a separate partition, which I did, and that worked fine. I started running into problems when I wanted to reinstate Grub to allow me to chose which OS to boot. 

I followed the instructions on this link: [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp) 

Now, whenever I try to boot off my hard drive I get an error at the following section:

Checking file systems...
fsck 1.40.2 (12-July-2007)
fsck .ext3:unable to resolve 'UUID = 5dd58cfe-615f-42b3-905b-2f27b19337d0'
fsck died with exit status 8


I am, needless to say distressed. And have heard tell of the wonderful helpfulness of this forum, so I'm hoping for good things.

Thanks in advance :)

---

### Post by PmDematagoda on 2007-12-21
Could you post the results of:-

```
cat /etc/fstab
```
and
```
sudo blkid
```

---

