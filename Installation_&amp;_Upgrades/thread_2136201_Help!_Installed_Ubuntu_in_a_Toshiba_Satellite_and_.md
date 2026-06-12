---
title: "Help! Installed Ubuntu in a Toshiba Satellite and I don't have ethernet or wifi!"
date: 2013-04-16
forum: Installation &amp; Upgrades
---

### Post by ptown on 2013-04-16
I have a Satellite l875-s7308 and I'm trying to make it where I can go online using Ubuntu 12.04 that I installed.  Ethernet connection was working, but while trying to get WIFI to work on it I must have put in some command that now keeps me from getting online at all.  I need some help and please talk to me like I'm five. I'm new to Ubuntu and this whole new way of doing things.  My Mom hates Windows 8 which was on the computer previously and since I've used Ubuntu on an older pc with no problems I thought she would like the switch. However, that will not be the case if I can't get the internet to work on the laptop.  Any help is greatly appreciated!!

---

### Post by ubfan1 on 2013-04-17
Guessing you have the Realtek 8723ae and the Athros 8161 for ethernet, you can either download on another machine either the wireless tarball
rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz or a more current deb for the kernel (which should come with a working alx driver for ethernet).  Assuming you get the wireless tarball (google for it), move it you your Toshiba via usb, unpack it, and run "make"
Then run "sudo make install"
You might have to move the two firmware files in tarballdir/firmware/rtl8723* to the /lib/firmware/rtlwifi directory.
     sudo modprobe rtl8723e
and if wireless does not start, reboot.
After wireless works, run the software updater and that will bring in a working alx driver for a new kernel, and will force you to redo
the
make install for the wireless (necessary each kernel upgrade).

---

### Post by grahammechanical on 2013-04-17
So, what have you done? Re-trace your steps. Have you disabled Networking? Have you switched off networking by the keyboard? Laptops usually save battery power by switching off networking devices when they are not being used. Have you disabled networking in the BIOS? Is Windows still on that machine? If we switch off networking in Windows then the adapter is not activated when we load into Ubuntu.

Someone recently claimed that since installing Ubuntu they were unable to enter the BIOS. In fact they were unfamiliar with the machine and were pressing the wrong key for entering the BIOS. You need to work your way through the stupid little things to discount them. You need to tell us about what you see or what you do not see on that machine.

Regards.

---

### Post by pompel9 on 2013-04-17
I had the same trouble with my toshiba satelitte L955D. If you are going to do the manual install, then you have to install it every time the kernel is updated.

I solved the trouble by installing Ubuntu 13.04. It's in the final beta stage, and is stable. I have no trouble with it. It will be released on April 25. But you can safely install it now.

---

### Post by Rekhillbill on 2013-04-18
I have the same problem with my wife's Toshiba with a Realtek RTL8723AE & plan to wait unit April 25th for the formal release of 13.04.

I installed 12.10 on my older Tosiba & I am very happy with it.  I have a dual boot with Windows 7.

I have never used Ubuntu or any other distribution before.  So, I am headed back to the Absolute Beginners Section.

---

