---
title: "X server makes screen go blank"
date: 2005-03-21
forum: Installation &amp; Upgrades
---

### Post by yarivvv on 2005-03-21
Hello,

I just installed Ubunto on a Compaq Presario 2145us laptop. The installation went smoothly until the X server started, when the screen went blank.

I rebooted into recovery mode, and tried executing /usr/X11R6/bin/X, and the same thing happened: the screen went blank.

Does anyone know how I would go about resolving this issue?

Thanks,
Yariv

---

### Post by Ruby on 2005-03-22
Same problem here... some one sugested me to try apt-get upgrade, but looks like there is nothing to upgrade... what shuld i try next?

---

### Post by Tomy on 2005-03-23
[QUOTE=yarivvv]Hello,

I just installed Ubunto on a Compaq Presario 2145us laptop. The installation went smoothly until the X server started, when the screen went blank.

I rebooted into recovery mode, and tried executing /usr/X11R6/bin/X, and the same thing happened: the screen went blank.

Does anyone know how I would go about resolving this issue?

Thanks,
Yariv[/QUOTE]
When this happened to me I edited /etc/X11/xorg.conf and changed the device driver to "vesa". 
The section looks like this:

Section "Device"
        Identifier      "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
**# I changed the following line from "via" to "vesa"**
        Driver          "via"
        Option          "DisableIRQ"
        Option          "EnableAGPDMA"
EndSection

You might also try reconfiguring the x server. I think the command is:

sudo dpkg-reconfigure xserver-xorg

Tomy

---

### Post by yarivvv on 2005-03-27
hey Tomy,

your suggestion worked! thanks a lot!

FYI, my device name was "ATI", not "VIA," but when I changed it to "Vesa" it worked.

I wonder what the cause of the problem is. Does X not support my ATI drivers? That would be weird...

Thanks,
Yariv

---

### Post by Tomy on 2005-03-29
[QUOTE=yarivvv]hey Tomy,
your suggestion worked! thanks a lot!
Yariv[/QUOTE]
Great, I'm glad I could help a little. I am still learning linux and usually I'm the one who needs help

---

### Post by Tolaris on 2006-02-06
[QUOTE=yarivvv]
FYI, my device name was "ATI", not "VIA," but when I changed it to "Vesa" it worked.

I wonder what the cause of the problem is. Does X not support my ATI drivers? That would be weird...
[/QUOTE]

The ATI driver works pretty well - more likely the lockup is an IRQ conflict.  Try adding this option to the video driver section of your /etc/X11/xorg.conf file:

Option "DisableIRQ"

It should work with that and the ati driver.

Regards,
Tyler

---

### Post by Tolaris on 2006-02-06
[QUOTE=Tolaris]
Option "DisableIRQ"
[/QUOTE]

Nevermind.  The ATI driver doesn't support the "DisableIRQ" driver.  For options for your driver, run "man ati" or whatever driver you are using.

---

