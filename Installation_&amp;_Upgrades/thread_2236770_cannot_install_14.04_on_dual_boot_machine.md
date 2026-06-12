---
title: "cannot install 14.04 on dual boot machine"
date: 2014-07-28
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2014-07-28
Desktop with AMD 64 bit processor. About 1 year old.  Two hard drives, Ubuntu 13.04 on one, Windows 8.1 on the other.  Burned Ubuntu iso onto a USB stick.  When I start the machine, it gives me the options of trying Ubuntu or installing it, etc.  I choose to try it, and after a long long wait it comes back with a message that it cannot find any file system.

What should I try?

---

### Post by Bashing-om on 2014-07-28
raymondvillain; Hi !

Did you
Verify the download iso's integrity ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Did you burn the .iso as an image - not data at a slow speed ?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Did you "check disk for defects" ?
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)


Then if the hardware is good,

[INDENT][INDENT][INDENT]should boot
[/INDENT][/INDENT][/INDENT]

---

### Post by raymondvillain on 2014-07-29
The USB startup stick was made correctly, I'm pretty sure.  Used it to update OS 13.04 to 14.04 on the notebook on which I'm typing now, no problems.  Will try again, plan to open the box, disconnect the hard drive with Windows, then see if the install will proceed.   Unless anyone has a better suggestion.  Thanks for your reply,  Bashing-om.

---

### Post by raymondvillain on 2014-07-29
More problems.  Once the install is finished, the machine will not boot.  Looks like graphics problems also, some flavor of radeon graphics card is installed.  Screen is either black or has purple stripes.  Booted to the USB stick and viewed the grub file, managed to add "nomodeset", but don't know how to update grub (the grub file on the hard drive) unless it will boot.

Any ideas?

---

### Post by Bashing-om on 2014-07-29
raymondvillain; Well,

I have a couple of ideas,

Can, do you, boot to the grub boot menu ?

1) From the grub menu, what results when you attempt to boot from a 'recovery' kernel ?
2) If you use the boot parameter "nomodeset" as a boot parameter in grub ( boot menu, press 'e' key). Are you able to boot to the desk top ?

3) Have you, once to the desk top, 
a) updated the system
b) looked at what drivers are provided in the "Additional Drivers" utility --Hey, not real sure it is still installed in 14.04 (??) 

[INDENT][INDENT]maybe yes,
[INDENT][INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by raymondvillain on 2014-07-29
If I install 14.04, is it automatically a "virtualbox" installation?

---

### Post by raymondvillain on 2014-07-29
Sorry, Bashing-om.  Didn't see your post.  

Grub does not appear.  Don't know what happened to it.  I have to go to the "settings" feature at boot up, and scroll down to the hard drive that has Ubuntu installed on it.  Then it boots.  I finally got it to work.  Don't really know what did it.  I think it started working when I removed the USB stick from the machine before booting to the hard drive.  Seems to work, yes, updated the system, looking for proprietary drivers now.  Thanks for checking up on me.

What should I do to have a "grub" screen appear at startup (the one with choices of Ubuntu, recovery mode, etc.)?

---

### Post by raymondvillain on 2014-07-29
Should mention that somehow the grub file now has "nomodeset" incorporated in it.

Once I use a proprietary graphics driver, how do I put it to use?

---

### Post by raymondvillain on 2014-07-29
Wow!  "Additional Drivers" is indeed included in 14.04, and after using it, the display is great.  Thanks very much for the tip, Bashing-om. Going to mark this thread "solved", but don't ask me how it came about.

---

### Post by Bashing-om on 2014-07-29
raymondvillain; Well that is just great !

> 
but don't ask me how it came about.


Hey, that is because you do good work, and "Additional Drivers" is some kind of smart.

As to grub's boot menu; if ubuntu is the only operating system installed onto the system - by default the boot screen is not displayed.
This behavior may be changed by an edit to the file '/etc/default/grub' if so desired.
else to see the boot menu try:
as soon as the bios screen clears, depress and hold the right shift key, -> else it is the escape key, else it is to repeatedly tap the keys ( after the bios screen clears).
This depends on what your bios/grub communicates.  

[INDENT][INDENT]enjoy 14.04.....[/INDENT][/INDENT]

---

