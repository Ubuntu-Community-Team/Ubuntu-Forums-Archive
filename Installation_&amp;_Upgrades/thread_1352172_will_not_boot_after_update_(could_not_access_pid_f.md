---
title: "will not boot after update (could not access pid file for nmbd-16-386)"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by BillyBobby on 2009-12-11
Just installed the latest updates from the updatemanager and booted.

Then the machine stops in the boot with the message: (in recovery mode)

...
init: ureadahead-other main process (527) teminated with status 4
* Reloading /etc/samba/smb.conf smbd only
* could not access pid file for nmbb


With standard boot I get a "mouse pointer cross" and on ctrl-alt-f1 I see some lines from the bootloader whit the "could not access pid file for nmbd-16-386" message above


What can I do???

---

### Post by gyurman on 2010-01-09
It is easy, have you any problem with /var?
Use boot in grub with edit  e key. change splash to nosplash
U see the /var can't mount. Ok?

---

### Post by BillyBobby on 2010-01-09
It did no good. Not even the "safe mode". I had a friend over with a lot of linux experience but we gave up and I have reinstalled the machine.

But I made a backup of all the files, so it was quick to get settings on the new install to match the old installation.

So I still have no idea what was really wrong. But thanks for trying to help, even if it's to late now.

---

### Post by dvdntwrk on 2010-01-26
I have been trying to install a nVidia 8400 GS and when I reboot after building the nVidia xconfig file I get the same message sans -16-386. 

I don't understand the reference to problems with /var.

To computers I'm not new to some of the linux jargon i'm very green can you help me look at this?

---

### Post by NotKeith on 2011-01-23
> **gyurman said:**
> It is easy, have you any problem with /var?
Use boot in grub with edit  e key. change splash to nosplash
U see the /var can't mount. Ok?

Sorry to dredge up an old thread, but this is the one I got when searching the only error message I saw.

I had a similar problem with my system (karmic, 2.632-22 generic kernel) hanging on the splash screen before login, and recovery mode hung as well, with the "could not access..." message from the OP.  Altering the 'splash' to 'nosplash' solved my problem.  I'm a curious guy, so what happened?  Can anyone direct me towards an explanation, and is there any way to get my splash screen back without hanging the system?

Thanks!

---

