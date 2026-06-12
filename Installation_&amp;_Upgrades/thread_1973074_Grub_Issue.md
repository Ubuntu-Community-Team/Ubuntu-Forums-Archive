---
title: "Grub Issue ?"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by nealaustin on 2012-05-04
Yesterday I upgraded loaded 11.10 onto a windows machine as a dual boot. I did change the grub to pause for only 3 seconds. Then I also installed all of the updates. Today I decided to upgrade to 12.04 but all I get is: 

[  31.537714][drm:drm_crtc_helper_setconfig] *ERROR* failed to set mode on[crtc:6]

and when I press enter then I get the command prompt. What can I do to to get to the desktop?

---

### Post by kc1di on 2012-05-04
> **nealaustin said:**
> Yesterday I upgraded loaded 11.10 onto a windows machine as a dual boot. I did change the grub to pause for only 3 seconds. Then I also installed all od the updates. Today I decided to upgrade to 12.04 but all I get is thecommand prompt. What can I do to to get to the desktop?

Try boot repair you can find it here;

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by nealaustin on 2012-05-04
Thanks, but....
the app did some stuff on my computer then asked me to reboot. This time I don't get any error message. but it does still end at the command prompt asking for the login. This is the paste bin info:

[http://paste.ubuntu.com/966898/](http://paste.ubuntu.com/966898/)

---

### Post by kc1di on 2012-05-04
how at the command prompt type the following and past any error messages you get here. 
```
sudo lightdm
```

---

### Post by nealaustin on 2012-05-04
thanks for your help kc1. I did get past the error messages. but to no avail.The computer continues but wouldnt load compiz. I  could get to the settings for the video card but not much else. somehow at the reboot the comuputer failed to set mode on crtc6. It's funny that this happend only in 12.04 (32). It happened from a clean install, an upgrade from 11.10, a dual boot install then upgrade from 10.10, and a dual boot from 12.04. I even tried all of the above with a new CD from a different mirror. I have now done a fresh install with 11.10 (32) and am leaving it there. Maybe in 1 or 2 rears I can buy an new system 76 computer. (It's my wife's 6 year old computer and a new one would make a good birthday present)

---

### Post by kc1di on 2012-05-04
Well it could be that it's just too old for 12.04.  But I would like to know what the video card is in it. As there have been problems with Nvidia cards and 12.04.

---

### Post by nealaustin on 2012-05-04
Yep it's a Nvidia and it uses the 173 driver. Even the 11.10 won't tell tell me which one it is. I can't find the manual anymore.

---

### Post by kc1di on 2012-05-04
> **nealaustin said:**
> Yep it's a Nvidia and it uses the 173 driver. Even the 11.10 won't tell tell me which one it is. I can't find the manual anymore.

That may be part of the problem your having with 12.04 as there is a but that affect some Nvidia cards.  

Good luck,
D ;)

---

### Post by oldfred on 2012-05-04
Article says nVidia has released a new version.
[http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ](http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ)
Fixing the performance regression of the 295.40 driver that affected GeForce 6 and GeForce 7 series hardware. 

If not GeForce 6 or 7 then you may have just needed nomodeset. 

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by nealaustin on 2012-05-04
Thanks Fred but i'm good now i'll stick with 11.10, andthanks kc1

---

