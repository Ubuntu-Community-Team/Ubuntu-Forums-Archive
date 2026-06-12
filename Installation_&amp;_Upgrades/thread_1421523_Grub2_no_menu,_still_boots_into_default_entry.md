---
title: "Grub2 no menu, still boots into default entry"
date: 2010-03-04
forum: Installation &amp; Upgrades
---

### Post by rezza on 2010-03-04
Hi all, I recently upgraded grub -> grub2 on my karmic box. Grub2 worked when chainloaded from legacy grub, and also the first time I tried it standalone. Both times the grub2 menu came up.

I ran vbeinfo at a grub2 command prompt, and found my monitor's native res listed - 1280x1024. I added that to my /etc/defaults/grub and then ran update-grub, and rebooted. This time no menu appeared and the default entry booted straight away. I suspected that the resolution was not supported for some reason or that the way I entered it in the config file was wrong, so I commented it out again in /etc/default/grub, and ran update-grub again - to no avail.

I have since tried lots of different formats for the GRUB_GFXMODE, such as 1280x1024@24, 1280x1024x24, and the normal 640x480, but none of them give me a grub menu. I have even tried using GRUB_TERMINAL=console, to no avail.

I have checked the /boot/grub/grub.cfg file each time to make sure my changes were put there correctly by update-grub. I have also made sure that timeout was set to 10, and the hidden timeout was set to 0. My GRUB_CMDLINE_LINUX_DEFAULT="quiet".

I have reinstalled grub2, grub-pc, and grub-common, and I have dpkg-reconfigured them all too.

I have no idea what to do to get my grub menu showing up again.

---

### Post by darkod on 2010-03-04
Do you have another OS on the machine? Doesn't the grub2 menu show only if another OS is present?

---

### Post by rezza on 2010-03-04
Nope, no other OS. And I have a timeout on the menu, so it should at least appear for 10 seconds.

---

### Post by darkod on 2010-03-04
> **rezza said:**
> Nope, no other OS. And I have a timeout on the menu, so it should at least appear for 10 seconds.

Nope, not when it's only OS. The logic is, the grub menu is to select an OS. In your case, what do you have to select?

Or course, there are ways to access it if needed (for example to select to boot the recovery mode entry). If you hit Shift for 9.10 it should show the grub menu. But you have to time it right, after BIOS is done but before ubuntu actually starts loading.

Also, from here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


**GRUB_HIDDEN_TIMEOUT=0**The hidden timeout option allows a  screen to be displayed [COLOR=Red]without[/COLOR] the Grub 2 menu, awaiting input from the  user for a given number of seconds. It is available to single-OS  computers - if multiple OS's are known to Grub 2, this option is  bypassed. 
**On single-OS computers:**
[LIST]
[*]The menu [COLOR=Red]will be hidden unless[/COLOR] the  user adds a # symbol to the beginning of this line ( #  GRUB_HIDDEN_TIMEOUT=0 ) and the GRUB_TIMEOUT value is greater than 0.
[*]If a background image is designated in 05_debian_theme it will be  displayed rather than a blank screen during a hidden menu timeout.
[*]**For integers greater than 0**:
[LIST]
[*]The system will pause  [COLOR=Red]without displaying[/COLOR] a menu for the designated number of seconds. If the  user does not press the *SHIFT* key during the timeout the system  will then boot the default OS/kernel.
[*]If the user presses the *SHIFT* key to display the menu, the  menu [COLOR=Red]will be displayed[/COLOR] for the number of seconds designated by the   GRUB_TIMEOUT value unless the user again intervenes.
[/LIST]
 
[*]With a value of **0**:
[LIST]
[*]Unless the user intervenes, the  system will boot the default OS/kernel with only a slight delay. No menu  will be displayed.
[*]The user may force displaying the menu as the computer boots by  holding down the *SHIFT*  key.
[/LIST]
 
[/LIST]


[LIST]
[*]**GRUB_HIDDEN_TIMEOUT_QUIET=true**
[LIST]
[*]true - No countdown is  displayed. The screen will be blank.
[*]false - A counter will display on a blank screen for the duration of  the GRUB_HIDDEN_TIMEOUT value.
[/LIST]
 
[/LIST]

---

### Post by rezza on 2010-03-04
My bad. Solved, thanks for the pointer. It was in the manual all along... /sigh

---

### Post by darkod on 2010-03-04
> **rezza said:**
> My bad. Solved, thanks for the pointer. It was in the manual all along... /sigh

No problem. For single OS systems, adding any kind of delay/timeout just makes your computer boot longer. As long as it's working fine, I wouldn't care much about displaying a grub menu.

---

### Post by rezza on 2010-03-04
Yeah it's sorted, the thing that made me worry about it in the first place was that I couldn't make the menu appear at all, even holding shift - but now the menu appears I can see it's an issue with my keyboard, strangely enough, because I can't change entries or affect the grub menu in any way. Plugging a different USB keyboard in works fine.

I wonder what varies between USB keyboards that would make some work on grub2 and some not work.

---

