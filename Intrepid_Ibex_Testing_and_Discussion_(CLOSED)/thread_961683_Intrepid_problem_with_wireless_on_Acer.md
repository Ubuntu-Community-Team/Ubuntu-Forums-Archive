---
title: "Intrepid problem with wireless on Acer"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Natsuko640 on 2008-10-28
I just recently upgraded my Acer from 8.04 to 8.10 and it has been causing me network problems. At first I couldn't connect to my encrypted network, but that didn't phase me as I had an unencrypted one as well. After receiving an update today, I could no longer connect to any network; and after a restart nm-applet does not run. 

I'm using a Linksys WUSB54GV2. The card is recognized in lsusb and lshw.

Any help is appreciated, thanks.

---

### Post by Malcolm Cringe on 2008-10-28
I'm experiencing a similar problem. I had installed some of the betas of Intrepid, and had wired and wireless networking fine. When I installed an update a few days ago, and both wired and wireless networking stopped working.

I'm running a recent beta update of Intrepid on my Acer Aspire One.

---

### Post by tshawkins on 2008-10-28
> **Malcolm Cringe said:**
> I'm experiencing a similar problem. I had installed some of the betas of Intrepid, and had wired and wireless networking fine. When I installed an update a few days ago, and both wired and wireless networking stopped working.

I'm running a recent beta update of Intrepid on my Acer Aspire One.

There was a recent change to remove the ath5k wireless driver from the kernel as it was causing problems, Im using an AAO too, and the only way to get it working is to install the linix-backports-modules, then the wireless works again. Re the wired network, im not sure what is happening there, it works fine on my current 8.10 on the AAO

---

