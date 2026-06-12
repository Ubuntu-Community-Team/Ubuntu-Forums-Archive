---
title: "Grub problem installing on a USB drive"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by mattperkins26 on 2007-08-13
Hi all!

I have been using Ubuntu at home for awhile, and I love it!  I also have a laptop and a 2 GIG USB drive, so I decided to install KUbuntu on the USB drive.

So everything works great except that now GRUB is being used as the boot menu and when I remove the USB drive, I get the error 21.  (I understand why this is happening.)   I would like to set up the following from my current situation:

1) With no USB drive connected, boot windows from the HD.
2) With USB drive connected, boot KUbuntu (with boot from USB selected in my lapop's boot menu.)

I can set up my laptop to boot from USB first.  I would rather avoid using GRUB as the boot menu and having to create a partition on my hard drive and all of that.  

Can I make the appropriate changes simply?  
Can I make the appropriate changes from what I've already done, or will I need to reinstall windows then reinstall KUbuntu with different settings?

Thanks in advance for your help!

---

### Post by sunami88 on 2007-08-13
Since noone has responded yet, Il throw in my .02.

Grab your Windows Recovery CD, and boot into "recovery console". Run  "fixboot" then "fixmbr"  and that will set the old Windows boot manager again. The only thing I'm not too sure about is if youl be able to boot from you USB key after that. You **SHOULD** be able to do a "one time boot menu" from your PC/laptop's bios (on my Dell is F12). Next time you install, make sure your /boot partition is on your primary hard drive.

Please note, I am in no way an expert. This is how I would tackle the problem. Wait for someone else to respond before taking my word as gospel, etc etc. This should at least fix it so you can boot into Windows.

---

