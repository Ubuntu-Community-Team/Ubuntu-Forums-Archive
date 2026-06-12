---
title: "RAID0 Grub Fails to Install"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by lee_connell on 2007-11-17
I am installing ubuntu gutsy on two SATA drives setup as RAID0.

/dev/md0 /boot (marked bootable)
/dev/md1 swap
/dev/md2 /

Everything installs just fine and then when it tries to grub-install it fails without a meaningful error.  The only way I can get a successful RAID0 install is if i keep the /boot partition outside of the RAID.  What is the deal here and how to fix?

---

### Post by Pumalite on 2007-11-17
Are you aware of this:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by lee_connell on 2007-11-17
thanks for pointing that out.  I will have a look at that.  How is Zenwalk going for you?

---

### Post by Pumalite on 2007-11-17
You are welcome. Good luck. Zenwalk is a nice little distro. Very happy with it.

---

### Post by lee_connell on 2007-11-17
The instructions are for making the disks work on a fakeraid that's controlle through BIOS, I do have this option in BIOS but it is all turned off.  

I still get this problem ONLY if i make my /boot partition part of the "software raid"  If i put /boot outside of "software raid" it works fine.

---

### Post by lee_connell on 2007-11-17
Well answer seems to be you just can't boot from RAID0.  I will just have to create /boot outside of the RAID.

thanks!

---

