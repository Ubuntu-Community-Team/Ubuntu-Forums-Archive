---
title: "problem getting ubunto to install on vista"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by Cearl62 on 2010-11-05
hello every one before i tell you what's wrong i will tell you what computer i am using,
first of all it is a Toshiba Laptop, it uses Windows Vista, It had AMD Turion64x2 Mobile technology whatever that is, USes ATI Graphics, and has Realtek wireless, also runs on 32 bit system, anything else you need to know?
 
ok well first things first i got the latest ubunto install which is 10.10 just downloade it yesterday so it should be the most up to date, i click on intsall with windows, so it installs it then i reboot it i get the two choices on which OS i want to start up and i press the down arrow and select Ubunto, and then my computer just goes to a black screen, i've let it sit there for about half an hour and came back to it yet still it was a black screen am i doing something wrong or something? my windows still works though so i don;t know what i am doing wrong any help will be glady apprecitated :) thank you very much.

---

### Post by P4man on 2010-11-05
You probably need to set "nomodeset". The link in my signature explains that for a normal installation or livecd, but I havent used wubi in a while (and I strongly recommend against using it) so Im not entirely sure if the procedure works for wubi as well. It should work if you create a livecd (or usb stick) and boot from that and do a regular dual boot install.

---

### Post by Cearl62 on 2010-11-05
may i ask why you are strongly set against it?, thank you for the very fast reply i was expecting to have to wait for about an hour before i got one, suprised me thank you :)

---

### Post by P4man on 2010-11-05
wubi installs ubuntu on a virtual filesystem that is hosted by a windows NTFS filesystem. Essentially you have two layers of filesystems. That costs performance and also means if something goes wrong with ntfs, you will not be able to boot ubuntu or might even not be able to recover your data. There are also problems with the bootloader wich tends to break every so often with an upgrade, rendering wubi and/or windows unbootable.

The idea of wubi is to lower the bar for windows users, since you can install it from within windows without even booting a CD,  but the downsides IMHO outweigh the advantages.

---

### Post by Cearl62 on 2010-11-05
so what would you suggest i do? how can i install unbunto without wubi? and still be able to use vista or ubunto? dual boot.

---

### Post by sikander3786 on 2010-11-05
+1 to the Wubi discouragers list :-)

Wubi was just meant to be a simple method of testing a Linux distro. Just to make up your mind before converting to it (I find many Windows users lazy and frightened about messing up their system, don't panic, I also used to be a Windows user some time ago).

So if you you want to go with Ubuntu or any Linux distro for long-term, dual booting will be the best option.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

We can answer all your queries and help you get there if you decide to dual boot.

Good Luck!

---

### Post by jroa on 2010-11-05
I had the same problem with one of my computers.  It would boot and everything looked good until I got to the log in screen, then it was just black.  It turned out that the CRT monitor was not compatible.  I could boot up fine when I hooked up my LCD screen from my other computer.  I don't understand why, but the CRT just did not like that log in screen.  I disabled the log in on start up and after that, I could use either monitor.

I don't know if this is the same problem that you are having, but it sounds similar to me.

---

### Post by P4man on 2010-11-05
> **Cearl62 said:**
> so what would you suggest i do? how can i install unbunto without wubi? and still be able to use vista or ubunto? dual boot.

Its ubunt**U**.
Yes you can uninstall ubuntu from within windows, just like an applications. Then create a bootable cd (or usb stick) and test it ubuntu the cd. If your videocard needs the nomodeset trick as I strongly suspect, check my signature to find out how to set it for the livecd session,  and after installing.

---

### Post by Cearl62 on 2010-11-05
sorry about that ubuntu* :), so if i were to use it from the live cd would i be able to save changes that i do to it, or would i need to install it on my computer, now when i install it on my computer from the cd or usb, most likely going to use the usb, can i still use windows and just have a dual boot?

---

### Post by P4man on 2010-11-05
> **Cearl62 said:**
> sorry about that ubuntu* :), so if i were to use it from the live cd would i be able to save changes that i do to it

Not from a cd. You can save changes if you create a so called persistent live usb stick, although that has its limitations (you can save files and settings, but not upgrade or install proprietary drivers). You can create such an USB stick from within ubuntu easily, or a bit less easily by following any of a gazillion guides on the web. But just install it to your harddrive.

> now when i install it on my computer from the cd or usb, most likely going to use the usb, can i still use windows and just have a dual boot?


Sure. The installation process will guide you through it; it should recognise the existing windows partition and propose a "side by side" install.

But once more, the black screen issue you are having is most likely NOT a wubi specific problem, but a kernel/videocard specific one that needs the nomodeset trick, regardless of how you install it and even when running ubuntu off a cd (or usb stick).

---

