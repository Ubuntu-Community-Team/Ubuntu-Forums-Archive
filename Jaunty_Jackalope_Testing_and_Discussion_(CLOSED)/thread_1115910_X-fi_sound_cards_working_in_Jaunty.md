---
title: "X-fi sound cards working in Jaunty?"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ynnek63 on 2009-04-04
I have an x-fi Titanium Fatality Pro sound card that I have yet to get working in any flavor of Linux despite all the tutorials I have found on the net telling me how to install the driver from Creative. 
I was just wondering if Jaunty will support these cards out of the box? 
Had I known the issues that this card has with Linux, I would have bought something else, but it's to late now since I bought it at Circuit City.
Yeah, I know. I should have done my research.

thanks

---

### Post by olskar on 2009-04-04
> **ynnek63 said:**
> I have an x-fi Titanium Fatality Pro sound card that I have yet to get working in any flavor of Linux despite all the tutorials I have found on the net telling me how to install the driver from Creative. 
I was just wondering if Jaunty will support these cards out of the box? 
Had I known the issues that this card has with Linux, I would have bought something else, but it's to late now since I bought it at Circuit City.
Yeah, I know. I should have done my research.

thanks

Sadly creative seem to have abandoned Linux. 

> It has been a while since last mentioning the Creative X-Fi sound cards at Phoronix, but it's not because the Linux support is all nice and working now that Creative open-sourced their X-Fi driver, but rather things have stalled. The X-Fi sound cards still are a sore spot on Linux and there isn't "out of the box" support in major Linux distributions. 

[http://www.phoronix.com/scan.php?page=news_item&px=NzE2Ng](http://www.phoronix.com/scan.php?page=news_item&px=NzE2Ng)

I know I will never buy a creativeproduct again.

---

### Post by uweklosa on 2009-04-04
You could use Open Sound System: [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

---

### Post by terry_gardener on 2009-04-04
the x-fi soundcard is currently unsupported under alsa. please check the following 
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

---

### Post by glasen on 2009-04-04
You must patch a header file in driver sources that the Fatality Pro is supported. Just change the pci-id in the file to the one your card delivers, recompile the driver et voila.

1. Download the file "XFiDrv_Linux_Public_US_1.00.tar.gz" and unpack it.

2. Open the file "ctdrv.h" and change the ids according to the pci-id "lspci" delivers for your soundcard.

3. Save the file, compile the driver.

---

### Post by ynnek63 on 2009-04-08
> **glasen said:**
> You must patch a header file in driver sources that the Fatality Pro is supported. Just change the pci-id in the file to the one your card delivers, recompile the driver et voila.

1. Download the file "XFiDrv_Linux_Public_US_1.00.tar.gz" and unpack it.

2. Open the file "ctdrv.h" and change the ids according to the pci-id "lspci" delivers for your soundcard.

3. Save the file, compile the driver.

I tried your suggestions and it worked!  thanks!

---

