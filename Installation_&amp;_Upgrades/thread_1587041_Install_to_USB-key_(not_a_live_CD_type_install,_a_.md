---
title: "Install to USB-key (not a live CD type install, a 'proper' install')"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by karlm on 2010-10-02
Hi folks :)


A friend of mine has a tiny-little netbook (Asus Eee PC 2G Surf) and the memory-card used for the harddrive is now dead...

So I came up with a bat-plan to use her 4GB USB key as the harddrive - the BIOS allows for booting from USB devices. 

I have installed the USB ISO from ubuntu's main page and it works flawlessly when booting...

However, the problem is - she needs it as a permanent installation - not just testing purposes. When we install something, it disappears the next time she boots. It doesn't seem to allow any kind of installations. 

On the desktop is an option to 'fully install' Ubuntu onto her computer. We tried that it keeps trying to install to the 'real' HD (the memory card that is built in, which is not only crap - but inadequate for a proper installation).


Is there a way in which I can make the USB act as if it were a 'real' hard-drive, so when we install a program it actually stays installed next time she boots?

All help appreciated :)

---

### Post by boublik on 2010-10-02
Check from your BIOS settings if you can boot from USB, get a bigger USB stick, since you're gonna be using it as your main storage device like a HDD. I would go for a 64GB and keep backing up. 
I installed 8.04 on an 8gb for troubleshooting and have avg anti-virus and this is what I did as far as I can remember:

-Format the USB stick to ext3.
-Disconnect your hard drive. 
-Plug in the USB stick 
-Run the_ live CD_ you were using, or 8.04. 
-Install and choose the USB as HDD (it should be the only one there you will know it by the size). 
-Restart and choose to boot from USB

Good Luck!!

Sorry I missed that you can actually boot from USB, you shouldn't have a problem. I googled that issue ages ago and one result came up where it says get a real external HDD to do this, among other things but couldn't be bothered so I did it the way mentioned above and it worked. So good luck again.

---

### Post by karlm on 2010-10-02
Excellent... Thanks for the ideas boublik. However, just an info, I've tried installing it to the pendrive while her card(harddrive) is still in, and the installer just will not show that the USB key is present when selecting drives to install to. 

I'm not sure where the card (harddrive) is physically located within the netbook, but if I can locate it I shall certainly give your idea a go! :)

Thanks again, Bert.

---

### Post by boublik on 2010-10-02
You might also try to format the stick to ext3 and try again might pick it up. Remember try to install from the CD to the USB. 

Cheers,

Boublik

---

### Post by karlm on 2010-10-16
> **boublik said:**
> You might also try to format the stick to ext3 and try again might pick it up. Remember try to install from the CD to the USB. 

Cheers,

Boublik

Excellent stuff! All sorted now thanks :)


I used a second USB drive to imitate a CDROM and installed it that way on to the EXT3 formatted USB key!

Thanks loads !!!

---

