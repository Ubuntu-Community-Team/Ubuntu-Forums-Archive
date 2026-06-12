---
title: "Hardy installation ends unexpectedly"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by volansspica on 2008-05-01
Hi, this is my first post :P

I 'm trying to install ubuntu hardy 8.04, i had installed gutsy in one partition and tried the upgrade, but it wrecked the start screen or something like that, so i couldn't log in.
I decided to make a back up of /home using another partition and to do a fresh install, however i've not managed to install ubuntu. The installer starts normally but it restarts the live session after getting to 79%

The last message was "Creating user" and then it all goes black and the live session starts.

I've already tried with two different cds, and two different cd drives with no luck.

Do you have any ideas to make it work?

Thanks in advice.

Additional information: Grub menu doesn't work anymore, it prints "Error 15" i think it should be corrected with a reinstall.
I have two partitioned hard drives, one of them contains Win Xp.

EDIT: After the live session restart, ubuntu informs about an error in ubiquity.

---

### Post by DHGE on 2008-05-01
Did you check the integrity of your CDs?

The md5sum of your iso-file or from the boot-menu of the live-CD.

---

### Post by DHGE on 2008-05-01
> Grub menu doesn't work anymore, it prints "Error 15" i think it should be corrected with a reinstall.

It could...

If not, try to edit the boot options you can
(hd, <TAB-Key> to see what's available.
I had to change (hd0,0) to (hd0,5) and then some cleanup in /etc/fstab

I had a wildly disturbed grub-menu after installing a fresh hardy over an unencrypted gutsy via the alternate installer.

Me thinks the installer got confused over a hidden hibernation/recovery partition on my ancient HP notebook.

---

### Post by volansspica on 2008-05-01
I did it!!

I had checked the cd's and they were fine. Something went wrong with my new /home partition, my data remains intact, but the installer got confused at some point and it failed to link my new  partition (i think), so i marked my /home partition not to be used by the installer and that's how the installation ended correctly.
GRUB is also fine at the end.

Thanks.

---

### Post by CFBauer on 2009-05-09
Just ran into this exact same problem, as you described. Will try leaving my home partition out. Thanks!

---

