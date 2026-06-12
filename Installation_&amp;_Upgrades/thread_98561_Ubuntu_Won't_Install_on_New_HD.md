---
title: "Ubuntu Won't Install on New HD"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by surfoutsider on 2005-12-03
I am a novice computer user attempting to rid myself of Microsoft software and convert to Ubuntu Linux.  However, I have had a bit of an issue trying to boot Ubuntu off of my Western Digital 120gb hard drive.  The first installation part (from the install cd to the hard drive) works flawlessly but will not proceed to the 2nd half of the installation.  When the computer restarts the bios won't recognize the new boot startup on the hard drive.  The bios is set to boot off the hard drive and Ubuntu will work and boot off of an older (8gb) hard drive.  Yet, it will  not boot off of the newer 120 gb hard drive.  Any help would be greatly appreciated.

---

### Post by bwog on 2005-12-03
So, install wnet alright.

"When the computer restarts the bios won't recognize the new boot startup on the hard drive. "

This can be fixed by changing the boot order in the BIOS, if I understood that statement well.

"The bios is set to boot off the hard drive and Ubuntu will work and boot off of an older (8gb) hard drive. Yet, it will not boot off of the newer 120 gb hard drive."

That means it is installed on the 8GB drive, doesnt it? Otherwise unbuntu wont work from the *GB drive

Anyway, these things can be repaired or redone, just give the forum more information.

(A workaround could be to unplug the 8GB drive for the  time being, and plug the large drive in the first IDE controller. Obviously there are better scenarios, but this would prevent installing on the wrong drive.)

---

### Post by surfoutsider on 2005-12-03
Hopefully this will make things easier.
1)Ubuntu was originally installed on large hard drive.  Bios was set to boot off of this hard drive.  Bios would not boot off of hard drive due to unknown reason.
2)Large hard drive removed.  Smaller older hard drive installed with Ubuntu.  Same bios setup as before yet this time Ubuntu starts.  
3)Why doesn't the newer Western Digital hard drive work and the older HD does work?
4)  I don't want the older hard drive, only the newer one.  However, I can't run Ubuntu on the newer hard drive, but only the on the older HD.
  This is my issue

---

### Post by bwog on 2005-12-03
Sometimes there are settings in the bios to recognize a large drive (LBA I think). Can you check that from your manual or bios?

When you cant find it, give the forum your harware specs.

---

