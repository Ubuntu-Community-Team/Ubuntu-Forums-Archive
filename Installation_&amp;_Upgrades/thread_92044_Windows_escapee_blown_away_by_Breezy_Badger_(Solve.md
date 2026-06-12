---
title: "Windows escapee blown away by Breezy Badger (Solved)"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by bistro on 2005-11-18
Hi

I've decided to try to move away from windows so I've just installed ubuntu 5.10. So hello to you all.

Seemed to install OK apart from not finding a network (I'm not on one!) & I installed the Grub thingie for dual boot OK (please forgive me if I get some words wrong, I've just learned 1,000 new ones in the last hour).

Anyhow, despite half-a-dozen attempts the screen always freezes after I've entered my password. I get a "failed" notice for "synchronising clock to ntp.ubuntulinux.org" each time Ubuntu starts. Is this anything to do with it?

Thanks very much!

Regards

Dave

---

### Post by tseliot on 2005-11-18
1) Do you insert your password from the graphical interface or from the command line?

2) What's your graphic card model?

---

### Post by bistro on 2005-11-18
Hello

1. I logged in from graphical interface

2. It's a radeon x600 series graphics card

---

### Post by canadianwriterman on 2005-11-18
[QUOTE=bistro]I get a "failed" notice for "synchronising clock to ntp.ubuntulinux.org" each time Ubuntu starts. Is this anything to do with it?
[/QUOTE]

No, this "failed" notice just means that Ubuntu was not yet connected to the Internet during that stage of the bootup, therefore, it couldn't sych the clock online. Once you can get logged on, you can disable that synch in the Terminal with:

$ sudo apt-get remove ntpdate

---

### Post by ubuntu27 on 2005-11-18
Failed to  "synchronising clock to ntp.ubuntulinux.org"

that thing only happened to me when I DON'T have Internet. So, that must eb the case for you too. 
I am not an expert with Linux and Ubuntu, but, I beleive that it is safe to ignore. Correct me if I am wrong. [I had this error many times when my ISP closed my connection, and didn't have any problems with the comp]

---

### Post by tseliot on 2005-11-18
[QUOTE=bistro]Hello

1. I logged in from graphical interface

2. It's a radeon x600 series graphics card[/QUOTE]

Restart your computer and boot in "Recovery mode" from the Grub menu (keep on pressing ESC as soon as you have rebooted so as to get to that menu).

It will take you to the command line:

Type:

sudo nano /etc/X11/xorg.conf

Then find the section Device and make sure the word I put in red is &#8220;vesa&#8221;:

Section "Device"
Identifier "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
Driver "[COLOR="Red"]vesa[/COLOR]"
BusID "PCI:1:0:0"

CTRL+O to save (yes, use the same name and overwrite the file)
CTRL+X to exit

Then type:
startx

If it works (and you see the graphical interface) then you can restart your computer

---

### Post by bistro on 2005-11-18
Dear tseliot

thank you very much indeed, that fixed it - I'm up and away now!

best wishes

Dave S

---

### Post by tseliot on 2005-11-18
[QUOTE=bistro]Dear tseliot

thank you very much indeed, that fixed it - I'm up and away now!

best wishes

Dave S[/QUOTE]

Now you can enjoy your Ubuntu :)

---

