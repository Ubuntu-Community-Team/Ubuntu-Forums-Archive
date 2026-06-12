---
title: "Ubuntu and Red Hat EL 3 dual boot"
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by whci98 on 2006-10-07
I need to install Red Hat EL 3 along with Ubuntu Dapper Drake on the same hd. I have tried doing it once already and it did not work out. I first installed Red Hat and then Ubuntu. But only Ubuntu would load. 

Can someone please tell me how do I go about bual booting both?

---

### Post by Kateikyoushi on 2006-10-07
You copy the relevant part from the menu.lst of the first install into the menu.lst of the second one.

---

### Post by Herman on 2006-10-07
Hello, whci98, 
Kateikyoushi's solution should work well enough.

If you want to be be a little bit fancier, I recommend the 'configfile' boot style entry, and there are some other ways to do it as well.
You would first need to verify the exact path and name of Redhat's grub's equivalent of our menu.lst file. I believe it is /etc/grub.conf
If you aren't sure, you can check that either by booting Redhat (if you can), and taking a look, or by mounting it and taking a look. I think it is /etc/grub.conf from googling and perusing some Redhat Web Forum threads and How-To's.

If that is correct,  then all you need to do is add something similar to the following lines to the bottom of your /boot/grub/menu.lst file in Ubuntu, ```

title        Redhat Linux
configfile   (hd0,0)/etc/grub.conf
``` Where: Redhat is on partition number 1, or (hd0,0) in Grub's numbering lingo. If your Redhat has a different partition number, then please substitute the correct one here.
Where: Redhat Linux's  Grub menu configuration file is in /etc directory and is named grub.conf

Be sure to add that below the bottom of your automagic kernels list, not together with your Ubuntu entries, or it will be automagically deleted next time Ubuntu gets a new kernel, and the automagic kernels list updates grub.

The advantage of using the configfile command style of Grub entry for multi booting Linux distros, is that they will then all boot up by their own grub menu, which each operating system can keep up to date automagically, if they have that feature. If they do, or use some other equivalent method, then they always boot their most up to date kernels. You won't need to keep manually editing each grub menu to update it for new kernels every time. 

Operating System Entries for Multiple Booting More Linux Systems............................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")

Regards, Herman :D

---

### Post by whci98 on 2006-10-08
Thank You, Kateikyoushi and Herman for your help. It works now. I can can now dual boot Ubuntu and RedHat.

---

