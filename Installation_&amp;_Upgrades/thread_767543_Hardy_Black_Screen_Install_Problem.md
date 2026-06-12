---
title: "Hardy Black Screen Install Problem"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by GeckoPie on 2008-04-25
Hi,
I'm attempting to install Hardy on my laptop (HP Compaq 6715s) using Wubi.  I've selected KDE5 and all installed Ok on the windows side.  I then proceeded to reboot when requested and selected Kubuntu from the Grub menu, the boot loading screen did its blue bar loading thing.  I was then however greeted with a black screen, the screen isn't dead as you can see the backlight...its just black.

Anyone any ideas to why this could be happening and how I could possibly solve it?  I'm running an ATI Radeon X1250 (Mobile) and an AMD Sempron (also mobile).  I did previously boot from the LiveCD and after a long long wait (In excess of 30mins) I reached the gnome and graphics were all working ok, I couldn't however install as I was presented with the same black screen...I gave up waiting and rebooted to try installing using Wubi.

Any help would be much appreciated, many thanks.

// Edit: I also tried using Ctrl+Alt+F1 though to F8 to try and get a terminal etc...all remained at a black screen.

---

### Post by GeckoPie on 2008-04-26
Update:
I finally managed to boot it after multiple tries, it booted into the install and started formatting, I went away for abit to return to the black screen once again :(
This is really bugging me since this is the first Ubuntu which actually supports my graphics card and I really want to get it installed :(

Please anyone, any help would really be appreciated :confused:

---

### Post by GeckoPie on 2008-04-28
Bump

Please...anyone :'(

---

### Post by Samw13 on 2008-05-02
Use the text based installer and either set noapic or acpi=off (press F6 twice to get a sub menu thing)
with noapic makes everything slow especially on boot
Hope this helps

---

### Post by alyaba on 2008-05-14
did this fix your problem? im having the same issue

---

### Post by Samw13 on 2008-05-18
I just gave up and went back to 7.10... Seems to be an issue with the new ACPI packages I think!

---

