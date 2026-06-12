---
title: "Ubuntu and Chrome OS Will Not Install"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by Luke oX on 2010-12-18
In the past, I have tried to dual boot Fedora, Ubuntu, and Chrome OS. I have only been successful with Fedora. When I put in the Live CDs for Ubuntu and Chrome OS, every thing seems fine. Every thing loads, and there is no problems. But after the install should load up Ubuntu or Chrome OS, my monitor just keeps switching between HDMI, Analog, Digital, repeatably, and nothing happens. Please help...

---

### Post by sikander3786 on 2010-12-18
Welcome to the forums :-)

Don't know about Chrome OS.

Regarding Ubuntu, highlighting the Ubuntu kernel entry in Grub menu, press 'e' to edit it. Navigate to words "quiet splash", delete them and type "nomodeset" in their place. Press Ctrl + X to continue boot. Hopefully you'll see the desktop this time.

Once on the desktop, go to System > Administration > Additional Drivers/Hardware Drivers and activate the recommended one's and the problem might go away for ever.

Regarding Chrome OS, can you install it to a normal desktop PC?

---

### Post by Luke oX on 2010-12-18
> **sikander3786 said:**
> Welcome to the forums :-)

Don't know about Chrome OS.

Regarding Ubuntu, highlighting the Ubuntu kernel entry in Grub menu, press 'e' to edit it. Navigate to words "quiet splash", delete them and type "nomodeset" in their place. Press Ctrl + X to continue boot. Hopefully you'll see the desktop this time.

Once on the desktop, go to System > Administration > Additional Drivers/Hardware Drivers and activate the recommended one's and the problem might go away for ever.

Regarding Chrome OS, can you install it to a normal desktop PC?

Thanks for the Ubuntu info, I'll try that. As for what you said about Chrome OS, are you asking if it is possible to install it to a desktop or if I've tried to install it to a desktop? I am trying to install it to my desktop.

---

### Post by sikander3786 on 2010-12-19
Where did you download Chrome OS? I think that needs to be compiled using Ubuntu?

---

### Post by Luke oX on 2010-12-19
> **sikander3786 said:**
> Where did you download Chrome OS? I think that needs to be ***piled using Ubuntu?

[http://getchrome.eu/download.php](http://getchrome.eu/download.php)

---

