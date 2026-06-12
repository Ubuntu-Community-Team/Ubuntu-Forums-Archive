---
title: "No monitor activity"
date: 2005-11-27
forum: Installation &amp; Upgrades
---

### Post by GuruMadMat on 2005-11-27
I installed ubuntu and i enabled all resolutions and now my monitor does nothing when login screen should come up!
i'm now in recovery mode but i don't know where to change this!
and with what command do I edit a file when i'm in recovery mode?

---

### Post by Xian on 2005-11-27
[QUOTE=GuruMadMat]i'm now in recovery mode but i don't know where to change this! and with what command do I edit a file when i'm in recovery mode?[/QUOTE]
Use this command:

$ nano -w /etc/X11/xorg.conf

---

### Post by GuruMadMat on 2005-11-27
and how do i change it so it uses 1024*768?

---

### Post by Xian on 2005-11-27
[QUOTE=GuruMadMat]and how do i change it so it uses 1024*768?[/QUOTE]
Find what your default depth is set to:

```
	DefaultDepth	24
	SubSection "Display"
```

Then set the first resolution on the Modes line to 1024x768.

```
SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
```

---

### Post by teaker1s on 2005-11-27
sudo dpkg-reconfigure xserver-xorg will ask questions and set it up for you

---

