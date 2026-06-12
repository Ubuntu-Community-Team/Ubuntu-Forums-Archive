---
title: "/boot partition and Grub2 problems"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by achase79 on 2010-07-02
Last night I was trying to install lucid (replacing jaunty) and was trying something new by spanning my system over 2 - 40GB drives.  I was trying to do this with LVM so I could possibly add more later.  I set up a minimal install with a 256mb /boot, 1.5gb swap, 20gb logical volume for /, and the rest for /home.  It would never boot.  Tried installing many times with slightly different configs, no luck. I searched this morning and saw that Grub2 (which is used default in Karmic and Lucid) can't handle a separate /boot partition.

I am now thinking I should set it up this way:
sda1  1.5GB   swap
sda2  20GB    ext4  /
sda3  18.5GB  lvm
sdb1  40GB    lvm

1 lvm group containing sda3 and sdb1
1 logical volume mounted as /home

Does this sound like it will work?  I will be building up from a minimal install.  I want to do it somewhat like this to make full use of what little hard drive space I have.

---

### Post by darkod on 2010-07-02
Where does it say grub2 can't handle /boot partition? Somewhere credible or just someone being a wiseguy on his blog?

You are using the Alternate Install CD for LVM, right? As far as I know, you need to use that cd for LVM and as long as you create primary /boot partition outside the LVM (as you are doing), it should work out fine.

Make sure you actually install grub2 when asked where. In text mode you select a disk by hitting Space, not Enter. With Enter it will just continue with nothing selected so you have no grub2 to try to boot at all.

---

### Post by achase79 on 2010-07-02
Last night I installed 5 times, each time it would try to boot for the first time and would just stop just after the bios startup where it would normally say it was loading grub.

---

### Post by achase79 on 2010-07-02
[this]("http://ubuntuguide.org/wiki/Ubuntu:Lucid") is the site that said not to use a separate /boot partition

---

### Post by darkod on 2010-07-02
> **achase79 said:**
> [this]("http://ubuntuguide.org/wiki/Ubuntu:Lucid") is the site that said not to use a separate /boot partition

I don't think they mean /boot partition, that's why they wrote it as boot. They might mean if you use the EFI process in which you have a small boot partition on your hdd. And it's correct, Lucid doesn't seem to handle booting this way correctly. But EFI is still rare in PCs today.

If they really mean the regular /boot partition, I have no idea why they say it doesn't work.

---

### Post by achase79 on 2010-07-02
I have had no problems installing any other version or distro on this computer and I have not changed any BIOS settings.

This is a ASRock K7VT4A, Athlon 1.0 GHz, 1GB Ram.

---

### Post by darkod on 2010-07-02
You didn't confirm, are you using the alternate cd?

---

### Post by achase79 on 2010-07-05
Yes, I used the alternate cd (can't do minimal any other way)

I installed according to my plan and it worked.. sorry I didn't post sooner, I was away for the weekend.

---

