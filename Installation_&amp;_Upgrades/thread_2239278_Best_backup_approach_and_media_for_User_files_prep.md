---
title: "Best backup approach and media for User files preparatory to major Dist-Upgrade?"
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by bcschmerker on 2014-08-12
I am currently reassessing the backup/restore situation in light of fundamental security issues in the Universal Serial Bus standard.  As of 12 August 2014, I am still running Ubuntu® 12.04.5-LTS, albeit with the Kernel 3.13.0-33-generic backport from 14.04.1-LTS (package: **linux-image-generic-lts-trusty**), which runs stably on my rig (albeit with twice the boot time of Kernel 3.2.0-67-generic).  The 14.04.1-LTS (14.04.2-LTS in the event of slowdowns acquiring the drives) installation I am planning will use multiple Western Digital® SATA hard drives, probably the WD10EFRX Caviar Red® on operating-temperature range, to supersede the aging Fujitsu and Hitachi Ultra-33/IDE hard drives currently in my rig.  Both my current Gigabyte® GA-MA78GM-S2HP and the ASRock® Z68 Pro3-M planned for a major hardware upgrade pack eSATA ports at the rear RFI shield.  (I had previously retrofitted an Antec® TruePower® New™ 750 Blue™, in anticipation of the hardware upgrades, into the modified Everex® TC-2502 case, which will be retained along with the Creative Laboratories® SB0250 I/O Drive and SB0350 audio card.)

Previous experience showed the custom-install approach best for major Dist-Upgrades such as I performed twice on this system, as jumps between LTS releases involve much incompatible software due to the evolution of all Binaries, Superbinaries, and Libraries since the pre-upgrade Releases were new.  What media would be the most suitable for backing up User files and profiles (specifically for Mozilla® Firefox® and Chromium™) in advance of a major Dist-Upgrade, and what (Super-)Binaries are needed to copy to the backup media?

---

### Post by ian-weisser on 2014-08-13
Why is backing up for an upgrade different from your normal data backups?

Why does your custom system design require special care during upgrades?

What is a Superbinary?

Last time I had more than 3 TB of data in a RAID, I reduced complexity and risk by using a much smaller, separate non-RAID boot drive.
Preserving data across an upgrade can be as simple as unplugging the data drives.
If you partition the boot drive, then you don't lose your older (working) kernel, system, and settings while migrating to the new.

---

### Post by bcschmerker on 2014-08-13
I tried your proposed approach for /home Dist-Upgrading from 10.04.4-LTS to 12.04.1-LTS and got borked. :-S Hidden application-data files often have significant differences in requirements across LTS releases.

---

### Post by ian-weisser on 2014-08-13
> **bcschmerker said:**
> Hidden application-data files often have significant differences in requirements across LTS releases.

Different kind of data from what I meant. And *of course* application-specific data schemas change over time.
Nevertheless, back to your question.... I still don't understand why your backup plan needs to be special for an LTS-to-LTS migration, nor why you are asking for media-writing binaries.

---

### Post by bcschmerker on 2014-08-22
This is the first time I have attempted to use a non-USB backup media (see also "[Fundamental flaw discovered in USB protocol](http://ubuntuforums.org/showthread.php?t=2238685)"); I have no experience building GZip, BZip, or other archives consistent with downloadable source-code "tarballs" on LinUX Websites.

---

### Post by ian-weisser on 2014-08-22
> **bcschmerker said:**
> I have no experience building GZip, BZip, or other archives consistent with downloadable source-code "tarballs" on LinUX Websites.

An LTS-to-LTS upgrade is entirely package-based, and has nothing to do with reading or writing tarballs.

Are you trying to say that you want to create a tarball before upgrading? I don't see how upgrading is relevant.
Or is this tarball related to backing up your data?

I still do not understand the problem you are seeking help with.

---

