---
title: "Ubuntu LiveCD Installer doesn't display (detect?) USB HDD"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Ash44455666 on 2008-10-31
Hello everyone.  I usually end up writing an unnecessarily large message (a question with more-than-enough information), so I'll try to keep it to the point.

I want to install Ubuntu 8.10 to an external (USB connected) HDD.

(As far as I know) I have it partitioned correctly, including the actual 18GB ext-3 partition, and the 2GB swap ..space... thingamajigger X_X

I open the installer, get to the partitioning choices, choose manual, hit next step, and it only shows my internal HDD. :confused:


Thank you for reading my thread, and for any help you can give me!


Edit: oops, forgot something.  I'm on the LiveCD this very moment.  Oh and I have to say, this version is AWESOME.  I can use dual monitors without ANY fuss or installing extra whatnot, and it detects (and actually lets me use) both my built in Realtek RTL8187B wireless adapter (it's called an adapter, right..?), as well as my USB Linksys wireless adapter.

Edit2: Here's a screenshot of the Installer.
[IMG]http://img116.imageshack.us/img116/5029/installscreenyyh3.png[/IMG]

---

### Post by Ash44455666 on 2008-10-31
Meh, got it to recognize the external HDD.  I unmounted it before starting the installer again and *almost *EVERYTHING seemed to go smoothly.  It finished, asked to restart, I did, I tried to boot from the external HDD (according to the computer, "USB Memory").  The displays went blank for about 45 seconds, and then it proceeded to boot from the Hard Drive.  Okay, I must've chosen the wrong one.  I restarted, and chose the only other possible choice: "FDD".  I figured it meant Flash Drive or something like that.  No luck.

Soooo I went into the Ubuntu already installed on the internal hard drive, added the Ubuntu installed on the XHDD to the GRUB boot list, restarted, booted into the new entry, and it ..did something weird.  It seemed to boot from it, but it didn't start with the usual "display".. the boot image, that shows the logo, and the progress bar.  Just booted up in some sort of verbose mode.  Eventually it it just stopped and dropped me into a shell.  I didn't write down the thing(s) it said, but is this a typical problem from booting from external USB hard drives or something..?

idk... if anyone can help, please do :-s

---

