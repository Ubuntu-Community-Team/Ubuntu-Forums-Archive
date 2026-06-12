---
title: "karmic cannot see sata disk, known bug?"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by mchlor on 2010-03-11
Is this a known bug?  I've not had problem installing 9.04 but 9.10 will not see HDD under partition manager(ubiquity) no matter the F6 boot options or fiddling around with bios.

If ubuntu can't see the hdd, I can't install.

785G chipset with SB710 FYI.

---

### Post by darkod on 2010-03-11
This usually happens if the hdd has been used in raid and karmic can detect raid meta data remains on it. If you are NOT running raid, simply boot the live desktop and do:

sudo dmraid -E -r /dev/sda

Replace /dev/sda with the exact name of the hdd in your case if needed.

If you ARE running raid, the installation method is different.

---

### Post by mchlor on 2010-03-12
> **darkod said:**
> This usually happens if the hdd has been used in raid and karmic can detect raid meta data remains on it. 

Thanks for the insight.

That is amazing.  Why I never knew raiding a pair of drives leaves meta date on the disks.  You are right, it was used in a raid0 setup once to see what's all the hoopla was about.  I dismantled the raid only after a few days seeing minimal gains.  Maybe dban can make the disk factory fresh??

btw, i solved this issue by typing "apt-get remove -y dmraid" and clicking on install icon.  it then worked.

---

### Post by soltanis on 2010-03-12
No need to dban the disk, it's just detecting a software raid partition more likely than not. Formatting the disk will get rid of that.

---

### Post by mikewhatever on 2010-03-12
> **soltanis said:**
> No need to dban the disk, it's just detecting a software raid partition more likely than not. Formatting the disk will get rid of that.

Well, and how do you format it, if no disk is detected?

---

