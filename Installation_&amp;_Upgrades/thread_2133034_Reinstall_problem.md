---
title: "Reinstall problem"
date: 2013-04-06
forum: Installation &amp; Upgrades
---

### Post by cdissler on 2013-04-06
Hi all,
A family members computer with ubuntu 12 recently started booting to the busybox screen. I've searched and can't find a solution to why this started happening but I cannot figure out how to load ubuntu. I decided to try a reintall but I can't get the Disc to load a boot. Tried all the key combinations...

Anyone have suggestions?

---

### Post by darkod on 2013-04-06
Are you sure the cd is good? If you can't even boot the computer with it, that's not good. Do you have nvidia graphics maybe? Often nvidia cards need a special boot parameter called nomodeset.

What is happening exactly when you try to boot with the cd?

---

### Post by cdissler on 2013-04-06
Thanks for replying. I don't even get an option to boot from the CD, the system goes right into busybox. I've tried two different cd's now, and it worked when I first installed ubuntu, so I'm not sure why it won't read it.

---

### Post by darkod on 2013-04-06
Check the boot devices order in bios. If it tries the hdd before the cd-rom it will never even try to load the cd. The cd-rom has to be before the hdd.

---

### Post by cdissler on 2013-04-06
Tried that, it's set correctly.

---

### Post by fantab on 2013-04-07
Firstly, check the CD/DVD it could be corrupt. [BURN]("http://www.ubuntu.com/download/help/burn-a-dvd-on-ubuntu") Ubuntu.iso to a new DVD/USB and try again. You might also want to check the integrity of you downloaded .iso with [MD5SUM CHECK]("https://help.ubuntu.com/community/HowToMD5SUM"). If its not okay then re-download Ubuntu.

You haven't confirmed if you have nvidea graphics? Give us some details of your computer's specs.

---

