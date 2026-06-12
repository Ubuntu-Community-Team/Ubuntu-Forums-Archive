---
title: "btrfs, compression and copy-on-write"
date: 2015-08-06
forum: Installation &amp; Upgrades
---

### Post by Gijsbert_Wiesenekk on 2015-08-06
Hi,

I have a 1TB SSD disk that I mainly use for virtualbox images. The ext4 df size of the filesystem is:

$ df /tmp6
/dev/sdb1                  961293640 814660908   97778716  90% /tmp6

Much can be gained from compression because the df size of the LZ4 compressed ZFS filesystem is 500796288 bytes. Performance of the ZFS filesystem became very bad after some time however, I think due to the lack of TRIM support in ZFS for Linux because performance was restored after deleting the ZFS filesystem, creating a temporary ext4 filesystem, trimming it and creating and restoring the ZFS filesystem. I wanted to switch to btrfs because it offers both on-the-fly compression and TRIM support. The recommendation is to switch off btrfs copy-on-write for virtualbox images, so I created the btrfs filesystem, mounted it with compress-force=lzo, disabled copy-on-write on the directory containing the virtualbox images using chattr +C and restored the virtualbox images. The images however were not compressed, as the df size of the btrfs filesystem was the same as the ext4 filesystem. If I do not disable copy-on-write the images are compressed because the btrfs df size became:

$ df /tmp6
/dev/sdb1         976752640 548782700 426115908  57% /tmp6

which is similar to the df size of the LZ4 compressed ZFS filesystem. My questions are:
Does disabling copy-on-write on a directory also disable compression?
If I now disable copy-on-write will updated and new virtualbox images be uncompressed so I will loose compression over time?

Regards,
Gijsbert

---

### Post by dino99 on 2015-08-06
sorry i cant elaborate about your question, but why have chosen btrfs ?
[https://delightlylinux.wordpress.com/2015/03/12/which-is-faster-btrfs-or-ext4/](https://delightlylinux.wordpress.com/2015/03/12/which-is-faster-btrfs-or-ext4/)

---

### Post by Gijsbert_Wiesenekk on 2015-08-06
Because btrfs offers both on-the-fly compression and TRIM support.. Meanwhile I am experiencing poor performance and VM freezes so btrfs does not seem to be ready yet for these types of workloads. I will revert back to ZFS.

Gijsbert

---

