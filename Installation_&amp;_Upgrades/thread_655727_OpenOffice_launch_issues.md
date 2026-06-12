---
title: "OpenOffice launch issues"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by indrajal on 2008-01-01
After upgrading to Hardy, I found that Open Office does not launch anymore. After taking it out and reinstalling, I am able to launch it from the command line by typing openoffice.

However, I am not able to launch it from the menu. Also, the look and feel has changed - it looks like a java application as opposed to a native application.

I am running Ubuntu Hardy on AMD64.
Would appreciate greatly for pointers on how to get it to work again.

Thanks!

---

### Post by Shinbu-Otaku on 2008-01-04
i had the exact same problem on 6.10, but when i upgraded to 7.04 it was fine after that, and i never did fully understand why the functionality disappeared, as i had re-installed it a good few times as well.

Come to think of it, it did start going funny after i installed the 3D driver for my Nvidia card, maybe it had something to do with tht. What graphics card do you have? and which version is Hardy Heron, i just use the number codes instead i.e. 6.06, 6.10 etc

---

### Post by indrajal on 2008-01-04
Yes, I do have an NVIDIA driver, but, the system worked fine before the upgrade. I am using 8.04.

Its really annoying not to have Openoffice launch from the menu - I wish there was a way to fix this.

---

### Post by jahst on 2008-06-25
I know this thread is old, but I just switched from Xubuntu to Ubuntu and ran into this same problem.
Its probably not even close to the correct fix, but at least I can launch openoffice from the menu.

I simple used the menu editor ... System - preferences - main menu
Clicked on Office menu on left
Unchecked the Office Write and Office Spreadsheet icons to hide them
Checked the OpenOffice.org icon to show

Then right clicked on the OpenOffice.org icon and selected the properties.

Changed the launcher command to 

/usr/lib/openoffice/program/soffice.bin

Close menu editor

Then launch OO from the menu and pick Text or Spreadsheet from the "new" icon in the top left corner.

Good enough for me

The default entry "oofromtemplate" worked for me too... but i didnt like the look and options.

---

