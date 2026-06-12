---
title: "Dual boot Windows 7 GRUB shows up, but I get a purple screen"
date: 2014-02-23
forum: Installation &amp; Upgrades
---

### Post by Michael_MacEachran on 2014-02-23
I have installed both Windows 7 and Ubuntu 12.04 LTS and the Ubuntu works fine.  But when I get the GRUB menu, I choose win 7, but I just see the purple screen.  What's weirder is that I can here the windows chimes, so windows is clearly booting up.  I can also type in my password, hit enter, and I can hear the welcome sound, so I believe that I am logged in.  But it's just the purple Ubuntu screen.

Any Ideas?   Thank you

---

### Post by Michael_MacEachran on 2014-02-24
I belive that the problem was a simple video setting.  GRUB (ubuntu) instantly recognised the video driver and set it to max resulution.  The problem was that it was a fresh install of Windows 7, and did not have the drivers for that installed yet. (Stupid Windows)  

Anyway, I installed GRUB Customizer,  set the windows video resolution to 640x480 and away I went...

---

### Post by jeremy17 on 2014-02-27
Hey Michael,

I know this thread is marked as SOLVED, but I was wondering if this is still working for you.

The reason is: I have the exact same situation. Purchased a cheap laptop that came with Windows 8 (Acer E1-532), got rid of 8, disabled UEFI, installed Windows 7. Works fine. Installed Ubuntu 12.04.4, and things seemed to work fine, but then the Windows 7 boot experienced the exact same thing. I couldn't see the screen,  but I could hear it, so I entered my password and logged in, then hit Alt+F4, Enter, which shutdown the computer. Logged into Ubuntu, updated the Grub file at /etc/default/grub by changing the resolution, and it worked!

And this is where things get weird. Booting into Win 7 only works twice. Seriously. 
Update Grub.
Restart computer, boot into Win 7. Works. 
Restart computer, boot into Win 7. Works. 
Restart computer, boot into Win 7. Purple screen. 
And it continues to present the purple screen until I reboot into Ubuntu again, make a minor change to the grub file (toggle the resolution between "1366x768" and "1366x768x32") and update it, then it works again. For two restarts.

Hopefully you're still checking this thread, and will give this a test. Sadly, I haven't found a permanent solution yet.

Booting into Ubuntu works perfectly, every time.

---

