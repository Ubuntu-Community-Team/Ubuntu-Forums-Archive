---
title: "Initramfs prompt after live USB update"
date: 2015-10-05
forum: MINT
---

### Post by mahela007 on 2015-10-05
I'm trying to install Linux mint and I got the Live USB to boot. I installed the Nvidia driver on the live USB and also updated the kernel to 3.19 (without which the driver doesn't seem to work). However, on subsequent atempts to boot from the live USB, the boot fails and an initramfs prompt appears..
What could be going wrong?

(I already tried adding live-media=/dev/sdb1 to boot parameters without success)

---

### Post by Bucky Ball on 2015-10-05
*Thread moved to **MINT**.*

You might also like to try posting in the Linux Mint forums as well. These forums are primarily for the officially supported Ubuntu flavours, but you might get lucky with some help here. Good luck. :)

---

### Post by mahela007 on 2015-10-05
thanks..

---

### Post by yancek on 2015-10-06
If I understand you correctly, you are saying that you were able to boot to the Desktop using the Live usb and made some changes?  Is this a persistent install?  Otherwise, a Live CD/DVD/flash drive is a read-only filesystem and no changes will be saved on reboot.  I don't see how making any changes on it would affect the ability to boot however.

---

### Post by mahela007 on 2015-10-06
to be hones, I don't understand exactly what persistent means. But in my experience, changes can be made.. like for example, installing drivers. Files I create on the live USB also remain. 
Moreover, my problem was solved. It only occurred on the live USB. I just went ahead and did a full install and everything was OK.

---

### Post by yancek on 2015-10-06
> I don't understand exactly what persistent means. But in my experience, changes can be made.

That's it.  Changes can be saved on reboot.  If you put the same iso on a CD/DVD and boot it and use it, then it runs in RAM and any changes you make or data/files you create are gone on reboot.  There are a number of different software programs which will allow you to create a persistent flash drive which can be quite useful due to it's protability but if you are using a single computer, the full install is the best method.

---

### Post by Bucky Ball on 2015-10-06
> **mahela007 said:**
> ... my problem was solved. It only occurred on the live USB. I just went ahead and did a full install and everything was OK.

Does this mean you no longer have an issue? If so, please see the first link in my signature. Thanks. :)

---

