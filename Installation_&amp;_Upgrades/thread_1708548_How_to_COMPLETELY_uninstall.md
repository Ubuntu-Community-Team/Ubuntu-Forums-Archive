---
title: "How to COMPLETELY uninstall?"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by Poppyann on 2011-03-16
Hello,

I have installed Kubuntu 10.04 alongside Windows Vista, but I have decided it's not for me.

How to I completely uninstall this? If I uninstall from control panel, it doesn't give me back my disk space that I allowed it as Ubuntu does :confused:

Sorry about the newbie question, but any help would be great.

---

### Post by Frogs Hair on 2011-03-16
Because Ubuntu appears inside windows you must be using Wubi. You could try defrag or wipe the free space with one of many free Windows utilities .This one includes file shredder free space cleaner. [http://download.cnet.com/Glary-Utilities/3000-2094_4-10508531.html](http://download.cnet.com/Glary-Utilities/3000-2094_4-10508531.html)

---

### Post by Poppyann on 2011-03-16
> **Frogs Hair said:**
> Because Ubuntu appears inside windows you must be using Wubi. You could try defrag or wipe the free space with one of many free Windows utilities .This one includes file shredder free space cleaner. [http://download.cnet.com/Glary-Utilities/3000-2094_4-10508531.html](http://download.cnet.com/Glary-Utilities/3000-2094_4-10508531.html)

So... to uninstall Kubuntu I need to use Wubi...? 

I thought I would have had to format the partition, Im just not sure how to do it

---

### Post by bcbc on 2011-03-17
If you installed inside windows (using Wubi) then just uninstall Ubuntu from the Control Panel, Add/Remove programs. 
No formatting required.  

You can tell if you installed with Wubi because the first menu you see when you bootup shows Windows and Ubuntu in the list, and after choosing Ubuntu you see the grub menu.

If you installed direct to partition - you'll see the grub menu first after booting - then you need to reinstall the Windows bootloader first and make sure it's booting direct to Windows (no grub menu displayed) and then you can delete/reformat the partition used by Ubuntu.

---

### Post by TechSupportx86 on 2011-03-17
If i understand correctly, you removed kubuntu via add/remove programs and you are missing the space it took up?

go into windows and open up computer manager (Start > Right click "Computer" > Manage), Click on "Disk management", Then see if you have any "Unallocated Space" under "Disk 0" (or wherever you installed it

Let me know what you see and we'll go from there :wink:

---

### Post by Poppyann on 2011-03-17
> **TechSupportx86 said:**
> If i understand correctly, you removed kubuntu via add/remove programs and you are missing the space it took up?

go into windows and open up computer manager (Start > Right click "Computer" > Manage), Click on "Disk management", Then see if you have any "Unallocated Space" under "Disk 0" (or wherever you installed it

Let me know what you see and we'll go from there :wink:

Hello! Sorry for the late reply, I was at college :(

Anyway, I would have done what you said BUT! I reinstalled Vista this morning. It's okay because I had only done it recently yesterday after a Windows 7 Problem, so no files were lost. I assumed it'd just be the simplest probably safest way, and it's turned out good. I am now back with Ubuntu and prefering it.

Thank you for your response, have some popcorn :popcorn:

---

### Post by Frogs Hair on 2011-03-17
> **Poppyann said:**
> So... to uninstall Kubuntu I need to use Wubi...? 

I thought I would have had to format the partition, Im just not sure how to do it

In order to have Ubuntu appear in add and remove programs in Windows you had to have installed using Wubi.

---

