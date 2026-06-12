---
title: "Acer 3680 Feisty Install Guide"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by jsares on 2007-05-01
Feisty had some problems when I installed it on my Acer Aspire 3680 Notebook.

The video resolution was 1024x768.  It should be 1280x800.  I fixed it buy running:

```
sudo apt-get install xserver-xorg-video-intel
```

The sounds wasn't working.  I fixed it by pasting:

```
options snd-hda-intel model=auto
```

at the bottom of:

```
/etc/modprobe.d/alsa-base
```

Things I'm trying to get to work:

Frequency Scaling
Trackpad Scrolling
Bluetooth

The good news is the wireless and desktop effects work out of the box.

---

### Post by jsares on 2007-05-01
Found the Trackpad fix.  Edit:

```
/etc/X11/xorg.conf
```

And add these lines below the mouse section:

```

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "SHMConfig" "true"
EndSection
```

Add this line in the ServerLayout section:

```
InputDevice "Synaptics Touchpad"
```

---

### Post by MaximusTG on 2007-05-17
I also have an Acer Aspire 3680, 
Instead of the new intel video driver I fixed the resolution problem bij installing 915resolution.

To get wireless to work (bcm4318 ) I first followed the howto for ndiswrapper, which worked almost perfect (couldn't get wpa_supplicant to work with a hidden SSID WPA-TKIP network) so I  installed the latest ndiswrapper from source.

Since I use my laptop in several places, I have 4 different wifi profiles, sadly I can't use Network Manager, because one of those profiles requires EAP-TTLS with PAP. And that is only supported in Network Manager 0.6.5, that isn't available for Ubuntu Feisty yet( or is it?)
Instead I setup /etc/network/interfaces so that wpa_supplicant is automatically started when the interface is brought up. I then use wpa_supplicant.conf to do the roaming.


Audio issues:
Out of the box, sounds didn't work on my HDA-intel ALC883, you have to enable the surround channel and use that to control sound volume. However, my headphones didn't work. So I installed latest alsa-driver, -lib and utils from source. After a reboot the main volume was now linked to the Front channel, and headphones worked, except that the volume of the internal speakers was linked to the headphones, I couldn't listen to headphones and mute internal speakers at the same time. 
So I added the option " snd-hda-intel model=3stack-6ch" to /etc/modprobe.d/alsa-base. After a reboot, sound from internal speakers was gone - only headphones worked. After changing channel mode from 2ch to 6ch, internal speakers worked again, now linked to the surround channel, and headphones linked to the front channel :). So now I can mute my internal speakers, and listen to my headphones!

If anyone would like specific instructions or conf files, just ask.

---

### Post by chickan on 2007-05-23
thanks for the guides, though I'm still looking on cpu throttling.  Through this and the other thread on Edgy, I have been able to get everything else to work.

---

### Post by CyberBob on 2007-05-25
I'm trying to get the wireless working on two Acer Aspire 3680 laptops - I got a great deal on these at a local store and installed Feisty on both.

laptop #1 - lspci output contains this line:

Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

laptop #2 - lspci output contains this line:

Atheros Communications, Inc.: Unknown device 001a (rev 01)

... and while I've read posts [post=2340037] here [/post] with similar issues, the detailed steps to solve them were not explained.

I tried using ndiswrapper to use the vendors driver, and after installing it this way the hardware is still not detected.  Also tried the switch on the front of the laptop to toggle the device on/off but nothing happens.

I'm still looking around for a solution, but if anybody can help directly here I'd appreciate it very much.


UPDATE:

found this after doing dmesg:

[   28.476800] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   28.574357] ndiswrapper (check_nt_hdr:153): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   28.574363] ndiswrapper (load_sys_files:216): couldn't prepare driver 'net5211'
[   28.574857] ndiswrapper (load_wrap_driver:118): couldn't load driver net5211; check system log for messages from 'loadndisdriver'
[   28.576339] usbcore: registered new interface driver ndiswrapper


now checking my system log ...

---

### Post by Jim March on 2007-05-27
I just got one myself, via the special Beast Buy was running ($399!).  This one is some sort of stripped down variant in that the 1280x800 screen is only 14.1" wide when the shell was clearly meant for 15.4 originally.  They also cheaped it out some by doing 512megs RAM, mediocre battery and the DVD is read-only (it does burn CDs though).

So far I've thrown both UbuntuStudio and regular Ubuntu Feisty on it, with interesting results. for both video and the Atheros WiFi system.

1) UbuntuStudio didn't auto-detect that it was an Intel chipset at all, so X crashed.  I managed to get things working at the command line, first with the i810 driver and then with the "intel" driver.  You have to load one or the other via synaptic or apt-get and then do a matching xorg.conf by hand.  BUT: in UbuntuStudio I could use the i810 driver and still get 1280x800 resolution, whereas in regular Feisty the i810 driver can only do 1024x768.  Very odd.  And when I do run i810 vs. "intel" I get a speed boost reported in glxgears of about 200fps.

2) Right now I'm running regular Feisty, "intel" driver, 1280x1024 and getting 750fps in glxgears.  This is with 2gigs RAM total (I had some leftovers from something else that died, yay!).  I've told the video system to use 128megs in both the BIOS and xorg.conf (quoted below).  I haven't yet started to work on dual display, I'll do that next.

3) My last rig that just died horribly was an old Compaq Evo N610c, based on the ATI Radeon 7500 Mobility.  I had a P4 2gHz and 768megs RAM.  Glxgears reported about 600 typically, yet ACTUAL video performance on this Acer is worlds ahead of the old Compaq in terms of Beryl working, game performance in stuff like Torcs, etc.  People keep saying "glxgears is not a good benchmark" and they ain't kiddin'.  I would guess that glxgears must be testing VERY primitive 3D effects and when pushed, the better cards can deliver a whole lot more.

My xorg.conf (Beryl compatible but can run without Beryl just fine):

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load "i2c"
	Load "bitmap"
	Load "ddc"
	Load "dbe" # added for Beryl
	Load "dri" # already here by default; Beryl asks for this
	Load "extmod"
	Load "freetype"
	Load "glx" # already here by default; Beryl asks for this
	Load "int10"
	Load "type1"
	Load "vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver "intel"
	BusID "PCI:0:2:0"
	Option "XAANoOffscreenPixmaps" # added for Beryl
	VideoRam        128000
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-40
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode 0666
EndSection

# the below was added for Beryl
Section "Extensions"
	Option "Composite" "Enable"
EndSection


**Atheros WiFi:**

YOU DO NOT NEED NDISWRAPPER.  M'kay?  Don't even think about it.

Here's what's worked for me, tested with both WEP and WPA encryption in plain Ubuntu Feisty:

1) Enable the Atheros restricted driver at System>Administration>Restricted Drivers Manager.

2) Under System>Administration>Network it wants everything to be "Enable Roaming Mode" - WiFi and cabled Ethernet.  Surprised me because I'd been using WiFi on the old Compaq via telling it directly which network to go to.  Anyways.  Use the "network" panel tool top right corner of Gnome to tell it which WiFi net to hit and specify parameters (DHCP, password, password type).  It will also list which networks it finds and their password status (no shield means open port).  There's also a "manual configuration" choice, works great.

Overall it's a damned decent machine, esp. for the money.

---

### Post by ex283 on 2007-05-28
in response to the above post. I bought the Aspire 3680(it actualy has the same 14.1WXGA display) after reading this thread. I'd hoped to ease myself into Linux after trying several times in the past to make the switch. I have  a basic familiarity with the cmd line and general linux. I ran into the same display as mentioned above but i'm not to worried about fixing that. My problem is with the Atheros Wifi. No doubt it's something elementary but nonetheless it's very frustrating.
I enabled restricted drivers, tried updating synamptic (by finding a hardline not easy here)

On booting i get the " HAL Hardware Revisoin Update not supported"
On installation the Atheros driver is enabled in the Restricted Driver area.
But there is no entry for it in the network manager.


------------------------
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
------------------------
dmesg
[   16.196000] ath_hal: module license 'Proprietary' taints kernel.
[   16.196000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   16.324000] sky2 eth0: enabling interface
------------------------
~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
----------------------
lsmod
ath_pci                97312  0 
wlan                  204484  1 ath_pci

---

### Post by Jim March on 2007-05-28
Huh.

I do recall that for some reason, it took a couple of reboots before UbuntuSTUDIO's Network Manager saw the card properly, but regular Feisty saw it right away.  I put it down to UbuntuStudio being weird but maybe not...maybe it's the Acer itself.

I'm going to go look in the BIOS, see if there's a "disable WiFi" option.  What I'm thinking is, maybe you can boot Feisty once with WiFi "off", shut it down, turn it back on again, bring it up and see if Feisty suddenly sees the dang thing?

Also: there are two switches on the front near the audio jacks, the right-hand of the two controls WiFi on and off.  Unfortunately it's not a "two position" switch, rather it's "momentary" - and the light indicator for WiFi on/off isn't working in Ubuntu yet.  But per one source somewhere, the switch IS working, able to turn on and off the WiFi hardware.  So if that's in the wrong state, it'll screw you. (Might be worth opening the case and removing the switch, so it can't accidentally engage on us?)

---

### Post by ex283 on 2007-05-29
thanks for the reply. Windows device manager is showing the wifi card as Atheros 5007eg Wireless Net adaptor - 
After checking the madwifi homepage i found this > 
Notes:	not supported by HAL as of 2007.03.12 
Notes:	'lspci' on Intel Mac Mini results in 168c:001c. Works w/o HAL problem. 2007.05.03. However used Atheros chip unclear

This dosen't clear it up but i think I'll have to try to install the ndiswrapper again. I have tried to compile the program on numeros ocassions and failed. I'll try again and copy the errors here.

---

### Post by Jim March on 2007-05-30
On another note: has anybody gotten dual-head (dual monitors, esp. where they aren't "clones" of each other but separate running apps) working on one of these?

---

### Post by bakhteiarov on 2007-06-05
> **CyberBob said:**
> I'm trying to get the wireless working on two Acer Aspire 3680 laptops - I got a great deal on these at a local store and installed Feisty on both.

laptop #2 - lspci output contains this line:

Atheros Communications, Inc.: Unknown device 001a (rev 01)

...
I'm still looking around for a solution, but if anybody can help directly here I'd appreciate it very much.

 ...

I have: 03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)

..and have a similar problem, any luck so far?

serge

---

### Post by CyberBob on 2007-06-07
Serge,

Still no luck here in getting the built-in wireless to work.  However, I do happen to have a US Robotics 802.11g Wireless Turbo PC Card, model USR 5410 (PCMCIA) that works with no problem.  I'd really like the one built into the laptop to function though ...

Apparently these Acer Aspire laptops have a variety of Atheros wireless devices installed, depending on when they were manufactured, I guess.  Some of them work, and some do not.  We seem to be the unlucky ones.

I'm hopeful somebody else out there figures out a way to get these to work if possible.  Anyone?  Anyone?

Bob

---

### Post by bakhteiarov on 2007-06-11
> **CyberBob said:**
> Serge,

Still no luck here in getting the built-in wireless to work.  However, I do happen to have a US Robotics 802.11g Wireless Turbo PC Card, model USR 5410 (PCMCIA) that works with no problem.  I'd really like the one built into the laptop to function though ...

Apparently these Acer Aspire laptops have a variety of Atheros wireless devices installed, depending on when they were manufactured, I guess.  Some of them work, and some do not.  We seem to be the unlucky ones.

I'm hopeful somebody else out there figures out a way to get these to work if possible.  Anyone?  Anyone?

Bob

Hi CyberBob,

Similar situation with me, got SonyEriksson GC 89 working as a (EDGE) modem for T-Mobile, but have not tried yet to use it as WiFi.

Have you managed to get  WiFi working on US Robotics? I am not sure what it (the card) is though.

cheers,

serge

---

### Post by bakhteiarov on 2007-06-11
> **MaximusTG said:**
> I also have an Acer Aspire 3680, 
Instead of the new intel video driver I fixed the resolution problem bij installing 915resolution.

To get wireless to work (bcm4318 ) I first followed the howto for ndiswrapper, which worked almost perfect (couldn't get wpa_supplicant to work with a hidden SSID WPA-TKIP network) so I  installed the latest ndiswrapper from source.

Since I use my laptop in several places, I have 4 different wifi profiles, sadly I can't use Network Manager, because one of those profiles requires EAP-TTLS with PAP. And that is only supported in Network Manager 0.6.5, that isn't available for Ubuntu Feisty yet( or is it?)
Instead I setup /etc/network/interfaces so that wpa_supplicant is automatically started when the interface is brought up. I then use wpa_supplicant.conf to do the roaming.


Audio issues:
Out of the box, sounds didn't work on my HDA-intel ALC883, you have to enable the surround channel and use that to control sound volume. However, my headphones didn't work. So I installed latest alsa-driver, -lib and utils from source. After a reboot the main volume was now linked to the Front channel, and headphones worked, except that the volume of the internal speakers was linked to the headphones, I couldn't listen to headphones and mute internal speakers at the same time. 
So I added the option " snd-hda-intel model=3stack-6ch" to /etc/modprobe.d/alsa-base. After a reboot, sound from internal speakers was gone - only headphones worked. After changing channel mode from 2ch to 6ch, internal speakers worked again, now linked to the surround channel, and headphones linked to the front channel :). So now I can mute my internal speakers, and listen to my headphones!

If anyone would like specific instructions or conf files, just ask.

After "playing" with sound, I finally completely lost it.. would you, please, post "specific instructions and conf files"?

thanks,

serge

---

### Post by CyberBob on 2007-06-11
Hello again Serge,

Yes I did get WiFi working on US Robotics card noted in my earlier post - the card was recognized after rebooting, but had to use  NetworkManager/Manual configuration  to get online.  In Network Settings I selected the wireless connection, clicked on "Properties", then had to DISABLE roaming mode and then selected my network name in the dropdown list.  Strangely enough, it didn't immediately connect but when I changed the password type (WEP key) from hexadecimal to ascii then everything worked fine.  I do not yet have WEP enabled with my router (trying to keep things simple first) - but now I am online with this WiFi card - the Atheros card built-in is just dead weight.

By the way, I've tried a variety of approaches including ndiswrapper (as noted in an earlier post), later I read that this is not needed with Atheros wireless devices, so I removed the ndiswrapper package.  I've since done at least two fresh re-installs of Feisty, trying to determine what is going on with these restricted drivers.  In the end it seems that the hardware just cannot get connected to a) a driver (in the case of the laptop I have with the AR5005G) or b) the pcieport-driver is attached in the other laptop I have with the Atheros "unknown device."  One of these laptops is a graduation gift for my son.

In the latter case, here's the relevant output from lshw:

 *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: Atheros Communications, Inc.
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=0
                resources: iomemory:34100000-3410ffff irq:17

---

### Post by CyberBob on 2007-06-12
Now this is really weird ...

I did a fresh install of Feisty on (my son's) Acer 3680-2633 with the AR5005G wireless device installed.  When the live CD prompted me to restart the system, I inserted another PCMCIA wireless card in the slot on the side of the laptop as the machine shut down.  When the system booted the first time after installation, I logged in and the AR5005G wireless card activated!

The PCMCIA card didn't even light up - it is a TRENDnet 802.11g card, model TEW-421PC.  I bought this thing for $20 a few years ago, and given my experience with my laptop I concluded it would be necessary to use an external card to go wireless.

Can anybody out there explain why this happened?  I am clueless - but HAPPY!

---

### Post by n8bounds on 2007-06-12
I have a 
0a:03.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
card, and it did the same thing,
the live cd would not bring up the ath0 interface, but once installed, it worked fine
the sd card reader didnt work until I upgraded to the ...-16 kernel
the sound
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
works fine, but is kind of soft (quiet) and doesn't really control well from the buttons...

if iwconfig shows wireless extensions for maybe an ath0 interface or WIFI0 or something, but network-manager chokes, give wicd a try, its better in almost every measurable way

---

### Post by n8bounds on 2007-06-16
Thanks for all your notes, by the way.  The touchpad and sound card fix are spot on!

---

### Post by tronica on 2007-06-18
I just but the acer 3680-2633, installed feisty on it. The wireless worked out of the box and sound work after I added surround to alsamixer and unmuted it. Bluetooth doesn't but i don't need it. I bought a 1 gig stick of ram to add to the 512 and it flys. thanks for the tips guys.

---

### Post by eltimbalino on 2007-07-06
Hi Jim,

I found this thread as a result of trying to get my new Acer Aspire 3680 to show both my Laptop Screen and my BenQ projection at the same time. I am able to get either to show without the other by booting with it hooked up or disconnected. I am not able to see both yet. Running the installed Windows Vista lets me have both on at once. 

I am very new to Linux and installed Ubuntu because Vista annoyed me (a lot). But I put these lines into my terminal to get the system to detect the new projector:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom

sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'

sudo dpkg-reconfigure xserver-xorg

I have no idea and just pasted them from: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

It started a configuration type of program and I followed it through. Must have set something wrong.

Now when I try to boot my system it fails:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. etc...

I then learnt how to make a back up of my file. But that is too late now. Oh well. I am certain that the file was autmatically generated. I might try booting off the CD instead or something. 

If you do find out how to run dual monitors I would love to hear from you.

Regards,

Tim

---

### Post by darrenrxm on 2007-07-08
I have also just purchased a acer 3680-2576. The sound works but not the headphones. I am really surprised by this because intel is such a big supporter of open source. I thought for sure everything would work. Well at least Ubuntu is way faster than the copy of windows vista that came with this laptop.

---

### Post by theDaveTheRave on 2007-07-13
Hello All.

I have recently bought this laptop also, and everything was working really well and I was a happy bunny.:)

Eltimbalino:

you mentioned playing with your xorg.conf file via a setup screen. When I did this recently it did in fact create an automatic copy of the original

Assuming that you have some form of GUI interface!  open a file browser window (or from a terminal type nautilus) and check the

[quote=]

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom

[/quote]

this did in fact create a copy of the original file. Assuming that you have some form of GUI interface!  open a file browser window (or from a terminal type nautilus) and vavigate to the folder /etc/x11/ 

It is possible that the setting in the file brower are a bit buggered up (read not as I like them!), I tend to select all the various option in the View menu (ie: Main Toolbar, Side pane, location bar and status bar)

It will now look similar to what you would be used to from Windows (I may hate windows but sometimes they do enable certain things in the correct fashion - or is I just set these as the defaults??).

In the sida pane on the left you should have a little title bar that says somehting like "place" with a down arrow - if not then click on the down arrow and you will see a set of options for how the side pane can look like - play until your hearts content with the result, but I stick with the "Tree" option. 

If your set up from factory was anything like mine you should have a bunch of options, relating to the pain ACER partition and the factory Vista backup partition - personally I got rid of these by playing with the FSTAB and using ntfs-g so as I can read write to them).

OK back to business.

click on File System    ----  a whole bunch of directories will spring up - not too discimilar to windows, but better in every way, do a search on the filing system in Linux it make for interestin reading...... but try to find a "brief" description or your head may start to hurt!

On the tree that is opened up click on the etc folder - Write access to this folder is only availabe with root permissions, so whatever happens you aren't going to destroy your system unless you are logged in as a user with root permisions - unlikely in Ubuntu, this is what the "SUDO" part of varios commands is doing, it forces "Super User DOmain" 


Look through the various files in the /etc and you will see a lot of interesting stuff floating around, generally the files are those that contain generalised configuration information for your system, the subdirectories on the other hand are related to a variety of systems available your system. If you scroll down you will come across a Gnome directory - obviously this contains Gnome specific setup config, and you will almost devinately see one for Open Office and Network manager etc. 

You may have twigged that there are things that the system need to funciton correctly whoever is accessing the terminal - any user specific information is stored in the /usr directory any software that you have installed for personaly use will have an entry with details pertaining to their initial setup and a some other information.


The one that we are interested in /etc however is /X11 - this is the underlying system that controls how your user interface looks and behaves.

You will find one of the files in here is xorg.conf    a quick by pass of what you did reveals to me that the code

> 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom



did in fact create a copy of the xorg,conf calling it xorg,conf.custom, you should see both of the files in the X11 directory.


> 
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'


I'm not totally sure on this comand, but I can say with some certainty that it is invoking a shell command (denoted by sh) and either creating or checking the md5sum of the file.

If you ever send emails to people they use a similar sort of idea, the mail is broken into lots of little bits and sent on its merry way. To ensure that the little bits all get to recipient in the correct order they each contain details of where they fit in the jigsaw and what the pitcure should look like at the end, in the instance above this picture is called the MD5 checksum, is is a unique number that should be the same at the befining and end of transmision (or inthe above case copying. This line seems to be comparing the "live" data xor.conf md5sum with the "backup" version in the libraries..... or something along those lines... I'm sure someone will correct me i I am wrong 8) .


> 

sudo dpkg-reconfigure xserver-xorg



Again from what I can tell I assume that this is calling a recofigure of the xserver system, so as your changes will be iplemented on your next boot up.

WHEW....

OK on to my question.

I had my system working nice and smoothly, had VLC playing videos and music etc, but didn't have a working swap, and only had the "cheap" 512mb RAM.

Managed to finaly get my SWAP and stuff functioning as I wanted and I realised I had lost my video and music playback.

VLC is throwing messages stating that it cannot locate the source, along with other similar messages that I saved to a file and are copied in below. I ran it from the commandline as the error messages, I ran it from the command line under SUDO so as to make sure it wasn't a permisions problem, and also it keeps the all the error messages :roll:

> 
run from comand line

davemyers@Aramis:~$ sudo vlc
VLC media player 0.8.6 Janus
starting VLC root wrapper... using UID 1000 (davemyers)
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: DVDVolume
libdvdnav: DVD Serial Number: bc6b77cc        
libdvdnav: DVD Title (Alternative): DVDVolume
libdvdnav: Unable to find map file '/home/davemyers/.dvdnav/DVDVolume.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000122
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0000117d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00013ff5
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x001d2f89
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001d2f8f
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0

libdvdnav: Language 'en' not found, using 'fr' instead
libdvdnav: Menu Languages available: fr 
[00000339] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
No accelerated IMDCT transform found
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85
davemyers@Aramis:~$ 




---

### Post by ubitsmith on 2007-08-03
I've installed Ubuntu 7.04 on a new Acer 3680 laptop.

Install from LiveCD went fine.

Just 3 issues:

1) resolution was not 1280x800... it was 1024x768.

I installed the resolution fix from post by 'jsares' and that was fixed.

2) no sound

I enabled surround channel as suggested by post from MaximusTG and got sound

3) no wireless

From reading posts, this is a bug problem which I will work on later.

At this point I could launch Firefox, surf the web, run apps, suspend/resume, very cool!
Thanks to all the people which made Ubuntu the top Linux distro.

**BUT** now the real problem... Ubuntu told me that there were 91 updates available.
So I let it download and install all 91 updates - worked fine.  Then I rebooted and ran
into another issue... seems like the system will no longer resolve host names.  Firefox
reports it can't find [www.yahoo.com](www.yahoo.com), can't ping any hosts by name... pinging hosts by
IP addr does work and the network manager does report that there is a wired network
connection.  I can ping hosts on the local net with IP addrs, just can't resolve names.

I've poked around, looked at log messages, etc, can't find anything wrong.

Any tips, hints, suggestions for debugging appreciated.  This is a nice laptop for the price -
$428 at local Walmart - and it would be great if Ubuntu was solid on it.

TIA.

---

### Post by crouger92 on 2007-08-04
Hi. I have the Acer Aspire 3000WLMi and everything was going fine... until the touchpad stopped working a few minutes ago. Can anyone help?

---

### Post by Michael%S on 2007-08-14
> **crouger92 said:**
> Hi. I have the Acer Aspire 3000WLMi and everything was going fine... until the touchpad stopped working a few minutes ago. Can anyone help?
If this is still relevant, you might wanna make sure you didn't disable it. My Aspire 3680-2682 toggles the touchpad on/off with fn+F7.

I haven't managed to get the system to see the wifi here, which is quite a problem because I need that wifi to connect to the internet in most places. If anyone knows of solutions that have not been brought to this thread yet I'd be very grateful to hear of them. I'm pretty sure this Aspire has an Atheros wifi adapter, btw.

---

### Post by Dan-Raoul on 2007-08-19
Okey, my mom recently purchased this computer, and asked me because I'm so much into Linux and Ubuntu, to instal Ubuntu on the computer.
One thing I have to say: this computer is the computer I have had least problems with to install Linux on! ^^
after doing what the two first posts says, I had no problem whatsoever. (okey, we don't have wireless at home, so haven't tried connecting wireless, but it found the neighbours wireless in no time)
the only problem was, that after rebooting the computer, suddenly the wireless wasn't found. I clicked the button in front 1, one time, rebooted, and then it worked, no problems ;) tried that? (okey, one thing different from others computers, my light is on all the time when I'm in ubuntu, but don't think that matters)

EDIT: answer to the post above, fn+F7 works fine here, actually, every hotkey I've tested so far(the ones on the touchpad excepted, they worked after the tweak in the second post), worked out of the box ;)

---

### Post by donnellymp on 2007-09-08
You guys are awesome...My speakers work fine now.

---

### Post by theDaveTheRave on 2007-09-18
One tiny thing, that to be honest I could live without.

the touchpad, I have been able to activate the "scroling edge" facility, but it is really large and I keep "scrolling" around pages by accident!

Is there a way to reduce the "sensitive area", I can do this withing Vista using the Acer touchpad thingy, but can't seem to do the same in Ubuntu??

Like I say it isn't really anything important, I just wondered if anyone else had found a way to do it.

Dave

---

### Post by tdrusk on 2007-09-22
My sound does not work after I hibernate. It only works if I boot into it.

Any ideas?

---

### Post by randytuggle on 2007-09-26
OK, After reading this entire guide thus far I am going to add the things I have done to get my 3680-2682 with the Atheros wireless to work:

1. Sound- simply double-click the volume control icon in the top panel and go to EDIT>PREFERENCES and enable the check-boxes for surround and front. THEN go to SYSTEM>PREFERENCES>SOUND. At the bottom, I clicked on SURROUND to highlight it as my choice for controlling the system volume from my Acer FN+UP/DOWN controls on the keyboard.

2. ATHEROS wireless will work great for me when I do these two things; install ndiswrapper-common from Synaptic Package Manager by loading the Ubuntu CD and opening EDIT > Load CD before SEARCHING to install the program. Once that installs, I install a file named atheros-ar5007eg-installer-0.1b.tar.gz. By installing that file after extraction in terminal, I restart the system, and all with wireless is perfectly fine.

3. The first posting in this guide gave me the resoultion fix. I do not need 915resolution. I tried it on my last install and it didn't work and better than the intel driver installation.

I would REALLY like to get the Texas Instruments media card reader to work! If anyone has a solution for that one, please offer it here.

---

### Post by PsycoGeek on 2007-09-26
The media card reader worked for me out of the box.  

I have not been able to get the Atheros WiFi working on my laptop no matter what I did.  Check out this thread I started as an alternate way to get WiFi on your Aspire 3680 without using your only PC card slot to do it:

[Acer Aspire 3680 WiFi saga update...]("http://ubuntuforums.org/showthread.php?t=551621")

The Trackpad fix is fantastic.  That thing was driving me insane...

---

### Post by randytuggle on 2007-09-26
I wonder why my media card doesn't work... does anyone care to post the containing section of their xorg file?

---

### Post by PsycoGeek on 2007-09-26
I would but there isn't anything in there for it.  Have you checked "System - Preferences - Hardware information" to see if it is there?

-edit-  You may also want to try this.  I did in an attempt to get wireless working, but it may also affect the card reader.

[ACPI install]("http://ubuntuforums.org/showthread.php?t=224350")

---

### Post by randytuggle on 2007-09-26
Yep! It states I have a Texas Instruments PCIxx12 cardbus controller. 82801 Intel Mobile PCI bridge.

---

### Post by PsycoGeek on 2007-09-26
Have you tried to put a card in the reader?  I wasn't sure if mine was working so I popped in a 512mb card from my camera and it mounted it on the desktop.

If it isn't working, try the ACPI install.

---

### Post by randytuggle on 2007-09-26
I've tried mounting it with no luck. I use a sony memory stick. I'll try the ACPI and see if that works.

---

### Post by randytuggle on 2007-09-26
where can I get the acpi? It's not in synaptic for the acer...

---

### Post by PsycoGeek on 2007-09-26
I had posted a link on how to install it.

---

### Post by randytuggle on 2007-09-26
I'm not able to find one. Do you have the link handy?

---

### Post by PsycoGeek on 2007-09-26
> **randytuggle said:**
> I'm not able to find one. Do you have the link handy?

Well, OK, here is the exact same link I posted above...  You have to follow the instructions in the link to get anywhere...

[ACPI install for Acer Laptops]("http://ubuntuforums.org/showthread.php?t=224350")

---

### Post by ljonesj on 2007-09-30
if you have the latest kernal update. it will get the card reader to work from what i hear

---

### Post by tdrusk on 2007-09-30
> **ljonesj said:**
> if you have the latest kernal update. it will get the card reader to work from what i hear
I'm slightly afraid to upgrade the kernal. I never have. I will just wait for Gutsy.

---

### Post by ljonesj on 2007-09-30
my kernal has been upgraded to the latest and its fine. plus my card reader works fine with the sd card dont know about my memory sticks for  my psp

---

### Post by tdrusk on 2007-10-01
This command should take care of resolution and wireless, the two biggest problems.

First run
```
sudo update-pciids && lspci
```

If you see (I marked it in bold)

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
**03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)**
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

you are ready to run my command

My command
```
sudo aptitude update && sudo aptitude install 915resolution && wget http://blakecmartin.googlepages.com/atheros-ar5007eg-installer-0.1c.tar.gz && tar xvf atheros-ar5007eg-installer-0.1c.tar.gz && sudo aptitude update && sudo aptitude install linux-headers-$(uname -r) build-essential && echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist && pushd atheros-ar5007eg-installer-0.1c/ndiswrapper-1.48/ && sudo make uninstall && make && sudo make install && popd && pushd atheros-ar5007eg-installer-0.1c/ar5007eg/ && sudo ndiswrapper -i net5211.inf && popd && sudo modprobe ndiswrapper && echo "ndiswrapper" | sudo tee -a /etc/modules && sudo init 6
```

---

### Post by randytuggle on 2007-10-01
I just want mine to read SONY Memory Stick media cards right now... I can't get a fix for it.

---

### Post by tdrusk on 2007-10-01
> **randytuggle said:**
> I just want mine to read SONY Memory Stick media cards right now... I can't get a fix for it.
Are you referring to the card reader on the side? That has been resolved (I THINK) in the new kernal. It is in Gutsy. If you must have it, you can upgrade the kernal. Search for
upgrade feisty kernal vanilla
in the search dialog.

---

### Post by randytuggle on 2007-10-01
that search on ubuntu forums just brought me right back here...

---

### Post by tdrusk on 2007-10-01
> **randytuggle said:**
> that search on ubuntu forums just brought me right back here...

[http://ubuntuforums.org/showthread.php?t=311158&highlight=vanilla+kernal](http://ubuntuforums.org/showthread.php?t=311158&highlight=vanilla+kernal)

sorry about that.

---

### Post by randytuggle on 2007-10-01
After reading all of that, I think I will just wait for the official Gutsy release. I hate messing with xorg. It always crashes when I do.

---

### Post by tdrusk on 2007-10-01
> **randytuggle said:**
> After reading all of that, I think I will just wait for the official Gutsy release. I hate messing with xorg. It always crashes when I do.

Yeah it's a pain. If xorg is a problem for you, you will love Gutsy. It has Bulletproof x, which helps prevents breaking of xorg. :)

---

### Post by randytuggle on 2007-10-01
I tried a copy of Tribe and it worked for awhile. I tried reinstalling it and it wouldn't install. Just got a bunch of error messages instead....maybe I'll do well to wait for the release since it's less than 2 weeks away, I think...

---

### Post by tdrusk on 2007-10-01
> **randytuggle said:**
> I tried a copy of Tribe and it worked for awhile. I tried reinstalling it and it wouldn't install. Just got a bunch of error messages instead....maybe I'll do well to wait for the release since it's less than 2 weeks away, I think...

Yeah it will be out about that time.

---

### Post by randytuggle on 2007-10-02
OK, I installed the Gutsy 7.10 using update manager. When I insert my sony memory stick, the stick lights up (as if it's loading) but doesn't mount or show up anywhere. Any clue on how to fix this issue? Otherwise, Gutsy seems ok - not much differences than Fiesty IMHO. Fonts look clearer though! :)

---

### Post by PsycoGeek on 2007-10-03
> **randytuggle said:**
> OK, I installed the Gutsy 7.10 using update manager. When I insert my sony memory stick, the stick lights up (as if it's loading) but doesn't mount or show up anywhere. Any clue on how to fix this issue? Otherwise, Gutsy seems ok - not much differences than Fiesty IMHO. Fonts look clearer though! :)

Maby a bad format on the memory stick?  I have an SD card a while back that worked fine in the camera, but when I put it in the card reader Windows couldn't read it.  I attached the camera directly to the PC and was able to transfer the images off of it, then I reformatted the card in the camera and it worked OK in the reader after that.

Try attaching the camera via USB to see if you can read the images off of it that way.

Please post you results.

---

### Post by ljonesj on 2007-10-03
yeah i have had that happen to my sd cards 
gutsy looks nice but i had a problem when i upgraded it. it asked about my custom mods i had to do to get my sound and other things working. i told it not to replace them which i think was part of the problem but after that my music came out of the speakers with popping and static like. i said it wanted to replace the custom sound mod but i told it not too could that have caused the problem

---

### Post by randytuggle on 2007-10-03
My gutsy took an xorg crap on me. I tried to change to display settings to make the video card - not an intel 180 - but a 915 or 945. The system asked me to log out for changes to take effect -- and BAM!! I couldn't save it. I reinstalled and 6.10 and upgraded my way to Feisty 7.04 again. I'm sticking with the basics until I get a confirmation that Gutsy will be working stable on the Acer Aspire 3680.

---

### Post by PsycoGeek on 2007-10-03
> **randytuggle said:**
> My gutsy took an xorg crap on me. I tried to change to display settings to make the video card - not an intel 180 - but a 915 or 945.

That's because the graphics are the Intel GMA 950 (as identified by Acer), not 915 or 945 (940GML is the chipset on the motherboard).  Ubuntu Identifies the graphics controller as the Mobile 945GM/GMS/940GML Express Integrated Graphics Controller in device manager.  I would not change the settings in xorg.

> **randytuggle said:**
> I reinstalled and 6.10 and upgraded my way to Feisty 7.04 again.

Why didn't you just install from a Feisty 7.04 CD?

---

### Post by randytuggle on 2007-10-03
my feisty cd doesn't work right. Didn't feel like making another with the official gutsy coming out soon.

---

### Post by tdrusk on 2007-10-04
I just updated to Gutsy. It still doesn't recognize blank dvds.

---

### Post by PsycoGeek on 2007-10-05
> **fuzzyhair said:**
> I just updated to Gutsy. It still doesn't recognize blank dvds.

Mabe that's because the Aspire 3680 comes with a CD R/W, DVD combo drive.  It isn't a CD R/W, DVD R/W drive.  It only reads DVD's.

---

### Post by tdrusk on 2007-10-05
> **PsycoGeek said:**
> Mabe that's because the Aspire 3680 comes with a CD R/W, DVD combo drive.  It isn't a CD R/W, DVD R/W drive.  It only reads DVD's.
Thanks for that info. Clears up a ton of problems :).

---

### Post by PsycoGeek on 2007-10-05
> **fuzzyhair said:**
> Thanks for that info. Clears up a ton of problems :).

I thought it had a DVD burner as well when I first got mine.

---

### Post by CapnK on 2007-10-07
Hi All -

I have an Aspire 3680-2682, purchased at WalMart a couple/3 weeks ago *(only $421, inc tax - yippee! If I had the extra $, I'd go get another before they're gone! ;))*. I am very impressed with the system overall, *especially* considering the price point. This has got to be the hands-down best deal out there, and believe me - I shopped *hard* before purchasing, to ensure I wasn't making a $400 mistake. :)

Though I'm not running K/Ubuntu from a hdd install yet (d/l'ing Kubuntu GG beta right now to try it, and that will likely become my default distro) - thought I'd post  my experiences so far, since this thread ranks so high in Google searches concerning this laptop. Most of my use so far has been using Mepis 6.5.2, which is Ubuntu-based (6.06 IIRC), but I'll be trying GG soon, and will post results afterwards.

Different from most of the users who posted previously in this thread, this Acer unit has a Dell 1390 wireless card, which uses the Broadcom BCM94311MCG chipset. It does work well under ndiswrapper, I am hoping for the same once I get GG on here.

The main reason for this post: In doing some searches regarding this laptop and Acer Invisilink wireless, I ran across a post in the TechRepublic forum where the poster ("Old Mycroft", apparently a UK-based IT guy) made a comment that keeping the screen at 10-15 degrees from vertical was essential for best wireless reception, and, to my amazement, this is exactly right. Since finding this obscure bit of info last night, I have played with screen angles, and found a direct correlation between the screen angle and the link quality.

Hope that little tidbit helps someone else out.

---

### Post by randytuggle on 2007-10-07
I've noticed that screen angles do make a difference. Thanks for the tip! GO WAL-MART! I've had mine for about 5 weeks. Other than mediocre graphics on WOW using WINE, it rocks!

---

### Post by CapnK on 2007-10-07
One additional post for you 3680 users -

Do/did you have several IRQ related messages on boot, particularly in reference to IRQ's 7,8, and 9?

I forget the actual messages, but found a workaround by adding the following to the GRUB boot options:

```
acpi=off pnpbios=off
```

The issue seemed to affect the ability to use the installed wireless card (Dell 1390, w/Broadcom BCM94311MCG chipset), but I am not yet positive of that, still testing.

Again, this was using Mepis 6.5.2, which is based on Ubuntu 6.06.

(My Kubuntu d/l is finished, CD is burnt, time for a try... :) ).

---

### Post by randytuggle on 2007-10-07
I get those messages on boot - but they don't bother me. I am assuming they are related to the TI Media Card Reader not being supported.

---

### Post by PsycoGeek on 2007-10-07
> **randytuggle said:**
> I get those messages on boot - but they don't bother me. I am assuming they are related to the TI Media Card Reader not being supported.

The TI media card reader works fine for me.  No errors on boot.

If you turn off ACPI then the built in WiFi card, and the TI card reader definitely will not work.

---

### Post by ubitsmith on 2007-10-07
ARG!!!!  I just tried installing gutsy gibbon beta and now it's back to the old problem -
after the install, the network works fine... but, if you try suspending the computer,
then it fails to suspend, and then the network stops working - like as if it can't resolve
dns names!

ARG!!!!  After installing all updates to feisty fawn a couple of weeks ago, the issue
with losing the network after a suspend was fixed, but I could not get wireless WPA
networking to work with an ASUS 802.11b/g card in the pcmcia slot - I could never
get the built in Atheros wireless networking to work ever.  With gutsy
beta, the wireless works on the ASUS card, but now the issue of the network
dns going away after a failed suspend is back!

ARG!!!!

I would be willing to donate this computer to the ubuntu developers if they agreed
to resolve this issue before gutsy goes final... any takers on the ubuntu team???

ARG!!!


> **ubitsmith said:**
> I've installed Ubuntu 7.04 on a new Acer 3680 laptop.

Install from LiveCD went fine.

Just 3 issues:

1) resolution was not 1280x800... it was 1024x768.

I installed the resolution fix from post by 'jsares' and that was fixed.

2) no sound

I enabled surround channel as suggested by post from MaximusTG and got sound

3) no wireless

From reading posts, this is a bug problem which I will work on later.

At this point I could launch Firefox, surf the web, run apps, suspend/resume, very cool!
Thanks to all the people which made Ubuntu the top Linux distro.

**BUT** now the real problem... Ubuntu told me that there were 91 updates available.
So I let it download and install all 91 updates - worked fine.  Then I rebooted and ran
into another issue... seems like the system will no longer resolve host names.  Firefox
reports it can't find [www.yahoo.com](www.yahoo.com), can't ping any hosts by name... pinging hosts by
IP addr does work and the network manager does report that there is a wired network
connection.  I can ping hosts on the local net with IP addrs, just can't resolve names.

I've poked around, looked at log messages, etc, can't find anything wrong.

Any tips, hints, suggestions for debugging appreciated.  This is a nice laptop for the price -
$428 at local Walmart - and it would be great if Ubuntu was solid on it.

TIA.

---

### Post by randytuggle on 2007-10-11
I'm still using feisty but my suspend just started to work on power and battery - for no reasons at all. If only my card reader would read my Sony memory stick....

---

### Post by theDaveTheRave on 2007-10-30
Hello again all.

I recently had a total systems failure (returned the laptop to Acer and they replaced the HDD).

So I got my first opportunity to do a "full clean ubuntu install"

This seemed to go without any sort of problem, the only issue has come with the touchpad.

When I enter the required lines into the xorg.conf file the next boot will not start the Xwindow system?? no matter what I try I can't see why this doesn't want to be a success!

The only differences I can tell on my new "clean install" are that I have started with fiesty 7.10 (i believe that when I first got this laptop and I used 7.06).

so the question is this: has anyone else had any issues with the touchpad and 7.10? or should I go back to 7.06, then upate to 7.10??

On an odd note UbitSmith states that he has had issues with WPA on his wireless networking. It never even occured to me that this may have been a system issue! I just thought I was being dopey and not setting it up correctly!

Either way I solved the "network security issue" by simply implementing MAC address filtering - maybee not very helpfull in a large institution but great for a 3 computer home network.

Dave

---

### Post by tdrusk on 2007-11-03
> **theDaveTheRave said:**
> Hello again all.

I recently had a total systems failure (returned the laptop to Acer and they replaced the HDD).

So I got my first opportunity to do a "full clean ubuntu install"

This seemed to go without any sort of problem, the only issue has come with the touchpad.

When I enter the required lines into the xorg.conf file the next boot will not start the Xwindow system?? no matter what I try I can't see why this doesn't want to be a success!

The only differences I can tell on my new "clean install" are that I have started with fiesty 7.10 (i believe that when I first got this laptop and I used 7.06).

so the question is this: has anyone else had any issues with the touchpad and 7.10? or should I go back to 7.06, then upate to 7.10??

On an odd note UbitSmith states that he has had issues with WPA on his wireless networking. It never even occured to me that this may have been a system issue! I just thought I was being dopey and not setting it up correctly!

Either way I solved the "network security issue" by simply implementing MAC address filtering - maybee not very helpfull in a large institution but great for a 3 computer home network.

Dave

I didn't have to do that trick in gutsy. The touchpad worked out of the box.

---

### Post by tdrusk on 2007-11-03
Hibernate and Suspend aren't working for me in Gutsy. Neither will resume.

Any ideas?

---

### Post by quanumphaze on 2007-11-04
I just installed Gusty yesterday.

Screen res is OK out of box
Atheros is OK out of box

Sound only worked out of internal speakers after unmuting surround. I tried to compile the ALSA drivers from source and now there's no sound and the volume control doesn't work. [From this guide]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

I can't figure out how to get it to use my 19' LCD (my n00bness nearly killed xorg.conf). The "Screen and Graphics" thing doesn't work and says I'm using the "intel - Experimental modesetting driver for Intel integrated graphics chipsets" (I don't like the sound of that "experimental").

Suspend doesn't work here either. But I will try the uswsusp thing.

At least Compiz Fusion works :)

---

### Post by tdrusk on 2007-11-06
This was the only hibernate workaround that I could come up with. Works well.
[http://techaspect.net/2007/11/06/make-ubuntu-shutdown-when-lid-is-closed/](http://techaspect.net/2007/11/06/make-ubuntu-shutdown-when-lid-is-closed/)

---

### Post by Kedster on 2007-11-20
i did ur instructions to get the sound workin but then i plug in my headphones and then the speakers stay on (the headphones work but speakers r on) i dont no if u could fix it or not but i hope i can

---

### Post by quanumphaze on 2007-11-21
> **Kedster said:**
> i did ur instructions to get the sound workin but then i plug in my headphones and then the speakers stay on (the headphones work but speakers r on) i dont no if u could fix it or not but i hope i can

This is what I did:

1: Back up alsa-base:
```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.bak.00 
```
2: Open alsa-base:
```
sudo gedit /etc/modprobe.d/alsa-base
```
3: Paste this in:
```
options snd-hda-intel model=3stack-6ch
```
If there is a similar line with options snd-hda-intel model=??? replace it with above
4: **Reboot**

You can try these alternatives: model=[auto, acer, 3stack, 3stack-2ch]
If it breaks then you can restore your backup

5: One you log back in you must open the volume control and un-mute front for headphone and un-mute surround for the internal speakers. I don't know how to get it to do it automatically in Gutsy but I made individual volume applets for each of them (PCM(both), front, and surround) and mute/unmute when necessary.

Post back if it works.

---

### Post by Kedster on 2007-11-21
hey umm i dont think it worked i took out the other line i put in the ealer that ended with auto and nothing worked then put both line in and it then when i put headphones in the speakers stay playin so like when im sittin in the livinromm and wanna listen to music while othr watch tv i cant cuz they get distracted and if i do it ur (no offence ment) i dont get any sound so what id like is for my speakers to go off when i plug my headphones in and vice-versa 

PS. sorry i had school alday therwise i woulda replyed faster

---

### Post by tdrusk on 2007-11-21
I just installed Linux Mint Daryna on the laptop. My god it runs great. Imo it is better than ubuntu and uses the ubuntu repos. Pretty great. 

everything worked out of the box except wireless.

---

### Post by quanumphaze on 2007-11-21
> **Kedster said:**
> hey umm i dont think it worked i took out the other line i put in the ealer that ended with auto and nothing worked then put both line in and it then when i put headphones in the speakers stay playin so like when im sittin in the livinromm and wanna listen to music while othr watch tv i cant cuz they get distracted and if i do it ur (no offence ment) i dont get any sound so what id like is for my speakers to go off when i plug my headphones in and vice-versa 

[Try this, it's the guide I used to recompile the alsa drivers from source.]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel") Then try to put the line in the alsa-base file.

Getting this sound card to work at all is a bitch. If anyone else can find out how to get it to auto-mute the internal speakers when I insert the jack it would be much apreciated.

My alsa-base looks like this
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# options snd-hda-intel model=3stack-2ch
options snd-hda-intel model=3stack-6ch
# options snd-hda-intel model=3stack
# options snd-hda-intel model=auto

```
(I put all of the options in ans commented out the unused ones). Remember to make backups!

Maybe we should start a new thread if this problem persists. Good luck.

PS:
> **Kedster said:**
> sorry i had school alday therwise i woulda replyed faster
Don't worry, I just turned on my computer 30 mins ago. :)

---

### Post by thaMANSTA on 2007-11-22
> **tdrusk said:**
> Hibernate and Suspend aren't working for me in Gutsy. Neither will resume.

Any ideas?

After upgrading from Feisty to Gutsy, I have trouble resuming from hibernate, but I can make it resume, with a little prodding:

When I click a key to wake the machine up, the DVD spins up for a second, the CPU face winds up for a second, then it just sort of sits thee, stuck.  If I flick the WiFi button on and off a few times, the HD access LED light flickers each time, then stops after like 5 or 6 times.  If I then hit a key on the keyboard again, the machine finishes waking up.

I think the machine is waiting for the WiFi card to do something it isn't doing, or it isn't waking up properly. 

My questions:

 - If I open the Volume Control gnome applet, and toggle Mute to on, in the mixer it mutes the PCM, and hence both the Front/Headphone is muted, as well as the Surround/Speakers.  BUT, if I use the keyboard mute key (Fn-F8), only the Front/Headphone is muted.  Where in the world can I change the action of the keyboard mute key to mute the PCM instead?  Why is Front muted by default?

 - After dist upgrading, my video worked fine.  Then I played with the new Screen and Graphics Admin Tool, and now everytime I reboot it's confused about my graphics setup, and keeps reverting back to the VESA driver.  How can I revert the settings for the control panel, and get it to redo it's initial configuration (which worked fine)?  This tool seems very good, just isn't ready for prime time.

---

### Post by tdrusk on 2007-11-22
> **thaMANSTA said:**
> After upgrading from Feisty to Gutsy, I have trouble resuming from hibernate, but I can make it resume, with a little prodding:

When I click a key to wake the machine up, the DVD spins up for a second, the CPU face winds up for a second, then it just sort of sits thee, stuck.  If I flick the WiFi button on and off a few times, the HD access LED light flickers each time, then stops after like 5 or 6 times.  If I then hit a key on the keyboard again, the machine finishes waking up.

I think the machine is waiting for the WiFi card to do something it isn't doing, or it isn't waking up properly. 



Here's the workaround
[http://techaspect.net/2007/11/04/how-to-wireless-ar5007eg-with-ndiswrapper-in-debian-and-ubuntu/](http://techaspect.net/2007/11/04/how-to-wireless-ar5007eg-with-ndiswrapper-in-debian-and-ubuntu/)

---

### Post by quanumphaze on 2007-11-22
> **thaMANSTA said:**
> 
When I click a key to wake the machine up, the DVD spins up for a second, the CPU face winds up for a second, then it just sort of sits thee, stuck.  If I flick the WiFi button on and off a few times, the HD access LED light flickers each time, then stops after like 5 or 6 times.  If I then hit a key on the keyboard again, the machine finishes waking up.

I find that mine wakes up from suspend when I fiddle with the screen close trigger button thing. Works best if I press it on/off in 1 sec intervals for about 8 times.

> **tdrusk said:**
> Here's the workaround
[http://techaspect.net/2007/11/04/how-to-wireless-ar5007eg-with-ndiswrapper-in-debian-and-ubuntu/](http://techaspect.net/2007/11/04/how-to-wireless-ar5007eg-with-ndiswrapper-in-debian-and-ubuntu/)
Does this work for the older AR5005G? My one works fine with the proprietary drivers provided but could it be the thing causing suspend the problem?

> **thaMANSTA said:**
> 
 - After dist upgrading, my video worked fine.  Then I played with the new Screen and Graphics Admin Tool, and now everytime I reboot it's confused about my graphics setup, and keeps reverting back to the VESA driver.  How can I revert the settings for the control panel, and get it to redo it's initial configuration (which worked fine)?  This tool seems very good, just isn't ready for prime time.

Don't touch the 'Screen and Graphics'. It usualy will break your xorg.conf file.

I figured out how to use 'xrandr' to change between monitors in Gutsy. It should also handle the TV out. (NOTE: This is what I remember I did and is not up to 'howto' quality so it may screw up :oops:)

Firstly you must go into the BIOS setup and change the video output option from **auto** to **both**.

Then fiddle with your xorg-conf file (back it up first) to look like similar to mine: (key parts are in bold)
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel 945"
        Driver          "intel"
        Option          "monitor-LVDS" "laptop"
        BusID           "PCI:0:2:0"
EndSection

[B]Section "Device"
        Identifier      "Intel 945 extern"
        Driver          "intel"
        Option          "monitor-VGA" "extern"
        BusID           "PCI:0:2:1"
EndSection[/B]

Section "Monitor"
        Identifier      "laptop"
        Option          "DPMS"
        Option          "LeftOf" "extern"
        Option          "Enable" "true"
EndSection

Section "Monitor"
        Identifier      "extern"
        Option          "DPMS"
        Option          "PreferredMode" "1280x800"
        Option          "Ignore" "true"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel 945"
        Monitor         "laptop"
        DefaultDepth    24
        SubSection "Display"
                [B]Modes           "1280x800" "1280x1024" "1024x768"
                Virtual         2048 2048[/B]
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```
[SIZE="3"]**Reboot**[/SIZE]

plug in the cable for your external monitor
in the terminal type```
xrandr -q
```
you should get something like this```
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2048 x 2048
VGA connected 1280x1024+0+0 (normal left inverted right) 376mm x 301mm
   1280x1024      60.0*+   75.0     59.9  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
LVDS connected (normal left inverted right)
   1280x800       59.9 +   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right)
```
(LVDS is the laptop's LCD)
Then try```
xrandr --auto
```
You should hopefully get cloned output on the LCD and external monitor.

some other xrandr example commands (the stuff after '#' are comments, don't type them):```
xrandr -q #this displays what is available
xrandr --output LVDS --off #turns of LCD
xrandr --output LVDS --left-of VGA #does dualscreen (with compiz)
xrandr -s 1280x800 #change screen res
man xrandr #gives better explanation
```

This is very fiddly, please share some feedback on how/if it worked for you. Corrections are welcomed.
Also does anyone knows how to map some of these (xrandr --auto) to the Fn+F5?
Good luck.

PS: we should start the Acer Aspire 3680 Gutsy install guide. Anyone up for it?

---

### Post by tdrusk on 2007-11-22
> **quanumphaze said:**
> 
Does this work for the older AR5005G? My one works fine with the proprietary drivers provided but could it be the thing causing suspend the problem?

It should work for all laptops I would imagine.

---

### Post by ozylog on 2007-11-23
> **quanumphaze said:**
> This is what I did:

1: Back up alsa-base:
```
sudo cp /etc/modprobe.d/alsa-base /etc/modprobe.d/alsa-base.bak.00 
```
2: Open alsa-base:
```
sudo gedit /etc/modprobe.d/alsa-base
```
3: Paste this in:
```
options snd-hda-intel model=3stack-6ch
```
If there is a similar line with options snd-hda-intel model=??? replace it with above
4: **Reboot**

You can try these alternatives: model=[auto, acer, 3stack, 3stack-2ch]
If it breaks then you can restore your backup

5: One you log back in you must open the volume control and un-mute front for headphone and un-mute surround for the internal speakers. I don't know how to get it to do it automatically in Gutsy but I made individual volume applets for each of them (PCM(both), front, and surround) and mute/unmute when necessary.

Post back if it works.


thanks quanumphaze it's really helpful for me

---

