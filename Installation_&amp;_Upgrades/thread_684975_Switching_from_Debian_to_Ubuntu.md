---
title: "Switching from Debian to Ubuntu"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by AndrewWalker on 2008-02-01
I'm using Debian Etch and I'm not too happy with it. Is it possible to switch to Ubuntu without a new install, i.e. can I easily convert my system?

---

### Post by Rocket2DMn on 2008-02-01
They keyword there is "easily", so the answer is no.  It CAN be done but you would spend hours and hours mucking with details, troubleshooting problems and dependencies, and in the end, probably would not have a very stable system.  I think you should just start fresh.

---

### Post by polmir on 2008-02-01
> **AndrewWalker said:**
> I'm using Debian Etch and I'm not too happy with it. Is it possible to switch to Ubuntu without a new install, i.e. can I easily convert my system?
 You upgrade Etch to Lenny. Lenny work stable. 
[http://www.go2linux.org/upgrading-debian]("http://www.go2linux.org/upgrading-debian")
[http://www.debian.org/releases/testing/index.en.html]("http://www.debian.org/releases/testing/index.en.html")

---

### Post by Rocket2DMn on 2008-02-01
> **polmir said:**
> You upgrade Etch to Lenny. Lenny work stable. 
[http://www.go2linux.org/upgrading-debian]("http://www.go2linux.org/upgrading-debian")
[http://www.debian.org/releases/testing/index.en.html]("http://www.debian.org/releases/testing/index.en.html")

I thought Lenny was still in development and is currently labeled unstable.

---

### Post by polmir on 2008-02-01
Yes officially. But, Lenny work very stable.

---

### Post by ubuntu-freak on 2008-02-04
> **Rocket2DMn said:**
> I thought Lenny was still in development and is currently labeled unstable.

 
Lenny is officially 'Testing' not 'Unstable'. Sid is 'Unstable', but for most users that equates to 'new'. You would be very unlucky to break Debian, even in Sid.
 
Just back up important files and install Ubuntu. It's a slim desktop Debian afterall. Then use my [how-to](http://ubuntuforums.org/showthread.php?t=661833) and get multimedia and more working.
 
Nathan

---

### Post by AndrewWalker on 2008-02-06
I should have mentioned it but the reason I installed Debian was because it was the only distro that could boot off a floppy and recognise my ancient PCMCIA CDROM drive. My laptop can only boot from floppy and whilst it has a usb port, it doesn't have an option to boot from it.
I also have a USB CDROM that SmartBootManager can't access any more than the PCMCIA one.
I'm running short of ideas now! Debian works but is a pain in the backside to set up, I thought Ubuntu might be easier. 
Hasn't someone hacked the Debian floppys to work with Ubuntu?

---

### Post by ubuntu-freak on 2008-02-06
> **AndrewWalker said:**
> I should have mentioned it but the reason I installed Debian was because it was the only distro that could boot off a floppy and recognise my ancient PCMCIA CDROM drive. My laptop can only boot from floppy and whilst it has a usb port, it doesn't have an option to boot from it.
I also have a USB CDROM that SmartBootManager can't access any more than the PCMCIA one.
I'm running short of ideas now! Debian works but is a pain in the backside to set up, I thought Ubuntu might be easier. 
Hasn't someone hacked the Debian floppys to work with Ubuntu?

 
Try this [guide](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html). 
 
What's so hard about Debian then? If you have the multimedia repo, w32codecs, mplayer, vlc, gstreamer plugins yada yada you should be fine. What you having trouble with?
 
Nathan

---

### Post by AndrewWalker on 2008-02-10
Where to start! 
I'll list a few, 
Lirc doesn't work,
My inbuilt modem doesn't work, 
ACPI and APM doesn't get detected or work,
My Comtrend wireless PCMCIA card isn't detected,
Shutdown doesn't shutdown, just halts system, 
SSH doesn't work, can ssh out but not in,
Battery monitoring doesn't work, probably due to ACPI problem

As you can see, I'm not having much luck!
Debian doesn't do much auto-detection of hardware and I haven't got the time to mess with kernel module compiling so I'd prefer Ubuntu.

Which guide were you referring to? Was there supposed to be a link on your post?

---

### Post by AndrewWalker on 2008-02-10
Funny, I refreshed the page and the link appeared!
Sadly my network card has no boot capability and the links to alternative iso's is broken!
Looks like someone up there has got it in for me!

---

### Post by Partyboi2 on 2008-02-10
[another option]("https://help.ubuntu.com/community/Installation/FromLinux") could be to install from a spare partition from an existing Linux system.

---

