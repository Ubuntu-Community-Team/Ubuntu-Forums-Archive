---
title: "two disks, dual boot; grub question"
date: 2016-10-17
forum: Installation &amp; Upgrades
---

### Post by col48 on 2016-10-17
I have just installed 16.04, successfully  overwriting 8.04 on one of my two HD (sda1)
The other (sda2) has 12.04.

I was already set up to dual boot which the choice of Ubuntu OS.

If I edit the boot order in BIOS so that the 12.04 disk (sda2) has priority, the 16.04 on sda1 is not offered to boot into (grub seems to think 8.04 is still available).

What is it best to do to remedy this?
1. Is it just a matter of copying the relevant lines in the grub.cfg on sda1 into the file in sda2 and deleting the ones which refer to 8.04?
2. Does it matter where in the file they go?
3. Are there any hidden traps - anything which would not be obvious to this cautious non-expert?

PS For grub, read grub2 throughout (I think!)

---

### Post by oldfred on 2016-10-17
Why would you then not just use the grub2 from 16.04?
Normally grub in MBR, is from most recent install and that then has control.
But you can install any other install's grub to MBR and then update grub. It should then find correct version.
From your 12.04
sudo update-grub

With grub2 you do not edit grub.cfg as it is recreated regularly. You can add boot stanzas to 40_custom if desired.
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

Note that each install on major updates, may reinstall grub to MBR.
It looks like 12.04 expires April 2017.

If manual update did not work, this also documents entire configuration which is good to have:
       
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by col48 on 2016-10-17
oldfred:- thanks. the update-grub worked in 10 seconds flat.  I didn't know you could do that.

I'm still using 12.04 until I get 16.04 the way I want it.

By the way, it is thanks to you that I have dual-boot, as you very kindly walked me through the process about 5 years ago.  There is an element of backup, but it means that I can test and migrate processes gradually from one system to the other without the risk of unpredictable downtime as I figure out why something doesn't work.  As I say, I'm cautious!

---

### Post by oldfred on 2016-10-17
Your are welcome, sorry I do not remember.

I do install new versions and now use LTS as main working install. My wife complained about too many changes when I was changing every 6 months.
I still reinstall next version several times and finally after fully released, I converted to using data partition that I could mount in every install. And most of those installs are still on my system as each only uses 25GB. Install is now very quick from one HDD to SSD or SSD to HDD, and then scripted mount & edit of fstab. And reinstall of all apps. So I can do a new install and 75% of reconfiguration automatically.

---

