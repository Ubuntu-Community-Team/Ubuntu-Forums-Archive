---
title: "Blank Screen After Boot Up From Ubuntu Installation"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by QUI2GUA on 2010-12-18
Hello,

I have recently did a fresh install on my computer with Ubuntu 10.10. When i used the live CD to install my monitor displayed a "No Input Signal" after I'd select either *install ubuntu* or *install ubuntu without any changes to your computer* . But i did a search on the web where i had to select **nomodeset** to make it work with my installation which it did. I finally had it installed but then after i reboot my computer it doesn't boot up ubuntu. After my BIOS boot screen shows a blinking underscore shows for some seconds then my monitor displays the "No Input Signal". GRUB does not show but i can tell after 10 to 20 seconds my computer is working because the login sound would play but i don't get anything on my screen. I need help and really appreciate it.

---

### Post by theasprint on 2010-12-18
Can I have details on your graphics card?
 
And after setting nomodeset, your computer boots up with a blank screen?
 
Does pressing Ctrl+Alt+F1 after the computer "officially logs in" help?

---

### Post by sikander3786 on 2010-12-18
Welcome to the forums :-)

Press and hold down Shift key from your Bios screen until you see the Grub menu. Highlighting the first entry, press 'e' to edit it. Navigate to words "quiet splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot.

Once on the desktop, go to System > Administration > Additional Drivers and activate the recommended drivers and the problem should go away for ever.

---

### Post by QUI2GUA on 2010-12-18
THANK YOU VERY MUCH! I've installed Ubuntu so many times in hope for it to work! I GREATLY appreciate it! May you have a wonderful Christmas filled with joy and a great New Year! (=

---

### Post by gau1992 on 2011-05-06
i have same problem.
but in additional drivers shows that no additional drivers found.
plz help me.

---

### Post by MAFoElffen on 2011-05-06
> **gau1992 said:**
> i have same problem.
but in additional drivers shows that no additional drivers found.
plz help me.
Look at  this sticky here:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by rambod on 2011-11-06
> **sikander3786 said:**
> Welcome to the forums :-)

Press and hold down Shift key from your Bios screen until you see the Grub menu. Highlighting the first entry, press 'e' to edit it. Navigate to words "quiet splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot.

Once on the desktop, go to System > Administration > Additional Drivers and activate the recommended drivers and the problem should go away for ever.
I try this first time worked but when i shut down my computer and turn on once more again doesn't work :confused::(

---

### Post by MAFoElffen on 2011-11-06
> **rambod said:**
> I try this first time worked but when i shut down my computer and turn on once more again doesn't work :confused::(
And while it "works" as you said... Did you gp to System Settings, then Additional Drivers > Select your driver and then select the "Ativate button?  Did you see the staus line in that applet say installing... done and the say driver is installed?

nomodeset temporarily added in the grub menu is a temporary fix to enable a graphical boot so you can install your graphics drivers.

---

### Post by rambod on 2011-11-07
> **MAFoElffen said:**
> And while it "works" as you said... Did you gp to System Settings, then Additional Drivers > Select your driver and then select the "Ativate button? Did you see the staus line in that applet say installing... done and the say driver is installed?
 
nomodeset temporarily added in the grub menu is a temporary fix to enable a graphical boot so you can install your graphics drivers.
 I did . i go to System and download and install my driver but again after that doesnt boot up , dunno now i feel like maybe its becuse of my ram i have 12GB RAM maybe , ubuntu doesnt support that or something like that.
is it possible ubuntu 32 bit and 64 bit both of them doesnt support my RAM?!

---

### Post by rambod on 2011-11-07
no not becuase of RAM i remove 2 of my RAMs and check it , wont work

---

