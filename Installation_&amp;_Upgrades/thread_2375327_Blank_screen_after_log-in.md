---
title: "Blank screen after log-in"
date: 2017-10-23
forum: Installation &amp; Upgrades
---

### Post by sp40140 on 2017-10-23
Machine: Elitebook laptop i7, 6gigs ram, Nvidia Video card. SSD (primary) and HDD.

Issue: Blank Screen after log-in.
I upgraded from 17.04 64bit to 17.10. In place upgrade (using updater utility). Just followed the prompts and there were no errors during upgrade.
After I reboot I get to gnome log-in screen. I put my credentials, password is accepted and than screen goes blank.
Since, I didn't get the gui, I reboot. The default session was Unity at the log-in screen. I changed to gnome. It worked, I got the desktop. So, I installed the gnome tweak utility and customized it a bit. Set-up Unity panel on the left side. But after reboot, same issue regardless of the desktop session chosen.

What I tried so far: 
Added "nomodeset" option in grub. Didn't work.
Tried all the desktop session available at the log-in screen (gnome, unity, gnome xorg, unity xorg). None of them give me gui.
I even installed xfce4 (from tty). Same issue. No gui after log-in.
Removed .Xauthority file from ~/.

Any suggestions?
Need help with this.

PS:I know it's typically risky to upgrade and especially since its a switch from Unity to gnome. But I am working on something which would benefit from newer kernel.

---

### Post by #&amp;thj^% on 2017-10-23
Do you have the Nvidia Driver installed?

---

### Post by sp40140 on 2017-10-24
Yes. I have Nvidia Drivers installed and they are being used (found out using "lspci" output shows that vga controller is nvidia NVS 3100M).

---

### Post by mc4man on 2017-10-24
you should probably go to a tty & purge nvidia* 
that may let you log in & clean up the mess you have.

By default in 17.10 there is only ubuntu session installed which provides 2 log in options
ubuntu (which is wayland which doesn't work if using nvidia-prime on optimus laptops & shouldn't even show up
ubuntu-xorg

gnome-session & unity-session are not default  installed though available, unity session is xorg only & works better with lightdm vs. gdm3

---

### Post by EowynCarter on 2017-10-24
A few things i found having the same kind of issue.

Fist, what mc4man said about wayland / xorg.

Then, my case I installed nvidia-current, that point to the legacy driver. (304). Not really working with my card. So, make sure you installed the version relevant for your card.

---

### Post by sp40140 on 2017-10-24
@mc4man
Thank you. Didn't want to do that. But I did it. And now the nouveau drivers don't work right. My resolution is stuck to 640X480. And that basically unusable as no screen fits in that resolution.
I re-installed the nvidia drivers but didn't work same as before. After log-in totally blank screen (not even wall paper.. just blank black screen). Tried with nomodeset on and off.

---

### Post by sp40140 on 2017-10-25
I got it working. I installed legacy version of Nvidia drivers and disabled them (as it didn't work). After re-boot (and removing the nomodeset flag) I got my proper screen resolution with nouveau drivers.

---

### Post by benisonsam on 2018-04-07
I am also facing the same issue. Difference here is that I have no nvidia drivers installed! Still struggling to figure out what's wrong here..

---

