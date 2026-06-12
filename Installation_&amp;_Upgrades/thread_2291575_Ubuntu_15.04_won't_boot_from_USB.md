---
title: "Ubuntu 15.04 won't boot from USB"
date: 2015-08-21
forum: Installation &amp; Upgrades
---

### Post by blake12 on 2015-08-21
Hi all, 

I am pretty new to Ubuntu so please forgive me if this is an easy fix. I made a bootable USB using Universal USB installer version 1.9.6.1 which completed successfully. I then change my boot priority to removable device first the secondly HDD. Just as note this is a blank HDD plugged in and there are no other HDD's installed at this point in time. All the screen shows me is " DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER'. I have tried 2 separate USB keys and both do the same thing. Both are able to be loaded from windows to install Ubuntu and this also gives me an error while trying to install Ubuntu. The error i receive is 'Cannot download the metadata and therefore the .ISO'

Thanks in advance.

Blake

---

### Post by blake12 on 2015-08-21
I found the issue in regards to the booting from the USB problem I had. The USB even though being a removable disk is registered as a HDD which is why it wasn't booting from the USB. To fix this i went into the BIOS and under the boot priority of the HDD's installed on your computer and you can change which HDD is first in the sequence. As far as what the metadata issue is i am unsure. 
I hope this post may help others with the same issue i had. 
Cheers
Blake

---

### Post by ajgreeny on 2015-08-21
Did you download the ubuntu.iso file from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) and use that to make your install USB drive?  If not, exactly how did you create this USB?

I do not understand what the system means by  'Cannot download the metadata and therefore the .ISO' as the iso file should not be needed at this point unless you are doing something unusual or have gone wrong making the install medium.

However, perhaps I am misunderstanding your second post; have you now managed to boot to the USB and install Ubuntu to the hard drive?

If so, can you please use the Thread Tools menu at the top and mark this thread as SOLVED.

---

### Post by blake12 on 2015-08-21
> **ajgreeny said:**
> Did you download the ubuntu.iso file from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) and use that to make your install USB drive?  If not, exactly how did you create this USB?

I do not understand what the system means by  'Cannot download the metadata and therefore the .ISO' as the iso file should not be needed at this point unless you are doing something unusual or have gone wrong making the install medium.

However, perhaps I am misunderstanding your second post; have you now managed to boot to the USB and install Ubuntu to the hard drive?

If so, can you please use the Thread Tools menu at the top and mark this thread as SOLVED.

I downloaded the ISO from here: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) and then i installed it using this: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

After following the above method that is what error i was given. 

In regards to the bootable USB yes i did manage to boot from the same USB that i was trying to install through windows. 

Thanks for your response.

Cheers
Blake

---

