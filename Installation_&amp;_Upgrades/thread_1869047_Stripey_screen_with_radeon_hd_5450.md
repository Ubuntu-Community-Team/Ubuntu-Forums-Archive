---
title: "Stripey screen with radeon hd 5450"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by Syrioth on 2011-10-25
I am trying to install ubuntu on my desktop however after i select run ubuntu before installing the next screen i get is coloured stripes. (it also does the same for install) I have searched for a solution but can only find one for after ubuntu is installed. Is there any way to get it to use a different graphics driver on install? or any solution? 
My graphics card is the radeon hd 5450, the motherboard has no on board graphics to use for install (asus formula IV) i have tried 11.10 and the LTS version.
sorry if this is posted in the wrong place, or is a duplicate thread.
 thanks

---

### Post by Syrioth on 2011-10-25
is there a way to install it in some form of safe mode?

---

### Post by 2F4U on 2011-10-25
You can try to add nomodeset to the grub kernel parameters and see if that helps.

---

### Post by Syrioth on 2011-10-25
ok how do i do that?

---

### Post by Hakunka-Matata on 2011-10-25
Ubuntu 11.10 Desktop i386 liveCD/USB (unetbootin) Boot to the liveCD, once you get the selection menu with blue background, press the [TAB] key, that should reveal the boot command line, add 'nomodeset' w/o quotes to end of line, leave a space before nomodeset.

When I press tab I get this:

> > /ubnkern initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --add a space and 'nomodeset' to the end of that line, hit enter to boot it.

I just tried it with deleting "quiet splash --" and replacing with "nomodeset", booted up no problem

---

### Post by Syrioth on 2011-10-26
ok ta very much.. just need to install the motherboards drivers now

---

### Post by Hakunka-Matata on 2011-10-26
There's not much to do when it comes to adding drivers for your motherboard.  Under System Settings, (see attached .png), select  Additional Drivers.

---

