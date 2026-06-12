---
title: "Newbie with Installation Problems"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by stevel-w on 2008-09-02
As a longstanding (and long suffering) Windows user I have now decided to take the plunge and switch to a real operating system. Having selected Ubuntu, I duly downloaded the image and burned it to a CD. After playing with the live system for a while I tried, this afternoon, to perform a full install.

After inserting the disk and powering up, I proceeded through the initial screens (setting timezone, user details and disk options) and waited. The system proceede to display a progress bar (at 5%)  which first claimed to be formatting the disk (I had elected to use the entire 100GB disk on the machine) then claimed to be installing the system. After freezing for a couple of minutes the screen cleared to black and the life system came up from the CD.

The system had not been up long enough to have formatted the drive and, on removing the disk and rebooting, the machine reported that no operating system could be found (the former Windows partition had obviously been removed.

At no point during the process were any error messages displayed and I have no indication of what went wrong. The partition editor indicates that I have an Ubuntu partition of 89.7 GB and a swap partition of 2.5GB.

I tried the entire process several times, all with the same result. Has anyone got any suggestions about how I should proceed? I really want to get this working.

Thanks

---

### Post by Pumalite on 2008-09-02
Probably a bad burn. Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Do md5sum on the iso, burn at 4x or less, check CD integrity before install. Do not use CD-RW

---

### Post by stevel-w on 2008-09-02
I'll try a re-burn tomorrow morning. BUt the disc I'm using was burned at X4 and the integrity check option on the Ubuntu start menu reports the disk to be okay. 

I have noticed that some of the apps don't run from the Live CD (Firefox runs and crashes, Evolution runs the configuration setup then dies and won't reload for instance). Is this consistent with a bad burn?

---

### Post by Pumalite on 2008-09-02
Did you do md5sum on the iso?

---

### Post by stevel-w on 2008-09-03
OK. I have now downloaded the image again and reburned it to a fresh CD. Exactly the same problem as before. I've done md5sum and checked the CD from the Ubuntu boot menu and both check out. The system still refuses to install without error messages and will run only in LiveCD mode. Some applications in this mode also refuse to run and generate an error - 'Could not launch menu item. Failed to execute child process. gnect "(input/output error).

At this point I should mention that I also have LiveCD versions of both Knoppix and Slax (cds created in exactly the same way - same software, same speed, same machine) and they both run flawlessly, so I don't think that there is a problem with the machine.

---

### Post by Pumalite on 2008-09-03
Use the Alternate CD then. You can also try some boot parameters

---

