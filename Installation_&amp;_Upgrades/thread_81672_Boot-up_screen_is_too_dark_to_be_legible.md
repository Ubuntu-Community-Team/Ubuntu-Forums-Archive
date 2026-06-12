---
title: "Boot-up screen is too dark to be legible"
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by blastus on 2005-10-24
In both Ubuntu Breezy and Kubuntu Breezy, the boot up screen, where the messages scroll by, are too dark to be legible. Also the bottom-half of the "Kubuntu" title is too dark...it is like the bottom half of the title doesn't exist. The "Ubuntu" title is OK, the bottom-half uses a bright enough color that I can see it. 

I am using the vga=771 option because I have to use it during installation of Hoary and Breezy otherwise my monitor is unstable during installation (it is an old but perfectly functional CRT monitor.) But using or not using vga=771 does not solve the darkness problem during bootup.

Can this be fixed?

---

### Post by Xian on 2005-10-24
Are you sure this isn't a monitor issue? I just use the default install values in the menu.lst and can see the scrolling text fine on my CRT. Your monitor may be perfectly usable but you might also want to check out the brightness and contrast range on the net using some charts to determine if there has been any degradation of performance.

[Monitor Calibration](http://www.normankoren.com/makingfineprints1A.html#Blacklvl)
[Display Calibration](http://www.displaycalibration.com/)

---

### Post by blastus on 2005-10-26
Thanks Xian for those links. Yes I have always adjusted the gamma settings on my monitor. I can do that with the NVIDIA drivers in both Windows XP and Ubuntu but only after the OS has loaded and I have logged in. There's no way I can adjust gamma settings during bootup. In the meantime though, before I'm able to buy another monitor, is there any way I can change the color of the messages that scroll on the boot screen?

The vga=771 thing, I believe that it due to the fact that the Ubuntu installation uses a default Vesa mode that is not supported on old CRT monitors. Even vga=791 works on my monitor. I haven't had problems with my monitor, except for adjusting gamma settings, but that is not the fault of the monitor, it is due to its age (about 8 years old.) My monitor is a Samsung SyncMaster 700b and back then it was the Editor's choice among several magazines for the best CRT monitor you could buy. 

Even now, my monitor renders text more clearly than many other CRT monitors I've seen. But the gamma stuff is a problem on Linux when it comes to video (video is usually darker than it should be.) The Linux NVIDIA driver does not support gamma settings for overlay, but the driver for XP does.

---

### Post by SilentCacophony on 2005-10-26
Hi. I have noticed the same problem on my setup. I chalked it up to my aging monitor not having a bright enough display, even with the settings maxed.

Anyway, I looked into it, and noticed there is a [bug report]("http://bugzilla.ubuntu.com/show_bug.cgi?id=18137") filed that is marked as 'trivial' in severity, so I doubt it'll be changed any time soon.

I also downloaded the [source]("http://packages.ubuntu.com/breezy/source/usplash") to see what would be involved in changing it manually, and by my *rusty* knowledge of C, it looks difficult at best.

It looks as if the palette that is used is derived from the bootsplash image itself, which was originally a png image. The catch here is that the original image is converted to some obscure framebuffer graphics library format called bogl upon compiling the package, and the resulting file is saved to /usr/lib/usplash/usplash_default.so.

The only possibility I see to fix it is to download the source, change the image palette of the original, and compile/install the package. Possibly there is some program out there to modify the usplash_default.so file itself, but I've no idea where.

[COLOR="Red"]**EDIT**[/COLOR] - Heh. I just ran across a post from someone complaining that they messed up usplash by using this wiki entry: [USplashCustomizationHowto]("https://wiki.ubuntu.com/USplashCustomizationHowto?highlight=%28usplash%29"). That sheds some light on the subject, though it didn't work for that person. ;) I may try it when I have more time to spare.

---

### Post by wwuster on 2005-10-27
I just removed the "splash" word in /boot/grub/menu.lst and don't even bother to  show the dim brown image. Mine was also very dark and was hard to read. It's bugs like this that make me have doubts about ubuntu.

William

---

### Post by SilentCacophony on 2005-10-27
I've written a HOWTO with two examples and instructions on installing them. I changed the text brightness and progress bar background of the original, and also made a corresponding blue one. It's not as terribly complicated as I originally thought, before I saw the wiki entry.

Link is here, if you're interested:

[http://www.ubuntuforums.org/showthread.php?t=82835]("http://www.ubuntuforums.org/showthread.php?t=82835")

---

### Post by blastus on 2005-10-30
Thank you wwuster for that tip and SilentCacophony for your extensive investigation into this and the HOWTO page! 

I will definitely look into this. It's strange because sometimes the colors are visible and other times they aren't. Like today and yesterday, when I turned my computer on, the boot messages were bright enough to be perfectly visible. Other times, I can barely read it and have to increase the brightness/contrast of my monitor some 25% to see it.

---

