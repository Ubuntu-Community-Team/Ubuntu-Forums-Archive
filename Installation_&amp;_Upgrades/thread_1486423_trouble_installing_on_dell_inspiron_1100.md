---
title: "trouble installing on dell inspiron 1100"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by iameatingjam on 2010-05-17
I've been trying to install linux on this piece of crap for a long time. My sister uses it and the windows installation had worked 'Ok' until recently when it is unbearable.

I tried to install ubuntu 9.04 on it a while ago. The same disk successful installed on this machine so I know its not the disk. it would boot until it gave the 'would you like to test or install' screen but wouldn't go any further than that.

So I try burning the new 10.04 to a cd but it kept saying there is not enough space. Even though the file is 699mb and the cd is 700. So i waste 3 cds and finally decide just to use a dvd. boot the laptop up and shows the ubuntu loading screen and then goes black and stays black. Try several more times, nothing.

Burn the file to a different brand dvd. Now it gets to the 'would you like to test or install' screen and I select 'test' and then I hear the opening sound and screen goes black again.

I try two more times and finally the live cd boots properly, I test it and its working wonderfully. I go for an install and it finished up like it should. I reboot finally excited and all it does is go to the linux terminal. Boots no load screen or gui or anything.

I also tried installing the os on an external hard drive on a different computer but the darn thing still refuses work.

What else can I try? I am desperate to get this computer into a working state again.

Dell inspiron 1100
1gb ram
2.4ghz pentium 4
40gb hdd

---

### Post by iameatingjam on 2010-05-17
alternatively, what distro could I try that might cause me less problems?

---

### Post by Kismet on 2010-05-18
Unfortunately since after 7.10 Ubuntu is not a very viable option for the 1100. The video memory is very limited in this laptop, and even with all the latest bios updates, it does not seem to be able to handle it. 

I've heard the random whispers about some convoluted hacks to get it to work but I've never had any luck.

So much for the Linux and old hardware bit eh?

You might try puppy linux, or damn small or some other really lightweight variant. I've tried Fedora, Ubuntu, and OpenSuse on my with no joy.

---

### Post by infamous-online on 2010-05-18
This is what I did because I have the same exact laptop, I burned the iso using windows and and problem solved. Also since the bios is old you can't boot from usb or external hd's on it so you're gonna have to try to burn the iso on windows.

---

### Post by Silvertones on 2010-05-18
I have an 8100 and I get the same black screen issue even just trying to boot to the live CD.
Karmic 9.1 is beautiful on this machine.

---

### Post by grege on 2010-05-18
To get the 1100 to work with newer Ubuntus or other newish  GNU/Linuxes you need to setup without Kernel Mode Setting (KMS) because of the awful way the old Dell's controlled memory. It can be done and you will end up with reasonable 2d acceleration, but it is very fiddly. KDE 4.x simply will not work, but KDE 4 apps will run under Gnome - figure that one out.

I recently just chucked mine away as no longer worth the trouble. See if you can find an older Ubuntu. From memory 8.04 worked well, after that the wheels fell off, although with this fix you can get 8.10 to work.

At boot you need to select recovery mode and get to a command prompt giving your password for maintenance.

Edit /boot/grub/menu.lst  as sudo

at the prompt 
cd /boot/grub
sudo nano menu.lst


Find the default boot line and at the end remove the word splash.

If this fix works for you then you can make it permament by seeking this section
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
And removing splash from the end. Thus when the kernel updates splash is not added to the boot parameters.

save (ctrl-o then enter) and exit (ctrl-x) then turn off by typing 
sudo shutdown -h now

Then turn on again.

Even with this fix you can still get an occasional blank screen at login requiring a ctrl-alt-bkspce to reload.

This fix will work for Ubuntus up to 8.10.

8.04 is still available for download from Ubuntu.

If you stick at it will work, but at best it will only work just good enough, the 1100 was a very Linux unfriendly notebook.

---

### Post by infamous-online on 2010-05-18
> **grege said:**
> To get the 1100 to work with newer Ubuntus or other newish  GNU/Linuxes you need to setup without Kernel Mode Setting (KMS) because of the awful way the old Dell's controlled memory. It can be done and you will end up with reasonable 2d acceleration, but it is very fiddly. KDE 4.x simply will not work, but KDE 4 apps will run under Gnome - figure that one out.

I recently just chucked mine away as no longer worth the trouble. See if you can find an older Ubuntu. From memory 8.04 worked well, after that the wheels fell off, although with this fix you can get 8.10 to work.

At boot you need to select recovery mode and get to a command prompt giving your password for maintenance.


Edit /boot/grub/menu.lst  as sudo

at the prompt 
cd /boot/grub
sudo nano menu.lst


Find the default boot line and at the end remove the word splash.

If this fix works for you then you can make it permament by seeking this section
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
And removing splash from the end. Thus when the kernel updates splash is not added to the boot parameters.

save (ctrl-o then enter) and exit (ctrl-x) then turn off by typing 
sudo shutdown -h now

Then turn on again.

Even with this fix you can still get an occasional blank screen at login requiring a ctrl-alt-bkspce to reload.

This fix will work for Ubuntus up to 8.10.

8.04 is still available for download from Ubuntu.

If you stick at it will work, but at best it will only work just good enough, the 1100 was a very Linux unfriendly notebook.


That's funny, I didn't have to do any of this and mine worked just fine.

---

### Post by beergutbrew on 2012-02-20
I have Ubuntu 9.XX installed on my Inspiron 1100 and it works fine, turned it on after two years of sitting and now the dell wireless card works fine. I started to upgrade to version 11 but stopped after realizing it may f up a good thing.

---

