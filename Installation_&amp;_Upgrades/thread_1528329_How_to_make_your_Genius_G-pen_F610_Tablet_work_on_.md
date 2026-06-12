---
title: "How to make your Genius G-pen F610 Tablet work on Ubuntu 10.04 Lucid Lynx"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by AlexDS on 2010-07-10
This is how i made my Genius G-Pen F610 Tablet on Ubuntu 10.04 Lucid Lynx. Everything works but the buttons the sides of the tablet, the buttons of the pen(stylus) work as well.  
 

     First I was looking at these websites, as a reference:  
     [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) 
     [http://ubuntuforums.org/showthread.php?t=1475433](http://ubuntuforums.org/showthread.php?t=1475433) 
     [http://ubuntuforums.org/showpost.php?p=9393179&postcount=1002](http://ubuntuforums.org/showpost.php?p=9393179&postcount=1002) 
 

     So, let's begin our journey:  
 

 [SIZE=5]**1**[/SIZE][SIZE=5]. [/SIZE]Add this ppa: [FONT=Verdana]**ppa:doctormo/xorg-wizardpen**[/FONT]
(I've went to System-Administration-Software Sources-Other Software-Add and copy-pasted this at the APT line: ** ppa:doctormo/xorg-wizardpen ** )
   
 [SIZE=5]**2**[/SIZE][SIZE=5].[/SIZE][FONT=Verdana, Arial, Tahoma]  Install **xserver-xorg-input-wizardpen**[/FONT] 
(I went to System-Administration-Synaptic Package Manager and typed** wizardpen** (on the QuickSearch bar)  
    It showed me that there is a packet called **xserver-xorg-input-wizardpen**, I have right-clicked and check Mark for Installation, and then went to **Apply** button.)  
 

 [SIZE=5]**3. **[/SIZE][FONT=Verdana, Arial, Tahoma]Run **cat  /proc/bus/input/devices** in the  terminal[/FONT]
(I openned Applications-Accessories-Terminal and there I pasted (by that I mean pressing Middle-mouse button – this way you can easely paste) this code: **cat /proc/bus/input/devices)**
     Now it will show all the devices on your computer, so you need to find the event for your tablet.
 My F610 tablet is recognised by Ubuntu like this:
 

 [COLOR=Navy]*I: Bus=0003 Vendor=172f Product=0034 Version=0110 *[/COLOR] 
 [COLOR=Navy]*N: Name="WALTOP International Corp. Slim Tablet" *[/COLOR] 
 [COLOR=Navy]*P: Phys=usb-0000:00:1d.1-2/input0 *[/COLOR] 
 [COLOR=Navy]*S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input4 *[/COLOR] 
 [COLOR=Navy]*U: Uniq= *[/COLOR] 
 [COLOR=Navy]*H: Handlers=kbd mouse1 *[/COLOR][SIZE=5]**[SIZE=4][COLOR=Navy]event4[/COLOR][/SIZE] **[/SIZE][SIZE=3][COLOR=#ff0000]**<---this is what you need to                                                          know**[/COLOR][/SIZE]
 [COLOR=Navy]*B: EV=10001f *[/COLOR] 
 [COLOR=Navy]*B: KEY=c03 1f0001 0 0 e080ffdf01cfffff fffffffffffffffe *[/COLOR] 
 [COLOR=Navy]*B: REL=103 *[/COLOR] 
 [COLOR=Navy]*B: ABS=1ffff0001000003 *[/COLOR] 
 [COLOR=Navy]*B: MSC=10 *[/COLOR] 
 

 **Remember the event that you have. (Mine is event4. Maybe your event is different than mine, so be careful to not use another even in the following ) ** 
 

      **[SIZE=6]4[/SIZE]**.Now we got to do the calibration:
     Paste[COLOR=#000000]     in the terminal[/COLOR]:      **wizardpen-calibrate /dev/input/**[COLOR=#ff0000]**event**[/COLOR][COLOR=#ff0000]**4      **[/COLOR][COLOR=#ff0000]           (or whatever event you may have, diferent than mine)[/COLOR]
          
          [COLOR=#000000]This is what I've got:[/COLOR]
          
     [COLOR=#000000]root@alexds-desktop:/home/alexds#     wizardpen-calibrate /dev/input/event4 [/COLOR]     
          
     [COLOR=#0000ff]Please, press     the stilus at ANY [/COLOR]     
     [COLOR=#0000ff]corner of your     desired working area: ok, got 716,11631 [COLOR=#000000][SIZE=2]*<---This     is when I have pressed the pen on                                                 to the     tablet*[/SIZE][/COLOR][/COLOR]
     
     [COLOR=#0000ff]Please, press     the stilus at OPPOSITE    [COLOR=#000000][SIZE=2]                               <---again the same thing[/SIZE][/COLOR][/COLOR]
     [COLOR=#0000ff]corner of your     desired working area: ok, got 19870,349 [/COLOR]     
     
     [COLOR=#0000ff]According to     your input you may put the following [/COLOR]     
     [COLOR=#0000ff]lines into your     XF86Config/X.Org configuration file:   [/COLOR][COLOR=#000000][SIZE=2]<---this     means that I have to paste this                                     on the the     70-wizardpen.conf[/SIZE][/COLOR]
     
     [COLOR=#0000ff]    Driver          "wizardpen"     [/COLOR]     
     [COLOR=Blue]    Option           "Device"          "/dev/input/event4"     [/COLOR]     [COLOR=Blue]
[/COLOR]      [COLOR=Blue]    Option           "TopX"             "716"                         
[/COLOR]           [COLOR=Blue]    Option           "TopY"          "349"                          
[/COLOR]           [COLOR=Blue]    Option           "BottomX"        "19870"                      
[/COLOR]           [COLOR=Blue]    Option          "BottomY"        "11631"                      
[/COLOR]  
 [COLOR=#0000ff]    [COLOR=#000000]I only gonna copy(and later paste) the last5 lines. [/COLOR][COLOR=#000000][SIZE=2]This means [/SIZE][/COLOR][COLOR=#000000][SIZE=2]_without:_[/SIZE][/COLOR][COLOR=#000000][SIZE=2] driver  “wizardpen” [/SIZE][/COLOR][/COLOR] 
 

 
 [SIZE=5][SIZE=6]**5**[/SIZE].[/SIZE][COLOR=#000000] Paste in Terminal: [/COLOR]** gedit **[COLOR=#000000]**/usr/lib/X11/xorg.conf.d/**[/COLOR][COLOR=#0000ff][SIZE=4]**70**[/SIZE][/COLOR][COLOR=#000000]**-wizardpen.conf **[/COLOR] 
 [COLOR=#000000](Here we are going to e[/COLOR][COLOR=#000000]dit this file using [/COLOR][COLOR=#000000]_root _[/COLOR][COLOR=#000000]privileges (check the "[/COLOR][COLOR=#0000ff]**number**[/COLOR][COLOR=#000000]" of your file name, maybe yours is different. You have to be root to do this. How to be root? Check that on Google or ubuntu forums.)[/COLOR]
 
 [COLOR=#000000]    A window should have poped-up with some text. You need to modify it to look like this:[/COLOR]
 
 [COLOR=#0000ff][FONT=Liberation Serif, serif][SIZE=3]Section "InputClass"[/SIZE][/FONT][/COLOR]
 [COLOR=#0000ff][FONT=Liberation Serif, serif][SIZE=3]        Identifier "wizardpen"[/SIZE][/FONT][/COLOR]
         [COLOR=#0000ff][FONT=Liberation Serif, serif][SIZE=3]MatchIsTablet "on"[/SIZE][/FONT][/COLOR]  
 [COLOR=#696969][FONT=Liberation Serif, serif][SIZE=3]# Here I hardcoded the event4, please check wich event is yours.[/SIZE][/FONT][/COLOR]
 [COLOR=#0000ff][FONT=Liberation Serif, serif][SIZE=3]MatchDevicePath "/dev/input/[/SIZE][/FONT][/COLOR][COLOR=#ff0000][FONT=Liberation Serif, serif][SIZE=3]event4[/SIZE][/FONT][/COLOR][COLOR=#0000ff][FONT=Liberation Serif, serif][SIZE=3]"[/SIZE][/FONT][/COLOR]
 [COLOR=#696969][FONT=Liberation Serif, serif][SIZE=3]# This line is the original one. I removed because my tablet was not matched:[/SIZE][/FONT][/COLOR]
 [SIZE=3][COLOR=Cyan][FONT=Liberation Serif,  serif]MatchVendor "UC-LOGIC|KYE Systems|Ace Cad[/FONT][/COLOR][/SIZE][COLOR=PaleTurquoise][COLOR=Cyan] [/COLOR] [/COLOR]  [SIZE=3][COLOR=Red]<----This is what i removed[/COLOR][/SIZE]
 [COLOR=#696969][FONT=Liberation Serif, serif][SIZE=3]*#[CALIBRATION] This data was taken from wizard-calibrate tool( the data from the yellow rectangle)*[/SIZE][/FONT][/COLOR]
 [COLOR=#0000ff][FONT=Liberation Serif, serif][SIZE=3]Option                   "Device"                  "/dev/input/event4"
[/SIZE][/FONT][/COLOR][COLOR=#0000ff][FONT=Liberation Serif, serif][SIZE=3]Option                                        "TopX"                "716"[/SIZE][/FONT][/COLOR]
[COLOR=#0000ff][FONT=Liberation Serif, serif][SIZE=3]         Option                                "TopY"                          "349"[/SIZE][/FONT][/COLOR]
[COLOR=#0000ff][FONT=Liberation Serif, serif][SIZE=3]         Option                  "BottomX"              "19870"[/SIZE][/FONT][/COLOR]
[COLOR=#0000ff][FONT=Liberation Serif, serif][SIZE=3]         Option                                        "BottomY"         "11631"      [/SIZE][/FONT][/COLOR]                 
   [COLOR=#696969][FONT=Liberation Serif, serif][SIZE=3]#[END CALIBRATION][/SIZE][/FONT][/COLOR] 
 [COLOR=#0000ff][FONT=Liberation Serif, serif][SIZE=3]        Driver "wizardpen"   [/SIZE][/FONT][/COLOR] 
 [COLOR=#0000ff][FONT=Liberation Serif, serif][SIZE=3]    EndSection[/SIZE][/FONT][/COLOR]
  [COLOR=#0000ff][FONT=Liberation Serif, serif][SIZE=3]    Section "InputClass" [/SIZE][/FONT][/COLOR] 
 [COLOR=#0000ff]  [FONT=Liberation Serif, serif][SIZE=3]    Identifier "wizardpen ignore mouse dev" [/SIZE][/FONT][/COLOR] 
 [COLOR=#0000ff]   [FONT=Liberation Serif, serif]    [SIZE=3]MatchIsTablet "on" [/SIZE][/FONT][/COLOR] 
 [SIZE=3][COLOR=#0000ff] [FONT=Liberation Serif, serif]    MatchDevicePath "/dev/input/mouse*" [/FONT][/COLOR][/SIZE] 
 [SIZE=3][COLOR=#ff0000] [FONT=Liberation Serif, serif]    [COLOR=#0000ff]MatchVendor "UC-LOGIC|KYE Systems|Ace Cad" [/COLOR][/FONT][/COLOR][/SIZE][SIZE=3][COLOR=Red]<----- This one i've kept[/COLOR][/SIZE]
 [SIZE=3][COLOR=#0000ff][FONT=Liberation Serif, serif]    Driver "" [/FONT][/COLOR][/SIZE] 
 [SIZE=3][COLOR=#0000ff][FONT=Liberation Serif, serif]    EndSection[/FONT][/COLOR][/SIZE]
 

 

 [COLOR=#0000ff][FONT=Liberation Serif, serif]    [COLOR=#000000][SIZE=5][SIZE=6]6[/SIZE].[/SIZE][/COLOR][COLOR=#000000] [SIZE=3]Now all that is left to do is to reboot and pray it works[/SIZE] :)[/COLOR][/FONT][/COLOR]

---

### Post by tudor117 on 2010-07-11
Very good post.

---

### Post by AlexDS on 2010-07-11
thaks to you ;)

---

### Post by AlexDS on 2010-07-11
> **tudor117 said:**
> Very good post.

thanks to you ;)

---

### Post by Favux on 2010-07-11
Hi AlexDS,

Good HOW TO!  :)

It looks like the problem is MatchVendor.  MatchProduct seems to work as in:
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchProduct "WALTOP"
   MatchDevicePath "/dev/input/event*"
   Driver "wizardpen"
	Option		"TopX"		"775"
	Option		"TopY"		"726"
	Option		"BottomX"	"19237"
	Option		"BottomY"	"11614"
	Option 		"TopZ" 		"20"  # minimum pressure, default is 20
	Option		"BottomZ"	"1023" # maximum pressure
EndSection

Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchProduct "WALTOP"
   MatchDevicePath "/dev/input/mouse*"
#   MatchDevicePath "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.0-mouse"
#   Driver ""
   Option "Ignore" "yes"
EndSection
```
If it does the next question is if in the first snippet you can change to a generic event rather than specifying it, like so:
```
   MatchDevicePath "/dev/input/event*"
```

Does any one know how to turn the sensitivity down?  Is there a speed, or cursor speed setting?  Or sensitivity, or sampling rate, etc.?

---

### Post by tudor117 on 2010-07-11
If by sensitivity you mean the pressure sensitivity, isn't the TopZ and BottomZ what does it?

As for the MatchVendor, if you don't remove the second one, wouldn't it theoretically have 2 events: the mouse and the mouse dev? Not quite sure what ignore thing is supposed to do so correct me if I'm wrong

---

### Post by Favux on 2010-07-11
I'm not a hundred percent sure either.  But apparently something in the hid section of the kernel creates a spurious device node and the second snippet assigns it no driver "" to block it.  Otherwise evdev probably tries to set up on it and messes things up.

Right, and there's a few more settings according the the README I just got.

---

### Post by AlexDS on 2010-07-12
Thanks Favux, I tried my best. 
Basically what i did with [COLOR=#000000]wizardpen-calibrate /dev/input/event4 [/COLOR] is what it says on this page [http://ubuntuforums.org/showthread.php?t=1475433](http://ubuntuforums.org/showthread.php?t=1475433).
So thanks to al.do, i've modified a little bit to match my tablet, according to his tips, and voila, my tablet works. 
Also I'm not really sure that all is right , but my tablet works, so i offered some info, for someone that might need it. Perhaps the setting can be adjusted more and still be ok, i don't know since i'm a ubuntu and linux beginner after all my life being a windows user.

---

### Post by AlexDS on 2010-07-12
Anyways, i needed the tablet for using it in Gimp, but for some strange reason it freezes the mouse , and i can paint/draw selections only with the pen, but i can still use the mouse only for clicking on File or Edit or View tabs and of course for closing the window, but not actually manipulate the image .
Any idea why? 

This is how Gimp sees my tablet: [http://yfrog.com/6rcumvedegimptabletaj](http://yfrog.com/6rcumvedegimptabletaj)

---

### Post by Favux on 2010-07-12
Hi AlexDS,

> Also I'm not really sure that all is right , but my tablet works, so i offered some info, for someone that might need it. Perhaps the setting can be adjusted more and still be ok, i don't know since i'm a ubuntu and linux beginner after all my life being a windows user.
The key is the HOW TO doesn't need to be perfect to begin with.  None of them are.  As long as you occasionally update it with what you've learned it'll be valuable to others.  Notice I've updated the post with the wizardpen.conf several times as I learn new stuff with Riffer, another Waltop user.  I'm hoping you'll test it out and update yours with what you find useful.

I'd think Gimp would see the name of your tablet.  What does:
```
xinput --list
```
in a terminal show?

---

### Post by tudor117 on 2010-07-12
That's weird because for me, I have my actual tablet listed.
You sure there isn't anything else in the drop down menu?

---

### Post by Lunaea on 2010-08-17
Hello, first I want to say thank you so much for posting this. Anyway, I was on step four and I put  wizardpen-calibrate /dev/input/event6 into the terminal and event device open: Permission denied is what I got. I'm not sure what to do now. Any help is appreciated, thanks.

---

### Post by _jay_ on 2010-08-17
Thank you so much for this excellent how-to AlexDS! I've been fiddling with my Medion for 3 days now, and it works again! Woo woo!

---

### Post by _jay_ on 2010-08-18
gah, spoke too soon- works only for a bit then goes wonky... have to unplug then plug in to get it working again...  Actually works tip-wise until I click the button to pan, then it gets all messed up from there. any help would be appreciated!  *actually it seems as though the pen button is scrolling through different button functions- switches up functions in a seemingly random manner.

---

### Post by tudor117 on 2010-08-19
Hi guys,
For Lunaea's post, try running it with super-user privileges.
As for _jay_, is seems that it is still using the default driver from ubuntu. I don't remember how to remove it, but trying removing any wacom packages.
Good luck.

---

### Post by tudor117 on 2010-09-02
Does this method support hot-plugging?
As in plugging-in the tablet without rebooting, so that the configuration reloads.

---

### Post by Favux on 2010-09-02
Hi tudor117,

As long as the WizardPen driver is handling the Waltop tablet properly it should.  The udev/.conf file is the HAL/.fdi replacement.

---

### Post by tudor117 on 2010-09-02
Hi Favux,
So far, it hasn't seem to do so. I had a mistake in my conf but while hotplugging I got no error (safety feature maybe lol). However on a restart, the X server wouldn't start.

I still have a problem however, the tablet still freezes randomly after clicking. Also, in gimp, sometimes there are weird wavy lines where there should be a smooth straight one. It all happens randomly.

Here's xinput list:
```
~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Desktop® 2.10	id=9	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet  	id=10	[slave  pointer  (2)]
&#9116;   &#8627; X10 Wireless Technology Inc USB Receiver	id=11	[slave  pointer  (2)]
&#9116;   &#8627; HID 0a5c:4503                           	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Microsoft Microsoft Wireless Optical Desktop® 2.10	id=8	[slave  keyboard (3)]
    &#8627; HID 0a5c:4502                           	id=12	[slave  keyboard (3)]

```
Here's the conf file:
```

Section "InputClass"
	Identifier "wizardpen"
	MatchIsTablet "on" 
	MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|Waltop International Corp."	 #<----I added waltop from lsusb
	#MatchProduct "WALTOP"   #lsusb didn't show waltop as product but as vendor
	MatchDevicePath "/dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-event-mouse" #from ubuntu documentation
	Driver "wizardpen" 
#[CALIBRATION] 
		#Option		"Device"	"/dev/input/event5"
		#Option          "TopX"          "295"
		#Option          "TopY"          "210"
		#Option          "BottomX"       "20000"
		#Option          "BottomY"       "12500"
#[END CALIBRATION] 
EndSection

Section "InputClass" 
	Identifier "wizardpen ignore mouse dev" 
	MatchIsTablet "on" 
	MatchDevicePath "/dev/input/mouse*" 
	MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|Waltop International Corp." 
	#MatchProduct "WALTOP"
	MatchDevicePath "/dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-mouse"
	Driver "" 
EndSection

```
As you can see, I've removed the calibration because I didn't know what to put as the device. I don't like having a hardcoded path.

---

### Post by Favux on 2010-09-02
Try my modified wizardpen.conf for the Waltop in post #5.

---

### Post by tudor117 on 2010-09-02
Thanks alot, it works much better, as in the cursor doesn't freeze up and all the lines in gimp are smooth.
But there's something very weird; the buttons randomly switch. Sometimes, the click or stylus tip just stops working and the other two buttons (which are now distinct buttons) randomly switch roles. So if one is the top is right-click and the bottom is middle-click, they become inversed: top is middle-click and bottom is right-click.
I've tested it in gimp, blender, and on the ubuntu desktop.

Also in gimp, you can't use the mouse when using the tablet.

---

### Post by Favux on 2010-09-02
At least one other Waltop user has run into that too.  I don't think we fixed it.  I suggested he use:
```
xinput set-button-map "WizardPen Tablet" 1 3 2
```
or one of the variations at the [WizardPen Commnuity wiki]("https://help.ubuntu.com/community/TabletSetupWizardpen").  In the "Configuring the buttons on the pen" at the "The second way" section.  Except of course for the Waltop it would be:
```
xinput set-button-map "WALTOP International Corp. Slim Tablet" 1 3 2
```
If a variation works can put it in a launcher or auto-start a script with it.

---

### Post by tudor117 on 2010-09-02
That didn't seem to do anything.
Xinput changed the button map but the same glitch happens
```
xinput get-button-map "WALTOP International Corp. Slim Tablet"
1 3 2 4 5 5 

```

---

### Post by Favux on 2010-09-02
OK, that's where I think we were before.  I'm not sure we want to be asking DrMO why his WizardPen driver doesn't work with a Waltop tablet's stylus buttons though.  ;)  Maybe something will come to us, if we're lucky.

---

### Post by sweena on 2010-09-08
hi,
i installed everything how is described in [the help]("https://help.ubuntu.com/community/TabletSetupWizardpen"). Everything worked fine, but suddenly the tablet stopped working and i can see anything in logs. it seems like the module doesn't exists, nothing appears when i type:
dmegs | grep wizardpen  -- tablet or waltop
cat /var/log/Xorg.0.log | grep "wizardpen"
lsmod | grep wizardpen

i've "xserver-xorg-input-wizardpen" installed 
it's weird, any ideas?

my xorg.conf:
```
cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "InputDevice"
    Identifier  "Tablet"
    Driver      "wizardpen"
    Option        "Name" "WALTOP International Corp. Slim Tablet"
    Option        "SendCoreEvents" "true"
    Option        "Device" "/dev/input/by-idusb-WALTOP_International_Corp._Slim_Tablet-event-mouse"
    Option        "TopX" "176"
    Option        "TopY" "261"
    Option        "BottomX" "10000"
    Option        "BottomY" "6000"
    Option        "TopZ" "10"
    Option        "BottomZ" "511"
EndSection

Section "Monitor"
    Identifier   "0-LVDS"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1366x768"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1024x768"
    Option        "TargetRefresh" "70"
    Option        "Position" "1366 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-LVDS" "0-LVDS"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   2966 2966
        Depth     24
    EndSubSection
EndSection

```

```

cat /usr/lib/X11/xorg.conf.d/70-wizardpen.conf 

Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-event-mouse"
##   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver "wizardpen"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/usb-WALTOP_International_Corp._Slim_Tablet-mouse"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
   Driver ""

```

---

### Post by sweena on 2010-09-09
[SOLVED] 
i don't exactly what i do to arrange the problem, after trying installing the driver and compiling,
i noticed that was a typo in xorg.conf, however i changed the input setup /dev/input/by-id/usb... to /dev/input/event6 (in my case)
now it's working perfectly,
i hope my mistake can help to someone ;)

---

### Post by sweena on 2010-11-01
There are interesting news for waltop chip tablets  in Ubuntu 10.10 Maverick Meerkat:
thanks Favux!
[http://ubuntuforums.org/showthread.php?p=9966110](http://ubuntuforums.org/showthread.php?p=9966110)

---

### Post by ginger5xm on 2010-11-07
Can someone adapt the information in this thread to doing the same for a Genius G-Pen F350 on Lucid ?

Thanks !!

---

### Post by EvilGavel on 2010-12-13
genius Gpen-F350 same problem, spend about 1 hour - nothing ((:popcorn:

---

### Post by Favux on 2010-12-13
Hi ginger5xm & EvilGavel,

Welcome to Ubuntu forums!

Do you know if your tablets are Waltops?  Post the output of:
```
xinput --list
```
in a terminal.

EvilGavel what release of Ubuntu are you using?

---

