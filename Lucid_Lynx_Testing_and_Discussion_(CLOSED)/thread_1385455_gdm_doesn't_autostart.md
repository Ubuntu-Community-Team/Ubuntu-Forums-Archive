---
title: "gdm doesn't autostart"
date: 2010-01-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Glowing Fish on 2010-01-19
I updated to lucid lynx, and since I have done so, gdm does not autostart. Instead I get a standard non-gui logon, and I can sudo and start gdm easily from there. But it seems like an odd thing that gdm is not going to start on its own.

Also, and I don't know if this is related, I have total system freezes that need a hard restart. This seems to have started a few weeks ago when I upgraded to karmic, and seems to be continuing with lucid

I think both of these might be some type of gui setting problem, especially since I have a new monitor (Flatron 22 inch LCD), but I haven't ruled out that I have some type of hardware problem, maybe in the memory.

---

### Post by VMC on 2010-01-19
> **Glowing Fish said:**
> I updated to lucid lynx, and since I have done so, gdm does not autostart. Instead I get a standard non-gui logon, and I can sudo and start gdm easily from there. But it seems like an odd thing that gdm is not going to start on its own.

Also, and I don't know if this is related, I have total system freezes that need a hard restart. This seems to have started a few weeks ago when I upgraded to karmic, and seems to be continuing with lucid

I think both of these might be some type of gui setting problem, especially since I have a new monitor (Flatron 22 inch LCD), but I haven't ruled out that I have some type of hardware problem, maybe in the memory.
You should have a memory test on your grub menu(/boot/memtest86+.bin).

Also list your hardware, video, ram, HD's, CPU, etc

---

### Post by Glowing Fish on 2010-01-19
I do have memtest, and went through 4 tests (not a complete pass), and nothing failed immediately. Since memtest can take some time, I wanted to know if there was a single line to be changed in a config file before I spent time on it.

Hardware: 2.6 GHz P-4, 512 megs of DDR RAM, onboard video, a single 40 gig harddrive, Flatron monitor...I can't think of anything else relevant.

---

### Post by VMC on 2010-01-19
> **Glowing Fish said:**
> I do have memtest, and went through 4 tests (not a complete pass), and nothing failed immediately. Since memtest can take some time, I wanted to know if there was a single line to be changed in a config file before I spent time on it.

Hardware: 2.6 GHz P-4, 512 megs of DDR RAM, onboard video, a single 40 gig harddrive, Flatron monitor...I can't think of anything else relevant.

If that "onboard video" is Intel that might be a problem, depending on what family.  I have an i865 with no issues, i845 does have problems I here. Try an add "nomodeset" on the linux line of your grub menu. This may not fix your issue.

Do you mean gdm doesn't autostart in that you have to put in your password?

---

### Post by Glowing Fish on 2010-01-19
I mean that I don't get a graphical login when I bootup, I get a command line login, and have to run gdm as a command to get the gdm login

---

### Post by MacUntu on 2010-01-19
What's in the file /etc/X11/default-display-manager? It should say '/usr/sbin/gdm'.

---

### Post by Glowing Fish on 2010-01-20
> **MacUntu said:**
> What's in the file /etc/X11/default-display-manager? It should say '/usr/sbin/gdm'.

That is what it says in that file.

---

### Post by Tompalaz on 2010-01-21
gdm has more or like stoped working for me since I did a fresh install of A2 + the nvidia 190 driver.

---

### Post by Glowing Fish on 2010-01-21
> **VMC said:**
> If that "onboard video" is Intel that might be a problem, depending on what family.  I have an i865 with no issues, i845 does have problems I here. Try an add "nomodeset" on the linux line of your grub menu. This may not fix your issue.

Do you mean gdm doesn't autostart in that you have to put in your password?

What file do I add this line to, and where?

---

### Post by VMC on 2010-01-21
> **Glowing Fish said:**
> What file do I add this line to, and where?

When grub starts, push 'e' to edit that partition, then look for this:
```
linux /vmlinuz root=UUID=05d7ba94-0d23-4ec5-8814-d89200128faf ro splash
```

You UUID will be different, but just add to the end of the line, like so:
```
linux /vmlinuz root=UUID=05d7ba94-0d23-4ec5-8814-d89200128faf ro  nomodeset
```Then issue Ctrl+X to boot it. I removed the splash so you can see the booting output.

---

### Post by Glowing Fish on 2010-01-22
I did this, and gdm didn't start up, until I told it to from the command line.

But, this might have helped my freeze issues: my computer had been freezing every 30 minutes, but after this it took several hours.

---

### Post by ranch hand on 2010-01-22
We have been getting x updates at an impressive rate, twice a day sometimes.  Keep it updated and it should straighten out.

---

### Post by Glowing Fish on 2010-01-24
> **ranch hand said:**
> We have been getting x updates at an impressive rate, twice a day sometimes.  Keep it updated and it should straighten out.

This is always a good strategy, and I guess this is also the point where I mention that gdm is one of the packages that is "kept back" when I run dist-upgrade

---

### Post by Jordanwb on 2010-01-24
```
sudo service gdm start
```

When you shutdown through gnome, you'll be asked for a password because other users are logged in. Enter the password. Gdm should startup automatically at boot.

---

### Post by Glowing Fish on 2010-01-28
I fixed the gdm problem the obvious way: I ran apt-get -f install gdm

But the freeze problems are still going on. I wonder if it is specific to my monitor?

---

### Post by Jordanwb on 2010-01-28
> **Glowing Fish said:**
> I fixed the gdm problem the obvious way: I ran apt-get -f install gdm

It wasn't installed?

> **Glowing Fish said:**
> But the freeze problems are still going on. I wonder if it is specific to my monitor?

Try MemTest. It's listed in the grub menu.

---

### Post by jerrylamos on 2010-01-28
> **Jordanwb said:**
> It wasn't installed?

Try MemTest. It's listed in the grub menu.

This is a multi-boot with i845 video graphics.

Lucid hangs frequently.  There's some reported bugs but no answers.  Yes I use "nomodeset" and driver "vesa".  Hangs or doesn't even boot if I don't.

This same pc has other partitions with SUSE, Fedora, DebianLXDE, Slax, Slitaz, and I've run Knoppix from CD.

All these don't freeze.  Ever. Same pc.

Karmic & Jaunty had a lot of trouble with KMS on Ubuntu, and looks like Lucid continues the pattern.  

Intrepid had trouble with Compiz, the Ubuntu solution was to "blacklist" Compiz on this pc.  Suits me.

Good luck...

Jerry

---

### Post by phenest on 2010-01-28
> **Tompalaz said:**
> gdm has more or like stoped working for me since I did a fresh install of A2 + the nvidia 190 driver.

Which is what I did, and mine works fine.

@Glowing Fish, if it's anything to do with your Intel video driver, could it be worth building a new xorg.conf file and trying that?
```
sudo service gdm stop
sudo Xorg -configure
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo service gdm start
```
Do this from a tty rather than a terminal because you mustn't have gdm running which the first line makes sure of. The 2nd line creates a new xorg.conf file. If the 3rd line fails, it's just making a backup if it does exist.

Whatever happens, post back the contents of that xorg.conf.new file, please.

---

### Post by Glowing Fish on 2010-02-05
> **phenest said:**
> Which is what I did, and mine works fine.

@Glowing Fish, if it's anything to do with your Intel video driver, could it be worth building a new xorg.conf file and trying that?
```
sudo service gdm stop
sudo Xorg -configure
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo service gdm start
```
Do this from a tty rather than a terminal because you mustn't have gdm running which the first line makes sure of. The 2nd line creates a new xorg.conf file. If the 3rd line fails, it's just making a backup if it does exist.

Whatever happens, post back the contents of that xorg.conf.new file, please.

Sorry for the delay, there was a few things going on. Including for a while my monitor would only display in minimum resolution, then it wouldn't display outside of textmode at all, until the apt-get brought me a new package of the xorg intel video driver.

I did follow your instructions, but the same lockup/freeze problems persist. This is what is currently in that file:
<code>

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "dbe"
	Load  "glx"
	Load  "extmod"
	Load  "record"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

</code>

At some point, should I file a hardware report bug?

---

