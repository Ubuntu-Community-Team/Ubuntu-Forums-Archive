---
title: "Is possible install Lubuntu in a BTRFS parition ?"
date: 2020-07-29
forum: Installation &amp; Upgrades
---

### Post by aug7744 on 2020-07-29
How install Lubuntu in an BTRFS partition in an disk being MBR and having only available one partition ?
Thanks for reply.

---

### Post by slickymaster on 2020-07-29
*Thread moved to **Installation & Upgrades**.*

---

### Post by guiverc on 2020-07-29
Use *Manual Partitioning*, create or select your partition, select *format* and then you can change the *file system type* which includes options of BTRFS, XFS and other file types.

BTRFS is in the tested *file system types* in Lubuntu Quality Assurance tests, and has been for a couple of releases.

I last used it yesterday (2020-07-28), and did it on a MBR partition table machine using Lubuntu 20.04.1 LTS in a QA-test.

For more details see [https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)

The *file system* entry is shown in the last picture on that page (where the image shows *ext4*, the drop-down is changed to BTRFS)

---

### Post by aug7744 on 2020-07-30
Thanks for replies. Lubuntu 20.04 installed without problems in BTRFS partition. Have an nice week.

---

