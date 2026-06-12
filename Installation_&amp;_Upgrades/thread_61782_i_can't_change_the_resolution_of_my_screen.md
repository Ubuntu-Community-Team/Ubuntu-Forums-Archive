---
title: "i can't change the resolution of my screen"
date: 2005-09-02
forum: Installation &amp; Upgrades
---

### Post by Donnie on 2005-09-02
i just currently intall  Ubuntu 5.04 for intel x86 into my computer. the software is booting finely, i have already configured it to connect to the internet. but my problem is: 1. i can not adjust the screen resolution into higher mode.
     2.  i am first hand user of linux, how can i connect to Windows shared documents or how can i browse and connect to the local area network.
please tell me how or what will i do.

you can send your answer to my e-mail: [email]xinaicleo@yahoo.com[/email]

thank a lot bro!

---

### Post by kamstrup on 2005-09-02
**1)** I'm afraid you'll have to resort to the command line for adding new resolutions... If you're up to it follow me...

Applications->System Tools->Terminal. In this type```
 sudo gedit /etc/X11/xorg.conf
``` Hit enter. It will ask you for your password; just type your normal user password. This brings up the text editor showing the X (the graphical system in Linux) configuration. The little "sudo" in front tells the system to open the file as the root user (also called super user)

In the text editor find the place looking something like this:
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"hp 7550"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
.
.
.
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
```
Change the Modes line in the section that says "Depth 24" to look like this:
```

		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"

```

Now save the document, and log out. In the log in screen hit control-alt-backspace. This restarts X. Wait for the system to come back up and log in. Now you should be able to select the new resolutions.

If you get in trouble or it doesn't work, feel free to ask again.

**2)** I really don't know much about this, but I do know that you'll need a program called "samba". My advice for you is to search these forums - they're a gold mine. Believe me: You are not the first one with this problem! :-D

Good luck!

PS: We keep the conversation here, so that others with the same problems can read it...

---

### Post by kamstrup on 2005-09-02
This site: [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) has a lot of valuable information. Also regarding Samba :-)

---

### Post by Hg80 on 2005-09-02
i was just about to about to ask the same question about screen res but hay its all here

---

### Post by frodon on 2005-09-02
There a nice [HOWTO](http://www.ubuntuforums.org/showthread.php?t=26438)  for noob to configure samba and share file with windows.

For screen resolution, if it still not work, open xorg.conf file (sudo gedit /etc/X11/xorg.conf) and add hsync and vertsync parameters in the monitor section :```
Section "Monitor"
Identifier "Dell"
Option "DPMS"
**HorizSync 30-76**
**VertRefresh 50-85**
EndSection
```
To know which value to use for hsync and vertsync parameters see your screen specification (horizontal and vertical refresh rates).

---

