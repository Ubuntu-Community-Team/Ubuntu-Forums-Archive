---
title: "[SOLVED] use usb grub to boot sdhc card"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by jonschin on 2008-10-07
I have a IBM X40 which had its HD die on me.  It has a built in sdhc card reader that i would like to use instead of getting a new HD.  I did a little research and found that the bios will not automatically boot to the sdhc card.  I know that i can set up my old 256 usb flash drive to load grub.  What i would like to do is use the usb to load grub and then have it load the os that i have already installed on the sdhc card.  I was wondering if this is possible?  mainly does grub have the capacity to load to a sd card like it loads to a hd, and if so what would i put the device as in the menu.lst for grub?

---

### Post by caljohnsmith on 2008-10-07
I think it *might* be possible, but only if Grub can use your BIOS on start up to access the SDHC card; i.e. your BIOS must at least recognize your SDHC card on start up, even if it is not possible to boot the SDHC card. I've never tried to do something like that, so I'm doubtful that Grub could boot the SDHC drive if BIOS won't boot it directly; but it wouldn't be too hard to find out.

If you all ready have Grub on your USB flash drive, boot that, and when you get the Grub menu press "c" for the command line. Then do:
```
grub> geometry (hd  
```
And press TAB for tab-completion. That should show you a list of the available drives, and hopefully your SDHC card will be listed. You can get info about a drive by completing that command:
```
grub> geometry (hd1)
```
That will give the partitions and drive size in sectors of (hd1) for example. If you can see your SDHC card that way, you might be able to use Grub to boot it. Let me know if you get this far and I can give you more specific instructions to help you boot the drive. Also, what OS is on the SDHC card?

---

### Post by jonschin on 2008-10-09
i got the usb to boot grub and was unable to see the sdhc card.  oh well these things happen.  on the upside i found a large usb flash for cheap so ill just use that.  to answer your question i was hoping to use ubuntu 8.04 which i will use on the usb.  Thank you for the timely response.

---

