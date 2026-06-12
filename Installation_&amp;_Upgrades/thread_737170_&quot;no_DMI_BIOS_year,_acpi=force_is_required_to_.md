---
title: "&quot;no DMI BIOS year, acpi=force is required to enable ACPI&quot; then HANGS!"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by wontstoptalking on 2008-03-27
I can't install Ubuntu on my (rather old) HP Pavilion A440.

After popping in the install CD, and hitting "start or install Ubuntu" (or whatever the normal top one is), the screen flashes "no DMI BIOS year, acpi=force is required to enable ACPI" and then it shows the normal Ubuntu loading bar where the little orange bar is gliding left and right.

Then it goes away and the only thing on my screen is a flashing underscore in the top left corner of my screen. And then it just hangs.

I really am new to this "acpi" thing, but I'm not THAT stupid. It's telling me ACPI needs to be forced, so I rebooted, hit f6 before "starting or installing ubuntu" and added "acpi=force" to the options. It made no difference at all. Then, after posting this in the forums awhile ago, I came really close to finding an answer: someone said to put "acpi=off" in the boot options, not "acpi=force". When I did that, it did not show "no DMI BIOS year, acpi=force is required to enable ACPI", so I got my hopes up and thought it worked. It didn't. Even though it didn't show the acpi error, it still hung with that flashing underscore. And no, the alternate ubuntu install for some reason of my own is not an option for me, so please don't suggest it.

I'm looking at the boot options page on this site, and I am going to try to enter as many combinations of "acpi" related options as I can, but I would greatly appreciate any help I can get. I really need to get this going!

thanks

---

### Post by wontstoptalking on 2008-03-27
Can I please get some help on this one? I have limited time, and Windows failed on that computer, so it's useless!

---

### Post by wontstoptalking on 2008-03-27
Please help??

---

### Post by pietjanjaap on 2008-03-27
Look at de screen there are more options, maybe with no acpi,.

Or try the alternate cd, ther you can choose more options like vga , no acpi

---

### Post by wontstoptalking on 2008-03-27
Your grammer dead suggestion did not help!

Anyone?

---

### Post by pietjanjaap on 2008-03-30
Did you try the alternate cd with vga install?

[http://ubuntuforums.org/showthread.php?t=737728](http://ubuntuforums.org/showthread.php?t=737728)

Search on google with "ubuntu+name pc"

---

### Post by Aearenda on 2008-03-30
I think the ACPI message is a red herring, and the real problem here is something else. Pietjanjaap's suggestion about the alternate CD is what I would try next. 

Why did Windows fail on that computer? Are you sure there is no other hardware problem present?

---

### Post by aquinashub on 2008-04-08
Also, if you want to try all the different boot options - have you looked through all the boot options once you're actually at the live CD menu? I forget which key it was, but it gives you an actual list of options that you can use as boot options - I know, I've been trying to get Ubuntu up and running on my MDG Pentium D duo, it turns out that the Linux kernel doesn't fully support the ACPI functions in my BIOS, and subsequently hangs everytime. I found the "acpi=off" option in this help menu.

Boot up and play around, since I can't remember the exact key, but it's there. Give it a whirl.

---

### Post by musther on 2008-04-28
I just had this problem on an old laptop - try leaving the machine (I know it looks like it's hung) for a while, this one took about 15 minutes to get past this and start booting the CD, but it worked in the end.

---

