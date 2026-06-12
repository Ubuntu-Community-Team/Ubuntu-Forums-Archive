---
title: "Cannot install on SSD"
date: 2017-09-10
forum: Installation &amp; Upgrades
---

### Post by natbrowne on 2017-09-10
I have my desktop, two HDD's for storage/backup, two SSD's, one 120GB and the other 250GB. I currently have windows 10 on the 250 GB SSD, but would like to dual boot it with ubuntu. I plug in the live usb installer and go into the set up, but when picking the disk to install ubuntu to I only get the one option, the 120GB SSD ( no other disk is select-able from the menu ).

I should mention the 120SSD has an older version of Kubuntu running on it, which I wish to get rid of eventually.

To solve the above, I unplugged all drives bar the 250GB one, and then installed and it worked, but when booting I never saw a GRUB screen -> straight into windows10, and the only way to access the Linux install was to go into the BIOS and enable legacy boot, and then to get into windows, back to the BIOS enable UEFI/secure of something

Bottom line, I wish to dual boot on the 250SSD, is there any easy way to do this?

---

### Post by Bucky Ball on 2017-09-10
Sounds like you installed Ubuntu in legacy mode if you can boot it in legacy. If Windows is installed in UEFI, as it sounds like it is, Ubuntu must be as well or you will get issues. As you are finding. Surprised you can do this much.

Reinstall and this time, look for the USB option with 'UEFI' next to it somewhere. If you boot with the install media inserted and hit F12, it should take you to a boot device menu. Here you should see two entries for the USB; regular (legacy) and UEFI (which will have  that somewhere next to it). 

You also need to have the BIOS set to UEFI for the install. Good luck on the second run.

* PS: Which release and flavour of Ubuntu are you installing?

---

### Post by natbrowne on 2017-09-10
Okay,
I have put the BIOS into UEFI on and Secure boot&legacy off. Live USB in, hit F12, see the option to boot from wndows boot manager, NIC IPV 4 and 6 then UEFI 8.07, I opted for UEFI 8.07, this boots from the Live usb into the live buntu desktop.
I clicked install, and back to my original problem, It only allows me the option of the 120GB SSD, not the 250GB SSD , what do I do now?

---

### Post by oldfred on 2017-09-10
What brand model system?
And what video card/chip?

Post this for each drive.
       sudo parted /dev/sda unit s print 

Is Windows fast start up still on? Then Linux NTFS driver will not mount normally and installer cannot see it. Windows does turn fast start back on with updates which may be in back ground. So you have to regularly check.

See also link in my signature.

---

