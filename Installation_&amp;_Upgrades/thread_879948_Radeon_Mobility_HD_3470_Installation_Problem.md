---
title: "Radeon Mobility HD 3470 Installation Problem"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by ukaratay on 2008-08-04
Hi all,

I've Asus M51Se240DV notebook which uses ATI Radeon Mobilitiy HD 3470 Graphic card and 3GB DDR2 RAM. In both of installations, 64bit and 32bit, it gives an error and drops to console. It cannot start X server. I couldn't remember all of the error message, but it is about X server. The graphic card cannot be identified by the X server. I've tried to change Driver option to mesa and ati but it again doesn't work. Also, I've tried installation with alternate cd, however, it cannot start after the installation and dropped to console. I've googled internet, but i couldn't find anything working.

I'm prisoned to vista :(

---

### Post by ukaratay on 2008-08-05
Does anybody has any idea?

---

### Post by dstew on 2008-08-05
Are you having a problem with a finished hard-disk installation, or with getting the Live CD or Alternate Install CD to run?

If the problem is with a finished installation, try booting in Recovery Mode (grub menu option). Choose the **xfix** option. That should get you a working desktop, but with poor resolution and no accelerations. If you get that far, then there are other things to try to get a better desktop.

---

### Post by ukaratay on 2008-08-06
> **dstew said:**
> Are you having a problem with a finished hard-disk installation, or with getting the Live CD or Alternate Install CD to run?

If the problem is with a finished installation, try booting in Recovery Mode (grub menu option). Choose the **xfix** option. That should get you a working desktop, but with poor resolution and no accelerations. If you get that far, then there are other things to try to get a better desktop.

In Live CD, I couldn't open the installation screen. Otherwise, alternate cd can open the installation and finished it. However, It couldn't run the X server. I tried xfix and changing the driver option in xorg.conf as I said, but they don't fix anything.

I've also reported it as a [bug]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/254908").

---

### Post by dstew on 2008-08-06
What happens when you boot in Recovery Mode, to a command line? Can you get that far?

---

### Post by ukaratay on 2008-08-06
> **dstew said:**
> What happens when you boot in Recovery Mode, to a command line? Can you get that far?

Yes, I can get there and i tried xfix and changing driver option in xorg.conf manuelly. But they don't work, same problem still remains.

---

### Post by dstew on 2008-08-07
After you boot to the command line, and type startx, what error messages do you get?

---

### Post by ukaratay on 2008-08-08
> **dstew said:**
> After you boot to the command line, and type startx, what error messages do you get?

Firstly, it gives memory error. Then, I change the driver option manuelly to ati and it gives no screen found.

---

### Post by ukaratay on 2008-08-14
I solved the problem, it's about memory management. Before boot, adding ```
mem=2900M
``` to kernel line solved the problem.

---

### Post by aconstantin on 2008-08-22
Hi, I'm having the exact same problem, only I'm using a M51S-1AAS, T8300, 4GB RAM, 250GB HDD.

Could you guide me to what I'm supposed to write & where ? 
I've tried adding "mem=4096M" (value that the memtest86 gave) to the end of the kernel line of the normal boot, but it still hangs on 
  "Running local boot scripts (/etc/rc.local)"
and the screen flashes.


Please help & thank you.

Alex.

---

### Post by vikrsyra on 2009-01-29
hello folks,
any answer abt this post? I have the same problem as you, as well using an asus laptop with ati radeon HD 3470. It happens that I'm kind of newbbie, I've just bought this laptop and now I realize why everybody complain about Vista, so I decided to change myself to ubuntu. However I'm having this problem with error messages saying that there is no screens, or something similar. I tried to do it in "recovery mode" as it is said. But I can't go that far the same happens with the liveCD, the graphic environment couldn't be started. So, what's your opinion? Any suggested solution?
I'll really apprecaite your help.
Thanks in advance!

---

### Post by markbuntu on 2009-01-29
when the menu screen comes up hit F4 and choose safe graphics mode. The live cd should then run properly. If you decide to install, make sure you select safe graphics mode before choosing install.

---

### Post by emoutal on 2009-01-29
I just found this thread and I'm having the same problem. I have tried safe graphics mode and it did the same thing.

---

### Post by emoutal on 2009-02-07
I was able to install ubuntu using the alternate install cd, but when I start ubuntu, it only gets to the command prompt, not the desktop. I can log into my account, but I don't know what to do after that. Could it maybe be that the drivers need to be updated?

---

