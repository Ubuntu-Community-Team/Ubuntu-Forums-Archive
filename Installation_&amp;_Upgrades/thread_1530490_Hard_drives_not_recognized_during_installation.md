---
title: "Hard drives not recognized during installation"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by Bi7wise on 2010-07-13
So I just put together a new desktop, and I'm running Windows7 on it.  No problems from the hard drives there.  However, I'm trying to dual boot Ubuntu, and I'm running into trouble during the installation.  When it prompts me to prepare the hard drives, neither of them show up in the list.  One is a 40 gig ssd, the other is a typical TB drive.  I have them connected via 6gb/s SATA.  Neither drive has ever been in raid as far as I know, but I did try sudo apt-get remove dmraid, just in case.

Any ideas?

---

### Post by moose4 on 2010-07-13
I recently installed Ubuntu after installing Windows7. I just used the Ubuntu ISO disk( I made from downloading the file) with Windows running. Open wubi.exe and it should recognize the hard drive where Window7 resides. It asks what space you want to allocate to Ubuntu (default is 17 GB, I used 20 GB. It proceeds to install Ubuntu and then when the computer restarts you should see both Window and Ubuntu. The second hard (without Windows installed) is recognized from both Window and Ubuntu OS. Ubuntu can be uninstalled when in Windows.

---

### Post by Bi7wise on 2010-07-14
> **moose4 said:**
> I recently installed Ubuntu after installing Windows7. I just used the Ubuntu ISO disk( I made from downloading the file) with Windows running. Open wubi.exe and it should recognize the hard drive where Window7 resides. It asks what space you want to allocate to Ubuntu (default is 17 GB, I used 20 GB. It proceeds to install Ubuntu and then when the computer restarts you should see both Window and Ubuntu. The second hard (without Windows installed) is recognized from both Window and Ubuntu OS. Ubuntu can be uninstalled when in Windows.

 So I tried this and it generates this error:  (initramsfs) /scripts/casper-premount/20iso_scan: line 46: can't open /dev/sr0: No medium found Cound not find ISO /ubuntu/install/installation.iso This could also result because of an operating system crash..blah blah, run chkdsk /r in windows, blah.  Obviously I tried their recommendation and then installing, but no luck.  I have a feeling that this is because both of my hard drives are using sata 6gb/s. Has that been a problem for anyone else?    Edit: I think both of my hard drives are sata II, so I'll try switching ports and report back later.

---

### Post by oldfred on 2010-07-14
I did see one other user with the new 6gb/s drives and he was not pleased as he had to set it back to 3gb/s to make it work. I do not know if there is a fix available. You may want to review bug reports and if none create one.

But some comments say the faster speed is not really used yet:
[http://forums.techguy.org/hardware/923405-solved-ensuring-sata-6gb-s.html](http://forums.techguy.org/hardware/923405-solved-ensuring-sata-6gb-s.html)

[http://superuser.com/questions/148843/why-does-ubuntu-10-04-not-see-my-hard-drives](http://superuser.com/questions/148843/why-does-ubuntu-10-04-not-see-my-hard-drives)
This says for Gigabyte:
FWIW, the Gigabyte page for your motherboard [gigabyte-usa.com/Products/Motherboard/…]("http://www.gigabyte-usa.com/Products/Motherboard/Products_Overview.aspx?ClassValue=Motherboard&ProductID=3317&ProductName=GA-X58A-UD3R/") has the following cryptic comment at the bottom. "Due to different Linux support condition provided by chipset vendors, please download Linux driver from chipset vendors' website or 3rd party website."

---

