---
title: "Logical volume dissappeard with 9.10"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by mikereed on 2010-04-09
Hi,
back with Ubuntu 8.04 I intalled onto my PC using lvm.  I had two disks mirrored on which I created a vg called VolGroup01 which I used for /home, and I had another single disk on which I had my OSs.  This has one partition with Windoze, another partition that I used for /boot and a third partition that was lvm with a vg called sata30.  So, occasionally, when a new version of Ubuntu came out, instead of upgrading I just created a new lv and did a fresh install of Unbuntu into it.  For a couple of years this has gone fine.  The first lv was called ubuntu, then I created unbuntu810 and then ubuntu904.
Now, with the ubuntu904 I just tried to upgrade to 9.10, but after the upgrade it did not boot.  I thought bugger, oh well, I'll just create a new lv and install 9.10 into it.

Booted up the ubuntu810 lv, no problems
created lv ubuntu910
rebooted with the 9.10 desktop CD
installed lvm2
partprobe
run installation

and then I found out why the 9.10 upgrade in the ubuntu904 lv wouldn't work.  9.10 can't see the pv/vg/lvs on the OS disk.  But earlier versions of Ubuntu still can see them, obviously, I rebooted my ubuntu810 lv to create the ubuntu910 lv.
Has anyone else heard of pv/vgs dissappearing under 9.10?
I have attached two files, one with some lvm commands run from booting the ubuntu810 lv and one with various commands run from the 9.10 desktop cd after installing lvm2.
The only worrying thing I see from the 9.10 cd is errors from "parted" about unrecognized disk label on the lvs in the sata30 vg.
Any help on where I should go from here would be much appreciated.
Thanks,
Mike.

---

