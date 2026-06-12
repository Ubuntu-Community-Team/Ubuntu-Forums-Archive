---
title: "Hash Sum Mismath while updating libcairo2 with Intel Graphics Update Tool on Yakkety"
date: 2017-02-15
forum: Installation &amp; Upgrades
---

### Post by riccardompesce on 2017-02-15
Hello everyone,
This afternoon I installed Intel Graphics Update Tool on my laptop running Ubuntu 16.10 Yakkety Yak. I also followed the guide at the bottom of the [official page]("https://01.org/linuxgraphics/downloads/intel-graphics-update-tool-linux-os-v2.0.3"), because it gave me errors with the GPG keys.
While upgrading, both through the tool and through the command ```
sudo apt full-upgrade
```, it gave me the following output:

```
Reading package lists...
Building dependency tree...
Reading state information...
Calculating upgrade...
The following packages will be upgraded:
  libcairo-gobject2 libcairo-script-interpreter2 libcairo2 libcairo2-dev
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 702 kB/1.588 kB of archives.
After this operation, 12,3 kB disk space will be freed.
Do you want to continue? [Y/n] Get:1 https://download.01.org/gfx/ubuntu/16.10/main yakkety/main amd64 libcairo2 amd64 1.15.2-0intel1 [568 kB]
Err:1 https://download.01.org/gfx/ubuntu/16.10/main yakkety/main amd64 libcairo2 amd64 1.15.2-0intel1
  Hash Sum mismatch
  Hashes of expected file:
   - SHA256:756ffe6dd23ed29c03295f86d8aca62981b85cc2dee42ed47f7fd61949b2fa13
   - SHA1:60c3d1e510af79c9cdc6b2204e61ec5cbb5f2c23 [weak]
   - MD5Sum:84bbaf1c1c20554bc033dccb4170095a [weak]
   - Checksum-FileSize:568080 [weak]
  Hashes of received file:
   - SHA256:cc21a8a43200a3d35624e0bd23849ca30c50ef255fb37ed7502cfa8c6ca34381
   - SHA1:640e49e1339734a385cbffca29485d6e866643e7 [weak]
   - MD5Sum:7c853ef25e2ecf23f9774dba49d39a2d [weak]
   - Checksum-FileSize:568080 [weak]
  Last modification reported: Wed, 23 Nov 2016 17:30:20 +0000
Get:2 https://download.01.org/gfx/ubuntu/16.10/main yakkety/main amd64 libcairo-gobject2 amd64 1.15.2-0intel1 [134 kB]
Err:2 https://download.01.org/gfx/ubuntu/16.10/main yakkety/main amd64 libcairo-gobject2 amd64 1.15.2-0intel1
  Hash Sum mismatch
  Hashes of expected file:
   - SHA256:c6b3b0670e833d16bd42355550dd3ceeb1567a540c1d8756da4af8359cca746d
   - SHA1:26350d583bbebd0d946e243bfa5da3c1b8464271 [weak]
   - MD5Sum:7fb0231133cee558fa8f7dea48b38b14 [weak]
   - Checksum-FileSize:133758 [weak]
  Hashes of received file:
   - SHA256:3d50aa89644a9a79ce8d56a22f33ada99b00aa5634ef306fd07c4994ba7a701e
   - SHA1:56f5eba1d34782ab2a36ea96cbc0d67fa3b36baf [weak]
   - MD5Sum:086ef35715963d3c674a5a654d4923bf [weak]
   - Checksum-FileSize:133758 [weak]
  Last modification reported: Wed, 23 Nov 2016 17:30:19 +0000
Fetched 702 kB in 1s (366 kB/s)

```

I tried with ```
sudo apt clean all
```, ```
sudo apt clean
```, ```
sudo apt autoclean
```. And I did ```
sudo apt update
``` after that, of course.
I also did ```
rm -rf /var/lib/apt/lists/*
``` and updated, without success.
Can someone help? Thanks.

EDIT. It now works. They have fixed it, apparently.

---

### Post by #&amp;thj^% on 2017-02-15
I was able to reproduce your problem following that link
Try this as a temp workaround...this "**should** be fixed soon"
for now you can go to Software & Updates, Click on "Other Software" tab and deselect or uncheck this update: "**[https://download.01.org/gfx/ubuntu/16.10/main](https://download.01.org/gfx/ubuntu/16.10/main)**/"
Now try update/upgrade again.

---

### Post by riccardompesce on 2017-02-16
> **1fallen said:**
> I was able to reproduce your problem following that link
Try this as a temp workaround...this "**should** be fixed soon"
for now you can go to Software & Updates, Click on "Other Software" tab and deselect or uncheck this update: "**[https://download.01.org/gfx/ubuntu/16.10/main](https://download.01.org/gfx/ubuntu/16.10/main)**/"
Now try update/upgrade again.

This solution works. Thank you! How long should I wait for?

---

### Post by #&amp;thj^% on 2017-02-16
Your Welcome.
You know this is just a guess here...but I would guess 2 to 4 days.
If this has anything to do with Canonical (and I doubt it) be paitent, they have thier hands full ATM.

---

