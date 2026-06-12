---
title: "No list of OS options on Dual boot"
date: 2012-06-17
forum: Installation &amp; Upgrades
---

### Post by vb10000 on 2012-06-17
I am facing a slight variation of the problem. I have XP installed on one hard disk (/dev/sda) and Ubuntu installed on a different hard disk (/dev/sdb). Please see the attached file for all the details.

During boot I see a blank screen with the message "Input Signal Out of Range. Change settings to 1440x900-60hz". Then the computer boots straight to Ubuntu since I had set the boot sequence on my computer to (1) the hard drive containing Ubuntu and then (2) the hard drive containing XP.

I know the options are available because if I hit enter, the computer boots straight into Ubuntu. If I hit the down arrow 6 times and hit enter, the computer boots into XP (why 6: grub-customizer shows several Linux options to choose from, and the 7th one on the list is XP).

What should I change to get the monitor to show me the OS options? The enclosed file shows 1440x900x24 as the monitor resolution.

After booting into Ubuntu, everything including display works fine (well except for fuzzy launcher icons after resuming from sleep .. but that is problem 2 of 2 I need to solve).

---

### Post by sffvba[e0rt on 2012-06-17
*Post moved to **own **thread.*


404

---

### Post by wilee-nilee on 2012-06-17
Your computer has 3 sets of kernels, those are before the Windows boot, in the grub menu. 

Since you made some resolution changes with the grub customizer I would start there.

---

### Post by vb10000 on 2012-06-17
I used grub-customizer to get information on OS types loaded on the computer. Did not make any changes to the system. By the time I get to the login screen, the correct resolution (1440x900) is used. The problem is during boot when the OS does not detect the correct resolution ... at least that is what I think. Any solutions?

---

### Post by drs305 on 2012-06-17
Assuming you are using the standard Grub files, and not those of Grub Customizer, try editing /etc/default/grub and **un**commenting
> **#**GRUB_GFXMODE=640x480
to
> GRUB_GFXMODE=640x480
Save the file and run "sudo update-grub".

---

### Post by vb10000 on 2012-06-17
Thank you. Worked perfectly. Now I can see all the OS installed and I can pick the one I want.

---

### Post by drs305 on 2012-06-17
> **vb10000 said:**
> Thank you. Worked perfectly. Now I can see all the OS installed and I can pick the one I want.

If you would like to reduce the size of the menu font you can change the values of the line you uncommented.

To see the values available at boot, which are *not* necessarily the same as the ones availabe once you are into your system:

At the grub menu, press 'c' to get to the grub prompt.
Type 'vbeinfo' to see the resolutions available to Grub.
Boot and edit the /etc/default/grub file as desired.
Run 'sudo update-grub' to update the settings.

Once you have things set the way you wish and don't require any more assistance please mark the thread SOLVED via the 'Thread tools' link near the top right of the first post.

Happy Ubuntu-ing

---

