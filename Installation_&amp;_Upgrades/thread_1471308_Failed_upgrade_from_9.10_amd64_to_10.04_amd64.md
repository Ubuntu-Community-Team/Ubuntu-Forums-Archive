---
title: "Failed upgrade from 9.10 amd64 to 10.04 amd64"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by purct on 2010-05-03
I have just tried to upgrade from 9.10 to 10.04 :(....upgrade failed with an error saying to run the packager and clean up/fix the failed packages but the system restarted before I had a chance to fix it. Now System no longer boots...grub starts but I see an error udevadm not found.

then drops back to a prompt to aid recovery....I looked about in the /dev etc and the disks are not listed (looked for the disks-by uid as well but not there!).

I downloaded the 10.04 livecd but will not boot.. says that there is a read error on the CD....(but I no its fine - I have burnt about 5 disks) 

I have been able to boot from a 9.10 Live CD ok.   

Now I have booted a 9.10 livecd...can I mount my root in place of the livecd root(then perform a package clean/repair to the 10.04 of my root) and if so how?

if I can't do that, can I mount it to /mnt/root and then force the packager read the repos from my root disk and write to /mnt/root to repair the upgrade?

---

### Post by Moustaffa on 2010-05-03
Try downloading Hiren's BootCD, it contains a lot of programs you can run from BIOS. It will also format your hard drive (with the program called KillDisk or something similar). After that you can try to do a fresh install

---

### Post by purct on 2010-05-03
> **Moustaffa said:**
> Try downloading Hiren's BootCD, it contains a lot of programs you can run from BIOS. It will also format your hard drive (with the program called KillDisk or something similar). After that you can try to do a fresh install

Thanks, not really what I want to do! I am unable to install 10.04 from cd because the there appears to be an issue with the cd driver.....it reports CD read failure (almost immediately) I know that the media & hardware is good.....

I can boot from 9.10 ok.....

I can mount the root disk ok.

I just want to repair the 10.04 packages on my root disk thats mounted in a different location from a booted 9.10 livecd

---

### Post by purct on 2010-05-04
sorted....booted from 9.10 livecd. mounted my root disk in directory then ran chroot to set new root directory.

ran dpkg --configure a

:)

---

