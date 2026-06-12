---
title: "Can't install 9.10 or 10.04 to old comptuer"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by Arleas on 2010-04-09
Hi guys,

I can't work out what I'm doing wrong - 

I requisitioned an old computer from work (2.0ghz P4, 512 ram) and can't get Ubuntu to install.

If I install from Windows using the wubi, it 'installs' but nothing happens - I get a dual boot screen which flashes up for a second and then disappears.

If I boot from the CD, my USB keyboard and mouse power down when the Ubuntu splash screen appears, and then attempts to load into a demo version of Ubuntu - but never gets there. However, I got further into the process before I used the wubi, but after installing and uninstalling ubuntu from the wubi I get a crash message.

I've never seen this before -I've installed 9.04 and 9.10 onto 3 other computers! I tried 10.04 originally, and thought it was a bug that was stopping it, but clearly it's a hardware problem...

Can anyone help?

------------------------------------------------------------

THREAD SOLVED: I think it was a hardware problem - and not the distribution.

It seems the DVD drive is defective and the symptoms were:

* LiveCD occasionally successfully booted to desktop, but would not install. Slow performance and pop-up errors.
* LiveCD more frequently crashed by either freezing or giving text error messages and then user is dumped to command prompt.
* Wubi installer for Windows could only install within Windows (no other functions worked), but would not boot afterwards.

Hope this helps if you have a similar problem - try a USB installation (if your BIOS will let you boot from USB). Good luck!

Tested using 10.04 beta 1 and 9.10 downloaded from Ubuntu's main site.

------------------------------------------------------------

---

### Post by MeNtuxRoKinU on 2010-04-09
Do you have a graphics card installed? If so, ubuntu may give you an issue with screen resolution causing the screen to black out. You can download the alternate install image and install through text based screen to get around this. As soon as you boot up after install you will be prompted to install the video card driver, and then restart, and your machine should work. 

Why wubi though? If your trying to install inside windows, I'd suggest suns virtual box software. Its like vmware so you can run multiple os's inside your machine. Just burn a copy of the install disk, download virtual box, and create a new virtual machine to install to. Soo easy. 

If you dont care to run them side by side, try creating a partition specifically for linux, and install there.

---

### Post by Arleas on 2010-04-09
Well, funnily enough I managed to let the boot cd menu time out and it actually (although, very slowly) loaded - so the GPU is fine.

Although, it wouldn't let me double click the installer - it'd try to load something and then die.

Very strange!

Also, not sure why it's disabling the USB ports on the cd boot menu. It just cuts all power to them, even though the lights are on at the BIOS!

---

### Post by snkiz on 2010-04-09
Is the iso good? did you run an MD5 check?
how many sticks of ram you got? one may be bad, strange things happen with bad ram. If you can try running with one stick at a time, If you have a bad one it should show fault faster if its the only one in the machine.

---

### Post by Arleas on 2010-04-09
> **snkiz said:**
> Is the iso good? did you run an MD5 check?
how many sticks of ram you got? one may be bad, strange things happen with bad ram. If you can try running with one stick at a time, If you have a bad one it should show fault faster if its the only one in the machine.

Just one stick, but it runs Windows fine. I've tried two Ubuntu versions now, 10.04 and 9.10 - I don't think it's that... thanks for your thoughts though!

---

### Post by snkiz on 2010-04-09
sorry :) I run an old p3, my computer does things like that as ram starts to go. Got lots of hand me down 128 sticks so I'm ok

---

### Post by Arleas on 2010-04-10
> **snkiz said:**
> sorry :) I run an old p3, my computer does things like that as ram starts to go. Got lots of hand me down 128 sticks so I'm ok

I think it might be the DVD drive? 

Cheers for your help - it may be the RAM, who knows? I guess this is the problem with trying to revive old hardware!

I think I've officially given up on this one. I'll build a new PC sometime in the future and dual boot it...

---

