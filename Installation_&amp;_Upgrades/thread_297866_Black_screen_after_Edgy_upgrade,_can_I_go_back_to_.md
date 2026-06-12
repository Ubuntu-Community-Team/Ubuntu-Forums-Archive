---
title: "Black screen after Edgy upgrade, can I go back to Dapper?"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by notnuforlong on 2006-11-11
I am stuck. Dapper was working fine (save for the wireless problem I was having), so I upgraded to Edgy and everything seemed to go smoothly until the first boot when the screen just went black after the new Ubuntu startup screen. 

Can I fix this or can I 'go back in time' and go back to Dapper? 

I am new to Ubuntu, very excited about it, but without being able to get online with Dapper and now this, It is hard to keep the ether levels high. 

Any advice on how to at least get it back up and running would be a great start and I promise I won't give up!!

---

### Post by bruenig on 2006-11-11
Going back to dapper is not an option, unless you want to fresh install with a dapper disc.

---

### Post by notnuforlong on 2006-11-12
Could I do a complete install of Edgy? (not that I want to go through that process again). The thing is I can't see anything on the screen in order to fix the problem. I can hear the greeting 'drums' and can log in by 'feel' but the video is missing.

---

### Post by bulldog on 2006-11-12
If you hit CTRL->ALT->F1 do you get a console?

If so try to type this```
sudo dpkg-reconfigure -phigh  xserver-xorg
```
If not try to boot in recovery mode and do the same command.

---

### Post by notnuforlong on 2006-11-12
ok That worked. I got a command screen, typed in your code, and got:

xserver-xorg postinst warning: overwriting possibly-customised configuration
     file; backup in /etc/X11/xorg.conf.20061112133239

Now what? That's all it does. Just shows me that.

Thanks for getting me a little closer bulldog.

---

### Post by notnuforlong on 2006-11-12
I tried typing in the "/etc/X11/..." code and got:

Permission denied

hmm.

---

### Post by DaveBorealis on 2006-11-12
> **notnuforlong said:**
> I tried typing in the "/etc/X11/..." code and got:

Permission denied

hmm.

sudo nano /etc/X11/xorg.conf

And use your password when prompted.

[edit] or yeah, when done changing the file, restart X by
```
sudo /etc/init.d/gmd restart
```
(or use kdm in place of gmd is you're not using Gnome)

Best regards,
Dave

---

### Post by notnuforlong on 2006-11-12
Well I got this edit screen up (with the GNU nano version, file name, and 'Modified' in the upper right with shortcuts at the bottom) but it's just blank. What do I type in there? 

Thanks for the quick responses

---

### Post by DaveBorealis on 2006-11-12
> **notnuforlong said:**
> but it's just blank.

Sounds like you have a typo in the path.  Cut and paste the following to open the file:

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by notnuforlong on 2006-11-12
Cool that worked, and I have scrolled down to my video card information. I presume that's what needs to be fixed right? 

Section "Device"
.............Identifier        "NVIDIA Corporation NV41 [Quadro FX Go1400]"
.............Driver            "nv"
.............BusID             "PCI:1:0:0"
EndSection

Section "Monitor"
............Identifier        "Generic Monitor"
............Option           "DPMS"
............HorizSync      28-84
............VertRefresh    42-60
EndSection

Section "Screen"
............Identifier         "Default Screen"
............Device             "NVIDIA Corporation NV41 [Quadro FX Go1400]"
............Monitor           "Generic Monitor"
DefaultDepth               16
SubSection   "Display"
.............Depth               1
.............Modes              "1680x1050"
EndSubSection



it goes on.. whew! If you need the rest I can type that in too...

---

### Post by bulldog on 2006-11-12
If you have installed a driver for you graphics you should change the driver from "nv" to "nvidia".

If you didn't install a driver yet ```
sudo apt-get install nvidia-glx nvidia-kernel-common
``` and
```
sudo nvidia-glx-config enable
```

---

### Post by DaveBorealis on 2006-11-12
> **notnuforlong said:**
> video card information. I presume that's what needs to be fixed right?
<SNIP>
Section "Monitor"
............Identifier        "Generic Monitor"
............Option           "DPMS"
............HorizSync      28-84
............VertRefresh    42-60
EndSection


It might also be a problem with 'HorizSync and VertRefresh. Get 'monitorname' and monitorrange':
```
sudo ddcprobe
```
The last lines gives something like:```

        monitorname: GATEWAY EV70
        monitorrange: 30-70, 50-120
```
For the above example, the '30-70' would be the HorizSync, and the '42-60' would be VertRefresh.  See if they match up to what's in xorg.conf.

Playing with these numbers (but keeping them within the specs of your monitor) might be the solution!

Dave

---

### Post by notnuforlong on 2006-11-12
I did the ddcprobe and it listed all the modes then it got to this:

edid:
edidfail

then prompt

---

### Post by DaveBorealis on 2006-11-12
> **notnuforlong said:**
> I did the ddcprobe and it listed all the modes then it got to this:

edid:
edidfail

then prompt

I wonder what's different in Edgy that this doesn't work.  Does anyone know of a replacement for /usr/sbin/ddcprobe?

Anyway, maybe you can get the info from your monitor's back or from the booklet that came with it (if you still have it).

---

### Post by notnuforlong on 2006-11-12
I still have the books for it. What info am I looking for? What's 'edid'?

---

### Post by notnuforlong on 2006-11-12
> **bulldog said:**
> 

If you didn't install a driver yet ```
sudo apt-get install nvidia-glx nvidia-kernel-common
``` and
```
sudo nvidia-glx-config enable
```

The laptop Ubuntu is installed on doesn't connect to the internet yet. After I figure this out I have to get the wireless card working with Ubuntu...

So when I tried these commands it said it couldn't connect to security.ubuntu.com...

---

### Post by DaveBorealis on 2006-11-12
> **notnuforlong said:**
> I still have the books for it. What info am I looking for? What's 'edid'?

The HorizSync and the VertRefresh...they might be listed as different terms, but it'll be something like horizontal sync and vertical refresh rate.  Then put those ranges into /etc/X11/xorg.conf as mentioned above.

---

### Post by notnuforlong on 2006-11-12
So I went back to Windows to see what the settings on my card are there but the only value for "refresh" is 60 hz

---

### Post by DaveBorealis on 2006-11-12
> **notnuforlong said:**
> So I went back to Windows to see what the settings on my card are there but the only value for "refresh" is 60 hz

I'm guessing that the 60 Hz is what the rate was set at.  So we know that's within the range.  Perhaps 'VertRefresh 60-60' will do for the time being?

In your monitor manual it should give something like this:
Timing ranges: horizontal = 30 - 70, vertical = 50 - 160

If not, you'll have to google your monitor to get the numbers.  Do you have an older monitor?  I've read that ddcprobe doesn't work on anyting before '97.

P.S.  Here's an interesting link for you: [http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

---

### Post by notnuforlong on 2006-11-12
It's actually a laptop. A Gateway M680 17". So I've been looking for monitor info on it, but nothing yet.

Still reading the link you just posted. Looks very thorough.

---

### Post by notnuforlong on 2006-11-13
Can i just look in Windows to see what the HorizSync and VertRefresh values are?

---

### Post by notnuforlong on 2006-11-20
I found another thread and changed the screen resolution under the default 16. Now I get brown and tan horiz dashes evenly spaced overr a black background. That's progress as far as I'm concerned, but it still isn't right. 

This is a laptop with a 17" LCD display. I wasn't able to find what the factory refresh rates are (called Gateway and they didn't know, just sent the specs for the computer). 

Do the dashes mean I'm getting close to resolving this? At least now I'm seeing something on the screen...

---

### Post by notnuforlong on 2006-12-05
ttt. Anybody?

---

