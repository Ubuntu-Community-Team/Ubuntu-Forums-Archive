---
title: "no desktop after upgrade - nvidia"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by carpman on 2010-07-29
Hello, ok did an regular (not version change) upgrade on friends pc and now have no desktop?

Boot loads to console and can logon to console but startx fails, checking logs it says it can't load nvidia module. As upgrade had included kernal i tried to boot to older kernel but this failed with grub error.

I tried console install of nvidia-current and nvidia-module (not sure if correct name but was nvidia kernel module) but still no joy.

Any ideas?

cheers

---

### Post by Krydahl on 2010-07-29
I've been having similar problems. I haven't got to the bottom of it, but removing the proprietary nvidia drivers and then reinstalling them seemed to fix it for me.

I did all the removing and reinstalling through the ubuntu hardware drivers GUI, nothing fancy.

---

### Post by dabl on 2010-07-29
Posts #10 -#16 on this thread should be informative:  [http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

---

