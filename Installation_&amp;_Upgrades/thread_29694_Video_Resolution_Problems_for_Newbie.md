---
title: "Video Resolution Problems for Newbie"
date: 2005-04-25
forum: Installation &amp; Upgrades
---

### Post by khari on 2005-04-25
Ive got everything installed properly but the refresh rate is still way too low.  I studied the forums and got to my config file to change the vertical and horizontal refresh rate but I am unable to make changes to the file in the text editor because it is "read-only".  I know this is stupid but how can I modify the file if it is read only?  Is there anyway that I can change it from "read-only"?


THanks

---

### Post by heimo on 2005-04-25
You must use root account to edit it. Run in terminal 
```

sudo gedit /etc/X11/xorg.conf

```
or what-ever the file is. Password this command asks is the same as your normal user password.

---

### Post by havesometea on 2005-04-26
I have a screen resolution problem also.  I am looking in the xorg.conf file and it lists the correct video card and resolutions but I am stuck with only 640x480 and 800x600.

I want to change it to 1024x760 but I don't get that option.

---

### Post by fordfan753 on 2005-04-26
[QUOTE=havesometea]I have a screen resolution problem also.  I am looking in the xorg.conf file and it lists the correct video card and resolutions but I am stuck with only 640x480 and 800x600.

I want to change it to 1024x760 but I don't get that option.[/QUOTE]

Find out how to change the VetiSync and HorizRefresh in /etc/X11/xorg.conf under the monitor section, plug in the specs supplied with your monitor, save, and ctrl + alt + backspace to restart X. When you log back in you should have all resolutions that your monitor can use.

---

### Post by heimo on 2005-04-26
Please check
[http://www.ubuntuforums.org/showthread.php?t=21984]("http://www.ubuntuforums.org/showthread.php?t=21984")
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21]("http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21")

---

### Post by fordfan753 on 2005-04-26
Actually, by default, VertSync and HorizRefresh are not in /etc/X11/xorg.conf so you will need to add them in...Apart from this its not too difficult.

---

### Post by havesometea on 2005-04-26
I have checked those links...thanks....but the resolution I want to use is already listed in the xorg.conf.  It appears to me the file is correct but when I go to the display properties to change it to 1024x760 I only see 640x480 and 800x600.

---

### Post by heimo on 2005-04-26
[QUOTE=havesometea]I have checked those links...thanks....but the resolution I want to use is already listed in the xorg.conf. It appears to me the file is correct but when I go to the display properties to change it to 1024x760 I only see 640x480 and 800x600.[/QUOTE]
 
Ehrm. What do you have in Monitor section of the xorg.conf? What's your monitor? What graphics card are you using, what do you have in Device section on line Driver? Can you attach (not inline in a message, but as an attachment), the log file for xorg (the correct name of this file on the thread I posted).
 
I'll check those later (in about 2 hours), if someone else isn't quicker.

---

### Post by havesometea on 2005-04-26
[QUOTE=heimo]Ehrm. What do you have in Monitor section of the xorg.conf? What's your monitor? What graphics card are you using, what do you have in Device section on line Driver? Can you attach (not inline in a message, but as an attachment), the log file for xorg (the correct name of this file on the thread I posted).
 
I'll check those later (in about 2 hours), if someone else isn't quicker.[/QUOTE]

The monitor is some piece of cheap crap made in China...like everything these days it seems...

In the xorg.conf it lists it as "generic monitor".

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-60
	VertRefresh	43-60


It is actually an EMC PX-769

Graphics card is a Cirrus Logic GD 5480 and that is correctly identified in the conf file.


I have uploaded the file as xorg.txt

Let me add too that I followed the directions in that second link...

I typed sudo xresprobe cirrus

and got

id:
res:
freq:
disptype:crt

---

### Post by havesometea on 2005-04-26
Well, I did this...the default depth was set to 24...I changed it to 16 and restarted X.

Viola.  Now I have more screen resolutions.

---

### Post by heimo on 2005-04-26
You probably have 2MB memory in that video card? Good thing you got it working.

---

