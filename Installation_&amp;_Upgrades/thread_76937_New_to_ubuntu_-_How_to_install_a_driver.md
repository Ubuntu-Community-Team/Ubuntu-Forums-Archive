---
title: "New to ubuntu - How to install a driver?"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by Superbrother on 2005-10-15
Hi guys!

I recently installed Ubuntu and I am very happy with it. But now I want to update my nvidia (geforce2 mx400) driver. I downloaded the file from the Nvidia website, but I do not know how to install the new driver. I am totally new at this, and I will appreciate if anyone can explain me a step by step process to install the new driver.

Regards!

Superbrother

---

### Post by claydoh on 2005-10-16
You won't need to use the driver from Nvidia, it is pretty easy:

Just open up synaptic, then go to settings/repositories, and make sure all the deb repositories are enabled (you can skip over any deb-src ones if you wish), then hit the "reload" button, and search for nvidia-glx, check it (but ***do not*** select the one called nvidia-glx-legacy), then click on "mark", then hit the apply button. It will select and install any missing dependencies alonf with the drivers.
Then you will need to open a terminal window and type in the following:
```

sudo nvidia-glx-config enable
``` 
This enables the nvidia related settings, etc. All that is left is to restart your X server by hitting ctrl-alt-backspace, and you should see the nice nvidia splash screen if all went well.

The latest drivers from nvidia can be installed, and there are how-to's here in the forums, but with your card, I do not think that they will offer you anything extra.

---

### Post by Superbrother on 2005-10-21
Thank you!!!! :D

---

