---
title: "The most awkward installation failure - Underscore Blinking on a Black Screen"
date: 2016-06-16
forum: Installation &amp; Upgrades
---

### Post by eugandara on 2016-06-16
[FONT=arial]
[/FONT]
[FONT=arial]Hi guys, [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I'm using Ubuntu since 5.04 and i never saw a so strange situation and i can't solved for myself.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]My live usb installation simple doesn't run, and start blinking an underscore on a black screen. I can open the First Screen where i can choose Try Ubuntu without installing; Install Ubuntu, Check disc for defects; Test Memory; Boot from first hard disk. If i click enter on Try without installing or Install Ubuntu happens the same, underscore blinking on a black screen. It happens also if i click enter on Check disc for defects.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]For you know:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]BIOS[/FONT]
[FONT=arial]* Secure Boot is disable[/FONT]
[FONT=arial]* Fastboot is disable[/FONT]
[FONT=arial]* CSM is enable[/FONT]
[FONT=arial]* Everything is on Legacy (on UEFI doesn't work also)[/FONT]
[FONT=arial]* Boot priority is ok[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]HARDWARE:[/FONT]
[FONT=arial]* I didn't change any hardware.[/FONT]
[FONT=arial]* I don't have Graphics Card. i used Intel from ASUS H97 Pro[/FONT]
[FONT=arial]* i'm using the same usb drive, one week ago it works the installation.[/FONT]
[FONT=arial]* I tried with more than one usb drive.[/FONT]
[FONT=arial]* On my laptop works, on my desktop not. Same ubuntu disc, same usb drive[/FONT]
[FONT=arial]* Im trying to install on a M.2 Plextor without dualboot, only Ubuntu.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]OTHERS:
[/FONT]
[FONT=arial]* I tried with nomodeset , nolapic, noapic, acpi=off (one each time) without success also.[/FONT]
[FONT=arial]* I tried to install Ubuntu 64bit, Ubuntu 32bit, Ubuntu Mate, Ubuntu Gnome, always without success.[/FONT]
[FONT=arial]* I tried to install trough CD Drive exactly the same underscore blinking on a black screen.[/FONT]
[FONT=arial]* I could install windows through usb drive flawless and i can install 100% so strange[/FONT]
[FONT=arial]* It happens also with Boot-repair usb disc, same underscore blinking on a black screen.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Who is the brave and enlightened that can have some solution for me= :)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]The most frustration was that one week ago i can do it and i didn't change NOTHING from that, everything is the same, hardware, usb drive, distribution, etc.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Many many thanks![/FONT]

---

### Post by ubfan1 on 2016-06-16
That "nomedeset" shoudl be "nomodeset" (typo?).  If you can select "legacy" instead of "CSM" that would be better -- CSM lets the machine decide, and the live media does both UEFI and legacy, so maybe it decided wrong, although why it changed I have no idea.

---

### Post by eugandara on 2016-06-16
Yes of course is nomodeset ;)

---

### Post by eugandara on 2016-06-16
> **ubfan1 said:**
> That "nomedeset" shoudl be "nomodeset" (typo?).  If you can select "legacy" instead of "CSM" that would be better -- CSM lets the machine decide, and the live media does both UEFI and legacy, so maybe it decided wrong, although why it changed I have no idea.

[COLOR=#000000]Yes of course is nomodeset [/COLOR]:wink:

[COLOR=#000000]With CSM Auto or Disable appear only black screen after i choose Install Ubuntu[/COLOR]
[COLOR=#000000]With CSM Enable and the option Boot Device Control on UEFI and Legacy OPROM appear black screen. With Legacy Only i have other screen on the boot, where i can choose the language and then the F6 options. But after i click install Ubuntu appear the [/COLOR][COLOR=#000000][COLOR=#000000][FONT=arial]underscore blinking on a black screen.

But and this is the awkward that i tell in the begging. One week ago i didnt need this options, i could boot the ubuntu from the usb with bios defaults. My curiosity ask me whats happens... so strange!!![/FONT][/COLOR][/COLOR]

---

### Post by ubfan1 on 2016-06-16
Now that you can boot, the rest sounds like a video problem.  USBs wear out, try the "check media" option instead of "try".

---

### Post by eugandara on 2016-06-17
> **ubfan1 said:**
> Now that you can boot, the rest sounds like a video problem.  USBs wear out, try the "check media" option instead of "try".

If it was video card problem why i can boot from windows usb drive and install until the end? 
I can't check the usb because after i clic on "Check disc for defects" appear black screen (only) and the same usb drive boot and works on laptop so the usb is ok. I believe that is something about my desktop but i didnt change nothing.

---

