---
title: "just can't seem to install....:("
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by travaciousd on 2007-11-03
im trying to install ubuntu 7.04 on  my hp 6000 notebook

i've downloaded the iso/successfully written it to a cd

when i boot my computer ubuntu boots and begins installation, however, shortly after  it begins i receive 
"error microcode 'bmc43xx_microcodes.fw'"

the download then continues for a few more minutes but always halts soon after 

have used linux in the past...but this is my first time trying to install it....any suggestions?

thanks

---

### Post by zvacet on 2007-11-03
Chek CD for errors.Chek md5sum.
[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

If some of these are not right download same iso with torrent and point download to the folder with existing iso.Torrent will chek your iso and replace corrupted files if you have it.After that burn it on lower possible speed.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29]("https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29")

---

### Post by travaciousd on 2007-11-03
thanks for the quick reply...tried that no errors :( 

heres exactly what happens:

*Starting kernal event manager... [OK]
*Loading hardware drivers...
error receiving uevent message: No buffer space available
firmware_helper[6767]: Main:  error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
[   177.086753] bcm43xx: Error:  Microcode  "bcm43xx_microcode5.fw" not available or load failed.
                                                                                                                                [OK]

*Loading kernel modules...                

at this point no progress is made (some times it goes a little further )

---

