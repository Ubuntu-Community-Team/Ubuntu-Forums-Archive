---
title: "Boot question for USB and card reader using Ubuntu"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by gurgsnekr on 2011-06-20
Hello,

I am working on an idea but I need to bounce it off others.  I did not know what forum to ask this so I decided to start here.  

My bios does not support booting to a card reader but it does support booting to a USB.  I was wondering if it is possible to boot to the USB into a DOS environment then run Ubuntu from the card reader.  If so, would it be possible to remove the USB stick? 

I know, it sounds kind of weird :D.

Thanks
gurgsnekr

---

### Post by vader95 on 2011-06-20
I don't know why you would want to do this instead of just using a live USB, but you might be able to get to grub from the usb and try to use it to boot into ubuntu from the card reader.

---

### Post by gurgsnekr on 2011-06-20
Hey Vader,

Thanks for the response.

The hard drive on my netbook broke just over a week ago.  I removed it and switched to using a Live USB.  It works great and I am loving it but I am getting worried about the USB stick.  It physically sticks out and I am afraid it is going to break off no matter how careful I am with it.  

Back in the Windows 98 era, it was not uncommon to boot to a DOS environment via floppy before booting into Windows 98.  I got to thinking about this and thought it might be possible to do something similar.  Boot to a USB in a DOS environment or similar then switch to the card reader and boot to Ubuntu from there.

If I can find a way to boot to the card reader I can stop worrying about the USB stick and give me more options.

---

### Post by vader95 on 2011-06-21
Perhaps if you use grub from the flash drive and then chainload to the card reader.

---

