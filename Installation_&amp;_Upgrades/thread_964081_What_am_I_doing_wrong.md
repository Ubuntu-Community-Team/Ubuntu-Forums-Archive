---
title: "What am I doing wrong?"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by stateeofmind on 2008-10-30
I recently downloaded Ubuntu and was pretty eager to install it. I am currently on Windows XP home edition on a laptop. I download the iso for ubuntu and began to mount the iso and install it to my pc.

It went on the c-d with no problems, then I ran the c-d. After I get to the menu on which to install I slect the regular way and I just get a "Please wait... Loading" text with a command prompt.

Any word on what I am doing wrong? The software from the loading stays blank and I can't do anything.

---

### Post by Partyboi2 on 2008-10-30
Have you checked the iso you downloaded that the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") matches and checked the cd for defects after you burnt it at x4 or less? To check the cd for defects it is one of the options at the main menu.

---

### Post by stateeofmind on 2008-10-30
I am checking now....

The command prompt starts with "initramfs".

---

### Post by Partyboi2 on 2008-10-30
If the md5sum passes then try using some boot options. At the main menu press F6 and at the end of the line add 
```
 all_generic_ide floppy=off irqpoll
``` then press enter and see how you go.

---

### Post by stateeofmind on 2008-10-30
CD came back good. I just did that and I got

"all_generic_ide : not found"

I just installed Ubuntu with the same disk on my sisters laptop and it worked perfect. I wonder why it's not on mine.

---

### Post by Sef on 2008-10-30
>  I just installed Ubuntu with the same disk on my sisters laptop and it worked perfect. I wonder why it's not on mine. 	

Likely hardware problem then.  Please list your hardware.

---

