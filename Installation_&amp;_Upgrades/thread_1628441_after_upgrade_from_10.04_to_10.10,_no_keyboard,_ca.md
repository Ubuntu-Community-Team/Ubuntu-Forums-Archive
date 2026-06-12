---
title: "after upgrade from 10.04 to 10.10, no keyboard, cannot login"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by avary on 2010-11-22
Hello,
just did upgrade from kubuntu 10.04 to 10.10.. after all done and reboot, when the login box shows up, my keyboard and laptop pad ( mouse ) dosn't work, (plugged in the usb mouse, it works sometimes, but never keyboard).
i went to recovery , the boot hung up when it says
 
```
[    17.704053] EXT4-fs (sda9): mounted filesystem with ordered data mode
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.

```
stuck here. nothing works except ctrl+alt+del
how to fix this? if this is not fixable, how i can revert back to 10.04? ( i'v searched the forum , saw few posts about loosing keyboard and mouse after 10.10 upgrade, but no solutions ) .. ?
 
 
[COLOR=red]**edit : solved it by booting from livecd, and mouting HD, chrooting and reinstalling upstart . seems that something went wrong during installing the packeges .**[/COLOR]

---

### Post by avary on 2010-11-23
just tried booting from livecd, and updated grub , but no change. also tried booting manually from grub command line, also no change.. everytime stuck at 
 
Begin: Running /scripts/init-bottom ...
Done.
 
so it is not grub problem . what to do ? if it is important i have ATI mobility radeon HD 5470 card .

---

### Post by ioargento on 2010-11-26
Why is this marked as 'solved'? There is no solution here, not even a msg that says that the problem has been solved.

---

### Post by avary on 2010-11-30
sorry for the confusion, i'v edited the main msg.

---

### Post by pgmagallanes on 2011-02-08
I'm still a bit confused: what does

 "chrooting and reinstalling upstart" mean?

Thank you.  I have a similar problem.

---

### Post by ytsionis on 2011-08-13
The SOLUTION  is [COLOR=Lime][HERE]("http://maarten.hondelink.com/index.php/No_Keyboard/mouse_when_upgrading_from_9.04_to_10.04_%28linux_Mint_7_upto_9%29")[/COLOR]

stop wasting your time 

i upgrade  to 10.04 and facing no mouse/keyboard after some googling found the right source...i hope this work for u too...:wink:

---

