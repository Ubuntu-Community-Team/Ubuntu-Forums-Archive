---
title: "Ubuntu and Windows boot from different HDDs (+monitor question)"
date: 2011-12-29
forum: Installation &amp; Upgrades
---

### Post by XenoReseller on 2011-12-29
I have Ubuntu installed on a 750GB drive and windows installed on a separate 650GB drive. when they are both plugged in Ubuntu boots. I tried editing the menu.lst, but it doesn't seem to affect anything. I might be using grub 2, but I'm not sure.

Anyways, I'd like to add windows to the grub boot menu and make it appear. 

Also on a side note, I have a new monitor, but it doesn't allow me to use 3 monitors on one port...Is there a work around?

Thanks.

---

### Post by fantab on 2011-12-30
> **XenoReseller said:**
> I have Ubuntu installed on a 750GB drive and windows installed on a separate 650GB drive. when they are both plugged in Ubuntu boots. I tried editing the menu.lst, but it doesn't seem to affect anything. I might be using grub 2, but I'm not sure.
 
Anyways, I'd like to add windows to the grub boot menu and make it appear. 
 
I am assuming both your HDD are internal. Are they?
 
With both HDD "plugged in" from Ubuntu run following in Terminal:
 
```
sudo update-grub
```

---

### Post by darkod on 2011-12-30
When you tried to edit the menu.lst did it open as an empty file or it had content?

Because if it opened as empty it means you created a new file that didn't exist previously, and having menu.lst can confuse grub2.

Which version are you using and did you do a clean install or upgrade from version to version? If you did a clean install of 9.10 or later, you have grub2. For grub1 to still be there you would have to do upgrade after upgrade since 9.04 and tell it to keep grub1.

As fantab says, running upgrade-grub should detect other OSs and add them to the menu automatically. Many people disconnect other disks when installing ubuntu and the other OSs are not found at install so you have to do the update-grub after.

---

