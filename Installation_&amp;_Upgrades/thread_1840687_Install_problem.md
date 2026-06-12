---
title: "Install problem"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by DMGrier on 2011-09-08
My wife has a Sony Vaio, when we install Ubuntu it install's and at the end of the install it does it's reboot nd everything is fine but once it reboots it just has a blinking line in the left corner and nothing happens. It is set to boot from HDD but we cannot figure this out, any ideas?

---

### Post by bloodorange on 2011-09-08
Which version of Ubuntu did you install?

---

### Post by DMGrier on 2011-09-08
we tried 11.04, 10.10 and 10.04, the wierd thing is me and my wife both have Vaio's with similar hardware and the only real difference in hardware I see is she has a bluray player and I don't. Does the bluray disc drive cause problems when it is installing?

---

### Post by Hakunka-Matata on 2011-09-08
**e: Blinking cursor after install** 			 			 			 		   		 		 		 	Quote:
 	 	 		 			 				 					Originally Posted by **sandpvrr** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9308874#post9308874") 				
 				*I'm double checking by reinstalling  now - (I had put Mandriva on just to use it) but I don't recall seeing  GRUB come up either.....*
 			 		 	 	 
In single boot systems (when not dual booting with another OS) the  boot menu doesn't show up to speed up booting because there is no other  OS to select.

In this case, for 10.04 and Grub2 press (or start hitting Shift) after  the BIOS POST finishes, at the start of booting. That will make a grub  menu show.
 		                   		  		  		 		 			 				__________________

---

### Post by Hakunka-Matata on 2011-09-08
It sounds like a graphics issue, it happens many, many times on first boot after install.  The LiveCD/USB installer graphics work fine, but once you have installed the system, and reboot it, it will display only the blinking cursor.

There are a million threads on this problem, search right here in these forums on "nomodeset", and - or "blinking cursor", you'll get lots of hits, and ideas.

A couple of ideas to try:

[LIST]
[*]Hit enter as soon as the blinking cursor appears
[*]Hit down arrow key once, then Enter as soon as blinking cursor appears
[*]Hit F6
[/LIST]

---

