---
title: "FAILED fluxbuntu, DSL, and puppy"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by henryjm206 on 2008-09-15
Help:confused: 

I can´t seem to get anything to work with my old laptop.
fluxbuntu installed after 4 hours but will not boot up.
DSL will boot from live CD but will not install.
Puppy linux will boot but I don´t know how to install it to the HDD.

My laptop has 4GB HDD and 160 MB of RAM CD drive and 1 USB

please help:(

Henry

---

### Post by snowpine on 2008-09-15
Hi Henry, 
What exactly happens when you try to boot Fluxbuntu? If it gets to the  splash screen (with the stopwatch) but then freezes (a common problem), try this:

   1.  Restart the computer and wait for Grub to appear.
   2. You will have 3 seconds to press esc to for Grub options.
   3. Press 'e' to edit the first line that starts 'Ubuntu 7.10 kernel'.
   4. Scroll down to the second line that starts with 'kernel' and press 'e'.
   5. Delete the word 'splash' at the end of the line.
   6. Press Enter.
   7. Press 'b' to boot.
   8. You'll see a series of text messages instead of the white screen. Hopefully, a login screen will load!
   9. Once logged in, double-click the Console icon at the top left and type:
      sudo nano /boot/grub/menu.lst
  10. Delete all instances (2 by my count) of the word 'splash'
  11. Save the file by pressing Ctrl+O, then Enter.

---

### Post by henryjm206 on 2008-09-15
I get the splash screen and it freezes up.


Ill make the changes now and try again thank you

---

