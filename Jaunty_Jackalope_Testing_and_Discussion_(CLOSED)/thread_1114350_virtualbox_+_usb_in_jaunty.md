---
title: "virtualbox + usb in jaunty"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lime4x4 on 2009-04-02
running 64 bit jaunty all updates installed. I installed virtualbox from a .deb file from virtualbox's website. When i try to add a usb device it's greyed out. I remember from intrepid i had to add a line in my fstab file for usb to work properly. Must i do the samething in jaunty

---

### Post by forumache on 2009-04-03
I'm running 32 bits, Jaunty, fully updated, latest VirtualBox (2.1.4).

I don't need the line in /etc/fstab anymore. I had it in Intrepid, I removed it and still I am able to use USB devices. The problem was in VirtualBox, so make sure to use the latest version (although it was fixed in 2.1 (I guess) so any 2.1.x should be OK)

---

### Post by ju2wheels on 2009-04-03
FYI not to forget that USB support is in the closed source version only and not the OSE of Virtualbox. So although their download page doesnt make that too clear the downloads at the top of the page listed as "binaries" are the closed source and the ones on the bottom are the OSE.

---

