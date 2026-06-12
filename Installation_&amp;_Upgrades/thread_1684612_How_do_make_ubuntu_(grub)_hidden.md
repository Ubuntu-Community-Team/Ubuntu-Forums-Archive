---
title: "How do make ubuntu (grub) hidden?"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by andrew1421lee on 2011-02-09
Hello WORLD!
and...I have a Problem..

I recently installed (dual boot with Windows 7 x64) ubuntu (10.10 x64) on a family computer and my siblings freak out when they see the Grub screen, as in they do not know what to do.

I searched on ways to hide it and foung this:

[http://ubuntuforums.org/showthread.php?t=1508028](http://ubuntuforums.org/showthread.php?t=1508028)

And I thought that the idea of having grub only showing up when a usb is connected pretty neat. The problem is that the forum post is nearly a year old and the Ubuntu installer no longer has 'Advanced' in it ( unless i missed it..)

Is there another way to do it?
Any alternatives to what I want to do?

---

### Post by Old_Grey_Wolf on 2011-02-09
You could install the "StartUp-Manager" from the Software Center. After it is installed it can be found on the "System > Administration" menu. You can select MS Windows as the default boot OS and set the grub timeout to something less than the default 10 seconds. 

If they don't do anything then after the timeout, it will boot into Windows.

---

### Post by Rubi1200 on 2011-02-09
I believe Grub Customizer will do something similar.

Check it out and the tutorial by drs305:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by presence1960 on 2011-02-09
Why don't you show them what to do when the GRUB menu appears. My 8 year old daughter tri-boots XP, 7 and Ubuntu 10.04, on her own machine-not mine. She knows how to choose what OS she wants to use. It is not too difficult to use the arrow key to select an OS and hit Enter.

You might not want to do that though- one day they may get curious and boot to Ubuntu and like it when they see how fast it is compared to windows.

---

### Post by andrew1421lee on 2011-02-09
Okay, I Installed Grub Customizer and read the tutorial and I really didn't find anything I needed. 
At the bottom of the Tutorial was the link to the Manual for Grub and I found something..
> 
Special Write Targets

Write grub to USB drive
The example command # grub-install --root-directory=~/usbdrive/ /dev/sdb installs to a USB drive enumerated at sdb, and which is also mounted at usbdrive. It was taken from UseCases/Ubuntu.


Will that do the job?

---

