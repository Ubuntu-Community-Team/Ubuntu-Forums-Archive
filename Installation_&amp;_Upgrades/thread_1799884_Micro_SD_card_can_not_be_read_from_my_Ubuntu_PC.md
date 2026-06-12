---
title: "Micro SD card can not be read from my Ubuntu PC"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by Peter2009 on 2011-07-08
Dear all,

I am trying to read my SD car trough the external car reader but it does not work.

A bit of maybe relevant info:
it a SD adaptor with a micro SD memory of 1 G
It came from a nokia phone.

what I know its working:
the micro SD card is working came out my mobile phone
the reader is working I have tested with other SD card 
the only left is the adaptor but very unlikely

Could some one help to with the command from the terminal to find the SD car drive name, mount it, and formatted?

Thank you in advance,

---

### Post by Peter2009 on 2011-07-08
> **Peter2009 said:**
> Dear all,

I am trying to read my SD car trough the external car reader but it does not work.

A bit of maybe relevant info:
it a SD adaptor with a micro SD memory of 1 G
It came from a nokia phone.

what I know its working:
the micro SD card is working came out my mobile phone
the reader is working I have tested with other SD card 
the only left is the adaptor but very unlikely

Could some one help to with the command from the terminal to find the SD car drive name, mount it, and formatted?

Thank you in advance,

A update!!!

do a sudo dmesg|grep mmc

and I get

[    0.813311] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   18.545764] ricoh-mmc: Ricoh MMC Controller disabling driver
[   18.545767] ricoh-mmc: Copyright(c) Philip Langdale
[   18.547239] ricoh-mmc: Ricoh MMC controller found at 0000:02:09.2 [1180:0843] (rev 12)
[   18.547566] ricoh-mmc: Controller is now disabled.
[   18.608102] Registered led device: mmc0::
[   18.609336] mmc0: SDHCI controller on PCI [0000:02:09.1] using DMA
[  899.104088] mmc0: error -110 whilst initialising SD card
[ 2028.667963] mmc0: error -110 whilst initialising SD card
[ 2342.633067] mmc0: error -110 whilst initialising SD card
[ 2348.960901] mmc0: error -110 whilst initialising SD card
[ 2534.544059] mmc0: error -110 whilst initialising SD card
[ 5274.819980] mmc0: error -110 whilst initialising SD card
[ 6337.196833] mmc0: error -110 whilst initialising SD card
[ 6860.544963] mmc0: error -110 whilst initialising SD card

I have tried lots of things!! but nothings work!

---

### Post by Peter2009 on 2011-07-08
> **Peter2009 said:**
> A update!!!

do a sudo dmesg|grep mmc

and I get

[    0.813311] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   18.545764] ricoh-mmc: Ricoh MMC Controller disabling driver
[   18.545767] ricoh-mmc: Copyright(c) Philip Langdale
[   18.547239] ricoh-mmc: Ricoh MMC controller found at 0000:02:09.2 [1180:0843] (rev 12)
[   18.547566] ricoh-mmc: Controller is now disabled.
[   18.608102] Registered led device: mmc0::
[   18.609336] mmc0: SDHCI controller on PCI [0000:02:09.1] using DMA
[  899.104088] mmc0: error -110 whilst initialising SD card
[ 2028.667963] mmc0: error -110 whilst initialising SD card
[ 2342.633067] mmc0: error -110 whilst initialising SD card
[ 2348.960901] mmc0: error -110 whilst initialising SD card
[ 2534.544059] mmc0: error -110 whilst initialising SD card
[ 5274.819980] mmc0: error -110 whilst initialising SD card
[ 6337.196833] mmc0: error -110 whilst initialising SD card
[ 6860.544963] mmc0: error -110 whilst initialising SD card

I have tried lots of things!! but nothings work!

I think its this one but I am not 100% sure

[http://hardware4linux.info/component/24782/](http://hardware4linux.info/component/24782/)

Why appear ricoh-mmc: Controller is now disabled.?

Regards

---

### Post by Peter2009 on 2011-11-21
> **Peter2009 said:**
> I think its this one but I am not 100% sure

[http://hardware4linux.info/component/24782/](http://hardware4linux.info/component/24782/)

Why appear ricoh-mmc: Controller is now disabled.?

Regards

Sorry for the delay on here! I have solve by getting a new SD card. I will get back to this as soon as I get some time!

---

