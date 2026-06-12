---
title: "issue with booting into ubuntu after hdd switch"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by Sir_Scrunchalot on 2008-06-05
ok, long story short, my comp had 2 hdd. one for storage primary master, and one for the op system primary slave. i had xp installed on the slave. worked fine, then i installed linux on secondary partition on that drive, linux worked fine but every time i tried to boot xp using grub it'd say that ntldr is missing. after trying to use bootcfg and the xp cd to fix the boot record and changing the settings in grub, i just decided to do a clean install of xp on my comp to fix the issue.
in the process, i switched the hdd's around so i could use the origional primary slave as the master for the two os's to uncomplicate things for linux.
installed xp.
now linux wont boot. doesn't even come up as a possibility. i had expected that.
used ultimate boot disk in order to boot from the second partition on that drive, now it gives me an error that just keeps looping. i will post it next after i am done updating xp and can restart.
all i am trying to find out is do i need to reinstall ubuntu or is there some way to redirect the instalation of ubuntu to the new drive boot order.

sory if this is garbled, i am completely new to linux and have been setting it up since last night.

thx for any suggestions

---

### Post by logos34 on 2008-06-05
[reinstall grub with the livecd]("http://ubuntuforums.org/showthread.php?t=224351") (or from the grub shell on UBCD)

---

