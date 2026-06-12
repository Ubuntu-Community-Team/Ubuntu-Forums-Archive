---
title: "Grub2 reinstallation"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by bubuzzz on 2010-08-02
Hi all,

I just played around with grub2 in ubuntu 10.04 and made a very stupid mistake today. What i did is change the default boot of file /etc/default/grub/ into 6 (window 7) and set the time out = 1 ( i was crazy at that time and didn't realize that 1 second is too short to press any button). So, now, every time booting, i cannot press fast enough to change back to ubuntu :frown::frown::frown:. I tried to reinstall grub but the grub file in the default folder is still there and there is no way for me to go to ubuntu to update grub. So is there any solution for this?

---

### Post by dino99 on 2010-08-02
so you might see the grub menu for a short time, be ready to use up/down arrow to select lucid, then change back your settings into /etc/default/grub and: sudo update-grub

---

### Post by drs305 on 2010-08-02
Hold down the SHIFT key as the system boots and your grub menu should display. You can then select Ubuntu and make the changes from within the OS.

If this doesn't work, you can boot the LiveCD, mount your Ubuntu partition, and then edit /boot/grub/grub.cfg
Change XY to the correct drive/partition (such as sda5).
```

sudo mount /dev/sdXY /mnt
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /boot/grub/grub.cfg

```
About line 53, set the timeout to 10.

grub.cfg is not really meant to be edited, but this is the simplest way to change the timeout with chrooting, etc.

Reboot and make the change to the correct file, /etc/default/grub, and then run "sudo update-grub"

---

### Post by bubuzzz on 2010-08-02
i edited the grub.cfg and it works. Thank you very much. :popcorn:

---

### Post by drs305 on 2010-08-02
> **bubuzzz said:**
> i edited the grub.cfg and it works. Thank you very much.

Don't forget to change the settings in /etc/default/grub so the change isn't overwritten the next time update-grub is run. 

If you don't mind, please mark the thread SOLVED if you have no further issues. This is done from the "Thread Tools" link at the top right of the original post. You can also removed the SOLVED tag from the same link, but of course we hope that won't be necessary.  ;-)

---

