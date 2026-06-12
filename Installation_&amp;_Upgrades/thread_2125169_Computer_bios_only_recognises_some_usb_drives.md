---
title: "Computer bios only recognises some usb drives?"
date: 2013-03-13
forum: Installation &amp; Upgrades
---

### Post by gwicks56 on 2013-03-13
Hi all, first time poster as i am new to ubuntu, not new to Linux or computers in general, but i have come accross a problem i have never had before, and a search of this and other forums seems to suggest it is not a problem many others have had, so I thank you all in advance for any help you may be able to offer.

I have a lenovo x220, and recently decided to run ubuntu off a usb drive rather than installing on the msata ssd i have in lappy. Installed 12.10 with univeral usb installer and it all worked fine, would boot up off a 16 GB sandisk cruzer i had. The problem was it was a very slow drive, 2MB a second, which made if painful. So i just bought a 32Gb sandisk extreme usb 3.0 drive - up to 100Mb/s read and write.

Followed the exact same procedure, but the bios simply does not see my new drive. Like not at all. f12 does not show up, in bios it doesn't, just not there at all. Now i am away at the moment so cant try it on another laptop ( may be able to try tomorrow), but i have never heard of such a thing. The drive works fine in windows, I have tried formatting to ntfs, fat 16 and fat 32. All work in windows, but cannot be seen by bios. Put the old 16gb drive in, and it boots up straight away. 

Now this is my first usb 3.0 stick, my x220 only has usb2 ports. Has anyone heard anything about this before? Seeinly my bios just does not recognise it, and for the life of me i cant think of anything else to try?

---

### Post by dabl on 2013-03-13
The first thing to do is to test that stick on another computer or two.  If there was some error installing grub on the mbr of the stick, then that would explain why it is not detected as a bootable device.

---

### Post by gwicks56 on 2013-03-13
except it's not that it is not recognised as a bootable device, its not detected at all. A non bootable usb will give an error message about boot loader missing, with this usb in drive it just ignores it and loads windows as though the stick is not in at all. But yes, will try on another computer ASAP, just bored at my hotel so trying to work it out ( these problems annoy me till i work them out)

---

### Post by dabl on 2013-03-13
I don't normally "see" a USB storage device in BIOS, unless it is a bootable device.  Non-bootable USB sticks or hdd's in USB enclosures in my computers do not appear in BIOS.

---

