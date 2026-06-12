---
title: "Cannot Install ubuntu/xubuntu 7.10"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by sentinel00 on 2008-03-17
Hi all,

on trying to run the UBUNTU 7.10 live cd, the splash screen appears and when the progress bar completes, my machine goes in an off/"hibernate" state.

I've downloaded XUBUNTU 7.10 alternate cd and installed the OS apparrently successfully. however, on loading from GRUB (i want to dual boot with my existing win XP install), the same thing occurs as with ubuntu.

Please note that I observed a "PCI: Cannot allocate resource region 3 of device 0000:00:00.0" at some point in the booting sequence with both ubuntu and xubuntu.


my config is :
asus P5RD1-V (BIOS 0907) w/ ATI X200 & Realtek ALC 8-channel audio integrated
512Mb DDR ram
3.0 Ghz LGA775 proc
120 Gb Maxtor IDE HD

Can anyone help please? 

Thanks

---

### Post by Peter09 on 2008-03-17
Are you sure its not just a black screen. Try <CTRL><ALT><F1> to see if you can get a system prompt.

PC

---

### Post by sentinel00 on 2008-03-18
Hi Peter09,

Tried <CTRL><ALT><F1> when the screen went off but did not work...each time i try to boot from 7.10 live cd (or xubuntu 7.10 alt. cd), the system goes into a ¨hang¨ state where I have to do a hard reset.

Note that I´ve installed ubuntu 7.04 ¨feisty¨ smoothly and it works fine.

Any idea please?

Thanks.

---

### Post by zo8890 on 2008-03-18
I've been having the same problem, almost exact aside from I used a burned alternate CD.  CD checked out, but I'm still not able to do anything after the OS loads.  Forces me to do a hard reset and problem comes up again.

Any help I'm sure would aid the both of us :)

---

### Post by Peter09 on 2008-03-18
I note that you can get to the system prompt with the alternate CD. Have you booted using recovery mode to get to the system prompt. Can you get a system prompt that way?

If not, then when the Grub prompt comes up hit the escape key, then the e key. This should give you the option to temporarily remove the quiet switch. Continue the boot and see what it says.

PC

---

### Post by sentinel00 on 2008-03-23
I can boot to ubuntu/xubuntu 7.10 using live cd in safe graphics mode. Think it's got something to do with the X200 GPU drivers but I'm not exactly sure how to proceed to solve the issue...

---

### Post by Skip Da Shu on 2008-03-23
> **sentinel00 said:**
> I can boot to ubuntu/xubuntu 7.10 using live cd in safe graphics mode. Think it's got something to do with the X200 GPU drivers but I'm not exactly sure how to proceed to solve the issue...

Installing Xubuntu 64b on various hardware (video) I always start with Live CD in safe graphics, do the install from their and then after install do a reconfig forcing it to use the VESA graphics drive.  This gives me least problems for headless machines, remote access via x11vnc and various monitors that might be occasionally plugged into them... might be worth a try.  I think the command is:```
sudo dpkg-reconfigure xserver-xorg
```  When running dpkg-reconfigure I take mostly defaults but I do tell it to use the kernel framebuffering (not the default) and the VESA driver.

---

