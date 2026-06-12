---
title: "64bit  Ubuntu 9.10 and 32bit windows 7"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by houseonfire on 2009-12-25
I tried to install 64bit ubuntu on a separate drive on my computer, with windows 7 32bit installed on another.
Grub wont even pop up, and it just sits a screen with a line blinking and nothing happens.
When i use a grub live disk, it gives me an Error 15 file not found error.
Do I need to install 64bit windows in order to get the 64bit ubuntu working?
I have to unplug the drive to get it to even start up.
I have a p5q asus motherboard, q6600 running at 3.2ghz.

I have installed ubuntu many times, so I know i did nothing wrong..

Windows 7 was already installed, and then i tried to install ubuntu. So I should get a grub scrren during startup...

---

### Post by taurus on 2009-12-25
It doesn't sound to me like 32bit (windows) vs 64bit (Ubuntu) as you would have suggested.  Where did you install GRUB when you installed Ubuntu?

---

### Post by audiomick on 2009-12-25
Hi. Taurus is right, it is nothing to do with 32 or 64 bit systems.

Grub2 form the installer doesn't seem to deal too well with more than one HDD.

If you look at this:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

you will find an explanation for the error 15. It says something along the lines of not having designated the drive when reinstalling grub, which doesn't match your situation, but gives you and idea of what has gone wrong.

You can try re-installing grub as described further down. If that works for you, well and good. If it doesn't (as it didn't for me), you should try changing the boot order of your discs.

There is also a very helpful boot info script (which helped me) floating around in the forums. I'll see if I can find it, and post it here.

edit:
here it is
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
run that and look at it's output. It will tell you if there is a grub installed anywhere on the computer, and where it is. The disc that it is on has to be the first one to be looked at during booting.

---

### Post by presence1960 on 2009-12-25
We need to see exactly your setup & boot process. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

