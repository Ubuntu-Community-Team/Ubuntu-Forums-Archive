---
title: "installing 12.04"
date: 2012-08-31
forum: Installation &amp; Upgrades
---

### Post by technmom on 2012-08-31
I have 32 bit 10.04 32 bit ubuntu installed as dual boot with windows 7. When I installed this I knew nothing. I am more familiar with ubuntu and use it almost exclusively but still need to keep Windows 7. 
Some of the software I use for my research requires an update and 64 bit. I want to keep my dual boot so i can use windows occaisionally. How can I go about this and preserve my home directory which I believe is not on a separate partition.

Thanks,

---

### Post by darkod on 2012-09-01
First make sure /home is not a separate partition. The command:
df -h

will show what is mounted where. If there is separate partition mounted as /home, then it's separate.

If it's not separate you will need to copy the content of your current home to external hdd or similar. Make sure you copy it by keeping permissions. In the new install, create the same first user like you did in 10.04, and when you copy it back it should have correct ownership and permissions of the home folder.

To copy keeping permissions, mount the external hdd somewhere, lets call it /mountpoint and execute:
```
cd /home
sudo copy -ax * /mountpoint
```

the options -ax make sure ownership and permissions are kept.

After that is done, when installing 12.04 you can use the situation and with using the manual partitioning, install this time with separate /home. Note how much you use from your / partition right now, discounting the size of your home folder, and that can give you an idea how big to make / in the new one, and how big /home.

I would create the partitions for the new install first, copy the content of home to the new partition planned for it, and then start the installer.

This is the general idea, if you have questions when doing it, just ask.

---

### Post by technmom on 2012-09-01
I did not see this reply and had already done the upgrade, with not much trouble but I still have the home directory on the same partition. Do you think it is worthwhile to move?

thanks,

---

### Post by darkod on 2012-09-02
If you did the upgrade with update manager the new 12.04 would also be 32bit. I was under impression you needed 64bit.

As for having separate /home, that's up to you. I prefer having it on separate partition because it makes clean installs very easy. But it's up to you really.

---

### Post by technmom on 2012-09-02
I did it with a live boot from USB and it is now 64 bit. So I assume I can follow the above directions for moving the /home directory still and all should be well

thanks

---

