---
title: "Cannot Configure Xorg - number of created screens does not match number of...&quot;"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by SecretImbecile on 2013-05-01
Hi, I'm trying to get a ubuntu OS running on an old laptop I recently aqquired. After failing to run lubuntu out-of-the-box, I've reinstalled as a command-line OS, and have manually installed the DE and File Manager.

However, The computer freezes on a black screen when I try to run startX. When I try X - Configure, It gives me the following error:
[B][I]number of created screens does not match number of detected devices
[/I][/B]Which I assume has been my problem so far.

This is a windows 98 era device, and I assume the odd monitor specs are causing the issue. The monitor is a 16-colour 640x480 LCD. (It may be useful to note that TinyCoreLinux works well on the system)

Does anybody have an Idea of what I can do to make Xorg configure correctly?

[SIZE=1]_Full Specs_
Intel Celeron
186MB RAM
6 GB HDD with 3GB for Ubuntu Partition
640x480 16-colour (4 bit) LCD monitor[/SIZE]

---

### Post by TheFu on 2013-05-01
Manually edit the xorg.conf using information from **xrandr** and the monitor technical specifications?
I doubt the DPMS option will work, so you'll need to get the HorizSync and VertRefresh settings perfect.

The 186M of RAM is a little concerning.  Good call on installing a text xface to start. Have you considered using a pure WM environment, without a DE at all?  Something like fvwm?  A remember running that on a 4MB system - with 8MB, it screamed with speed.

Ah, the no-so-good old days.  For $180, you can build a comparatively powerful system using dual core Atom/AMD CPUs that use about 25W. If that is too much, a Raspberry Pi solution will be half that price.

Good luck!

---

### Post by SecretImbecile on 2013-05-01
I'm not familiar with editing X's config files, is there a link you can point me to for editing that (I could only find articles on 10.04 and earlier)

Also, I managed to get the test screen running correctly (the command escapes me but it ends with -retro), does that suggest it's just a problem with my script setup, or could there still be issues?

---

### Post by TheFu on 2013-05-01
xorg.conf has been around for 20+ yrs. Older articles are fine.  Most people would google for a working xorg.conf for the same monitor/GPU and use that, I suspect, especially for a laptop.  The main concerns would be getting the resolution correct and the other items I specified above correct. Google is your friend.

I don't recall any -retro option to any command I've seen and **apropos** doesn't find

---

### Post by SecretImbecile on 2013-05-01
I actually get an error when using xrandr
[I]
Can't open display
[/I]


EDIT: I've found an article which should help me with this

---

### Post by TheFu on 2013-05-01
Ah - that makes sense.  xrandr needs a running X/Server to query. If X won't start, then there's no server to ask.

Just be certain you don't "overdrive" the display. On old equipment, doing that could burn out the monitor beyond repair.  I destroyed a monitor around 1993 that way.

---

### Post by SecretImbecile on 2013-05-01
I can't seem to change to another virtual terminal after starting X, do you have any idea what I'm doing wrong or how I should be doing it?
(I'm logging off for tonight, many thanks for your help so far :))

---

### Post by TheFu on 2013-05-02
Do other terminals work if X/Windows is running?  We are talking about <alt>-F1, <alt>-F2 ... F3, F4  ... right?  Those don't work with X/Windows.
To kill the X/Server process, I use <cntl><alt>BACKSPACE, but that is a local override.  I can't remember what the new default is.  I got used to CA-BackS and when it was changed about 4 yrs ago, I manually changed it back to the default I've known for 20+ years.

Sorry, can't really help.

---

### Post by MAFoElffen on 2013-05-02
First off... from a commandline sys... install package hwinfo
```

sudo apt-get install hwinfo

```
Then do
```

sudo hwinfo --framebuffer
sudo hwinfo --monitor
lspci -vnn | grep -i VGA

```
Post all that info. Also post the make and model of your old Monitor.

Here's what goes on from all that- Your old monitor, that you say only supports 640x480 us probably too old to contain internal EDID data... So before you create an xorg.conf file for your system, you need to know what modes the monitor supports and the modes your video card supports at a certain scan rates... To create modelines to place in the xorg.conf file to recreate that missing data. Dependng on the video card, that configuration file can also point to the pertinent video driver.

If you really want to do that yourself, go to the 2nd post in my Graphics Resolution sticky (link in my sig line) and look for the modeline tutorial links... Or I can just create it all for you from the info you post.

---

### Post by MAFoElffen on 2013-05-02
> **TheFu said:**
> To other terminals work if X/Windows is running?  We are talking about <alt>-F1, <alt>-F2 ... F3, F4  ... right?  Those don't work with X/Windows.
To kill the X/Server process, I use <cntl><alt>BACKSPACE, but that is a local override.  I can't remember what the new default is.  I got used to that and when it was changed 4 yrs ago, I manually changed it back to the default I knew for 20+ years.

Sorry, can't really help.
Just FYI--

I think I remember <Cntrl><Alt><Backspace> keymapping being removed over 3 Ubuntu versions back... Now that is <Right-Alt><Print-Screen><K>. Yes... I still remap mine also. ***Cleaner method is to jump to a new tty session, loggin, then 
```

sudo service lightdm stop

```
Virtual tty terminals: TTY1=<Cntrl><Alt><F1>, TTY2=<Cntrl><Alt><F2>... (etc.) are a normal process provided by Linux kernel and their (now) graphical display is VGA palette, independent of XServer.. They started using that graphical display of those TTY sessions back with 11.04 and Grub2 1.99rc1... Their display characteristics are set via /etc/default/grub and SetPaletteRGB().

---

### Post by SecretImbecile on 2013-05-04
--framebuffer
```
> hal.1: read hal dataprocess 3680: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_ls_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhai.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
```

--monitor
```
hal.1: read hal dataprocess 3687: arguments to dbus_move_error() were incorrect, assertion "dest_ == NULL || !dbus_error_ls_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhai.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
19: None 00.0: 10000 Monitor
  [Created at fb.71]
  Unique ID: rdCR.EY_qmtb9YY0
  Hardware Class: monitor
  Model: "Generic Monitor"
  Vendor: "Generic"
  Device: "Monitor"
  Resolutio: 800x600@75Hz
  Driver Info #0:
    Max Resolution: 800x600
    Vert. Sync Range 50-90Hz
    Hor. Sync Range 31-48 kHz
  Config Status cfg=new, avail=yes, need=no, active=unknown
```

lspci -vnn | grep -i VGA
```
01:00.0 VGA compatible controller [0300]: Trident Microsystems CyberBlade i1 [1023:8520] (rev 6a) (prog-if 00 [VGA controller])
```

Thanks for the assistance.

---

### Post by MAFoElffen on 2013-05-04
Here you go. 
```

# trident-xconfig: X configuration file modified by MAFoElffen 2013.05.04


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection


Section "Files"
EndSection


Section "InputDevice"


    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


Section "InputDevice"


    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Generic"
    ModelName      "Generic Monitor"
    HorizSync       31.0 - 48.0
    VertRefresh     50.0 - 90.0
    Modeline       "800x600_75"  48.91  800 840 920 1040  600 601 604 627  -hsync +vsync
    ModeLine       "640x480_60"   23.86 640 656 720  800 480 481 484 497 -hsync +vsync
    ## Valid Monitor Modes
    Option         "PreferredMode" "800x600_75"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "trident"
    VendorName     "Trident"
    BoardName      "CyberBlade i1"
    Option         "UseEDID" "False"
EndSection


Section "Screen"


    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option "metamodes" "800x600_75 +0+0; 640x480_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
Copy this to a text file named "xorg.conf". Save it somewhere in your home directory as a backup... for example in ~/Documents.

Then copy to /etc/X11/...
```

sudo cp ~/Documents/xorg.conf /etc/X11/xorg.conf

```
Reboot.

If, for some reason it doesn't like that modeline, (the just in case's) delete or rename the filename and reboot... you'll be back to square one.

---

### Post by SecretImbecile on 2013-05-05
I copied the conf file over to a new installation of Lubuntu 13.04 (I'm unfamiliar with manually setting up DE's so I just used a default lubuntu installation so the DE configuration wouldn't be the fault), However the screen was still blank after the lubuntu loading screen.

---

### Post by MAFoElffen on 2013-05-05
I should have taken a clue from prefix "all variants"... I assumed Ubuntu. Using Lubuntu and LXDE desktop... Here you go:
```

mv /home/jack/.config/lxpanel/Lubuntu/panels/panel /hpme/jack/Documents/panel.old
lxpanelctl restart

```
If the panel doesn't restart, logout the login.

---

### Post by SecretImbecile on 2013-05-05
I'm a little stuck here, and this is probably a bit of a newby mistake.

I've gone to root shell prompt from recovery mode to access the terminal, and get the following error when I try that command
*cannot stat '/root/.config/lxpanel/Lubuntu/panels/panel': No such file or directory*

---

### Post by SecretImbecile on 2013-05-05
I changed the user from root with su, and got the same error, but /home/jack/.config...

---

### Post by MAFoElffen on 2013-05-05
You need to do that as "you" so you hit the profiles in your home directory. "root" has no graphics or desktop profiles. Either that or use the full path to your home (ie" /home/jack/...

No? Sorry I corrected/edited  the above post with the correct command for you.

---

### Post by SecretImbecile on 2013-05-06
I tried that, but there is no .config folder (ls -a shows only .bashrc .bash_logout .profile)
and when I try the lxpanelctl command it gives *Can't connect to display: (null)*

---

### Post by MAFoElffen on 2013-05-06
root has no X privileges. You need to be logged in a you (a user). Describe how you are getting in.

---

### Post by SecretImbecile on 2013-05-07
I cannot seem to open a virtual terminal from a normal boot at all, so I've been booting to a root terminal from recovery, and using su to change to my username.

---

### Post by MAFoElffen on 2013-05-08
What happens if you use these instructions to boot?
[http://ubuntuforums.org/showthread.php?t=1743535&page=72&p=11383888#post11383888](http://ubuntuforums.org/showthread.php?t=1743535&page=72&p=11383888#post11383888)

---

### Post by SecretImbecile on 2013-05-08
it ends up with a root terminal, most of the text seems normal, but the last line reads

[36.453955] via686a 0000:00:07.4: base address not set - upgrade BIOS or use force_addr=0xaddr

---

