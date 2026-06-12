---
title: "LiveDVD nomodeset nVidia GeForce 6150 SE"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by MoeNeigh on 2014-08-22
I am currently trying Ubuntu 14.04 on the LiveDVD 64-bit. I had to use the nomodeset option to get the graphics to display in Ubuntu (to avoid the black screen). It first comes up as 1024x768. Then in Software Updates under Additional Drivers I seclected nVidia 173, which covers GeForce series 5 through 9. My card is GeForce 6150 SE nForce 430. I logged out of the live session and back into it, and the graphics were updated based on the 173 proprietary driver.

My question is, if I select "install Ubuntu" now from this live session, will I have another chance to select nomodeset, so I won't have to deal with a black screen, and then I can install the nVidia 173 driver again (for real this time), or will I end up with a black screen? Are there any advanced options during the first boot where I can select nomodeset if I have to?

Currently, I am using opensuse 13.1, and I thinking of switching to ubuntu 14.04 LTS.

Thanks in advance for any help.

~George

---

### Post by ubfan1 on 2014-08-22
Usually you just install the nvidia-current package and let the appropriate driver be installed -- that was Nvidia 304.116 on my 6150.  At the grub menu, (hold down shift key to force the menu to display if only one OS on the machine), you can type "e" to edit (instructions at bottom of screen), and add the "nomodeset" to the line starting with "linux".  Then you can install the nvidia-current and hopefully be all set.

---

### Post by MoeNeigh on 2014-08-24
Thanks, ubfan1. Do I hold down the Shift or tap it several times? I've seen conflicting reports on this. I guess I hold it down as soon as I turn the computer back on, or do I wait for a certain point in the boot process?

---

### Post by ubfan1 on 2014-08-24
Try holding down the shift key after the Power On Self Test (POST), or at the vendor logo splash screen.  Some machines might think a key is stuck if held down too early, hence the "hit several times".

---

