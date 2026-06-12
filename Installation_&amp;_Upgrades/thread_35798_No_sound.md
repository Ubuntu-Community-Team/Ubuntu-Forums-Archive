---
title: "No sound"
date: 2005-05-20
forum: Installation &amp; Upgrades
---

### Post by in_omaha on 2005-05-20
Ok, install went great. I apt-get mozilla firefox plugins for mplayer. Now when I try to view a trailer or something, I have no sound and the clip buffers to 25% and stops. Any ideas?

Thanks in advance!

---

### Post by f.prisson on 2005-05-20
I had a similar problem. For me it was fixed when I edited the /etc/mplayerplug-in.conf and uncommented and edited the entry "ao=artsd, esd, alsa"

---

### Post by in_omaha on 2005-05-20
Thanks for the reply. I will give that a shot tonight and see how it goes.

---

### Post by Ali_Baba on 2005-05-21
Here is a good HOWTO about sounds [http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567) you should check that too :)

---

