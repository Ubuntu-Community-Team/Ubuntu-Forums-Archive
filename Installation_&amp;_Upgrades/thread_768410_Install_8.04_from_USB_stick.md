---
title: "Install 8.04 from USB stick"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by nikosm on 2008-04-26
Dear community,

I found these instructions on how to install the latest ubuntu from a USB stick since my laptop doesn't have a optical drive (I changed "gutsy" to "hardy"):

[http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive#The_Quick_Method](http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive#The_Quick_Method)

Of course I tried the quick method first:

sudo zcat boot.img.gz > /dev/sdb1

Then I should copy the alternative CD iso, but that doesn't work because I am told that there is not enough space! Indeed, if I open it with gparted it shows that only abour 250 MB are free. If I select all files it sums up to 7.4MB which is next to nothing (there are no hidden files, I checked).

I also tried with a 2GB stick, again the above command uses up almost the whole space (1.68GB out of 1.91GB).

What am I doing wrong? What occupies all that space?

I also tried the slow method, but nothing happens after selecting to boot from the USB stick (which is recognized correctly by the BIOS).

Any ideas?

Thank you very much,
Nikos

---

### Post by Pumalite on 2008-04-26
Maybe this helps:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by nikosm on 2008-04-26
> **Pumalite said:**
> Maybe this helps:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Hi Pumalite,

Yes! The script on the page you pointed at did the job (even though the descriptions is for gutsy, you can simply exchange the iso for hardy and it still works).

Thanks for your help!
Nikos

---

### Post by Pumalite on 2008-04-26
You are welcome. Good luck.

---

