---
title: "&gt; Unbuntu Installation Problems!"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by DLLN on 2008-07-12
Alright I tried to install Ubuntu in my local E drive which hasn't been used at all yet. Something went wrong so i wanted to uninstall Ubuntu from add and remove in windows. I did that and when i rebooted Ubuntu still booted up. Then i went to windows and looked at the Properties of my Local E and it now says its 15Gb(which was the amount i assigned for the Ubuntu OS) and before the drive was 104Gb. WHAT THE HELL, where did all the hard dirve space and my didn't Ubuntu unstall?? I still would like to run Ubuntu when i sort this out. Can i just format my local drive E with out affecting my Drice C which has all my windows files on it.

THANKS

---

### Post by avtolle on 2008-07-12
How did you install Ubuntu on the E drive? Wubi, or an install directly from the installation CD (not Wubi, a/k/a "Install Under Windows")? If the latter, you can format the partition to remove Ubuntu. If the former, have you looked at the Wubi Users Guide for correct removal procedures?

---

### Post by DLLN on 2008-07-12
I installed from a disc in windows.  So if i format the E drive it will go back to being 104Gbs? I havent read the user guide, but how would you suggest to reunistall Unbuntu on My Drive E once it has been formatted, use wubi or the disc?

Thanks

---

### Post by avtolle on 2008-07-12
I think I need a bit of clarification (due to the lack thereof in my original questions to you). Let's keep it simple; the answer to the first question appears to be that you did "install under Windows", which is by a program known as Wubi. Is this correct?

EDIT: If this is correct, see [https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d) for uninstalling.

---

### Post by DLLN on 2008-07-12
Ok i see sorry.  I installed it under windows.

---

### Post by avtolle on 2008-07-12
No need to format the partition, then; in fact doing so might foul up your Windows installation. Look at the link added by edit to my prior post; if using Add/Remove under Windows didn't work, there are some other options provided you.

---

### Post by DLLN on 2008-07-12
I don't know somethings really messed up!   I did this "In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line."  But the line wasn't there!  I unistalled it from add and remove but when i boot up it's still there as an OS option. But theres more then just one Ubuntu OS to choose from, there's about five options two of them say recovered or something in brackets.  I Formatted the Local E and there still there. And the Drive E stills says that it's 15Gb instead of 104Gb!!

---

