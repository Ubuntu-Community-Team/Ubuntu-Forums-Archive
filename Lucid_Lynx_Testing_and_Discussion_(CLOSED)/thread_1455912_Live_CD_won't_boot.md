---
title: "Live CD won't boot"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by amd is the best on 2010-04-16
Hello Everyone,

I've been running 10.04 on my laptop for a month or so now, and am really liking it.  It runs great on my laptops hardware (AMD dual core 2.2 and ATI 4650) with ATI graphics out of the box.  So, I really want to install it on my desktop now and I am having no luck.  I set the PC to boot from CD, it brings up the purplish/pink ubuntu screen then just goes black, sits there and does nothing until I power it off.

Would anyone have and info on this?  I tried to search but didn't come up with much.

System specs:
AMD Phenom 940 (3GHz x 4)
8GB Memory
ATI 4850X2 (2GB)
2 WD Caviar Black 1TB in RAID 0

Thanks in advance!
Nick

---

### Post by ronparent on 2010-04-16
Same basic system specs similar results. You can try playing with the kernal boot options on the grub menu (hit e to edit the lucid boot line and <ctrl> x to execute).

Mine runs with the parameter nodmraid added and splash deleted. If your boot is getting as far as the background screen then dmraid is probably not involved. Try removing the splash parameter. Hopefully if that is it it will be corrected by final release. Also try nomodeset.

After playing with the kernel boot parameters you can make permanent the ones that work using **sudo gedit /etc/default/grub** to change them on the kernel line in the configuration file. My hp laptop with AMD 64 X2 incidently also worked out of the box. Good luck.

---

### Post by -Robert- on 2010-04-16
That sounds familiar...
I don't know if it's the solution for your problems but perhaps you could try this and see if it works (#3):  [http://ubuntuforums.org/showpost.php?p=9097425&postcount=22](http://ubuntuforums.org/showpost.php?p=9097425&postcount=22)

I'm having similar problems. I subscribed to some bug reports, but nowadays I still can't boot 10.04 without  editing the boot parameters. If I don't the Live CD just hangs at the Plymouth splash screen. I sure hope this will get fixed before April 29th. :(

---

### Post by cariboo on 2010-04-16
Have you tried nomodeset, available when you press F6 at the initial boot screen?

---

### Post by amd is the best on 2010-04-16
Thank you all for the tips however I just tried all of the above mentioned things and still no go.

---

### Post by jaco223 on 2010-04-16
> **amd is the best said:**
> Thank you all for the tips however I just tried all of the above mentioned things and still no go.

Maybe try turning off acpi. You can do this from the boot screen by pressing f6
selecting "acpi off" hitting enter, then hitting esc.

---

### Post by ronparent on 2010-04-17
amd is the best - I should have read your post more carefully. I am currently completely stalled on loading lucid on a raid0. My machine with the same specs as yours just will just not boot the live cd or an installed system without the nodmraid boot options. Otherwise the boot process will just stall when trying to mount the raid drives. Since dmraid is needed to see a fake raid array I have yet to find a way out of this loop. The tips I gave you will get the computer to boot lucid from the live cd or a non-raid drive, but, not from a fake raid! 

They might get it fixed for the release but I am not holding my breath. I've had to fight one fake raid issue or another since 8.04 and watch bug reports and fixes put on the back burner! I have no plans to install karmic, lucid or whatever follows until the problem is workable.

---

