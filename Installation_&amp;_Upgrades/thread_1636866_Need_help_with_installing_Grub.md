---
title: "Need help with installing Grub"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by poZiaC on 2010-12-03
Hello,

I am running Windows/Linux in dual boot mode. I have to reinstall Grub  to access my Linux. I have read in the Grub forums that I can reinstall  it from a Live CD using the command ```
sudo grub-install  /dev/hda 
``` However, I am not sure where the config file  for this installation will end up. How do I connect the new grub install  to the current grub.cfg I already have? Thank you.

---

### Post by kansasnoob on 2010-12-03
> **poZiaC said:**
> Hello,

I am running Windows/Linux in dual boot mode. I have to reinstall Grub  to access my Linux. I have read in the Grub forums that I can reinstall  it from a Live CD using the command ```
sudo grub-install  /dev/hda 
```. However, I am not sure where the config file  for this installation will end up.How do I connect the new grub install  to the current grub.cfg I already have? Thank you.

What can you boot right now?

---

### Post by Quackers on 2010-12-03
Are you using grub or grub2? Which version of Ubuntu are you using?
It would be better if you could please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by kansasnoob on 2010-12-03
> **Quackers said:**
> Are you using grub or grub2? Which version of Ubuntu are you using?
It would be better if you could please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
Code:

sudo bash ~/Desktop/boot_info_script*.sh

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

+1! It's impossible to start from nowhere :)

ATM all I could say is Ubuntu hasn't used the "hd" prefix for drives in a very long time.

We need to know what led up to this and what you can boot now.

And the output of the Boot Info Script is always helpful:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Quackers on 2010-12-03
kansasnoob, 
wasn't hd prefix used for pata drives? Not sure.

---

### Post by kansasnoob on 2010-12-03
> **Quackers said:**
> kansasnoob, 
wasn't hd prefix used for pata drives? Not sure.

Yes. It still is occasionally, for sure in Debian Lenny which is still their stable release. I haven't looked at Squeeze for several weeks.

The Boot Info Script differentiates very well.

I still sometimes use either an old DSL or Knoppix disc for troubleshooting and repairs. They still use hd but it doesn't really matter, you just want to pay attention to how the OS you're working with recognizes things.

Of course if you're working in a chroot then you're no longer working with the Live CD. Fdisk, parted or df will always tell you what the proper device designation is.

I wish I had the skills to post a video. It's really easy.

---

### Post by poZiaC on 2010-12-03
I don't have a live disk with me right now, but I'll try to get one tomorrow. The problem arose because I did a Windows install. I do know that I'm using Grub 2.

---

### Post by Quackers on 2010-12-03
Ok. It would really give us a much better idea of your current system (ie where everything is) if you can do as suggested in post #3 and post the output of the boot script. At least then more accurate advice can be offered.

---

### Post by ronparent on 2010-12-03
I think what you have to do is simply to reinstall grub 2. That process is relatively simple as presented here: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

---

