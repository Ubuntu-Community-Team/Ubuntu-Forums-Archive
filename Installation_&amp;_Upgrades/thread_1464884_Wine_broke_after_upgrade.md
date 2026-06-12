---
title: "Wine broke after upgrade?"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by Doug11 on 2010-04-28
I just upgraded to Lucid a few days. All went well and I seem to like it. But when I went to get a new program to run in wine, any EXE i try to install will not work. Is there a fix for this? I will try find the exact message.

---

### Post by Doug11 on 2010-04-28
Here is what the error is
> The file '/home/doug/Downloads/angel201b2.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by Doug11 on 2010-05-03
*Bump

---

### Post by lechien73 on 2010-05-03
Wine isn't broken, it's just Nautilus stopping you from executing an untrusted file.

To get the file to execute, right click on the file and go to Properties. Click on the "Permissions" tab, and check the box that says "Allow executing file as program".

If the .exe file is an installer, then Wine will automatically give the installed program executable permissions.

HTH

---

### Post by Doug11 on 2010-05-05
> **lechien73 said:**
> Wine isn't broken, it's just Nautilus stopping you from executing an untrusted file.

To get the file to execute, right click on the file and go to Properties. Click on the "Permissions" tab, and check the box that says "Allow executing file as program".

If the .exe file is an installer, then Wine will automatically give the installed program executable permissions.

HTH

Thanks, that did the trick. I had to do that with all the exe files that i had.

---

