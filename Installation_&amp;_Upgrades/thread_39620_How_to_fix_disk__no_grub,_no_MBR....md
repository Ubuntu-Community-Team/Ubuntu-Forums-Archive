---
title: "How to fix disk?  no grub, no MBR..."
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by thechris on 2005-06-05
ok, i've got an odd problem.  i want to use grub on the MBR of hda.  however ubuntu tells me that i can use neither grub nor the MBR of hda...  i cannot fix the MBR with any tools i have.  i have tried the universal boot cd (has many tools).  any fdisk tool crashes with a devide by zero error.  currently i'm running memtest86 to confirm that this is not a memory related error.

i am given the option of installing LILO on either hdb or hda1 or hdb1.  currently LILO is installed on hda.  it was installed on a gentoo install becasue grub kept segfaulting when it attempted to do:  setup (hd0).  gentoo had issues possibly related to the video card.  an inactive screen (sleep mode led) was the result of a boot attempt.  earlier i had tried the 64bit verison of ubuntu which did boot, but did not detect my common network card...

this is for a PVR box, so i am now trying the 32bit version of linux for better media support.

i cannot boot from a windowsXP CD on this computer...  this however is because the people at MS can't make an installer that works...

EDIT SOLVED:  i had to change the parition table in order to get the system to work.  in the end i moved swap to be hda4 instead of hda3.  it seems this for some reason fixed the problem.  memtest86 ran 2hours without errors.  things seem to be looking up.  now lets just hope my video card keeps working...

---

