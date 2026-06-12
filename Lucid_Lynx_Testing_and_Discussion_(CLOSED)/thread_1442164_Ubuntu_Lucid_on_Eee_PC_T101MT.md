---
title: "Ubuntu Lucid on Eee PC T101MT"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Plippo on 2010-03-29
**As this thread has been locked due to the release of Lucid Lynx, I've created a new one here: [http://ubuntuforums.org/showthread.php?p=9210836](http://ubuntuforums.org/showthread.php?p=9210836)**
--------
 [COLOR=Red]**THE INSTRUCTIONS IN THIS POST ARE OUTDATED, PLEASE LOOK AT THE FIRST POST OF THE NEW THREAD LINKED ABOVE.**[/COLOR]

Hi everyone,

since I bought the brand new Eee PC T101MT touch screen netbook-tablet-hybrid (a truly magical device ;) ) a few days ago and installed Ubuntu Lucid Beta on it, I'd like to give you a little how-to about what you need to do to make it run almost perfectly on this amazing little computer.

Almost everything works out-of-the-box, only the touch screen needs a little work. It's almost nothing you need to do, but to find it out I had to search and try things out for quite a long time, so I thought I could share my experiences with you so you don't have to do this work again.

**WARNING:** All of this information here is about Ubuntu Lucid Lynx, which is still beta (but already works great). **It will not work for earlier versions!**

So, first of all the good news. **What works perfectly out-of-the-box:** Graphics with acceleration (compiz is really smooth), touch pad, Ethernet, Wifi, Bluetooth, USB, screen brightness control, sound output (speakers and headphones, speakers are switched off automatically when you use headphones), internal mic, card reader, display of battery status, suspend-to-RAM, suspend-to-disk, some hotkeys (Fn+F1 - suspend, Fn+F5/F6 - brightness, Fn+F6 - screen off), webcam (although with mine, the image was top-down, but you can rotate this in most webcam software).

**What I haven't tested yet:** VGA out (but xrandr shows the port, so it should work), microphone port.

**What doesn't work (yet):** Some hotkeys (Fn+F2, Fn+F3, Fn+F7-F12, Fn+Space), Multi-touch

**What works with really little effort: **Touch screen (no multi-touch).
[B]
To make your touch screen work:[/B] download this package: [http://www.philmerk.de/dwl/deb/eeepc-t101mt-touchscreen_0.6.1-1_i386.deb](http://www.philmerk.de/dwl/deb/eeepc-t101mt-touchscreen_0.6.1-1_i386.deb), double click on it and install it. After this, you should be immediately able to use your touch screen, though it's probably not accurate. So run the calibration utility from System > Administration and everything should work.

*(Explanation: To get the touch screen going, you simply need to make the kernel load  the module "usbhid" with the options "quirks=0x0eef:0x480d:0x0040".  That's all. But to calibrate the screen, there is some more effort  necessary. There is a program available for this, but this doesn't work  correctly with this screen so I modified it to make it work and to make  its use a little bit more convenient. So I've created a .deb package to load the module with the options on boot and  install the calibration utility. It will make the module load with the  correct options, install the calibrator and put an icon "touch screen calibration" into your  System > Administration menu.)*

If it doesn't work (probably because I've forgotten some package requirements), just write me here. Also if you have some ideas about the Fn keys (they don't send any ACPI event or key code), let me know. Or if you have a multitouch driver, of course :-)

Sources: The calibration program is based on this one: [http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator) - the source code for my modified version is here: [http://www.philmerk.de/dwl/deb/egalax-calibrator.tar.gz](http://www.philmerk.de/dwl/deb/egalax-calibrator.tar.gz)

---

### Post by HHGAG on 2010-03-30
Thnx for share, it's working fine. I've found a blueprint: [https://wiki.kubuntu.org/X/Blueprints/Multitouch](https://wiki.kubuntu.org/X/Blueprints/Multitouch) which should enable multitouch capability. T91MT is listed there.

---

### Post by Plippo on 2010-03-30
Thank you for the link, I didn't know this blueprint. I knew that there are some Multitouch drivers already in the kernel, but unfortunately I wasn't able to boot 2.6.34 on my machine. There doesn't seem to be a multitouch driver for the eGalax touchscreen of the T101MT yet (it's different from the T91MT's). But I'll try to build the existing drivers against the Lucid kernel, like described in [http://www.lii-enac.fr/en/projects/shareit/linux-howto.html](http://www.lii-enac.fr/en/projects/shareit/linux-howto.html) - maybe one of them also works with this screen if you force it.

---

### Post by HHGAG on 2010-03-30
i've found some more informations on heise: [http://www.heise.de/newsticker/meldung/Linux-lernt-Multitouch-181702.html](http://www.heise.de/newsticker/meldung/Linux-lernt-Multitouch-181702.html)
and a video with multitouch support for compiz [http://www.lii-enac.fr/en/projects/shareit/linux.html](http://www.lii-enac.fr/en/projects/shareit/linux.html)

eGalax is also supported: [http://www.lii-enac.fr/en/projects/shareit/multitouch-devices.html](http://www.lii-enac.fr/en/projects/shareit/multitouch-devices.html)

Here is a x.org howto: [http://www.lii-enac.fr/en/projects/shareit/xorg-howto.html](http://www.lii-enac.fr/en/projects/shareit/xorg-howto.html)

---

### Post by Plippo on 2010-03-30
Well, eGalax is not really supported. The page only says that they produce multitouch screens, but there is no driver support yet.

Unfortunately I wasn't able to compile any kernel module from the ENAC homepage, I'll look into this another time.

What I managed is to check the raw data that the driver sends (into /dev/hidraw0), and I found out how it works, it's a really simple protocol. So I wrote a very simple program in Java that reads the raw values from the device as they come from /dev/hidraw0 (I don't know how raw this data really is, but at least it contains the multitouch information!) and displays the positions of both fingers on screen. I also wrote a very simple algorithm that seperates the data into two fingers, and it works better than I thought (if it works, you see one finger in blue and one finger in red on screen).

If you want to try it out, you have to install Java (sudo apt-get install default-jre), then download my program from here: [http://philmerk.de/dwl/deb/tstest.jar](http://philmerk.de/dwl/deb/tstest.jar) and save it to any folder.

Use the terminal and navigate into the folder where you saved the file, then first call
```
sudo chmod a+r /dev/hidraw0
```so the program can access the raw data from the device, then call
```
java -jar tstest.jar
``` to start the program. A window should pop up in which you can happily touch with two fingers and see the red and blue magic happen.

Of course this program isn't really useful, but it shows how it works. As soon as I find the time (and manage to compile the kernel modules), I'll send everything I found out to the people at ENAC and hopefully they can then produce a driver for the screen.

---

### Post by NCLI on 2010-03-31
Someone really needs to work on the touchscreen support in Linux. It's no problem for experienced users, sure, but we want to attract new users too.

---

### Post by mrspacklecrisp on 2010-04-01
I had fantastically difficult time installing Ubuntu on the T101MT. It was worth it. I really didn't want an OS that would actually throw away access to my boot menu. Lucid seems alright so far, *however...* When I try to install that touchscreen package I get the error "Wrong Architecture 'i386' ". Being a little inexperienced, I am kind of at a loss.

---

### Post by mrspacklecrisp on 2010-04-02
> **mrspacklecrisp said:**
> I had fantastically difficult time installing Ubuntu on the T101MT. It was worth it. I really didn't want an OS that would actually throw away access to my boot menu. Lucid seems alright so far, however... When I try to install that touchscreen package I get the error "Wrong Architecture 'i386' ". Being a little inexperienced, I am kind of at a loss.

Ah, well, I've found a major issue- Can't find the module "usbhid". Need some help here, please.

---

### Post by dtw on 2010-04-02
Thx for sharing your experience.

In a german preview video of this Netvertible, I've seen that I can write with the pen and having the hand on the screen at the same time. Is this working on ubuntu?

Thats the video (14:50): [http://www.youtube.com/watch?v=gBChnhE8SZU&feature=player_embedded](http://www.youtube.com/watch?v=gBChnhE8SZU&feature=player_embedded)

---

### Post by mrspacklecrisp on 2010-04-02
> **mrspacklecrisp said:**
> Ah, well, I've found a major issue- Can't find the module "usbhid". Need some help here, please.I now have the touchscreen working beautifully, after following this: [http://ubuntuforums.org/showthread.php?t=1412582](http://ubuntuforums.org/showthread.php?t=1412582)

I had to deviate from these instructions slightly by putting this in terminal, because the touchscreen calibration tool doesn't show up in system-->administration like it's supposed to.
```
eGalaxTouch
```

My only issues now are getting pressure sensitivity to work and eliminating that annoying lag that happens when writing/drawing. Wouldn't that be a dream in GIMP? Just like a fancy expensive wacom tablet?

---

### Post by Plippo on 2010-04-04
**@mrspacklecrisp** You are using the proprietary driver for the touchscreen which has this bad lag, I also experienced this. With my solution, the built-in driver from Linux is used so there is no lag and GIMP works smoothly.

The "wrong architecture" bug indicates that you have maybe installed the 64 bit version of Ubuntu? That could also explain the problems you had during installation. I used the 32 bit one and everything went smoothly.

I don't think that pressure sensitivity is possible with this kind of touchscreen.
[B]
@dtw[/B] The palm detection (which is what is shown in your video) doesn't work in Linux yet, for this we would first need a multitouch driver. I managed to set up a build environment for the ENAC drivers, but none of the existing ones don't work with our screen, but I'll write to Stéphane Chatty from ENAC after the holidays and ask him if he can help with the driver.

---

### Post by HHGAG on 2010-04-04
I've got trouble with right click. As far as I know it should be activated by clicking 3 seconds on same place

---

### Post by Plippo on 2010-04-04
Yes, right clicking doesn't work with the evdev driver that comes with ubuntu. To get it, you could use the proprietary driver like mrspacklecrisp describes, but it has a terrible lag - after some time, all your input is only recognized with a heavy delay.

---

### Post by HHGAG on 2010-04-04
thnx for info. I'm using cellwriter and the menu button at the moment

---

### Post by mrspacklecrisp on 2010-04-04
The screen is a resistive one, which is specifically responsive to pressure. The asus product page describes this machine as having 256 levels of pressure: [http://www.asus.com/product.aspx?P_ID=xK9O0XZhFswxrTrn](http://www.asus.com/product.aspx?P_ID=xK9O0XZhFswxrTrn)

....Not totally sure, but I think this stuff in my /boot/config-2.6.31-20 means I have 32-bit. I could be entirely wrong, however.

An important-looking chunk:
```
#
# CONFIG_64BIT is not set
CONFIG_X86_32=y
# CONFIG_X86_64 is not set
CONFIG_X86=y
CONFIG_OUTPUT_FORMAT="elf32-i386"
CONFIG_ARCH_DEFCONFIG="arch/x86/configs/i386_defconfig"
CONFIG_GENERIC_TIME=y
CONFIG_GENERIC_CMOS_UPDATE=y
```

Appears as though you can use the evtouch driver in place of egalax's driver (Which may be a lot better, because I think egalax's drivers are like six years old). kgingeri got it working on the T91MT ([http://ubuntuforums.org/archive/index.php/t-1237709.html](http://ubuntuforums.org/archive/index.php/t-1237709.html)) and mentions that it's "pressure sensitive", but I'm not sure he had the same meaning as I do. Some T91 fixes might be worth looking into, or even eee fixes in general.

I've found that the brightness keys change this setting randomly, and that the microphone is also failing. There's also an issue with getting the rotate button to work- If someone could find the correct value to put into here: /etc/acpi/events/asus-rotate and figure out how to dissociate that button with the screensaver, it would work perfectly. On the T91, it's 0000007b, but that didn't work for me. And the brightness keys and rotate button aren't recognized by xev, so I've got nothin'.

---

### Post by mrspacklecrisp on 2010-04-04
I reinstalled Ubuntu. For whatever reason, your install worked this time, but I have the same complaints-there's a lag and there's no pressure sensitivity.

Perhaps this computer uses a wacom chip, like some other Asus tablet computers.

---

### Post by cprofitt on 2010-04-04
I know that it required special software according to the descriptions -- and the screen was supposedly not multi-touch w/ gestures, just the touchpad. I have seen too many conflicting articles to know what the real story is.. and the Asus US site does not have the model yet.

---

### Post by mrspacklecrisp on 2010-04-05
Earlier, when I used eGalax's drivers, I could put two fingers on the screen and a second cursor would appear. More fingers didn't do anything, but that's pretty promising. Mike at netbooklive.com used multitouch on the screen itself, too. 

I'm pretty upset over this lack of pressure sensitivity, though. It sounds like an issue with the way the driver itself is written, and that's way out of my league. Anyone think that this could be solved through xorg.conf?

---

### Post by Plippo on 2010-04-05
I now found the information about pressure sensitivity on the ASUS home page, that would be really great if we could get this to work in Linux.

The screen definitely has dual-touch functionality, so you can use it with up to two fingers. In the pre-installed Windows, things like zooming and rotating pictures with two fingers on the screen work. As I'm not using Windows normally, I did not test yet if pressure sensitivity works there, too, but as it can distinguish your palm from the stylus, I guess it does. So it should also possible to use it in Linux, as soon as there is a correct driver for this screen.

This is what we have at the moment: The touchscreen is recognized by the Linux kernel as a HID device, and if you give it some hints (which are added with my package), it can map the input events to the correct axes and make single touch work. For X, we have three possible drivers: Evdev, which works well but has no extended features like tap-and-hold for right clicks. Evtouch, which should also work after you have installed my package but I have not tested yet because it is quite old. And the eGalax driver which has tons of features and a nice settings application but is slow.

This is how I understand the things that are still missing: Due to the fact that the kernel driver only sends normal single touch events to the X drivers, we have at the moment no multitouch and no pressure sensitivity. For this, a special kernel driver is needed which transforms the HID data sent by the device into the correct Linux input events. When this driver works, it should be able to use pressure sensitivity without further work in applications like GIMP and Inkscape. Multitouch events would also be produced, but at the moment X is not yet ready to process them. But you could also add some emulation into the kernel driver which e.g. can emulate two-finger scrolling or palm detection by manipulating the events it emits to the upper layers.

I'll write to Stéphane Chatty from ENAC today, he has already created kernel drivers with multitouch support for other touchscreens and hopefully he can help to create a special driver for our screen. As soon as this driver works, I'll look into how special features like pressure sensitivity or palm detection can be built in. And then we should have really cool support for this screen under Linux.

---

### Post by Plippo on 2010-04-05
Good news! Stéphane, the creator of many other multitouch drivers for Linux, kindly offered to create a driver for the T101MT. He'll send me a debugging driver with which I have to do some tests (as he doesn't have the netbook himself) and then he thinks he'll be able to create a working driver.

Of course, this doesn't mean that we will immediately be able to use multitouch gestures in applications as multitouch support in Linux is quite new, but it should not be too difficult to write a helper application that recognizes multitouch gestures and sends keypress or mouse wheel events to the running application (like turning a zoom gesture into Ctrl + which zooms in documents or webpages or turning a two finger scroll gesture into a scroll wheel event to scroll your document -- I guess that's how Windows also does it). And of course, the cool Compiz effects you see in the video from the ENAC homepage would be possible.

And if we get pressure sensitivity working, I'm pretty sure palm detection should be easy to implement so you can use the stylus to write while resting your hand on the screen.

So be patient, good things are coming :-) And thanks again to Stéphane for his support.

---

### Post by André Schnabel on 2010-04-09
Thanks Plippo. Your quirks parameter and patched calibration tool works well on my t101mt with Lucid 64bit, after compiling the calibration tool from source. Unfortunately when rotating the screen in display settings, the touchscreen doesn't work correctly anymore. Even after calibrating it again. :-/

---

### Post by StCh on 2010-04-10
Hi,

with the help of Plippo I was able to write a multitouch kernel driver for the eGalax panel, and I submitted it today for inclusion in the mainstream kernel. I also notified the Canonical team, hoping that they will be able to include the driver in their kernel. Cross your fingers :-)

In any case, there should be good news for multitouch users in Lucid, because the Canonical team is definitely spending efforts on supporting it as well as possible. If the driver is not included, it should be easy to add it.

Actually, there is a small bug remaining in the single touch emulation (when using two fingers, the cursor sometimes jumps from one to the other), but because the Lucid team is planning to freeze their kernel soon I decided to submit the driver as is and work on the bug later.

---

### Post by mrspacklecrisp on 2010-04-11
Fix for the microphone: [http://setupguides.blogspot.com/2009/12/fixing-asus-t91-microphone-on-ubuntu.html](http://setupguides.blogspot.com/2009/12/fixing-asus-t91-microphone-on-ubuntu.html)

---

### Post by mrspacklecrisp on 2010-04-11
Wonderful news on the multitouch front. Soon we can implement pressure sensitivity, too!

---

### Post by Plippo on 2010-04-11
StCh's driver also provides pressure sensitivity, so it will be available as soon as the driver is in the kernel. Just use "6" for the pressure axis in GIMP's or Inkscape's input device settings and it works. I really hope the Ubuntu team includes the driver in the kernel, that would be great. As soon as it is available, I'll also try to add a patch the calibration utility as it doesn't work any more after recent changes to X in Lucid.

---

### Post by Plippo on 2010-04-11
The problem about screen rotation is that the evdev driver doesn't respect the orientation of the screen. So you have to rotate the screen and the touchscreen to get both working in the same way. I've written a little script that does both. The script and the instructions how to use it are now in this post: [http://ubuntuforums.org/showpost.php?p=9210836&postcount=1](http://ubuntuforums.org/showpost.php?p=9210836&postcount=1)

---

### Post by André Schnabel on 2010-04-11
Thanks Plippo. Your script works great on first try. Parameters are EXACTLY the same on my T101MT. But of course checking that beforehand was not a bad idea, just to make sure. Can't wait for the new multitouch driver with pressure sensitivity to be delivered by a kernel-update sometime soon. Also it would be great if there would be a way to get right click done in Gnome by just pressing the stylus/finger/left-mouse-button for some seconds.

Anyway, when the new driver is there, I have to remove the xserver-xorg-input-evtouch package, "update-rc.d usbhid-t101mt-fix remove" before and then everything is fine?

---

### Post by Plippo on 2010-04-11
Exactly, removing the quirk and removing evtouch (which seems to be broken) is all you need to do, except that you have to calibrate again as in multitouch mode the screen sends different coordinates. For that you can use my calibrator or the original calibrator from tias, but the problem is that due to recent changes in X in Lucid, the calibration will not be restored after reboot.

I hope that until then, I will have been able to modify the calibrator to save the settings to the new place, as a file in xorg.conf.d (at the moment this doesn't work because Ubuntu doesn't yet provide any default rules there, so if you add one, all other input devices stop to work).

Oh, and you'll probably also have to change the inputdevice parameter of the rotation script from 11 to 10.

If the Ubuntu people decide against adding the driver to the kernel, I'll have to create a package with the driver or we'll have to ask the people that maintain the Ubuntu multitouch PPA to add it.

---

### Post by StCh on 2010-04-11
Andy tells me he picked all the drivers that were in 2.6.34-rc3, that is 3M, MosArt (T91MT), Quanta (a few machines), Stantum and N-trig. I told him about the new driver (which, btw, is now in Jiri Kosina's for-next queue), let's cross fingers.

I will also try to convince Canonical to build HID support as a module, that should help in the future for adding new multitouch devices to the kernel.

Plippo, please report all your wishes about -evdev to Benjamin, he might be able to take them into account. I'm also trying to convince another colleague to improve the panel-to-display mapping in -evdev.

---

### Post by André Schnabel on 2010-04-12
Btw does anyone know if there's a way to increase the display brightness in Ubuntu to something that is brighter than what the Gnome-panel and keyboard shortcuts allow? Because in my opinion the screen is a bit darker with Ubuntu compared to Windows 7. Maybe there's a low level way to do that, like eeectl. I don't know. Also am I the only one with that problem or is it widespread on T101MTs running Lucid?

---

### Post by Plippo on 2010-04-12
André, I'm not sure about the brightness issue. I also thought that in Ubuntu the screen is darker, but I couldn't confirm it. But there is one thing I suspect (but I haven't tested it): Maybe you can only raise the brightness to the level to which it was set the last time in Windows. I believe I once reduced the brightness when testing Win7 and later couldn't make the screen any brighter in Ubuntu. But again, it's just a guess.

---

### Post by mrspacklecrisp on 2010-04-12
I'm able to make mine just as bright, it's just that the brightness levels are out of order... Meaning I was wrong earlier, and the brightness fn keys work fine, it's just a problem with the driver. They would work correctly I think if the driver was sorted out.

---

### Post by Plippo on 2010-04-13
Yes, I now also tried it out and it seems brightness in Linux is completely independent from the setting in Windows. So it was just my imagination I think...

---

### Post by nsicad on 2010-04-13
I would like to know the technical specification of t101mt. I am particularly interested of the chip set of the wireless pci-e card, who makes this wifi card. I know it is 802.11n. And also the LAN chip set.

However, it would be good if somebody can post the whole specs of this device.

Please do:

/sbin/lspci

/sbin/lsusb

Post the resuts please.

Thanks.

---

### Post by André Schnabel on 2010-04-14
Here we go, lspci dump:```

00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

And lsusb dump:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0eef:480d D-WAV Scientific Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5111 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Hangman228 on 2010-04-15
Plippo, I tried your script to rotate the screen and get touch calibrate working. But I had notice that the computer is slow when it's inverted. Do you know why ?
Edit : In fact it's same if I use the integrated rotate in ubuntu... So it's a problem with ubuntu

---

### Post by Hangman228 on 2010-04-16
Hi, 
For the upside down webcam, Hans De Goede made us a new libv4l.
You can download it  [here]("http://people.fedoraproject.org/~jwrdegoede/v4l-utils-0.7.92-test.tar.gz")
To install it :
tar xvfz v4l-utils-0.7.92-test.tar.gz
cd v4l-utils-0.7.92-test
make PREFIX=/usr
sudo make install PREFIX=/usr

And you'll be on earth !

---

### Post by penguininja on 2010-04-16
Thanks everyone for the instructions here, my T101 is running great with Lucid, including the touchscreen with Plippo's screen rotate script. (The setup was much faster than I expected!)

Has anyone had any luck with the volume function keys?  Or with mapping the function keys?  I tried using the keyboard shortcuts dialog, but it didn't recognize the Fn+F10-12 keys.  I also tried grabbing the function key events with xev, but the output was so large I couldn't tell which ones were the Fn keys!  I had vol mute/down/up mapped to F10/F11/F12, but that interferes with the F11 fullscreen hotkey on many applications.

Thanks again!

---

### Post by mrspacklecrisp on 2010-04-16
I've had a really bad day, and now my pen won't stay in the stylus bay. Any suggestions? Please?

---

### Post by mrspacklecrisp on 2010-04-18
Pressure sensitivity is nonexistent... Gimp, atleast, recognizes the capability, but it won't even allow the touchscreen to make marks. Rotating the screen makes at least xournal  act very strangely, and I see what you mean about the screen brightness. Lucid is pretty buggy anyway, even in this late stage. I want to downgrade to Karmic again.

---

### Post by Plippo on 2010-04-18
@Hangman228: The rotated screen being slow (and even if you rotate it back, it stays slower than normal) is the Intel graphics driver's fault, I don't know if there is a solution for this, but it doesn't only happen on the T101MT. And thank you for the tip with the webcam, I haven't tried it yet but it looks good!

@mrspacklecrisp: Of course pressure sensitivity doesn't work at the moment as StCh's driver hasn't landed in the kernel yet. It's unclear if this will haben for Lucid, as StCh wrote. If they don't add it, I'll have to package it myself (in the worst case a new package for every new Kernel version, but I'd then try to use DKMS to prevent that).

For the problem with the pen no longer staying in the bay, I have no idea, but at least it's not Ubuntu related :-) Maybe the magnet isn't strong enough any more?

@penguininja: I've had no luck with the Fn+F keys yet, it looks as if they aren't even recognized by xev. I've mapped the volume to Windows+F10/F11/F12 instead.

---

### Post by Plippo on 2010-04-27
As I doubt that the multitouch module will be built into the Lucid kernel, I've created a package that contains the pre-compiled module for kernel 2.6.32-21-generic (32 bit).

So if you like to test it, you can try the following:

[LIST]
[*]Update your Lucid system so it uses the 2.6.32.21 kernel
[*]If you have used my old package before, uninstall that one.
[/LIST]

[LIST]
[*]Install the new calibrator package you can download here: _[http://www.philmerk.de/dwl/deb/eeepc-t101mt-calibrator-0.0.2-1-i386.deb](http://www.philmerk.de/dwl/deb/eeepc-t101mt-calibrator-0.0.2-1-i386.deb)_[]("http://www.philmerk.de/dwl/deb/eeepc-t101mt-calibrator-0.0.1-1-i386.deb")
[/LIST]

[LIST]
[*]Install the kernel module package you can download here: [http://www.philmerk.de/dwl/deb/egalax-multitouch-driver-0.4-1-i386.deb](http://www.philmerk.de/dwl/deb/egalax-multitouch-driver-0.4-1-i386.deb)
[/LIST]

[LIST]
[*]Reboot
[/LIST]

[LIST]
[*]Calibrate the screen using the calibrator you find in your system menu
[/LIST]

You should now be able to use the new driver.

As the Linux multitouch stack isn't ready yet, you won't notice any difference, except that pressure sensitivity in GIMP should work if you go to GIMP's input device settings (Edit &#8250; Settings &#8250; Input devices &#8250; configure extended input devices), choose there »eGalax Inc. USB TouchController«, set the mode to »screen« (or display, I don't know how it's called in the english version) and set the »pressure« axis to 6. You should then be able to draw with different opacity depending on your pressure.

If you like, please test the driver and report if it works for you. Please notice that there are still some problems: If you suspend the Eee PC and power it on again, the touchscreen won't work. You should be able to fix this by opening a terminal and entering:
```
sudo rmmod hid-egalax
sudo modprobe hid-egalax
```Please also notice that after a kernel update, the driver won't work any more, so avoid updating to any kernel newer than 2.6.32.21 until I have created a new version of the package.

I hope it works for you as smoothly as it does for me!

Plippo

---

### Post by TH_ on 2010-04-27
Thanks for your commitment!

I've installed it, but it doesn't work. The record in my system menu references to "gksudo egalax-calibrator-x11", but the command doesn't exist. It seems to be egalax_calibrator_x11 (with underlines). I can start the calibration and the first three points will be captured correctly. But the calibration of the last point at bottom right is a infinite loop. I can abort but the calibration has no effect then.

System: Ubuntu 10.04 Netbook Edition
Kernel: Linux t101mt 2.6.32-21-generic
The old package worked perfectly.

---

### Post by Plippo on 2010-04-27
Hi TH_,
the first thing you mentioned was a problem with the calibration package, it created a shortcut to the wrong file. I uploaded a new version as soon as I found it out, but you have been faster :-) So if you download and install the calibration package again, it should work.

That the fourth point doesn't work is strange, that should not happen. Because the old driver and the new one send different coordinates, maybe the calibrator gets confused if you still have the old calibration applied. 

You can try to calibrate it manually by executing the command (without sudo)
```
xinput set-prop --type=int --format=32 10 "Evdev Axis Calibration" 411 32557 45 32517
```The values here are for my screen, so maybe your calibration is a bit off after executing the command, but at least you should be able to use the screen. If that works, you can try to start the calibration again. You can also try to start the calibration from the terminal with
```

sudo egalax_calibrator_x11

```and post the output.

Regards
Plippo

---

### Post by TH_ on 2010-04-27
The command for manual calibration works and then the calibration tool works, too. Thanks! :)

In Windows there are two modes: One for finger and one for pencil and you can switch between them. So you can write in pencil-mode and if you touch the screen with your hand, the cursor will stay at the position of the pencil. Is there any chance to get this feature in Linux? ;)

---

### Post by Plippo on 2010-04-27
Good that it works for you now!

Yes, it would be cool to have this pen mode also in Linux, but it seems that the distinction between palm and pen is not done in hardware but in the Windows driver, which has to guess a lot to make the distinction. I tried to modify the Linux driver to differentiate between them by pressure, but that didn't work well, I guess a more sophisticated algorithm would be needed. Maybe I find the time to do a few more tests.

---

### Post by mrspacklecrisp on 2010-04-28
Thanks for putting up this driver and doing so much to make it work.

It still doesn't have pressure sensitivity in GIMP or any other program, though. After restarting it won't even make marks on the canvas, and the input configuration lists it as one item instead of three.

---

### Post by Plippo on 2010-04-28
That it is listed as only one device instead of three is intended. Pressure sensitivity should work though, have you set pressure to axis "6"?

Maybe you also have to press a bit harder as the device has a threshold below which it always reports a pressure of 1.

---

### Post by lorenzoferrara on 2010-04-28
Hello, does anyone have low screen brightness issues?

cat /proc/acpi/video/VGA/LCDD/brightness gives me:

levels:  0 3 5 7 9 11 13 16 19 23 26 30 33 37 41 46
current: 46

46 is the max value available, but in Windows 7 the screen is much brighter.

Thanks!

---

### Post by mrspacklecrisp on 2010-04-28
It is set to 6 and I cannot make any line on the canvas, let alone one with variation. Xournal allows me to make lines, but they are not varied either. In both programs I have made sure pressure sensitivity is turned on. Mypaint has always ignored the touchscreen.

And yes, I think the screen did reach a brighter setting on windows 7. In Karmic I could get that maximum brightness (and sound up/down, and sound would automatically switch to headphones when they were plugged in) but in Lucid I think there is a discrepancy. I've been trying different things for a while now... I admit, I don't know much, but I think if it is possible and plausible to revert to Karmic drivers and settings, that'd be ideal. But, then, we'd have to be careful about it because the settings were limited (super bright, medium, really dark) and repeated in a random sequence in the brightness bar.

I've also discovered that although the computer recognizes the camera and the microphone I cannot take video. Videos display as a couple of frames a minute with zero sound. It fails to work in cheese, kamorama, skype, I think empathy, pidgin, and possibly some others I've forgotten.... I can, however, take pictures in cheese and record sound.

---

### Post by Plippo on 2010-04-29
In Xournal it also doesn't work for me as Xournal seems to always use axis 3 for pressure. But in GIMP it definitely should. In the input devices dialog, I have set the X axis to 1, Y to 2, Pressure to 6 and all other axes to »none« for the eGalax screen and its mode to »screen«.  Does it work (without pressure sensitivity) if you uncheck all boxes in the »Brush Dynamics« settings for the paintbrush tool?

It's interesting that screen setting and sound hotkeys worked in Karmic, there seems to be a regression in ACPI. I'll analyze that.

--------
**As this thread has been locked due to the release of Lucid Lynx, I've created a new one here: [http://ubuntuforums.org/showthread.php?p=9210836](http://ubuntuforums.org/showthread.php?p=9210836)**

---

### Post by Hangman228 on 2010-04-29
I can confirm, it works on gimp. The problem is that you have to touch the screen very low (I don't know the word in english...) to see the difference. It would be great if we can set more than 6 in pressure in gimp's setting.

---

