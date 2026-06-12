---
title: "Can't see properly after install"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by Haltcrypto on 2005-11-12
Hi all.

I'v recently installed Breezy and it gets through base and package installation fine. Then I presume it gets to the login screen, but it is all fuzzed up and yellowish. Its the type of thing that would happen in windows if you set a resolution or refresh rate higher than graphics card can handle.

Now i'm not experienced at all with Linux, but must I some how edit the Xserver? I can't get into gnome so please guide me through changing something to fix the problem.

Thanks

---

### Post by teaker1s on 2005-11-12
at grub hit Esc and boot recovery 
sudo dpkg-reconfigure xserver-xorg
this will bring up a graphical wizard which helps change the settings

---

### Post by Haltcrypto on 2005-11-13
Thanks 
I tried this and went through the xserver config thing a few times, using default settings, using minimum settings such as 800*600 resolution, and other combinations, and nothing works. Same yellowy mess after reboot.

I have a Nvidia Gforce 6600 with a 19" monitor (normal crt not lcd or anything)

What now?
The same will happen with the live cd. This problem also happened with the liveCD of Hoary, but I did not have this problem when installing hoary using VMWARE on top of windows. Now I have installed straight to hard drive.

Thanks

---

### Post by Haltcrypto on 2005-11-14
I'm still having problems.

Can someone please help.

---

### Post by yesplease on 2005-11-14
I cant solve your problem, but perhaps others can when they have more information, such as the type of your mainboard. There is also information in various logs.

/var/log/messages Many programs dump their log here.  
/var/log/kern.log Messages from the kernel
/var/log/syslog Another dump
dmesg This command shows kernel kernel logs
/var/log/xorg.0.log Messages from X server

Perhaps you can check these logs and post things that seem relevant.

This does not seem related to install, because all your CDs give this problem. During install you get a question wich resolution you want to use, do you remember what you chose?

---

### Post by Haltcrypto on 2005-11-15
I have a P4 Titan GA-8SIMLH-P Sis 651 chipset motherboard.

When asked about resolution, I chose 1280x1024, and when that didn't work, I reinstalled and used 1024x768, and have even tried with lower resolutions.

Nothing seems to work. And I chose the NV drivers option during graphics setup.

Thanks

See attached logs

---

### Post by yesplease on 2005-11-15
In your xorg file I do not see "Validated modes for display device CRT-1". Also your monitor is probed at a small range"(II) NV(0): Generic Monitor: Using hsync range of 30.00-65.00 kHz
(II) NV(0): Generic Monitor: Using vrefresh range of 50.00-75.00 Hz"

This may be perfectly normal, but it wont hurt to use the offical range in the manual of your monitor as described here:

[http://www.ubuntuforums.org/showthread.php?t=83973&highlight=xorg](http://www.ubuntuforums.org/showthread.php?t=83973&highlight=xorg)

and add a resolution your monitor is capable off (from the manual).

I hope you will get answers from experts, but this what I could think off.

---

### Post by Haltcrypto on 2005-11-15
My monitor is capable of running resolutions above 1280x1024 (as i am in now with windows). I did try enter in the exact horizontal and vertical sync from manual during one of my many xserver reconfigures but still no change. This is very frustrating. Is something not compatible?

---

### Post by yesplease on 2005-11-15
You have the Nvidia 6600 GT card. It should work without a problem (my 6800 gt did).

I do not see how a reinstall would help, because you have this problem also with the live CD, but you could try. The only thing I can think off is to install the nvidia drivers.  There are Howtos for that.

You can also try to get a reaction at the video subforum, because it seems nobody can help you here.

---

### Post by Haltcrypto on 2005-11-16
I managed to get into Ubuntu using Vesa drivers.

Why is this?

---

### Post by yesplease on 2005-11-16
Vesa drivers work for all cards and run basic functions, no acceleration.

How does your screen look now? Can you install the nvidia drivers now via Synaptic?

---

### Post by Haltcrypto on 2005-11-16
I have dialup and Ubuntu doesn't recognise my modem, so I'll have to download the drivers in windows and install manually.

The screen looks ok. Its running 1280x1024 now.

---

### Post by yesplease on 2005-11-16
[QUOTE=Haltcrypto]I The screen looks ok. Its running 1280x1024 now.[/QUOTE]

That sounds good.

[QUOTE=Haltcrypto]I have dialup and Ubuntu doesn't recognise my modem, so I'll have to download the drivers in windows and install manually. .[/QUOTE]

Perhaps you can try to get the modem working first and then install with Synaptic. Synaptic is able to recognize dependencies and installs those dependent packages. 

Search for howtos for your modem or ask a question in the hardware forum.
Good luck.

---

### Post by Haltcrypto on 2005-11-17
Thanks will do!

---

