---
title: "newbie"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by ghostrider_gr on 2011-03-11
well my problem is that i installed ubuntu 10.10 alongside with windows 7, and from that moment my pc does not ask which operating system i want, but boots automatically ubuntu.. can anyone help me on that cause i am newbie and i dont know what to do..?
thanks in advance..

---

### Post by cbowman57 on 2011-03-11
[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub")
Hidden
The user can interrupt the boot process and display the menu by holding down the SHIFT key until the menu displays. Grub 2 searches for a depressed SHIFT key signal during boot. If the key is pressed or Grub 2 cannot determine the status of the key, the menu is displayed. Note: The "SHIFT" keystatus check is currently nested within in a conditional statement within /etc/grub.d/30_os-prober and may not work under certain circumstances.
The time the screen remains blank but available for display is determined by a setting in /etc/default/grub.
To provide visual feedback during while the countdown continues, a countdown display can be shown on the screen.
At the end of the timeout, the default entry determined in /etc/default/grub will be selected.

---

### Post by Hippytaff on 2011-03-11
Try opening a terminal in ubuntu (CTRL+ALT+T) and doing ```
sudo update-grub
```
 
watch to see if grub finds windows and then reboot to see if it appears in the grub menu

---

### Post by ghostrider_gr on 2011-03-11
> **Hippytaff said:**
> Try opening a terminal in ubuntu (CTRL+ALT+T) and doing ```
sudo update-grub
```
 
watch to see if grub finds windows and then reboot to see if it appears in the grub menu
i tried this but nothing changed.. it still boots ubuntu.. where i am supposed to see anything about windows?
> **cbowman57 said:**
> [http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub")
Hidden
The user can interrupt the boot process and display the menu by holding down the SHIFT key until the menu displays. Grub 2 searches for a depressed SHIFT key signal during boot. If the key is pressed or Grub 2 cannot determine the status of the key, the menu is displayed. Note: The "SHIFT" keystatus check is currently nested within in a conditional statement within /etc/grub.d/30_os-prober and may not work under certain circumstances.
The time the screen remains blank but available for display is determined by a setting in /etc/default/grub.
To provide visual feedback during while the countdown continues, a countdown display can be shown on the screen.
At the end of the timeout, the default entry determined in /etc/default/grub will be selected.
well i did this, and i see the grub menu.. bout there is no windows.. but i am sure that i chose "alongside with aother operating system" during the install.. so do i have to install w7 again?

---

### Post by smurphy_it on 2011-03-11
That depends on if it is still there or not.  In my signature there is a link to booting problems.  Go there, download the script, and post the output here.
That'll tell us.

---

### Post by Hippytaff on 2011-03-11
+1 Boot script results

---

