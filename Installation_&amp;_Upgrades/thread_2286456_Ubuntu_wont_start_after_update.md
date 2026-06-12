---
title: "Ubuntu wont start after update"
date: 2015-07-12
forum: Installation &amp; Upgrades
---

### Post by anders-soerensen on 2015-07-12
I installed Ubuntu and updated, now it wont start and show me this..Any ideas ?

---

### Post by Bashing-om on 2015-07-12
anders-soerensen; Hi ! Welcome to the forum.

My old eyes can not make out what release you are running. Please advise.

In any event: 
can you boot to the grub boot menu ?
can you boot to terminal ?
can you boot with the "nomodeset" boot option ?

"assuming" a lack of experience at this time, additional advise is pending to get you to a terminal access condition.
Once in terminal we can do the diagnostics and determine where the fault lies.

Booting too
[INDENT][INDENT][INDENT]is just a process
[/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-07-12
Actually, even with the image on its side all the actions are marked as OK. There are none marked as Fail, as far as I can see. The last action shown on the screen is to start Light Display Manager which is also marked as OK and brings the loading process to the login screen. Or should do.

What happens next? "Wont start" is not descriptive enough. Does the login screen not appear?

Do you see a boot menu? If you do then select Advanced options for Ubuntu and then select Recovery Mode and at the recovery menu select Resume. That should load Ubuntu to a desktop using a fail back open source video driver. Does it?

Regards.

---

### Post by anders-soerensen on 2015-07-13
Nothing happens after this.. I tried to enter GRUB menu but i cant.. I can acsess the boot menu but i tried changeing almost everything in there with same result as the picture.. The release i think is 14.??, i cant remember the ending - sorry

---

### Post by anders-soerensen on 2015-07-13
Its the 15.04 version, i finally came into the GRUB menu, but what am i supposed to do here.. It wont connect to network as it cant start network manager, i tried running the failsafex, but it says error No screen..

---

### Post by Bashing-om on 2015-07-13
anders-soerensen; Sorry;

As much as it pains me to say, with 15.04 not much I can advise . Release 15.04 uses systemd as the initiate system and I have no experience to this date with the new system.

I am open to this learning situation, hopefully others will advise on booting 15.04 from the grub menu.

[INDENT][INDENT]if I knew it all
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT] [/INDENT][/INDENT]

---

### Post by anders-soerensen on 2015-07-14
I have been trying for a few days to fix this, somehow it wont install the libgbm1 xorg package, i think the problem have something to do with the driver to the screen..

---

### Post by Bashing-om on 2015-07-14
anders-soerensen; Hey;

As advised I have very limited experience with 15.04, I do have it installed and I have been experimenting getting a terminal from the grub boot menu. My results somethings to be desired.

However, This might work for us in your case to get us a working interface with networking.
Here we must have a wired internet connection .

Boot the install to the grub menu. With the latest kernel selected (asterisk) press the 'e' key for edit mode -> boot parameters screen.
Arrow down to the line starting with 'linux' ; similar " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff" and arrow across to " quiet splash" and insert the term "nomodeset" -without the quotes -following "quiet splash". Key combo ctl+x to continue the boot process.

Can you now get to the GUI login screen ?
can you activate the GUI desktop when username and password is entered ?

IF you are now at the desk top - degraded graphics IS OK at this point - does key combo ctl+alt+t gain you a terminal interface ?

IF you can get a terminal interface, now we have a means to do something !

[INDENT][INDENT]If I knew better
[INDENT][INDENT][INDENT]I would say
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

