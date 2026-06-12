---
title: "Dual Systems, not dual boot"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by Agencyman on 2010-09-17
To All,

I'd unsuccessfully tried to accomplish this, and gotten a wide variety of complaints from Ubuntu's installer and partition utilities.  Once, during partitioning of the 'U" Drive, Mr. Computer even told me; "This is a BAD IDEA", and used all caps for "Bad Idea"!!!  I quite enjoyed that little bit of decidedly human inflection! :) :)

I finally settled on the following solution, for security reasons:

Pull the plug, (yes, the SATA one), on the "U" Drive, the dedicated Ubuntu HDD, load Hiren's Boot CD 11.0, and restore the Win 7 MBR on the dedicated "W" Drive to remove the dual boot menu.

Shut down, restore the SATA cable to "U" Drive, then pull the plug, (yes the other SATA one), on the "W" Drive, and load my .iso image disk of Ubuntu 10.04.01.

Allow it to do a full installation on its own drive.  No dual boot complications, because it never sees the "W" Drive.

Next, I went into BIOS Setup, set the boot sequence to show the Win 7 HDD 1st, the Ubuntu HDD 2nd, then the DVD, finally the BluRay.

Now the computer, which is sometimes used in the guest room in private, by house guests, will simply awaken as a Windoze machine, with guest priveleges.

I have the option to access the boot menu, via {Function 11} during startup, and of course, the password to launch Ubuntu, -and if I die, no one will ever know that one!  The entire HD is encrypted too.  :)  

The files I might want on the "W" Drive are also encrypted, so guests will not have access, and a Windows FAT 32 partition on the "U" Drive is also in the mix. 

Just FYI, and FWIW, in case I'm not the only one with a desire to have such a setup.

Works exactly like I had hoped.  COOL BEANS!
Bruce

---

