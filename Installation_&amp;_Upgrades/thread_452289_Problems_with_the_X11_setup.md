---
title: "Problems with the X11 setup"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by baldrick on 2007-05-23
Hi all,

After successfully installing ubuntu-6.10-desktop-i386 using VMware Server version 1.0.3. I realized that I had to reconfigure the X11 in order to increase the resolution as the max. resolution to be selected in the GUI was 800x600. I used "sudo dpkg-reconfigure xserver-xorg" but may have run into problems as the program was suddenly ended just after entering the color depth as 24 bit. However, I managed to start the X11 by the "xstart" command. 

I then had a sucessful session with 1024x768 resolution (the one I chose in the setup). My problems started on the next login. I now have a "login" screen. I use "ubuntu" as user and "ubuntu" as password. However, after logging in the X11 appears not to be able to start as it simply blink once or twice - I see the black screen for a split second and then it turns back to the "login" screen. So, how do I get "back" to the non-X11 screen? Is there a smart "hot key" to get there? I have tried a lot of Alt+Ctrl+Fx combinations with no luck... I figure that if I can get back then I will be able to restore my back-up version of the X11 configuration. This is the first problem... 

The second of course is to get ubuntu to run in high res... Any suggestions? I have an IBM/Lenovo T60 laptop - 14" high resolution version. I run 1600x1200 in Windows with no problems.

Thanks a lot in advance

Allan

---

### Post by haskelm on 2007-05-23
I had the same problem with Debian today: I messed around with the x11 file and then when I reboot the login screen was re-appearing again and again, so I just downloaded Ubuntu and installed. 

So now I'm back at the same problem: How do I get my monitor resolution to 1280x800? 

My graphics card is 82915G/GV/910GL Integrated Graphics Controller. The computer is a Dell Dimension 4700. The monitor is a Samsung SyncMaster 226bw 22" (1680x1050 max native resolution).

---

