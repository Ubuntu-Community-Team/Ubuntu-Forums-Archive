---
title: "Installation of Ubuntu after installing Windows 7"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by Waffletaco on 2010-01-16
Ok sooo heres my deal.  And im srry if this was answered in another thread but i am REALLY noob atm, so any help would be appreciated.  I installed windows 7 on a 500gig HD then put in an 80 gig HD and installed Ubuntu.  For some reason when i turn on my computer now with either of the HD's in the first boot sequence i get a screen that just says GRUB and thats it Like i cant type anything or do anything and GRUB _ is all that appears.  If you know what i did wrong and also if you could right my wrong without having to REINSTALL windows please let me know =D.
Thanks alot 
Matt

---

### Post by alwayshere on 2010-01-16
try diconecting unpluging the ubuntu hd and see if thr win7 boots ok then ?
when i used to dual boot from seperate hd's i would  go to the bios and turn the hd off i didnt want to use(im not talking boot order here)'I found i didnt seperate them all hell would brake loose resulting in o.s reinstalls .
These days I use virtualbox see the link  [http://www.virtualbox.org/]("http://www.virtualbox.org/")

---

### Post by Waffletaco on 2010-01-16
So i took your advice i unplugged the ubuntu drive and it still came up with GRUB _ .  then i plugged it back in and uplugged the Windws 7 drive and it now says Reboot and Select Proper boot device or inert boot media in selected boot device and press a key

---

### Post by kansasnoob on 2010-01-16
When you installed Ubuntu it grub probably installed to the mbr of the Windows drive (no worries, it's easy to fix), but to get a truly clear picture of exactly what's going on I need you to post the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Of course you'll have to boot the Live CD and run that from the live desktop.

---

### Post by Waffletaco on 2010-01-16
ok so, im not even able to get on to Ubuntu.  but now that i have unplugged the ubuntu harddrive Windows 7 loads for me.  So i wont be able to get you the report you were looking for

---

### Post by kansasnoob on 2010-01-17
With both drives plugged in you should be able to run that script from the Live CD. Just boot to the live desktop by choosing Try Ubuntu without changes ..... from the Live CD boot menu.

---

