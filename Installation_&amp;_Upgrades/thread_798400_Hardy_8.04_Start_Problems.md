---
title: "Hardy 8.04 Start Problems"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by threecolt on 2008-05-18
I installed 8.04 on an Asus Eee but cannot get it to fully boot. The install was straightforward: Xandros on internal 4GB - hd(0,0) - and Hardy on 8GB SD - hd(1,0). I took the Guide option and gave the installer the full SD to keep the install vanilla. The only thing that I did was to take the option to install GRUB to /dev/sdb to keep it out of the way of the Xandros install. Here is what happened:
[LIST]
[*]For Xandros GRUB showed a drive of hd(0,0) and for Hardy hd(1,0)which is correct BUT **_all_** GRUB options produced ERROR 15 - File not found.
[*]Changing Xandros drive to hd(1,0) booted Xandros all the way through.
[*]Changing Hardy to hd(0,0) booted Hardy to the logon screen but once user/ password were entered the screen went a light tan blank except for the cursor which still worked. Pressing the I/O button dropped Linux off the screen into the command line showing various drivers got the shut down signal and then Linux ended.
[*]Changing Hardy to hd(0,0) and logging on to a failsafe terminal got to a command line that works fine. 
[*]All other logon options do NOT work.
[/LIST]

I would assume 
[LIST]
[*]the kernel is not loading X11 or whatever since I can logon to a command prompt but nothing else. 
[*]the kernel is looking on a path where it cannot find what needs to be loaded next (though it does find base drivers).
[*]the issue is a bad install.
[/LIST]

My problems at this point are
[LIST=1]
[*]With such a straightforward install I do not know what was done wrong.
[*]I do not know why the GRUB command execution expects the hd's to be "reversed".
[*]I would not know where to begin to look for what needs to load next.
[*]Even if I did know I would suspect that after the next fix there is a next bad path and next and next ...
[/LIST]

Help and thoughts would be greatly appreciated.

---

### Post by weblordpepe on 2008-05-31
Yeah I have noticed that Ubuntu 8.08 is giving me some trouble when I boot off an SD card. It's fine until it gets to 'Loading USB' somethingorather. 

Its a neusance. I have installed it using manual install, with GRUB on the sd card, but I altered its menu options to say that Ubuntu was on 0,0 because when it boots from the SD card, the SD card is viewed as 0,0.

It stinks cos I REALLY want Ubuntu 8 running on this EEE.

---

