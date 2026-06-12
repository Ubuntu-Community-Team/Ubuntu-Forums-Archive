---
title: "Burning Ubuntu to USB does not work"
date: 2014-05-03
forum: Installation &amp; Upgrades
---

### Post by Charlie_Smith on 2014-05-03
I recently have tried to install Ubuntu 14.04 (Trusty Tahr) and I am using Ubuntu 12.04 (Precise Panglion)
I have opened up Startup Disk Creator and wiped my 8.0 GB USB. When I press the "Make startup disk" button, I get a error message that reads:An uncaught exception was raised:
[Errno 5] Input/output error
Plese help :eek:

---

### Post by Charlie_Smith on 2014-05-03
The USB has all the files though...

---

### Post by zombienerd1 on 2014-05-03
sudo apt-get install unetbootin

You'll be much happier with it vs Startup Disc Creator.

---

### Post by sammiev on 2014-05-03
> **zombienerd1 said:**
> sudo apt-get install unetbootin

You'll be much happier with it vs Startup Disc Creator.

+1 and if you still have problems use GParted to delete the USB and format it.

---

### Post by sudodus on 2014-05-04
If you still have problems with both Startup Disk Creator and Unetbootin, I suggest that you make a direct clone of the iso file. Use mkusb for a safe flashing process. See this link.
[URL="http://ubuntuforums.org/showthread.php?t=1958073"]
Howto make USB boot drives[/URL]

See this link for more details and alternatives

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Charlie_Smith on 2014-05-04
Thank you all. I will try the programs that you guys recomended and see later on today what the results are.

---

### Post by bapoumba on 2014-05-04
Please keep this bug in mind if you choose to reinstall : [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)
The wording is confusing and you may endup erasing everything. Depending on you situation.

---

### Post by Charlie_Smith on 2014-05-04
When I press the F12 key on my Toshiba Satellite running Windows XP it tells me this:
                                      Unetbootin
Default
Help
Try Ubuntu without installing
Install Ubuntu
Check disk for defects
Test memory
Boot from first hard disk

Invaild or corrupt kernel image
boot:

But the machine's BIOS version is 1.10, is that too old?
What should I put in for "boot"?

---

### Post by sammiev on 2014-05-04
Press F12 on a Toshiba Satellite when you first see the Bios screen and you should have a sub-menu pop up with 4 to 6 choices that you can boot on.

---

### Post by sudodus on 2014-05-05
> **Charlie_Smith said:**
> When I press the F12 key on my Toshiba Satellite running Windows XP it tells me this:
                                      Unetbootin
Default
Help
Try Ubuntu without installing
Install Ubuntu
Check disk for defects
Test memory
Boot from first hard disk

Invaild or corrupt kernel image
boot:

But the machine's BIOS version is 1.10, is that too old?
What should I put in for "boot"?

It seems to be Unetbootin's boot menu. Which of all those menu options did you try? (I suggest that you try more than one of them)

If still no go, try the USB boot drive in another computer.

Or try ***mkusb***.

-o-

I wouldn't try to change the BIOS. You arrived at Unetbootin's boot menu, so I think you can boot the computer from USB.

---

