---
title: "Installing Ubuntu to USB 3.0 drive with booting workaround"
date: 2015-09-05
forum: Installation &amp; Upgrades
---

### Post by kschepps on 2015-09-05
I have been trying to install Ubuntu to my USB 3.0 drive in an attempt to dual boot. I am posting this thread to convey my findings just in case someone else is trying to do the same thing I am. This is not a solution to boot into a USB 3.0, but instead a workaround. I searched for an actual solution, and I could not find anything which worked for my situation.

My reason to us a USB 3.0 drive is because my PC has limited storage and I'm looking to dual boot. I have a Samsung ATIV Smart PC Pro which barely has enough storage to comfortably hold Windows and all my applications.

Installing Ubuntu to USB 3.0 drive:
I used a 128G USB 3.0. I followed the instruction from the [How to install Ubuntu on a usb stick [duplicate]]("http://askubuntu.com/questions/307802/how-to-install-ubuntu-on-a-usb-stick") thread. However, I ran into issues booting into Ubuntu after installing. The PC would boot into a Grub command prompt screen. I tried to find a solution through the [Trouble booting from USB 3.0 Device]("http://ubuntuforums.org/showthread.php?t=1628665") thread, but unfortunately I could not find a preferred solution to boot from by USB 3.0 drive. I would have replied with these finding on the last thread, but it has already been closed so I started a new thread instead.

Issue booting from USB 3.0 drive:
The Samsung ATIV Smart PC Pro only has one USB port on  the main part of the PC and that is a USB 3.0. There are 2 more USB 2.0  ports on the removable keyboard, but I need to get into the BIOS in  order to boot from the USB and the keyboard blocks the Start Key  required to open the BIOS. I would need to use a small flat head screwdriver to push the Start Key when the keyboard is attached, and I did not want to do this every time I started Ubuntu because I didn't want to risk scratching my PC. Also, I want the option to remove the keyboard at any  time so I can use my PC as a tablet as it was designed. Therefore, I did  not want to use the USB 2.0 ports at all after installation. I discovered that my USB 3.0 port will  successfully boot USB 2.0 drives and my USB 2.0 ports will successfully  boot my USB 3.0 drive. 

Not preferred solution to booting issue:
My solution was to plug the USB 3.0 drive into a short USB 2.0 extension and then plug that into the USB 3.0 port. The only problem is Ubuntu is now running on slow USB 2.0 speeds, and it was noticeable. Programs would constantly freeze, and it was annoying. I wanted USB 3.0 speeds.

Analysing not preferred booting solution:
From my first attempt, I concluded that there is absolutely nothing wrong with booting from my USB 3.0 port or my USB 3.0 drive. I'm not entirely sure if the issue resides in my PC not being able to handle booting with the extra USB 3.0 pins active or if this was a Grub issue. However, Grub had no issues with USB 2.0 drives.

Solution to obtain USB 3.0 speeds:
I purchased a 2-port USB 3.0 hub and the smallest USB 2.0 drive I could find. I plugged the USB 2.0 drive and the USB 3.0 drive into the 2-port USB 3.0 hub. I reinstalled Ubuntu with this configuration, but I mounted /boot to the USB 2.0 drive and set the "Device for boot loader installation" to the same drive while mounting root and swap to the USB 3.0 drive. This configuration works great for me.

I hope this helps anyone trying to install Ubuntu to a USB 3.0 drive.

---

### Post by TheFu on 2015-09-05
Running an OS off USB of any type is problematic.  Some USB chips have major queuing issues. Basically, they can only deal with 2-3 storage requests at a time - more than that and the system gets confused and locks up.  I see this all the time.  Only the newest USB chips seems to have gotten around this issue. Add-in cards don't always help either.

There are times when running off USB works well. IME, those are the exception, not the rule. 
Or did I just have bad luck with all the systems and USB3 addon cards we've tried?  Have an MSI board with a USB3 addon (Core i5 CPU) that will lockup all 4 CPUs when doing transfers. It is sad, really.  OTOH, a newer G3258 CPU and Gigabyte MB doesn't notice any USB3 transfers - it happily moves the data at expected speeds without any other impacts noticed.  Who knew?

---

