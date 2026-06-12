---
title: "Compiz makes everything disappear and nothing work"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by pluckypigeon on 2008-10-18
When I enable compiz, everything on the screen disappears apart from the background and mouse cursor.

The only way I can get out of it is to manually turn off the pc. 

CTRL+ALT+BACKSPACE, CTRL+ALT+DELETE or even ALT + PRNTSCREEN + REISUB doesn't work 

I have used compiz on this pc before so I am not sure why it does it.

I can't give you a terminal output because it disappears.

I have recently upgrade to intrepid... i dunno if thats helpful.

Here is some info:

sudo lshw:

```


 vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device


```

xorg:

```


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection


```

lspci:

```


00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)


```

---

### Post by beno1990 on 2008-10-18
If you've just upgraded to Intrepid, your old configuration might not be compatible with the new release.

I'd say delete the .compiz folder in your home directory and try starting compiz again. You'll completely delete your Compiz configuration but it might fix any faulty configuration that Intrepid doesn't want to look at, and create a new config folder from scratch with the default settings when you next start compiz.

---

### Post by pluckypigeon on 2008-10-18
> **beno1990 said:**
> If you've just upgraded to Intrepid, your old configuration might not be compatible with the new release.

I'd say delete the .compiz folder in your home directory and try starting compiz again. You'll completely delete your Compiz configuration but it might fix any faulty configuration that Intrepid doesn't want to look at, and create a new config folder from scratch with the default settings when you next start compiz.

I've tried that. I've also purged everything to do with compiz and reinstalled.

---

### Post by pluckypigeon on 2008-10-18
I don't know if this is any use:

I ran [compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check")

Output:
```


Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```

---

### Post by pluckypigeon on 2008-10-18
is this problem unheard of? am i the only one?

---

### Post by pluckypigeon on 2008-10-20
xserver and compiz have updated recently but I'm still getting the same problem.

anyone?

---

### Post by caryb on 2008-10-20
It's not just Compiz, Metacity in Kubuntu is screwed as well. I have to disable enhanced graphics otherwise I get the black screen & only mouse on the screen.


Cary

---

### Post by bash on 2008-10-20
What is the error you get when you just type in the terminal:

```
compiz --replace
```

---

### Post by pluckypigeon on 2008-10-20
> **bash said:**
> What is the error you get when you just type in the terminal:

```
compiz --replace
```

no error.

everything just disappears before the terminal output

---

### Post by jerrylamos on 2008-10-20
> **pluckypigeon said:**
> is this problem unheard of? am i the only one?

Nope, you're not the only one.  There are a number of us with compiz problems.  See Launchpad bug 277344 and scout back through the forums for various "black screen" or "wallpaper" or "no desktop" problems.

I use an IBM Thinkpad R31, 1 gHz 32 bit Celeron, Intel graphics.  Last Ubuntu Intrepid that ran on it without workaround is Alpha 5 NOT UPDATED.

Every few days I try again with a new daily build download to catch all the then current updates.  Ever since Alpha 6 and Beta, booting up proceeds until the Gnome desktop should appear and then the laptop freezes up solid.

My fix is to install in a separate partition from the Alpha 5 so I have a running install in case the new one screws up.
Boot the new install.  Sure enough it fails.  Then after hardware reset, boot in recovery mode.  Linux boots up without X windows to a selection window. 
select root prompt.
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot.

Now I'm all about applications such as full screen internet, full screen Office, full screen Picassa digital pictures, ... so I could care less about compiz "eye candy".

Another alternative is to use Xubuntu Intrepid which doesn't use compiz, and doesn't do "eye candy" or else if you want lots of "eye candy" use Kubuntu Intrepid.

Last Ubuntu I tried was dated Oct 16.  I couldn't try Oct 19 or 20 because they are too fat to fit on a 700 mb CD.

August 12 ran, then updates the next day killed the Thinkpad.  Sept 4 ran but updates killed it again.  If something doesn't show up in the next week, Release Code will fail too.  Bug 277344 is marked "low" importance.

See also [http://ubuntuforums.org/showthread.php?t=947005](http://ubuntuforums.org/showthread.php?t=947005)

Jerry

---

