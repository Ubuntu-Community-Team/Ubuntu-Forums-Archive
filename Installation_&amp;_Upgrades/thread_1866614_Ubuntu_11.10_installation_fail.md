---
title: "Ubuntu 11.10 installation fail"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by SoWhat.lv on 2011-10-21
Tried to install from Windows, tried to install from USB, finally burned CD and every time the same result:

[http://www.youtube.com/watch?v=567zh9xNPxw](http://www.youtube.com/watch?v=567zh9xNPxw)

---

### Post by MG&amp;TL on 2011-10-21
You mean it's the wrong way around?

That is...interesting. Maybe you should report a bug to the ubuntu devs on launchpad or something.

[http://launchpad.net]("http://launchpad.net")

---

### Post by Utew on 2011-10-21
This has to be a joke....

---

### Post by SoWhat.lv on 2011-10-21
no no, its just because of my web camera :) problem was that it stays in this position and doesn't continue installation.

but I found a solution - you have to press F6 and turn off ACPI, then installation continues further. here is more info [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by MG&amp;TL on 2011-10-21
Have you built your own pc or anything? I guess if you wired the monitor cable the wrong way...

OH, right, okay. We thought that was the issue. Oops, sorry.

---

### Post by Utew on 2011-10-21
Ok, so when you say further.. how far?

---

### Post by MG&amp;TL on 2011-10-21
Well, I can only suggest that you play around with the boot options,  until something gives.

You can then boot from grub (once installed) and change the boot options there, then set them permamently in the grub boot options file. If you give me a minute I'll find which one you need to edit. If you get that far.

---

### Post by SoWhat.lv on 2011-10-21
My first linux installation finally is over and successful.

Now I cannot start ubuntu until ACPI mode is not turned off permanently. How to achieve this is written here [https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation](https://help.ubuntu.com/community/BootOptions#Changing_boot_options_Permanently_for_an_Existing_Installation)

Thanks for help, guys! Even though I found solution myself, this is quickest support I have ever experienced.

---

### Post by MG&amp;TL on 2011-10-21
Well done! I hope you enjoy it. And it is very fast here. :)

Oh, btw you can temporarily change the grub boot entries.

---

### Post by SoWhat.lv on 2011-10-21
Did you find how to turn off ACPI permanently? I am reading through this documentation and it is too advanced for a beginner like me :( the only method I understood is to burn Boot-Repair in CD, but I don't have any free CDs left.

---

### Post by MG&amp;TL on 2011-10-22
See here:

[http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")

Works for me. :)

---

### Post by SoWhat.lv on 2011-10-23
thanks! It was so simple :) perfect manual!

---

