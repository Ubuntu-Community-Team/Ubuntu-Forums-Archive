---
title: "How to add another disc to the encrypted lvm?"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by hal2100 on 2008-08-12
Hello,

I installed my Ubuntu 8.04 according to this small how-to:
[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html]("http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html")

Now I am confused how I can add another disc, and enlarge the lvm-home. I was able to add the disc to the VG and enlarge lvm-home, but I think that the encryption is only used for the first disc. So my questions are:

0. What is the easiest way to get the (currently unencrypted, if I am right) disc out of the LVM. I think I will try the LiveCD.
1. How can I add the disc to the LVM with encrytion.
2. How can I configure the encryption to open both encrypted containers on startup with just one password?

---

### Post by triple.eh on 2008-10-28
What were your results?  I'm planning on doing the same and would like to hear about your experience.

Thanks!

---

### Post by hal2100 on 2008-11-02
It is a long time ago, but it was like this:

Attache the new drive, create a encrypted partition, add this partition to the LVM, edit the startup files that both partitions will be unlocked during startup <- the last one is important!

Do you need further assistance?

---

### Post by MountainX on 2009-02-28
Hey, I could use some tips on this.

My existing volume is set up where the disk is the physical volume for LVM. Then I make a volume group and logical volume. And then the LV is the "physical" volume for encryption. So LVM is first then crypto on top of that.

Now I want to add two more disks to my system. For each disk I need to create a partition and use that partition as the physical volume for LVM. Then I need to make 1 VG and 1 LV on each HDD. In each LV I need to set up a crypto volume.

I have only done this from the installer in the past. Now I need to do it on an installed system. Either the GUI or command line is OK for me, but I need a find a how-to. Can you point me in the right direction? Thanks.

---

### Post by hal2100 on 2009-03-02
> **MountainX said:**
> Hey, I could use some tips on this.

My existing volume is set up where the disk is the physical volume for LVM. Then I make a volume group and logical volume. And then the LV is the "physical" volume for encryption. So LVM is first then crypto on top of that.

Now I want to add two more disks to my system. For each disk I need to create a partition and use that partition as the physical volume for LVM. Then I need to make 1 VG and 1 LV on each HDD. In each LV I need to set up a crypto volume.

I have only done this from the installer in the past. Now I need to do it on an installed system. Either the GUI or command line is OK for me, but I need a find a how-to. Can you point me in the right direction? Thanks.

No,
it is a little bit different, at least if you want to increase your LVM which is installed by the alternate installer.

The crypto partition is the basis for the LVM LVs.

If you have it differently, then you have to extend the existing LVM, and enlarge the encrypted partition afterwards.

Do you create the LVM or do you want to extend a existing one?

---

### Post by MountainX on 2009-03-02
I want to create a new VG and LV. Then I was going to put the crypto volume in the LV.

---

