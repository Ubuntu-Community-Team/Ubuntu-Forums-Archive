---
title: "How to install ubuntu with two drives as one logical volume and encrypt both drives"
date: 2018-04-15
forum: Installation &amp; Upgrades
---

### Post by reybango on 2018-04-15
I have a laptop setup with UEFI and two SSDs, a 250gb & 500gb. I'd like to install Ubuntu with:

[LIST]
[*]LVM 
[*]Encryption on both drives 
[/LIST]
I'd like to setup the two drives as one large logical volume using LVM and have the whole thing encrypted.

From previous single drive installs I know that during the install  process I'm prompted if I want to encrypt my drive and use LVM. At this  point am I able to configure the two drives as one large logical volume  and have that encrypted or does Ubuntu solely allow me to install it to  one physical drive.

  Thanks and please let me know if I've not provided enough info. Happy to offer more if I can.

---

### Post by reybango on 2018-04-21
Bump. Would love some help with this.

---

### Post by Dennis N on 2018-04-21
To get one volume group to occupy both drives, I believe you need to have an LVM physical volume on both, then make a volume group that comprises both of those. I don't span disks with a volume group because of the caution given below, but if I wanted to do this, my best guess would be to first set up drive A only with disk encryption, then expand the vg and expand the lv to include the second lvm phyical volume on the second drive as well. I expect the expanded vg and lv would fall under the encryption umbrella.  

Caution: May not be the best idea to span two drives with one volume group. If one drive fails, you risk data becoming inaccessible or lost on both drives that use that volume group.

---

