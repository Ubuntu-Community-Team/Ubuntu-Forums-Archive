---
title: "newbie here who's very very stuck..."
date: 2005-02-25
forum: Installation &amp; Upgrades
---

### Post by subways on 2005-02-25
altho its probably really easy to solve

downloaded the warty-install-i386.iso file, then used nero to burn it to cd (im on XP)

I rebooted pc and let it boot from cd-rom...

got as far as the screen that asks press enter to start installation etc...


the very next screen is about my location/keyboard.......but the lights on my keyboard arent on, and altho the english one is selected i cannot seem to press any button to make it continue, where did i go wrong??

---

### Post by bored2k on 2005-02-25
grab the md5sum from the site u dl it from , and check ur .iso
if it dl correctly, they both should hav the same number

[http://www.brandonstaggs.com/filecheckmd5.html](http://www.brandonstaggs.com/filecheckmd5.html)

its not a solution btw

also, b4 u press enter at the start, press F1 to see if u need any of the special boot parameters [ur keyb whatever

---

### Post by Sgood1971 on 2005-02-25
[QUOTE=subways]altho its probably really easy to solve

downloaded the warty-install-i386.iso file, then used nero to burn it to cd (im on XP)

I rebooted pc and let it boot from cd-rom...

got as far as the screen that asks press enter to start installation etc...


the very next screen is about my location/keyboard.......but the lights on my keyboard arent on, and altho the english one is selected i cannot seem to press any button to make it continue, where did i go wrong??[/QUOTE]


Also, try reburning at the slowest speed you can set your drive to. Faster burn speeds some times cause weird problems.

---

### Post by subways on 2005-02-25
Sadly Ive done all that, and even tried with a version of fedora that my mate has, all to the same problem, as soon as the gui loads I cannot do anything on the first screen as it just wont take commands from the keyboard

---

### Post by W. Irving on 2005-02-25
Is it a USB keyboard?
In which case, perhaps BIOS doesn't provide USB support..

---

### Post by subways on 2005-02-25
No its the standard keyboard attachment (forget the name, but the purple circle end :) )

---

### Post by W. Irving on 2005-02-25
That'd be PS/2 then (;)).
Right. Check for glitches. PS/2 connectors seem to be prone of 'ejecting' themselves.
Does the keyboard work in DOS? Or before Windows has started loading?

I'm only just starting out with Linux myself, but my 15 years of XT/PC experience tells me Ubuntu is not to blame.

---

### Post by subways on 2005-02-25
Yeah the keyboard works in both DOS and on boot-up (can get into BIOS and other things)

I was hoping there may be a command i could type in to set it, if its any help the keyboards made by genius and is a standard keyboard layout. I tried with a different keyboard, albeit a USB one and got the same results

---

### Post by nikopol on 2005-02-25
[QUOTE=subways]Yeah the keyboard works in both DOS and on boot-up (can get into BIOS and other things)

I was hoping there may be a command i could type in to set it, if its any help the keyboards made by genius and is a standard keyboard layout. I tried with a different keyboard, albeit a USB one and got the same results[/QUOTE]
 I had a problem a while back with a Trust keyboard - is that the brand of yours? There was no solution I'm sorry to say - I just changed keyboard...

---

### Post by cheel on 2005-02-27
Im also getting the same problem.  It is either Ubuntu or the 2.6.10 kernel
USB works fine in the following OS's
WinXP
Mandrake 10.1
Debian 3
Knoppmyth
Slackware 9 and 10

I have used all of those and usb works fine, but when I installed ubuntu it just cut out during the install.  If anyone can post an actual fix that would be great.

Note: Im thinking its the kernel my research is pointing towardsthat

---

### Post by ebrowne on 2005-02-27
One of my friends had this problem with a different distobution but it turned out that his system had ide-raid controllers and standard ide controllers he had his ide's on the raid controllers and windows workd fine but linux wouldn't allow them to work that way.  move the disks to the standard controller and it installed fine and the good part is windows didn't even notice :)
Hope this helps!

---

