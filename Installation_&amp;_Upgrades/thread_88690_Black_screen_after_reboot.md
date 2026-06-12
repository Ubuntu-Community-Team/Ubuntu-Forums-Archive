---
title: "Black screen after reboot"
date: 2005-11-10
forum: Installation &amp; Upgrades
---

### Post by trelirodia on 2005-11-10
Dear all, 

I finally got the time and upgraded to Breezy from Hoary and everything looked great until I decided to reboot! All processes seem to terminate nicely, but when it comes to the point of restarting ... it just freezes printing a restart ... message. After that you need to turn it off manually (ie press the button). 
I have a sony fs195xp laptop (dual-boot) and had no problems what so ever with hoary. I did not have any problems with shutdown, only reboot. X works fine and there aren't any detectable errors on the logs either. 

Does anyone have a clue what else should I be checking and how should I solve this? I'd hate having to shutdown everytime I need to reboot :) 

Thanks for all the help

---

### Post by trelirodia on 2005-11-11
Solution found after a bit of a search. If you are experiencing similar issues have a look below. The reboot problem is apparently a bug that has now been reported and will be fixed in the next release.

The quote below is posted here: [http://www.ubuntuforums.org/showthread.php?t=75314](http://www.ubuntuforums.org/showthread.php?t=75314)

Many thanks to varunus and Matthew Garett. 

[QUOTE=varunus]Guys, I found out the problem!

I posted to a bug report, and Matthew Garett was kind enough to give a fix.  This issue will be fixed in dapper, but until then, follow the following guide:

Open up your /boot/grub/menu.lst file using:

```
sudo gedit /boot/grub/menu.lst
```

Find your kernel lines (mine is 686, yours could be 386 or k7):

```
title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot
```


Change it to:
```

title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash reboot=h
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot
```

(Add the reboot=h to the end of the kernel line.)

Reboot once again by turning off and on, and the next time you boot up and reboot, you'll be able to choose reboot from System->Log Off![/QUOTE]

---

