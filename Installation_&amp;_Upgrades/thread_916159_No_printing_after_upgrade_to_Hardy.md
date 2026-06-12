---
title: "No printing after upgrade to Hardy"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by BiggoCharley on 2008-09-10
I just upgraded from Dapper to Hardy and can't get my printer to work.  The printer dialog box shows the printer and that it is "ready" but when I try to print all looks ok but nothing happens.
The printer is a Brother multi function MFC-5840CN connected as a local printer.
Here is what i did so far to try to get it working. I completely removed it from the system, downloaded the cupswrapper driver from the Brother website, and reinstalled it.  I have switched USB ports to no avail.  I know the USB ports are mounting ok since I have a SD card in a card reader in the same hub I'm using for the printer and it shows up ok.  
Incidentally I have used this same printer successfully with Dapper as a local printer and as a network printer.  I currently have it connected as a local one.  I dual boot with XP and the printer works fine with XP so apparently the printer itself is ok. 
Any help will be much appreciated.

---

### Post by PaDV on 2008-09-14
Did you try installing the brother-cups-wrapper-extra package from multiverse as described here: [https://wiki.ubuntu.com/BrotherDriverPackaging](https://wiki.ubuntu.com/BrotherDriverPackaging) ?

---

### Post by BiggoCharley on 2008-09-14
> **PaDV said:**
> Did you try installing the brother-cups-wrapper-extra package from multiverse as described here: [https://wiki.ubuntu.com/BrotherDriverPackaging](https://wiki.ubuntu.com/BrotherDriverPackaging) ?

Thanks for your reply Pascal.
I tried this with the same results --except now the printer dialog box shows that there is a print job in the queue but under "Status" is "Stopped:job-stopped".

---

### Post by TopEnder on 2008-09-16
BiggoCharley,
I have a simalay set-up to you - dual boot Hardy 64 bit & Win XP but no network, when I changed from Ubuntu previous version I installed the printer drivers from Synaptic Package Manager, do a search for yor printer from within Synaptic Package Manager  - drivers are the same as I installed my printer/scanner.  I uninstalled all drivers (printers & scanner, dis-connect both power & USB cable, installed drivers,powered down re-connected cables powered up and the printer worked.  The Scanner functions was a bit of a problem but by used the post by BroardDWorld HOWTO: Ubuntu All Brother Printer & Scanner Driver Installation for Newbies! (a lot of post but worth the read) and using the Brother site I have the Scanner working by it's Control Panel or program like "Xsane Image Scanner".
Hope you get it working any problems then you can Private Message me, I have a few rough notes/points on the installation of the scanner that may help you and if so I'l post them on the forum.

---

### Post by BiggoCharley on 2008-09-17
Top Ender:
Can't thank you enough for your help.  I have been tied up on another project for the past day or so.  Can't wait to get a "hole" in my schedule so i can try your suggestions.  I will let you know by both post and private message how things turn out. Thanks again.
Charley

---

### Post by BiggoCharley on 2008-09-18
Top Ender:
the printer works like a charm.   I haven't done anything with the scanner as yet --I will continue to work on it.  I wasn't able to find the post "BroardDWorld HOWTO: Ubuntu All Brother Printer & Scanner Driver Installation for Newbies" that you referred to. 

Thanks again
Charley

---

### Post by timcredible on 2008-09-18
if it worked before updating, then broke, it's probably that you got a new kernel.  try using the old kernel and see if it works (you may need to reinstall all the printer driver/software).  choose the old kernel at the grub boot screen to test.  if this works, you could just keep booting off the old kernel.

---

