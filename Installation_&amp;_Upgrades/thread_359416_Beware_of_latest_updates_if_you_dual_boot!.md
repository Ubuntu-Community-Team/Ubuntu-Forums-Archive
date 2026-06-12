---
title: "Beware of latest updates if you dual boot!"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by trents on 2007-02-11
Beware of the latest Dapper kernel updates. I installed them today and they removed the references to Windows XP in the menu.lst file. I couldn't get into Windows until I reinstalled Ubuntu. There may have been an easier way but I wasn't sure what the sytax should be to include XP in the boot list. Anyway, I renabled all the repositories after the new installation and performed all the updates again and guess what? Windows was removed from the boot list again. Fornunately, I made a backup copy of menu.lst before updating this time to refer to for syntax.

Steve

---

### Post by logos34 on 2007-02-12
Just out of curiosity, where did you have your windows entry? Was it in the debian automagic kernels list section or after it?

---

### Post by trents on 2007-02-12
I moved it from the "Other OS" section to the top of the automatic section. I update Dapper frequently and this never happened until today.

Steve

---

### Post by logos34 on 2007-02-12
I think that's your problem...Works fine until an update when automagic kicks out any non-ubuntu kernels.  
[URL="http://users.bigpond.net.au/hermanzone/p15.htm"]
"4. What NOT to do-  don't paste your Windows entry anywhere inside the automagic kernels list because it will be deleted when you have a kernel update in Ubuntu."[/URL]

---

### Post by Herman on 2007-02-12
logos34 is correct, you should not paste entries for any foreign operating systems inside your debian automagic kernel list or they will be automagically deleted every time you receive a kernel update.

Possibly you followed some bad advice about how to make Windows boot first by default?

Here is a Windows boot entry from the bottom a typical menu.lst file. You may copy this one and paste it to the bottom of your to repair it if you haven't already done so. You may need to edit it to make it suit you particular setup.
```
### END DEBIAN AUTOMAGIC KERNELS LIST
                                                                 
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP
rootnoverify        (hd0,0)
savedefault
makeactive
chainloader    +1
``` Regards, Herman

---

### Post by Herman on 2007-02-12
If you want, you can paste your Windows entry above the top of the automagic kernels list, then it will boot first by default and it won't get deleted.
The top of the automagic kernels list means above the lines that look like this,
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```Regards, Herman :)

---

### Post by trents on 2007-02-12
Thanks, I'll try it. But still doesn't answer the question of why this never happened before. Like I said, I update the Dapper OS frequently. Has there been a recent change in how foreign OS's are handled in the update process?

Steve

---

### Post by Herman on 2007-02-12
No Steve,  the automagic kernels list has been the same as long as I can remember. Most likely you were receiving updates alright, but this must have been the first time you received a new kernel in the update. Not all updates include new kernels. Most of the time they just contain updates for the rest of our software.
Regards, Herman :)

---

### Post by trents on 2007-02-12
> **Herman said:**
> No Steve,  the automagic kernels list has been the same as long as I can remember. Most likely you were receiving updates alright, but this must have been the first time you received a new kernel in the update. Not all updates include new kernels. Most of the time they just contain updates for the rest of our software.
Regards, Herman :)

Yep, that must be it, Herman. Thanks.

Steve

---

