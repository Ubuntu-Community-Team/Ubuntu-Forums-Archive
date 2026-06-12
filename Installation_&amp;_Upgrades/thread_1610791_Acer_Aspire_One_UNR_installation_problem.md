---
title: "Acer Aspire One UNR installation problem"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by triumpher on 2010-11-01
I have an Acer Aspire One Model no ZG5, with a Kingston 8GB SD card installed in the storage expansion slot on the left hand side.  It has been running Linpus quite happily since I bought it.  I decided to replace Linpus with Ubuntu Netbook Remix 10.10
 
I have created a bootable memory stick with UNR on it.  I can boot from that that and run the installation all the way through - answering all the questions, but at the end when the installation is completed and a reboot is required, the machine goes past the Acer startup screen and then just hangs with a flashing underscore cursor and will not do anything else at all.
 
I have tried downloaded the UNR iso file more than once and have tried different memory sticks, but despite many attempts the result is always the same.  I have successfully re-installed Linpus from a USB memory stick with recovery software on it, so I guess the hardware is OK?
 
Anyone got any ideas?

---

### Post by jrev on 2010-11-01
you could try to install via an external CD reader connected to the USB sockets (it cost me about 60 euros)

---

### Post by triumpher on 2010-11-02
I do have a USB CD/DVD drive, but I have been unable to find a single iso file for the netbook optimised version UNR 10.10
 
The download page only seems to offer the USB stick option, which downloads a zip file containing many files, with no option for the iso to burn to CD

---

### Post by mohnkern on 2011-01-27
I am seeing exactly the same thing, with both 10.10 and 10.04.


Did you find a solution?

---

### Post by crashbang on 2011-01-29
So justt to make sure I understand properly, you are trying to install unr on a sd card from usb? I was able to install unr 10.10 just fine on my HDD via usb on my aspire d250

---

### Post by sham63 on 2011-01-29
I just had this same problem when I went to install UNR on my Acer Aspire One. I tried it several times, but each time it would only boot to the flashing cursor after install. I then installed Easy Peasy 1.6, and it installed and booted without any problems. I believe this is based on Ubuntu 10.04, so I do not see how this would work, but not UNR.

Jim

---

### Post by Quackers on 2011-01-29
It could be that grub is getting installed to the usb stick, instead of the hard drive. If you install and the same thing happens, boot from the live usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Lordcorvin on 2011-02-13
Hey guys I have same problem, but I don't get flashing cursor or anywhere near that, what i get is an error with
Kernel Panic

---

### Post by crashbang on 2011-02-13
> **Lordcorvin said:**
> Hey guys I have same problem, but I don't get flashing cursor or anywhere near that, what i get is an error with
Kernel Panic

Are you getting the kernel panic after install or at boot? If at boot try one of the alternative Iinstall ISO. Just Google alternate ubuntu install.

---

### Post by Lordcorvin on 2011-02-13
> **crashbang said:**
> Are you getting the kernel panic after install or at boot? If at boot try one of the alternative Iinstall ISO. Just Google alternate ubuntu install.

It hapens when booting and tried to reinstall multiple times

---

### Post by crashbang on 2011-02-13
> **Lordcorvin said:**
> It hapens when booting and tried to reinstall multiple times

I had the same problem with Linux Mint on an old Toshiba laptop and ended up having to update the BIOS. If this is an older laptop I would check that first to see if a BIOS update is available first. When I get home I will find a link for the alternate unr ISO and try different options for noapci and avoid=off and such. Can you tell what it says after the kernel panic or does it go too fast to tell?

---

