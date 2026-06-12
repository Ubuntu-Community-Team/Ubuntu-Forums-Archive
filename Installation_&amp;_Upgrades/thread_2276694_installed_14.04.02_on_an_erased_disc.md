---
title: "installed 14.04.02 on an erased disc"
date: 2015-05-04
forum: Installation &amp; Upgrades
---

### Post by greg79 on 2015-05-04
I've installed 14.04.02 on an erased 250GB acer aspire 1. There is no other operating system on the disc. I created partitions /boot 1000MB, swap 4000MB, / 30000MB, /home 100000MB, the rest is free space. After installing it I ran the boot repair instructions for 14.04 and clicked on recommended as the boot repair option. The successful repair message came up. The reboot produced a purple screen. I have tried various combinations of this general approach several times with the same purple result. The latest boot info is [http://paste.ubuntu.com/10983717/](http://paste.ubuntu.com/10983717/)
Hope someone has more ideas for me to try

Regards,
Greg

---

### Post by Vladlenin5000 on 2015-05-04
Hi and welcome.

First of all, your partitioning seems a little too complex for a single OS machine for personal use. However, it should work and whatever is happening is unrelated to that.
Why boot repair? That tool is meant for situations where dual boot isn't working but it should. What was the problem that led you into using boot repair?

---

### Post by greg79 on 2015-05-04
The release notes suggested that there is a problem with installing 14.04 and that boot repair would solve it. The problem is that the system won't boot up.

Cheers,
Greg

---

### Post by greg79 on 2015-05-04
I know the partitioning might be over the top but I wanted to eliminate it as a possible cause.

Cheers,
Greg

---

### Post by Bucky Ball on 2015-05-04
Install again and at the end of the installation, just reboot like the screen tells you to. Shouldn't be any need for Boot Repair. Explanation from Vladlenin5000.

With no other OS shouldn't be an issue. Not sure where you got the info that you needed to run Boot Repair after installing Ubuntu, single boot, dual boot or otherwise. Only for use when you're in trouble, and doesn't sound like you were. Or were you? Did you install, reboot and the machine wouldn't boot??? So you ran Boot Repair?

---

### Post by greg79 on 2015-05-04
I did install, reboot and the machine wouldn't start. So I booted from the install disc and ran boot repair. It still doesn't start. It does give the impression that it is rebooting but nothing appears until eventually it settles on a purple screen.

---

### Post by Bucky Ball on 2015-05-04
When you boot, do you get to any screens, or just the purple one? No kernel screen where you can choose which kernel to boot?

Did you try Ubuntu directly from the live install media prior to installing and have the same issues?

---

### Post by greg79 on 2015-05-04
Ubuntu does work from the installation disc. I have just chosen install again. I took the top option a simple erase of the current 14.04.02 and re install. After the installation I've clicked on the restart. It asked me to remove the media and close the tray and press return. I now have the purple screen. There were no intermediate options or anything else on the screen.

Cheers
Greg

---

### Post by Bucky Ball on 2015-05-04
Could you now post the bootinfo from Boot Repair, please (if it is different from the one already posted)? 

If it is the same (the first part at least), then when you're at the purple screen, can you hold down control+delete then hit F1 and get to a CLI (a big terminal)? If so, log in and try this:

```
sudo grub-install /dev/sda
sudo reboot -h now
```

A wild stab (because it is possibly your graphics), but any different?

---

