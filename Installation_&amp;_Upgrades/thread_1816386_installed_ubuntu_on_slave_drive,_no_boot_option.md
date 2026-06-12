---
title: "installed ubuntu on slave drive, no boot option"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by Virtua-Touch on 2011-08-01
I have windows 7 installed on my 320gb master drive and i just installed Ubuntu 10.04 (can't find my 11 disc lol) on my 160gb slave drive and i can't boot into it because there is no boot option.

---

### Post by Hakunka-Matata on 2011-08-02
> **Virtua-Touch said:**
> I have windows 7 installed on my 320gb master drive and i just installed Ubuntu 10.04 (can't find my 11 disc lol) on my 160gb slave drive and i can't boot into it because there is no boot option.

There is no boot option, as in BIOS does not allow you to boot the slave drive?  Or are we talking about no Grub dual boot menu showing up as the first screen?

---

### Post by Virtua-Touch on 2011-08-02
I had no grub menu, just my windows boot menu, and when i tried to set the slave drive to boot first, it skipped straight to the master. I also came up with another problem. I tried installing it straight onto the master, but it wont boot. Just gives me a black screen with the blinking underscore in the top left corner. I have a feeling its because of the card, but the LiveCD booted fine and graphics were perfect, so maybe my boot records are just all screwed up.

---

### Post by Hakunka-Matata on 2011-08-02
Apparently you're getting the Grub menu and can select Ubuntu?  
What Release Ubuntu? 10.04 or have you gone to Natty?


nomodeset option may fix it for you.

Look at the first post in the thread link below.  it has a good graphic of how the command line in question should look after adding nomodeset option
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

When the grub menu comes up at boot time, you want to edit the Ubuntu selection, and add nomodeset to the very end of the line that starts with 
"linux /boot/vmlinuz-...(and probably ends with) ........... quiet splash 

,,,,,,,,,,,,,,,, quiet splash **nomodeset**

If that works set additional drivers active and hopefully you'll get the right nvidia driver installed.
**System > Administration > Additional Drivers**

---

### Post by Virtua-Touch on 2011-08-02
it's all good. I think my 10.04 disc wasn't burned properly or corrupted. I installed 11.04 this morning and I'm booting fine.

---

### Post by Hakunka-Matata on 2011-08-02
Hey, that's great, glad to hear it.

---

