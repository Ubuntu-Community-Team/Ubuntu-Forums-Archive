---
title: "Cant install because screen is too small"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by raspa_sete on 2007-01-29
I have ubuntu for some time now, but I had some problems and had to reinstall everything my problem is the following:

The usual definition of the screen is 1024x768 (the kernel booted with the vga=791 option).

I downloaded and burned the latest version of Ubuntu, when I run it, it runs a definition of 800x600 for the screen. The problem is to install, because the window it opens is bigger than the screen and I can pull it up enough to be able to press the OK button.

I've tried everything I know and can't manage to install the thing.

I went to the screen definitions but it only sees the 800x600 definition.
I don't have a graphic card, or better, it comes with the motherboard and share the RAM.
I tried to put the vga=791 in the command line to start the ubuntu in the first screen (where it asks for options..) but it didn't work.

I have no idea how to install the driver, better, which driver I have to install and then  restart X11 with the new definition.

The other way is to install from the command line, but I haven't found the command to do it!

So: HELP SOMEBODY!

Thanks in advance

---

### Post by an.echte.trilingue on 2007-01-29
Does CTRL+ALT+MINUS help?

---

### Post by raspa_sete on 2007-01-29
> **an.echte.trilingue said:**
> Does CTRL+ALT+MINUS help?

No because the computer doesn't have alternative choices to the 800x600 screen definiton.

I have to increase the option, but I have no ideia how to do it. It seems the right drivers are already installed, I just don't seem to be able to star ubuntu in the right definiton. bah...

---

### Post by an.echte.trilingue on 2007-01-29
how about switching to a virtual terminal (ctrl+alt+F2) and running 
```
sudo dpkg-reconfigure xserver-xorg
```
picking the resolution that you need, then switching back to the GUI ctrl+alt+F7 and restarting X with CTRL+ALT+Backspace?

Also, I can tell you how to install the driver if you let me know what graphics card you have.  If you don't know you can go to the virtual terminal and type ```
lspci | grep VGA
```

---

### Post by mscclr3 on 2007-01-29
What kind of card is it? If it is intel onboard search the forum for 855resolution Sorry if you said what kind of card it is and I missed it

---

### Post by raspa_sete on 2007-01-30
Hei, blarg

OK, the
```
lspci | grep VGA
```
gives:
```
0000:00:02.0 VGA compatible controller: Intel corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (Rev 03)
```
(I have no idea what it means...)


I've tried this also
```
sudo dpkg-reconfigure xserver-xorg
```

But it seems that I don't know what I am doing, because now X fails to restart due to some misconfiguration! blah!

Can someone point me to an "how to configure X" tutorial?



> What kind of card is it? If it is intel onboard search the forum for 855resolution Sorry if you said what kind of card it is and I missed it
I know it's an onboard card, but I have no idea how to check it! unless its the information that the system gave when I did the "lspci | grep VGA" command. (the output is above)

Thank you for giving me some atention! really thanks!

---

### Post by raspa_sete on 2007-01-30
how about switching to a virtual terminal (ctrl+alt+F2) and running
Code:

```
sudo dpkg-reconfigure xserver-xorg
```

picking the resolution that you need, then switching back to the GUI ctrl+alt+F7 and restarting X with CTRL+ALT+Backspace?


This time it worked!
beautiful!

Thank you so much!=D> \\:D/

---

### Post by an.echte.trilingue on 2007-01-30
> **raspa_sete said:**
> Hei, blarg

OK, the
```
lspci | grep VGA
```
gives:
```
0000:00:02.0 VGA compatible controller: Intel corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (Rev 03)
```
(I have no idea what it means...)

It means that you have an Intel integrated graphics card, probably something like an 855, which means that you don't need to download any drivers (as far as I am aware).


> I've tried this also
```
sudo dpkg-reconfigure xserver-xorg
```

But it seems that I don't know what I am doing, because now X fails to restart due to some misconfiguration! blah!
It is natural that you don't know how to do something you have never done before.  Let's try to work through this.  First of all, if you got an actual error message you should let us know what it is because that will help us correct the problem.  
1.  You can either try to run the wizard again without changing anything but the resolution, or,
2.  you can edit the config file by hand:
```
sudo vi /etc/X11/xorg.conf
```
To use vi, you press "i" (for insert) to start editing, and when you are done you hit ESC, then ":", then "wq" and then then hit enter.
You are going to want to find the section that looks like this and change the resolution to the one you want in each and every SubSection "Display":
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```



However, I would recommend that you try to mess around with dpkg-reconfigure a little more before trying this.

Finally, if you just want to install and not mess around with this, you can download the alternate CD and do a text based install following [these instructions,]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/index.html") but you will probably have to deal with this again when you get your system installed anyway.

Let me know if this helps.

Take care
-mat

---

### Post by raspa_sete on 2007-01-31
I re-installed ubuntu just to have the hang of it :)
and this time I tried an.echte.trilingue solutions! It's a little bit more troublesome, since you have to navigate the files and the file it self but it works fine.
Thanks alot, both of you.

---

