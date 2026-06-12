---
title: "Install problem with AMD Duron"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by dutchfisher on 2011-01-25
Hello,

I have an install problem with 10.04 LTS Live CD on a Amd Duron 1.2mhz 384mb 120gb Nivida TNT2 WinXP SP3 already installed  PC
I've already installed on a DELL C840 and a DELL Insprion 530 with the cd no problems.

Attempting the very same act on the AMD had the boot run k for about 30 secs then the CD drive stopped and the Num Lock and Caps Lock light started flashing. I've had problems b4 with acpi with this motherboard when installing WinXP. So i set ACPI mode to S3 and OS PnP to no. Rebooted and the boot was just blank screen, no text, nothing. Rebooted  hit F6 put an x next to acpi=off and nomodeset. Choose Install from the menu. Result, black screen and flashing cursor.

Now stubbed, any ideas??

Cheers

---

### Post by Zzl1xndd on 2011-01-25
If you are using a LiveCD you might want to try the Alternate install CD. 

It uses a more traditional Text installer and will likely work better on a machine with such a low amount of ram.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by presence1960 on 2011-01-25
+1 on the [text based alternate CD]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate"). You don't have enough RAM to use the Live CD see [here]("https://help.ubuntu.com/community/Installation/SystemRequirements")

---

### Post by dutchfisher on 2011-01-25
Ah hah.

Thanks for that. 

I did just try an x next to edd in the install F6 This ran ok until i got error messages about SQUASHFS and then it stopped. Not sure if it makes any difference to your answer, but I go d/l your advice distro and see what happens.

Thanks again

---

