---
title: "Help!...Cannot reinstall 8.0.4 LTS."
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by doubleleo on 2008-05-19
I just replaced my motherboard. I now have a MSI MS-7033 with Intel Pentium 4 Prescott (LGA 775). I have dual boot setup (Ubuntu 8.0.4 & Windows XP Pro). Things worked great with old motherboard. Now, I cannot boot from 8.0.4. Screen ultimately stays blank whether I try booting from CD or hard drive. In recovery mode, it appears that everything is loading and looking OK, but at a certain point, screen just stays blank. I'm able to boot into XP with no problems...

Everytime I try to reinstall from Live CD, I get to a point where it just seems to hang/stop--no HD LED or anything.  I just don't understand why I can't reinstall just because I change motherboards.  Any help would be greatly appreciated!  I want Ubuntu back!

It's a little disturbing that XP works fine....:confused:

---

### Post by cdtech on 2008-05-19
Are you running a dual drive setup? How is the bios setup?

---

### Post by doubleleo on 2008-05-19
No, I don't have dual drive setup.  Ubuntu and XP are on same drive.  I use Grub to choose at boot up.  What should I check in the BIOS?

---

### Post by cdtech on 2008-05-19
So you selected a partition of windows to install ubuntu. You can select the windows partition using grub, correct? You should be able to hilite the ubuntu selection in grub, press "e" to edit the command line and see which partition the ubuntu points to.

It should look something like this:
hd0,1 (the second partition on the primary disk)

Windows would probably look something like:
hd0,0 (the first partition)

If Ubuntu see's hd0,0 it will get lost, because it cant find the boot image

Hope this helps.....

---

### Post by doubleleo on 2008-05-19
Ubuntu sees hd0,2...There's another strange symptom-When I try to boot to Ubuntu on HD or from Live CD, my floppy drive light stays on continuously as though it's trying to read a floppy that isn't there.  This occurs when I get the black screen freeze effect.  The only indicator lights are power and floppy drive...Again, this does not happen when booting to XP.

---

### Post by Franc88 on 2008-05-19
Did you check to see if that MB and bios is compatible with Linux?  I mean you did change a major part of your system so expect some issues.

---

### Post by punkybouy on 2008-05-19
Your floppy light is probably on because you have the cable connected wrong.  I believe the part with the twist in it goes toward the power plug so flip it around and see if that fixes it.

---

### Post by punkybouy on 2008-05-19
The other question would be about the CPU. Did you switch from AMD to Intel?

---

### Post by doubleleo on 2008-05-20
I'm certain that floppy drive is connected properly--as I inserted a floppy disk and copied files from it in XP successfully.

I only changed the MB--nothing else.  The processor is the exact same one used in the other MB--Intel LGA775.

I will research tomorrow to see if MB is Linux compatible.  It's disturbing to think that it is not.  I didn't realize that there are MBs that are only friendly with Windows...

---

### Post by Gio-van-I on 2008-05-20
I had that same thing on feisty. Blank screen instead of GUI. My solution was ctrl+alt+backspace. For some reason the GUI loaded correctly afterwards.

Can't garanty it will work. But if it can get you in the Live-CD you can at least think of your next action.

---

### Post by Cap'n Skyler on 2008-05-20
is the boot sequence right?or is it at the defaults from the motherboard 
bios settings?:popcorn:

---

