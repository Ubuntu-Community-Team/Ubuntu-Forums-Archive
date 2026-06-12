---
title: "false raid + win 7 + ubuntu 9.10"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by nakednorman on 2010-02-18
Greetings to all from a *buntu newbie.

I have a 4 disk Raid 10 with Windows 7 installed & working.  (Win 7 sees this as 1 disk.)

I installed 9.10 onto a 5th disk, but I ***think*** that ubuntu saw the Raid 10 as 4 separate disks and wrote the boot loader to hd0- I had to rebuild my array & I couldn't load 9.10

For the second attempt, I disconnected my Raid 10 and 9.10 is now alive & well on the 5th disk, (presumably with the boot loader on the same disk).

Both Win 7 & Ubuntu 9.10 now work but I have to steer to the required disk via the bios for loading.

I'm reluctant to play with the boot loader (GRUB?) from 9.10, because it doesn't seem to like my Windows disk array.

Would something like EasyBCD (used from Win 7) be an option?

Regards,
NN

---

### Post by darkod on 2010-02-18
Yes, EasyBCD would be an option. And the reason grub didn't work fine previously is because you need to use the Alternate Install CD for RAID and/or LVM. Since you didn't want to actually install ubuntu onto the fakeraid, I guess the alternate cd would still help you install grub onto the array MBR correctly.

---

### Post by nakednorman on 2010-02-18
Many thanks for the reply.

If I never darken your doors again, you'll know it worked :)

Regards,
NN
--------------------------------
Windows 7 64bit and Ubuntu Desktop 9.10 64bit
(hoefully soon to be comfortable with each other)

---

### Post by darkod on 2010-02-18
Just for information, the fakeraid howto:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Although this explains how to install on fakeraid which you didn't want to do, but the section about installing grub stays the same.

---

