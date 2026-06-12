---
title: "Synaptics Touchpad @ Jaunty = Not Scrolling"
date: 2009-01-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ValaV on 2009-01-17
This is my xorg.conf
Can anyone tell me if there is something wrong?
I'm using 2.6.28-4

Thanks in advance
```

Section "ServerFlags"
    #DontZap # disable  (server abort)
    Option  "DontZap" "off"
    AllowMouseOpenFail # allows the server to start up even if the mouse does not work
    #DontZoom # disable / (resolution switching)
    Option "IgnoreABI" "true" # Evita que el driver nVidia de por **** por viejo
EndSection

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Synaptics Touchpad"# "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
   Identifier "Synaptics Touchpad"
   Driver "synaptics"
   Option "SendCoreEvents" "true"
   Option "Device" "/dev/psaux"
   Option "Protocol" "auto-dev"
   Option "HorizScrollDelta" "0"
   Option "SHMConfig" "on"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

#Section "Extensions"
#    Option         "Composite" "Disable"
#EndSection

```

---

### Post by mc4100 on 2009-01-17
I had this issue too, when I upgraded; 
but it was simply fixed by unchecking and then rechecking the "Enable vertical scrolling" box in:
System -> Preferences -> Mouse, and then the "Touchpad" tab.

---

### Post by ValaV on 2009-01-17
I cannot do that, the version of "mouse" app that I've installed did not have this option.

Also, gsynaptic, raises a "SHMconfig and value true" error.

---

### Post by Mark V on 2009-02-26
You can find the setting at system>preferences>keyboard under the mouse keys tab.  Just click the setting 'pointer can be controlled using the keypad'
but this does not solve the problem for me.

---

### Post by vikrant82 on 2009-02-26
Same here, no vertical scrolling with synaptics. But there are already a few bugs open in Launchpad regarding this..

---

### Post by Vaun on 2009-02-26
Try the package in tseliot's PPA.  It fixed the issue for me that has been broken since I upgraded from Intrepid back in January.

[https://launchpad.net/~albertomilone/+archive/ppa]("https://launchpad.net/~albertomilone/+archive/ppa")

---

### Post by jfernyhough on 2009-02-26
Setting options for mouse in xorg.conf hasn't worked for me for a while. I eventually found how to do it now with the new auto-configuration X: HAL configuration files.

I created a file **/etc/hal/fdi/policy/11-x11-synaptics.fdi** with the following content:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="Synaptics TouchPad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
    <!-- Arbitrary options can be passed to the driver using 
         the input.x11_options property since xorg-server-1.5. -->
    <!-- EXAMPLE:
    -->
        <merge key="input.x11_options.AlwaysCore" type="string">true</merge>
        <merge key="input.x11_options.Protocol" type="string">auto-dev</merge>
        <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
        <merge key="input.x11_options.SHMConfig" type="string">true</merge>
        <merge key="input.x11_options.LeftEdge" type="string">1700</merge>
        <merge key="input.x11_options.RightEdge" type="string">5300</merge>
        <merge key="input.x11_options.TopEdge" type="string">1700</merge>
        <merge key="input.x11_options.BottomEdge" type="string">4200</merge>
        <merge key="input.x11_options.FingerLow" type="string">25</merge>
        <merge key="input.x11_options.FingerHigh" type="string">30</merge>
        <merge key="input.x11_options.MaxTapTime" type="string">180</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">true</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">true</merge>
        <merge key="input.x11_options.CornerCoasting" type="string">true</merge>
        <merge key="input.x11_options.CoastingSpeed" type="string">0.30</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">100</merge>
        <merge key="input.x11_options.HorizScrollDelta" type="string">100</merge>
        <merge key="input.x11_options.MinSpeed" type="string">0.10</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">0.60</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.0020</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">2</merge>
        <merge key="input.x11_options.TapButton3" type="string">3</merge>
      </match>
      <match key="info.product" contains="AlpsPS/2 ALPS">
      </match>
      <match key="info.product" contains="appletouch">
      </match>
      <match key="info.product" contains="bcm5974">
      </match>
    </match>
  </device>
</deviceinfo>
```
Found this on the Arch Linux forums - can't remember exactly where so sorry if the author reads this. :D

Annoyingly, though, it doesn't fix the fact I can't multi-finger tap on my touchpad... (though I'm just about to try with Alberto's driver).

---

### Post by scaine on 2009-02-28
> **Vaun said:**
> Try the package in tseliot's PPA.  It fixed the issue for me that has been broken since I upgraded from Intrepid back in January.

[https://launchpad.net/~albertomilone/+archive/ppa]("https://launchpad.net/%7Ealbertomilone/+archive/ppa")

Thanks Vaun.  Not sure if it was the PPA, or general updates, since I did both at the same time (stupid!), but I now have vertical scrolling on my synaptics again (Toshiba U400 laptop).  Funny how you take certain things for granted until they're missing...

---

### Post by vikrant82 on 2009-03-01
Well that PPA fixed vertical scrolling for me too.

---

### Post by Sand &amp; Mercury on 2009-03-01
I just realised after reading this thread that my touchpad isn't working at all. I'm not too bothered since I never use it, but still...

---

### Post by scaine on 2009-03-01
That's a bug in Alpha 4 - think it's fixed in Alpha5 though.

From :
[http://www.ubuntu.com/testing/jaunty/alpha4](http://www.ubuntu.com/testing/jaunty/alpha4)
> 
The X.Org synaptics driver is absent from the liveCD, which may prevent touchpad devices from working on laptops. As a workaround, use Ctrl+Alt+F1 to switch to console, log in, run sudo apt-get install xserver-xorg-input-all to download the drivers from the network, and then return to your session with Alt+F7.

---

### Post by Sand &amp; Mercury on 2009-03-01
^ That did the trick, thanks. Never even thought to look at the release notes... d'oh. Strike 2 for me.

---

### Post by pinklerose on 2009-03-28
I have Compal FL90. Scrolling works for me only when i use two fingers (anywhere) on touchpad. Horizontal scroll works bad.

---

### Post by scaine on 2009-03-28
Two fingers scrolling is how multi-touch scrolling works I think.  What do you mean by "scroll works bad"?

---

### Post by cyclist23 on 2009-03-29
Add one more to the list.

Vertical scrolling does not work for me also.  Whereas, others were able to get this fixed with the PPA update, it did nothing for me.  I enabled SMHConfig and turned off TwoVertScroll and it still did not work.

Please help!

Beside this issue, Jaunty Beta has been a blast.  Much has improved from Ibex.  I did not opt for Ibex and chose to stay with Hardy LPIA for my Dell Mini, because Dell did an excellent job with the customization.  But still, I was restricted from a few excellent softwares.  Ibex couldn't do it for me, really slow and laggy.  Jaunty has been excellent even with compiz on.

One more issue with Jaunty is I'm not able to get aircraft manager on it.  So I'm still waiting on that.  And I couldn't get X-Unikey to work with OpenOffice.

---

### Post by pinklerose on 2009-03-31
> **scaine said:**
> What do you mean by "scroll works bad"?

Sometimes is able to scroll left or right side but most of my tries fail.

---

### Post by scaine on 2009-03-31
Just yesterday I installed Jaunty on a friend's Acer Aspire One and couldn't get vertical scrolling to work, except once, by accident and I couldn't get it working again after that.  Very strange, since my Tosh U-400 still has perfect synaptics/vertical scrolling and all I did to get that working was add the PPA mentioned earlier.

Sorry, I have no idea about this, but I'll have a hunt on launchpad later in the week if updates haven't changed the situation on his Aspire One by then.

---

