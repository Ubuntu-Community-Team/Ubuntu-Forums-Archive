---
title: "Printer install problem in Mint"
date: 2017-03-02
forum: MINT
---

### Post by kurja on 2017-03-02
Hello,

I connected a Linux Mint laptop to a new Samsung M2070W printer, it shows as expected with lsusb, launched the Printers app to add/configure it, and it seems to be recognized OK, but adding it I get a dialog where I have to specify a driver to use for the specific model; but that printer model is not listed as an option. I tried choosing a few other models but printing did not work, print dialogs show up as if it was working fine but the printer doesn't actually wake up or do anything. I removed the printer from the Printers app and downloaded & installed the Samsung driver from their web page (extracted the tarball and ran sudo ./install.sh) and tried adding the printer again but I saw no difference of any kind.

Odd thing is that on my Ubuntu laptop I could just plug it in, add it in Printers and it automagically found the right driver and it just worked. I'm kinda stumped on how to troubleshoot this on Mint... help?

---

### Post by howefield on 2017-03-02
Thread moved to the "*MINT*" forum.

---

### Post by kurja on 2017-03-05
Samsung's web site isn't too clear on what drivers to download, and I found two different versions there - 1.00.29 and 1.00.37_00.99, and with the latter version everything "just worked". Marking as solved

---

