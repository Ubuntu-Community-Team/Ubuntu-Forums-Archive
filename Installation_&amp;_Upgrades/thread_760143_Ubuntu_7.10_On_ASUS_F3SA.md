---
title: "Ubuntu 7.10 On ASUS F3SA"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by metzen_w on 2008-04-19
e-mail: [email]dinkvill@hotmail.com[/email]
:guitar:
ASUS F3SA Ubuntu Setup
----------------------

Beginning keynotes
-----------------
This setup guide deals with Ubuntu 7.10 Gutsy
This is a work in progress and I will updates it with the built in web cam and fingerprint reader.

1) Install Ubuntu

2) Download and Install Envy from[COLOR="Red"][ here]("http://albertomilone.com/nvidia_scripts1.html")[/COLOR][ http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html"). 
[INDENT]a) Follow the setup for automatic ATI install.
b) ****IMPORTANT**** If you restart and get a blank screen or can not access alternate tty screens with Ctrl+Alt+f1 through f8 then you need to reboot the machine into failsafe mode. At the failsafe mode type [COLOR="Red"] envy -t[/COLOR]
c) Repete the setup with option 3 or the option that says ATI automated install.
d) reboot.
[/INDENT]
3) --Audio / Sound--
[INDENT]a) Add this line to the /etc/modprobe.d/alsa-base  *please note you can add this line to just about any file in the modprobe.d folder.[/INDENT]
	   [INDENT]options snd-hda-intel model=lenovo[/INDENT]

---

### Post by master_kernel on 2008-04-20
Fingerprint reader: [http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)
Don't know if it'll work, but it doesn't hurt to try ;)

---

