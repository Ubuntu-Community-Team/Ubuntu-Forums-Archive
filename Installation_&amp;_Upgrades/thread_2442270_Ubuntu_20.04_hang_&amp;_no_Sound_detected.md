---
title: "Ubuntu 20.04 hang &amp; no Sound detected"
date: 2020-05-01
forum: Installation &amp; Upgrades
---

### Post by sjhare2 on 2020-05-01
I have Dell Inspiron I5 7000, with configuration: 
System Model	Inspiron 7591 
Audio	NVIDIA Virtual Audio Device (Wave Extensible) (WDM)

In my Ubuntu 18.04 LTS suddenly sound was stopped working, i tried all the troubleshooting mentioned ubuntu help forum, and finally i Installed Ubuntu 20.04 LTS, but as i install, while boot it hang, i tried two three time to reboot the system, some time it boots but hang after and some time it hang on loging screen. once it loaded and when i check for sound setting again it hang as i opened the sound setting. 

I am using Windows 10 side by and there is no issue with sound card/sound, it happens only with Ubuntu 18.04 and 20.04 LTS versions, i never tried earlier non LTS versions.

---

### Post by CelticWarrior on 2020-05-01
If it has Nvidia Graphics then you better disable Secure Boot because that prevents loading the Nvidia drivers tha were hopefully installed if you selected that option during installation.

---

### Post by sjhare2 on 2020-05-02
It have NVIDIA graphics and secure boot is also disabled, that the way 18.04 was worked but 20.04 is hang as soon as system start, it hangs on booting, why ubuntu 20.04 is not supporting nvida graphics while in all new laptop is a general configuration.

---

### Post by do7phin-hotmail on 2020-06-29
Running a brand new Inspiron 7591, 
  I tried 20.04 and kept getting keyboard lockups. 
  I tried 18.04 and lost mic and sound. 
After two weeks of fighting, I found a solution at 
  [https://askubuntu.com/questions/912862/system-freezes-including-keyboard-mouse](https://askubuntu.com/questions/912862/system-freezes-including-keyboard-mouse)
I  reloaded 20.04 then CTRL+ALT+T 'd  
  sudo apt-get update && sudo apt-get upgrade && software-properties-gtk --open-tab=4
All better. 
 (Disclaimer: Some cars not for use with some Hot Wheels sets.)
Good luck, better skill, and best wishes!
  -b.abel

---

