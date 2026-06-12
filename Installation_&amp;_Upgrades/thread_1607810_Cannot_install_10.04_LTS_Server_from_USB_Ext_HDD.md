---
title: "Cannot install 10.04 LTS Server from USB Ext HDD"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by benbooth on 2010-10-28
I can create the USB HDD installation image and it starts perfectly, but when it tries to copy installation files it fails saying 'No CD in drive' or similar. Of course there is not CD in the drive as I'm trying to install via USB HDD.

If I create a USB image based on the Live Desktop image it works perfectly.

Is there anyway to get around this?
Maybe a guide to installing Server via USB?

The site claims this can be done, but it simply doesn't work.

Ben

---

### Post by linux-hack on 2010-10-28
So if I understand wel your trying to install the server version with a USB key ? Am I geting this right ?

how did you make your key bootable ?

---

### Post by benbooth on 2010-10-28
+++++++++SOLVED!+++++++++

Once the USB image has been created on the USB device simply extract the contents of the ISO image used to the root of the USB device in a folder of the same name!
Then simply enjoy an error-free installation from USB of Ubuntu Server!

This was done using 10.10 Server x86_64.....will need to be tested on 10.04 x86_64.

Ben

---

### Post by linux-hack on 2010-10-29
Can you put a RESOLVED in the title of your post so other users having the same problem can easely find it.
Thanks

---

