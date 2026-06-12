---
title: "Install Gutsy on new partition, USB mouse stops working on old"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by wolfger on 2007-11-10
I've got an odd problem... On my main partition I'm running Kubuntu Gutsy that was upgraded from Tribe 5. I mailed a fresh Kubuntu Gutsy disc to a friend of mine, and so I decided to wipe Feisty off my backup partition and do a fresh install of Gutsy there. I got the fresh Gutsy working, but when I tried to reboot into my main partition again, the mouse doesn't work. At all. Now how in the heck could an install on the backup partition ruin the mouse for my main partition? Is there some file somewhere that assigns a UUID to the mouse???

---

### Post by Fire_Chief on 2007-11-11
If they were truly separate installations, then it should have no effect. Does the mouse work if you boot off the live CD?

---

### Post by wolfger on 2007-11-12
Yes, it was working on the new install and from LiveCD, Just not on the old install. The only shared components between the two installs were SWAP and /home/wolfger/shared (movies, music, pictures)
The solution, it turns out, was to unplug and re-plug the USB mouse while booted into the old install.

---

### Post by wolfger on 2007-11-16
Not quite closed yet... Unplug/replug gets the mouse working again, but I have to do it every single time I reboot. Very, very annoying. So, anybody got any ideas?

---

### Post by bulldog on 2007-11-16
Try in a terminal```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by wolfger on 2007-11-18
> **bulldog said:**
> Try in a terminal```
sudo dpkg-reconfigure xserver-xorg
```

That did not fix it.

---

