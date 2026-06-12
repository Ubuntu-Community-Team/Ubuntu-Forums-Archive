---
title: "Ubuntu 11.10 Blinking Cursor Screen"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by amtur_poet on 2012-03-01
I was finally able to get 64-bit Ubuntu 11.04 working on my Toshiba X775 last night using nomodeset in the boot options to let me install the necessary Nvidia driver and then upgrade to 11.10. After the upgrade was complete, it asked me to restart. I did, but it froze partway through, and I was stuck with an image of the default wallpaper. So, I did a cold shutdown, and restarted. When I tried to start Ubuntu, it gave me the purple screen of death after the GRUB menu. So, I did another cold shutdown, and this time (along with every other time after it), it gave me a blinking underscore cursor sign after the GRUB. It doesn't let me enter any text, either. I tried using nomodeset again, but nothing new happened. I tried booting into recovery mode, and that ran a whole bunch of text before giving me the following kernel panic error:

```
[   5.533369] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

My laptop has two separate hard drives in a non-raid setup. Would this be the problem? How do I fix it?

---

