---
title: "Xorg can't find video driver (Lucid)"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MarcoPau on 2010-03-19
Hello, after upgrading to Lucid I can't load radeon driver thou xserver-xorg-video-ati and -radeon are installed. Xorg will try to load module ati but it says it's not present, thou ati_drv.so is there, as well as radeon_drv.so.

Thus I tried setting up a xorg.conf file, but Xorg won't just read it (log still says "using built in configuration file").

Do you guys have any hint?

TIA

PS: Xorg log pastebin: [http://pastebin.com/1NanSedR](http://pastebin.com/1NanSedR)

---

### Post by MarcoPau on 2010-03-19
The weird thing is that xserver-xorg-video-vesa is not there, and so isn't /usr/lib/xorg/modules/drivers/vesa_dri.so. But still it's using vesa driver... what the hell?!

---

### Post by Chame_Wizard on 2010-03-19
Check if you can install the proprietary drivers via Hardware Driver.

Otherwise removed all drivers present and reinstall them again.

---

