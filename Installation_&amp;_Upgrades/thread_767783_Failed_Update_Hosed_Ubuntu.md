---
title: "Failed Update Hosed Ubuntu"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by fallenbuddha on 2008-04-25
I tried the upgrade option from the update manager, going from 7.10 to 8.04, and let the download and installation proceed overnight.  It looked like everything was fine and I was prompted to restart. 

On restart, it seemed like the computer stalled after the line "Running local boot scripts (/etc/rc.local) [ok]," but after a minute or so displayed this error message:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

A yes response resulted in "Warning: Could not retrieve EDID because get-edid is not installed (1)" and "The X server is now disabled. Restart GDM when it is configured correctly."  Then it kicked me out back to the initial screen with the "local boot scripts" message.  After ten minutes of inactivity, I gave up and reboot the machine.

I figured something went awry during the upgrade process and decided to try a fresh install from a CD. When I selected the option to install from the CD, it just kicked me out to a command prompt. 

So, I'm stuck with the inability to boot into ubuntu and the inability to run a fresh install. Before I decide to revert to a fresh install of 7.10 and give up on 8.04, does anyone have any suggestions on how I might fix this problem?

In case it is relevant, I'm running a Dell Dimension 8400 with 2GB ram and ATI Radeon x800SE.  

Any assistance will be appreciated. Thanks.

---

### Post by Bubba64 on 2008-04-25
> **fallenbuddha said:**
> I tried the upgrade option from the update manager, going from 7.10 to 8.04, and let the download and installation proceed overnight.  It looked like everything was fine and I was prompted to restart. 

On restart, it seemed like the computer stalled after the line "Running local boot scripts (/etc/rc.local) [ok]," but after a minute or so displayed this error message:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

A yes response resulted in "Warning: Could not retrieve EDID because get-edid is not installed (1)" and "The X server is now disabled. Restart GDM when it is configured correctly."  Then it kicked me out back to the initial screen with the "local boot scripts" message.  After ten minutes of inactivity, I gave up and reboot the machine.

I figured something went awry during the upgrade process and decided to try a fresh install from a CD. When I selected the option to install from the CD, it just kicked me out to a command prompt. 

So, I'm stuck with the inability to boot into ubuntu and the inability to run a fresh install. Before I decide to revert to a fresh install of 7.10 and give up on 8.04, does anyone have any suggestions on how I might fix this problem?

In case it is relevant, I'm running a Dell Dimension 8400 with 2GB ram and ATI Radeon x800SE.  

Any assistance will be appreciated. Thanks.

Did you run the install from BIOS I was reading a thread earlier and that was the description of how to do it and are you sure that your CD is correct. Also there is the option of doing a alternative ISO download and burning a CD then installing with that. It could be that if you can get to the log in screen and choose terminal a sudo dpkg --configure -a command might put it back to install the right package I don't know being that you were installing during a period of swamped servers I assume. I would look for info on how to clean your original install in the end and then try a CD install. The alternative is what I used to install last week after wiping my system basically clean, the ISO has an installer to direct the BIOS. Here is a link to the daily downloads if needed you should be able to use the desktop CD or the alternative. 
[http://cdimage.ubuntulinux.org/ports/daily-live/current/](http://cdimage.ubuntulinux.org/ports/daily-live/current/)

---

### Post by fallenbuddha on 2008-04-26
Thanks for the reply. My CD is the x86 Desktop edition and came up error-free. I'll give the alternative ISO a try. I guess there's another overnight downloading session in my near future.

---

### Post by Bubba64 on 2008-04-26
> **fallenbuddha said:**
> Thanks for the reply. I'll give the alternative ISO a try. I guess there's another overnight downloading session in my near future.

Personally I would only download when I could observe it. the Install is when you want to be there watching mostly at times it may ask you during the install if you want to save an old setup or accept the new one. I always choose he new one but all my computers are old and generally need generic stuff. Make sure when you burn the CD that you do at a slow speed I chose 4x and it burned the CD in 20 minutes in a text mode. Check around and make sure that the ISO downloads are working, I have seen posting that questions that right now. When I installed with an alternative a week ago the only way to get it to work and install the correct grub was to unplug the computer from the net during the install. Good Luck

---

### Post by fallenbuddha on 2008-04-26
The alternative ISO did the trick. Now I just have to solve this ATI Radeon driver issue and I'll be set... Thanks.

---

### Post by Bubba64 on 2008-04-26
> **fallenbuddha said:**
> The alternative ISO did the trick. Now I just have to solve this ATI Radeon driver issue and I'll be set... Thanks.

Cool man I didn't want you to go back to Gutsy unless you needed to.

---

