---
title: "Dual Booting Ubuntu and windows 7"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by iSamuel on 2010-08-04
I have windows 7 installed and it has been installed for a few months now

i have downloaded the ubuntu-9.10-desktop-i386 file. I have burned the CD using imgburn and have the it running from boot to the point where i get the options to run from the cd install check CD or memory and another option. 

I have checked memory and CD and they have both been fine with no errors found, but when i try and use the live CD or the install i get the normal loading screen then i get vertical lines on the screen at first they are green and yellow then they change to blue and white i think then back to green and yellow. they flash sometimes and little blocks change.

I read to try and press ctrl + alt + F1 which i did and i got some command lines but was unable to do type anything although i could press ctrl + alt + F7 and return to the vertical lines.

I am lost of what to do this is my first time using ubuntu or any linux based operating system. 

i have dual booted windows 7 and xp with no problem before so once i can get ubuntu installed i should be ok but i need to know how to get past the lines that appear

thanks

---

### Post by oldfred on 2010-08-04
Have you tried pushing F6 on the initial screen and add settings? Yours sounds like a video setting but most did not have trouble with Karmic but now with Lucid as they updated default video drivers.

What video card do you have?

---

### Post by RamsesII on 2010-08-05
Hello,

I think 10.04 has some kind of issues with your drivers (most likely your video card driver). If it doesn't have the drivers for your video card pre installed on the installation CD, there's not much you can do from your CD **only**. What I suggest is to first try an earlier ubuntu version on live mode. Then if it works fine to install it and then uprade to 10.04 if you **really** want 10.04 and nothing else. Upgrading, from my experience increases your odds to solve your drivers issues. Because during the upgrade process the system avoids (normally) to touch to well-running things unless there's some critical security update to do. Keep me abreast

RamsessII

---

### Post by iSamuel on 2010-08-07
I have managed to get 9.10 installed using the F6 option free software only but i am still unable to log into ubuntu due to the flashing screen on login this has stopped me from logging to update my driver i have also tried to use recovery mode and download the driver update but if will no connect i presume it is because i am using a wireless connection anybody have any idea what my next move can be i am able to use a wired connection but it is a lot of hassle.
thanks

---

### Post by oldfred on 2010-08-07
On first boot after install I had to use the e on the grub menu to edit the kernel line with the nomodeset to get it to boot into the graphics screens. (Same setting I used on LiveCd). After Video driver updates I have no issues.

On initial and most updates hard wired is better as it is a lot faster and more reliable.

---

