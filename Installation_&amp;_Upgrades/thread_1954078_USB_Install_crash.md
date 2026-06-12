---
title: "USB Install crash"
date: 2012-04-07
forum: Installation &amp; Upgrades
---

### Post by chechr on 2012-04-07
Hi,

I've created a boot USB as follows:

- From Windows7 Home Premium
- insert USB (kingston 4gb)
- Run Universal-USB-Installer-1.8.9.0
- choose image: ubuntu-11.10-desktop-i386.iso 
- checked the format box
- seems to run well, no errors. 
- I eject the USB drive.

I plug the USB into the read port of a brand new build. 
- Asus F1A55-M LE Motherboard
- AMD A4 3400 APU
- 4 Gigs of RAM
- No hard drives installed

When I power on the machine I get the "Installer boot menu" screen.
The menu options are: 
-Run ubuntu from this USB
-Install ubuntu on a hard disk
-Test Memory
-Advanced options
-Help

If I pick "Run ubuntu from this USB" I get a few screens full of system messages, too fast to read them, and then a blank screen with the machine hung.

Any ideas what's wrong?

Thanks,
Chris

---

### Post by 2F4U on 2012-04-07
What graphics card do you have? Some ATI and nVidia cards cause problems. Can you try the nomodeset boot option? It is accessible through F6 in the boot menu.

---

### Post by chechr on 2012-04-07
No graphics card, the AM A4 APU has built in graphics ( Radeon HD 6410D)
I tried F6 on the boot menu, no response. I tried all the F keys, nothing.
Under advanced options there is only a 'back' choice.
Thanks

---

### Post by chechr on 2012-04-07
Hmmm, if I press TAB I can edit the menu entry. The 'run ubuntu' menu has the following command:

/casper/vmlinuz noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz splash_--

Should I change something?

---

### Post by chechr on 2012-04-07
Might be a problem with the AMD A4 APU. Here's a comment from a reviewer:
[COLOR=SeaGreen]
*Cons:* I've had quite a bit of trouble with Linux OS's. Live  CD's hang and won't load video. Until the Linux community addresses  this, this will be a problem. I was able to get Ubuntu 10.04 to run, but  not Ubuntu 11.10 or openSUSE 12.1.[/COLOR]

[COLOR=Black]That would really suck, I'm building this machine specifically for linux.[/COLOR]

---

### Post by 2F4U on 2012-04-07
From this thread it looks as if using nomodeset could be worth a try:

[http://www.linuxquestions.org/questions/linux-hardware-18/installing-any-linux-on-amd-a4-3400-box-925292/](http://www.linuxquestions.org/questions/linux-hardware-18/installing-any-linux-on-amd-a4-3400-box-925292/)

While the guy from the thread uses 12.04, it could also work with 11.10.

---

### Post by chechr on 2012-04-07
Excellent, looks promising. Thanks.

---

