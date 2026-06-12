---
title: "I can't get a recent version to install and boot twice."
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by Marvin666 on 2013-04-18
Basically, due to various installer issues, I've been stuck on Karmic since it's release. I've never gotten a clean install of anything newer to function correctly, so I was too afraid to update my working, but really showing it's age, Karmic install. I have a dual boot with Precise, but after the first reboot, I was unable to use the login manager. I can log into a shell, but attempts to invoke graphics from it fail. Last night, I tried to do an install of Quantal over it, but it was a miserable failure. With all the other post-Karmic versions, I at least made it to the interactive part of the installer. This one displayed an error message warning of a GPU lockup, then alternated between errors about being unable to idle threads (it may have been cores, etc; I can check for sure when I get home) 2 and 3. Every few cycles of this, a garbled screen would display for about 5 seconds. Based on the blue, black, and white displayed, I can tell it was meant to be the first interactive page of the installer. It was the exact same each time it appeared. Each time one of the errors displayed, a number at the beggining of the line would increment up. I decided to just let it run and see what happens, and after at least an hour or two, it finally stopped it's seizure and only displayed the same garbled screen. Any help in getting Quantal installed, or Precise to behave long enough to try and update would be much appreciated. When I get home in about 4 hours, I can provide exact text of error messages, or more information if needed. The machine in question is the one in my signiture.

---

### Post by oldfred on 2013-04-18
Have you been using nomodeset? And then installing nVidia graphics. I think it was since 10.04, and changes to kernel that I have had to use nomodeset on all live install boots, and first boot after install or until I get nVidia driver installed. I installed nvidia-current-updates with my 9600GT as there are several version now in repository.

       # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

   Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)


 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Marvin666 on 2013-04-18
The Precise install seems to be acting different than I remembered. It display a few random bars of color, then locks up when the login manager is trying to start. I can't access a shell via normal booting. In recovery mode, I selected enable networking, and after some hestitation, the login manager launched correctly, and I was able to login to a desktop. After I update it, I'm going to have to install nvidia's drivers, the screen is stuck in 1280 x 720 mode, and reports it's refresh rate as 0 Hz.

---

### Post by Marvin666 on 2013-04-18
Is it normal for an update to change (and in this case mess up) the names of things in grub? Also, how could I go about manually renaming them to what they were?
The updated install fell back into the gpu errors, but slightly different, and a black screen with an immobile cursor.
```
 [  47.284723] [drm] nouveau 0000:02:00.0: GPU lockup - switching to software fbcon
[  52.392015] [drm] nouveau 0000:02:00.0: Failed to idle channel 2.
[  57.652015] [drm] nouveau 0000:02:00.0: Failed to idle channel 3.
[  72.624016] [drm] nouveau 0000:02:00.0: Failed to idle channel 2.
[  77.884915] [drm] nouveau 0000:02:00.0: Failed to idle channel 3.
```
This time it stopped after a few more cycles, and I can use the shell.

---

### Post by oldfred on 2013-04-18
Is that with nomodeset or recovery mode?

Have you installed nVidia drivers?

---

### Post by Marvin666 on 2013-04-19
That was with recovery mode, then enable networking, and no other prompting.
I used purge to remove all nvidia related packages, and tried to use nouveau's default, and that gave similar errors. I got nvidia-experimental-304 to install, and it has gone to 1600 x 900 mode. There's a few quirks to it though. The nvidia splash doesn't show before the login manager starts. There's also no nvidia config applet in the applications menu. This is after installing the matching settings for experimental 304, and a reboot. Finally, the card isn't reporting a correct core temp (or at least not to the sensors monitor). It displays a constant 50 C. Sensors does correctly read the cpu core temps, however.

---

### Post by oldfred on 2013-04-19
Did you run this?
 sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot

      
 From  bogan
To bring it fully up to date, instead of: 'nvidia-installer --update', use 'nvidia-installer -f --dkms'.
The '-f' option implies the inclusion of: '--update', but will force a re-installation even if the currently installed version is the same as the 'latest' which it will download and install.
The '--dkms' option, with driver versions 3.04.xx and later, will check that 'dkms' is installed and offer the option to register the driver with dkms, so the kernal module gets updated automatically when a new kernal is installed. and does not need to be manually re-installed.

---

### Post by Marvin666 on 2013-04-19
I used:
```
sudo apt-get remove --purge nvidia*
sudo shudown now -r
*reboot*
sudo apt-get install nvidia-experimental-304, and
sudo apt-get install nvidia-settings
sudo shutdown now -r
```
On reboot when graphics worked, I used synaptic to remove the generic nvidia settings package, and add the experimental 304 settings package. I rebooted again, and noticed there was still no nvidia splash or applet, and that the core temp reported was incorrect.

---

