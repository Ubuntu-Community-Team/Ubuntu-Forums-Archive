---
title: "wubi install fine, &quot;normal&quot; install not"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by swift.monterey on 2011-10-13
i used a wubi install for weeks with no problem whatsoever. i decided to go for a full side-by-side install alongside windows 7 64bit (the same windows install i used with wubi). now, although everything is setup exactly the same as far as i can tell, 1) i get random lock-ups and hard crashes, 2) neither microphone jack will work no matter what i do... 3) the chromium browser doesn't want to remember its configuration (default browser status, etc). as i say i had none of these issues with a wubi install.

my assumptions/guesses:

could it be that the sound driver being used by the real install is not the same as that used by the wubi install? why else would the mic not work? anyone know how i might look into this? everything i know to check, the device names and settings are identical to the functioning wubi install.

the only other difference is the way the drives are setup. as opposed to the single 30gb wubi virtual drive i now have several real (logical) partitions: 500mb /boot, 3gb swap, 10gb root, 100gb /home. these partitions are sequential logical partitions contained in a single primary partition, on a hard drive with a couple of other NTFS partitions.

could the chromium issue be some kind of permissions problem, stemming from the fact that, unlike with the wubi install, there are other partitions holding some of the config info (perhaps)?

i was really impressed with how fast a real install was compared to wubi... this OS is *fast*. i would love to get this all working! any help would be greatly appreciated!

---

