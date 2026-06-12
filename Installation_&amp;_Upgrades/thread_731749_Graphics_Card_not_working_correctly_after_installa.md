---
title: "Graphics Card not working correctly after installation"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by mattrobinson999 on 2008-03-22
Ive just installed Ubuntu on my old computer and it was working perfectly until I enabled my correct driver for my graphics card (ATI Radeon 7600)
Now when ever, I reboot I get a message saying...
"Ubuntu is running in low graphics" (800x600)
I click onto the configure option and Ubuntu knows what graphics card I got but uses a "plug and play" monitor where I can only use 800x600 and also uses the "vese - Generic VESA-compliant videocards" instead of my real "ATI Radeon 7600"
Ive enabled the correct graphics drivers in Administration but Ubuntu still wont let me use my preferred 1280x1024.

Does anyone have any advice?

---

### Post by Tomatz on 2008-03-22
You need to add the proper resolutions to /etc/X11/xorg.conf "screen section". You will have to get your monitor specs (h v refresh rates, resolutions) though just google your monitor model number.

[B]put this in a terminal 
[/B]
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup

sudo gedit /etc/X11/xorg.conf 

edit the "screen" section for your resolutions, refresh rates supported by your monitor. Below is a good guide:

[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

save

then ctrl alt bkspace

**Failing that put this in a terminal:**

sudo dpkg-reconfigure xserver-xorg
[I](write this^ command down before the whole process incase step 1 goes horribly wrong then you can run it from the command line)
[/I]

**Finally if its a driver problem(if the other steps dont work):**

Maby try using envy to install the latest ati drivers.

[B]Use this at your own risk
[/B]
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Just download and install envy then uninstall your current graphics drivers, reboot then run "envy".

After uninstalling your original drivers and rebooting if you cant start x dont worry just type "envy" at the command line


:)

---

