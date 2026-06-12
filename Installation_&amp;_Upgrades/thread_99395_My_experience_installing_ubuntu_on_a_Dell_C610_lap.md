---
title: "My experience installing ubuntu on a Dell C610 laptop"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by qiet72 on 2005-12-05
Hello!

Someone said in another forum that I should post my experiences with ubuntu during installation.  So here it is according to my installation on a Dell C610 Latitude laptop:

Keyboard:
-------------
During installation, don't try the autodetect option of the keyboard - I use a Danish keyboard and it screwed up the keyboard layout even after changing to the correct layout.  To fix this, choose the correct layout the first time without trying autodetect.

Multimedia keys:
----------------------
Some of the Fn-key combinations seem to work - sound adjustment keys work (gives an OSD at the same time) - brightness/contrast work and the CD eject Fn key combo worked too.  The OSD only works under gnome.

Video card:
---------------
If you have an ATI Mobility Radeon M6 LY card which is installed in laptops like the Dell c610 Latitude, then remember to switch the driver in xorg.conf from "ati" to "radeon" otherwise 3D accelleration will not work. The 3D accelleration also requires quite a bit of video memory so you may have to switch your color depth from 24 bit to 16 bit in xorg.conf. The solution took me 3 days to figure that out. The solution is so simple that it seemed ridiculous.

The video memory on the ATI Mobility Radeon M6 LY card was only 16MB.
If you enable 24bit display mode and 3d accelleration at the same time, then it will require about 17.5MB of video memory.  Accelleration seems to require at least 12 MB of video ram on this card (Check Xorg.0.log).  16bit (65536 colors) at 1400x1050 seems to require 2940000 bytes of video memory (1400x1050 / 8 * 16)  24 bit (16.7 million colors) at 1400x1050 seems to require 4410000 bytes of video memory (1400x1050 / 8 * 24).

Don't try the fglrx driver - very unstable and it will not work with the ATI Mobility Radeon M6 LY card!!!
I never got the fglrx driver to work on this laptop.  It seems the driver does not support the pci id of this card (1002:4c59), but you could try and force it to recognise it by use the ChipID parameter of xorg.conf.  If you do try the ChipID parameter, then you also need to tell the fglrx.ko module that too.  Unfortunately, I haven't found out a way to do that yet (probably requires recompiling the module from source).

Last but not least regarding video card issues: The installation automatically detected the optimal resolution of my tft display (1400x1050) - I have never seen that before in a linux distribution.  Usually I have to tweak xorg.conf/XF86Config-4 to get it right.  Another congrats to the developers on this!

Sound:
----------
I noticed a lot of people having problems with programs that use the OpenAL api for sound like Chromium. This is because OpenAL uses /dev/dsp directly which conflicts with the Enlightenment Sound Daemon (esd) which also uses /dev/dsp. The most elegant solution I have found is to create a file called ~/.openalrc and paste the following line into the file:

(define devices '(alsa esd native))

Save the file and it should work immediately without reboot or logout.

The line tells OpenAL to try and use alsa, then esd, then /dev/dsp for sound output. Reference to this information is here:

[http://ggo.sourceforge.net/manual/ar01s09.html](http://ggo.sourceforge.net/manual/ar01s09.html)

2005-12-4 Update: Pingus doesn't seem to give sound. The following makes the sound work but is not elegant:

As root type: echo "pingus 0 0 direct" >/proc/asound/card0/pcm0p/oss

2005-12-5 Update: dosbox and sometimes mplayer don't give sound either, again fixed by adding the executable name to /proc/asound/card0/pcm0p/oss

If anybody else knows a more elegant way than this, post.

Another fix for mplayer sound is to do a "sudo chmod 666 /dev/dsp".


CD Recording:
------------------
CD-ROM burning is really weird.  cdrecord has a very long delay (5 minutes or so) before beginning to write to a cd.  It may also be because a linux 2.6 kernel + cdrecord + USB 2.0 cardbus card + USB 2.0 burner don't work optimally.
cdrecord(ing) of audio CD's failed completely for me.

DVD:
-------
DVD playback works great when used together with version 1.2.8-1unofficialubuntu3 of libdvdcss2.  Don't use 1.2.9 - it does weird things in navigation and playback crashes at some point.
DMA was not enabled by default on my DVD drive which gives choppiness on DVD playback.  Quickly fixed by doing a "sudo hdparm -d1 /dev/hdc" or modifying /etc/hdparm.conf for a permanent fix.

Infrared:
-----------
Infrared has gotten a lot easier than when I first tried it 2 years ago.  Now you can just install the irda packages (use synaptic to find them) and use irobex_palm3 to send and receive files to obex devices such as my Nokia Communicator 9210 :-)
Best of all, you don't need to be root anymore to use irobex_palm3 - really cool.

USB support:
------------------
Plug and play of USB devices works like a dream - which is why I chose ubuntu in the first place!  I had tested a quite a few distributions and ubuntu seemed to be one of the very few where you can attach a usb key and use it right away without mounting/unmounting it as root.  A proper icon comes up on the desktop and dissapears again when the device is unplugged - the way usb is meant to be!

smb/windows shares:
----------------------------
Accessing samba/windows servers is ok, but gnome and kde do it in a way that some programs (like mplayer) can't find the files you click on.  A lot of console based applications like to work with files mounted directly on a file system like /mnt/media and not like smb://server/share/file.

There are a couple of gui's to handle mounting of samba/window shares, but none that I have found that can mount hidden shares (still has to be specified explicitly by command-like use "mount -t smbfs" or smbmount.)

Wireless:
------------
The wireless applet in gnome is really cool and looking nice.  I got my Buffalo wireless card (model wli-cb-54g) to work using ndiswrapper.
Install gkrellm and gkrellmwireless plugin to see link/noise/signal levels as well as what speed you are associated with (54/48/11 mbps, etc).

Update 2005-12-06: Also tested my Hawking Technology HWU54G Wireless-G USB Adapter (0ace:1211).  Kernel 2.6.12 had a driver already and loaded it right away - got my wlan0 interface, unfortunately, i could not get any further than this.  iwconfig reports no wireless extensions.  I haven't tried downloading the latest zd1211 source yet - will report back if i do.  Also tried it with ndiswrapper.  'ndiswrapper -i' was able to install the driver but could not load the driver using modprobe ndiswrapper.  Again, probably compiling ndiswrapper code could solve the problem, but i haven't tried it yet.

Fonts:
--------
Beautifull!!!  I could swear the fonts look even better than XP's cleartype.
Best of all - unicode support - now I can see all those Chinese/Japanese/Russian characters that come up when googling.  They used to be boxes with some number in them when I ran Slackware 9.1 (Slackware 10.2 still had that problem).

CPU/Laptop Cooling Fans:
---------------------------------
If you have a recent Dell computer, you can load the i8k modules and use the i8k utilities to control and monitor the two fans.  If you use gkrellm, then with the i8krellm plugin - you can control and monitor the fans directly using the gui.

Games:
-----------
Chromium - after fiddeling for 3 days getting my 3d accelleration working and fixing the OpenAL problem, Chromium is working perfectly now.
Pingus - sound issues - fixed using the /proc/asound/card0/pcm0p/oss fix.
Neverball - disable reflections and the game works properly.
planet-penguinracer - sound issues - see Pingus fix.

Emulators:
---------------
dosbox - sound issues - see Pingus.
qemu - download the source instead, including kqemu and compile, this gives you at least 10x more acceleration for emulation.

Hibernation:
----------------
At first I though that hibernation wasn't supported yet, so I started to try and patch the kernel with SoftwareSuspend 2.  It worked but not optimally - framebuffer graphics didn't work at all at the console level.

Then I discovered that kernel 2.6 and ubuntu already had native hibernation support using version 1 of SoftwareSuspend.  Tried it out and it worked perfectly - that taught me to try it out before fixing things.

Window Managers:
------------------------
Gnome and KDE can exist together.  After installing ubuntu, install the kdesktop package through synaptic and you can choose at logon which manager to use.

Interesting note, the very first time I installed ubuntu and installing kdestop, the ubuntu logo changed to the kubuntu logo during boot.  The second and third time I installed ubuntu, this didn't change but KDE worked like it should.

Printing (2005-12-06):
----------------------------
Worked out-of-the-box.  Just like in a windows environment - click on new printer, select correct driver and voila - it works.  I used the HP Officejet-7400 driver for my HP Officejet 7410 wireless printer.

Quinn

---

### Post by bwog on 2005-12-05
Excellent! This is very helpfull for users who search the forums (yes they do exist). Thanks qiet72.

There is a recent thread about installing several desktops and using them with sessions: [http://www.ubuntuforums.org/showthread.php?t=99356](http://www.ubuntuforums.org/showthread.php?t=99356) , but you probably know all that already.

---

### Post by geek.de.nz on 2006-04-24
Have you not had a problem with the touchpad at all? Because when I installed Breezy (5.10), my touchpad went wild (stuck in either right upper or left upper corner). So far, the only solution was to turn it off completely in the Bios. Any clous, comments? Btw, with kernel 2.4.x distros I do not have this problem.

---

### Post by geek.de.nz on 2006-04-28
[Solution]("http://ubuntuforums.org/showthread.php?p=964716#post964716")

---

### Post by AlphaMack on 2006-06-17
The Dell Inspiron 4100 also has the M6 LY.  Downgrading the config to 16-bit certainly helped with acceleration especially while playing Planet Penguin Racer.  At 24-bit it was very choppy.

---

