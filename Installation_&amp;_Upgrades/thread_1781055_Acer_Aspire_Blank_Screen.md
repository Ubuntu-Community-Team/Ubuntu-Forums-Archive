---
title: "Acer Aspire Blank Screen"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by mawil1013 on 2011-06-12
I'm working through this issue with my Acer Aspire 5336-2524. Blank screen, can't see anything after reboot.

(Display=Mobile Intel (R) 4 series express chipset family)

Enter; 'msinfo32.exe' in the search programs and files box. Open it up after search finds it. You'll then be able to see BIOS version. Go to Acer support and update BIOS if needed. I needed to and so far the result has been that I'm not able to see the install of Ubuntu, butttt, cannot see it after going through all the start up, up to the point where the desktop page should be, then blank screen again.

snipped

I'll come back with results.

I also am thinking about updating video driver too. (Tried but said it was up to date)

Additional (6-14-11@7:36PM) So far by updating BIOS I was able to view ubuntu long enough to install, but couldn't view fully loaded OS (as in couldn't see desktop). As mentioned by foresthill, plugging an external monitor into the laptop allows me to see everything on the external monitor. Ahhh, sweet progress! Waiting for reply from foresthill about exactly what they did in grub for a permanent fix.
Additional Two: FYI: Xubuntu 10.10 runs great on the laptop. But no wifi (I cannot remember if I updated and ran across broadcom driver install as 10.04.2 did)

Finial Update: I Installed ubuntu 10.04.2, which had no problems with screen, couldn't use wireless until I update and then a note poped up about broadcom driver which I allowed to install, now I have a fully functional ubuntu. Someone recommended using "LTS" versions for initial install, then go from there if you want to try different versions. I'll wait for the LTS before messing around, just glad to finally get a fully functioning ubuntu!

---

### Post by foresthill on 2011-06-13
How about some hardware information. That would be helpful.

You might need to do what I do when I install 11.04 on my notebook, which is plug in an external monitor. That's the only way I can do it. Then, once I am done with the install, I have to add a couple lines to my grub.cfg file to make the backlight work.

You MIGHT be experiencing a similar problem, namely, no backlight. Have you tried shining a flash light or lamp onto your screen and seeing if there is stuff displayed on your screen but you can't see it due to the backlight being turned off?

---

### Post by mawil1013 on 2011-06-13
> **foresthill said:**
> How about some hardware information. That would be helpful.

You might need to do what I do when I install 11.04 on my notebook, which is plug in an external monitor. That's the only way I can do it. Then, once I am done with the install, I have to add a couple lines to my grub.cfg file to make the backlight work.

You MIGHT be experiencing a similar problem, namely, no backlight. Have you tried shining a flash light or lamp onto your screen and seeing if there is stuff displayed on your screen but you can't see it due to the backlight being turned off?

I will try that! I appreciate your tip!!! I'm at work now or I'd have tried already!

---

### Post by mawil1013 on 2011-06-14
> **foresthill said:**
> How about some hardware information. That would be helpful.

You might need to do what I do when I install 11.04 on my notebook, which is plug in an external monitor. That's the only way I can do it. Then, once I am done with the install, I have to add a couple lines to my grub.cfg file to make the backlight work.

You MIGHT be experiencing a similar problem, namely, no backlight. Have you tried shining a flash light or lamp onto your screen and seeing if there is stuff displayed on your screen but you can't see it due to the backlight being turned off?

You have helped greatly! I can see with an external monitor attached! Now, can you tell what it was you typed into grub for a permanent fix?:popcorn:

---

### Post by foresthill on 2011-06-14
Have you confirmed that it's your back light not turning on is the problem? If it is, you ought to be able to just barely make out some details on the screen if you shine a bright light on it when you're logged in.

So assuming the back light is the problem, here's what i did to fix the problem on my notebook. Enter this command in the terminal:

[PHP]gksudo gedit /etc/default/grub
[/PHP]

When your grub file comes up, paste these two lines at the end of the file, where you see similar code:

[PHP]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"[/PHP]

then enter this command:

[PHP]sudo update-grub
[/PHP]

This will save the changes.

Now, when you reboot, the brightness keys on your keyboard ought to work. On my notebook, the keys are "Fn" and "arrow down". Assuming the fix works, you'll have to adjust the keys every time you reboot. 

HTH, and good luck.

---

