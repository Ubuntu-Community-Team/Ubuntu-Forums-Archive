---
title: "cp: cannot stat '/boot/grub/search.mod': Input/output error"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by slugicide on 2010-01-30
This is what I get when following the instructions to fix grub. I type in "grub-install /dev/sda" and that's the error I get.

I'm trying to put Ubuntu or Mint on a Dell Mini 9 with 16gb ssd, but no matter what I do I cannot achieve this goal. 

I'd love some help and advice. Thanks.

---

### Post by slugicide on 2010-01-30
So, any help out there?

---

### Post by slugicide on 2010-01-31
Am I out of luck on this?

---

### Post by ELoXL on 2010-12-20
I-AM-SO-WITH-YOU-ON-THIS!  

I installed Win7 over like an idiot and tried to follow the steps necessary to reinstall GRUB2 via [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) , but I'm getting no luck at all and running into the same error as you - EXACT.

---

### Post by drs305 on 2010-12-20
> **ELoXL said:**
> I-AM-SO-WITH-YOU-ON-THIS!  

I installed Win7 over like an idiot and tried to follow the steps necessary to reinstall GRUB2 via [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) , but I'm getting no luck at all and running into the same error as you - EXACT.

If you completed the Ubuntu installation but are missing Grub2 modules your best bet is to boot a LiveCD, chroot into your real Ubuntu installation, and purge and reinstall G2. Here is a link to a guide that helps you do that. There are simpler procedures but since we don't really know the extent of the 'damage' to Grub2 this is probably what will give you the highest change of solving it on the first attempt.

[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

---

