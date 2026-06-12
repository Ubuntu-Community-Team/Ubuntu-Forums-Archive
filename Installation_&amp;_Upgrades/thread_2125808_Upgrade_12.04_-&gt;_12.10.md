---
title: "Upgrade 12.04 -&gt; 12.10"
date: 2013-03-15
forum: Installation &amp; Upgrades
---

### Post by CraftyZA on 2013-03-15
While doing my weekly checks for updates, I found I can upgrade to 12.10. So instead  of running package updates, I clicked Upgrade.
After the upgrade was done I was asked to reboot. I Clicked OK.
On start up, I saw a message briefly saying something about unable to mount drive that holds /tmp. However, there is just one drive.
I was still looking at the options I have like pressing m for manual, and missed the other option(s), then the screen went blank.
Now If I boot up again, it skips the message, screen goes blank after the Ubuntu logo appears during boot-up.
I have no access. ctrl&alt F1 - F12 does nothing. No other consoles available, so cannot investigate. Also it does not seem to use lilo, so I have no idea how to bypass X, and go straight to single user mode.

Any help?

---

### Post by coffeecat on 2013-03-17
I don't believe Ubuntu has ever used lilo - you would have to replace grub by installing lilo yourself if you wanted the lilo bootloader. Anyway, assuming that you haven't and that you are still using grub, it sounds as though you are not seeing the grub menu. If so, press and hold the shift key at the POST screen and this should reveal the grub menu. Select "Advanced options for Ubuntu" and this will take you to a submenu with all your installed kernels as choices. Select the recovery mode option for the latest kernel - this is single user mode. If you select dropping to a root shell prompt, the filesystem will be mounted read-only. To remount read-write, you would need to:

```
mount -o rw,remount /
```

However, before you do that a couple of thoughts.

The error message is about being unable to mount /tmp. You say you have only one drive. When you installed Ubuntu originally, did you create a separate partition for /tmp or would /tmp be in your root partition? If the former you might want to check your partitions and the health of the /tmp partition with a live CD/USB.

The other thought is a suggestion based on a wild guess only. I wonder if your initrd for the 12.10 upgrade didn't build properly. Try booting into one of the older 12.04 kernels from the advanced options submenu in the grub menu. If you can do this, then at least you'll have a GUI for investigating your problem.

---

### Post by CraftyZA on 2013-03-22
Tried most of that, but without any luck. Lucky for me I had still all my files as backups from my upgrade from Fedora. 
I just reinstalled 12.04, and will be using that for a while longer. 
I've just downloaded the full install for 12.10, and will wipe xbmcbuntu from my media center, and installing this. Will start xbmc automatically. That way I can see if it is worth giving 12.10 to the study pc as well.

---

