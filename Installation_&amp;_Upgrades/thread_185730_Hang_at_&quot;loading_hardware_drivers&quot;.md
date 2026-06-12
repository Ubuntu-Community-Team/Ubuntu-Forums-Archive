---
title: "Hang at &quot;loading hardware drivers&quot;"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by 1002285 on 2006-06-01
I burned a release candidate of 6.06 to a CD (about 5-6 hours before the official release came out), but as I have read, it shouldn have been a very different version from the official release.
(CD check was fine).
It hanged at the stage "loading hardware drivers". I tried to boot from it both with the PCMCIA ethernet card connected and USB wifi card disconnected and vice versa, and with both of them disconnected - the result was the same: hanged in "loading hardware drivers".
I have used 5.10 until now and the only problem was that the USB wifi card Canyon CN-WF518 did not work.
The computer is Dell Latitude CPi with P II 133 Mhz and 128 Mb memory.

---

### Post by JSchwage on 2006-06-01
I'm having the same problem. My suggestion would be to try the alternate install CD, which is what I'm doing right this moment. Also, the recommended amount of RAM for running the Live CD is 192 MB.

---

### Post by Zarneth on 2006-06-03
edit: Seems my problem's quite a bit diferent than I origionally thought. not related to this thread then.

---

### Post by brj on 2006-06-03
i had the same problem. 
but after removing "quiet splash" from the boot options in /boot/grub/menu.lst it worked.

you can test if it works for you by editing the boot command in the grub menu.

jakob

---

### Post by jarkema on 2007-01-15
Follow up on brj:

If you press "Esc" at the beginning of the grub boot, you can select/browse/modify etc. the boot commands.  I noticed that if I choose the Recovery Mode boot, the splash screen doesn't appear, but lots of boot information shows in the terminal mode display, and it never hangs up on "Loading Hardware Drivers".  Not to say it never hangs up, but every time I reboot in Recovery Mode, it proceeds past the place it hung up the previous time :)  so usually I can boot within three tries max.  Note that when it succeeds, it stops at a command prompt; just enter "exit" to go into the login screen.

I observed that the difference between the default boot and the Recovery Mode boot is that default boot uses the boot option "quiet splash" and Recovery Mode uses "single" (default also has a command "savedefault" just before the command "boot" that Recovery Mode lacks, I have no idea what that does).

To make my computer skip the splash screen by default, I opened the Terminal application on the desktop, typed "sudo gedit /boot/grub/menu.lst", scrolled to the very bottom where the actual boot menu secections are, located the kernel line for the default boot, replaced "quiet splash" with "single" and saved it.

---

### Post by haight6716 on 2007-08-06
I just wanted to add to this thread a very odd way to wind up with this problem - I accidentally ran 'svscanboot' while in my /etc.  This created all kinds of junk under each folder in /etc.  So if you have this problem and you can't figure it out, you might just look for silly pipes and things in your /etc/udev folder.

---

