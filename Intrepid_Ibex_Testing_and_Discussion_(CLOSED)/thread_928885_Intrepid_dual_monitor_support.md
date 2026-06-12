---
title: "Intrepid dual monitor support"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xeddog on 2008-09-24
I have been reading about dual monitor support in Hardy and it seems like it has a long way to go before it is ready for prime time.  It is do-able, but takes a lot of tweaking and so forth to get it to work, and even at that there seems to be some trade-offs.  

I hate to bring up Windows, but they do some things well and multiple monitor support is one of those things.  The lack of simple and effective multiple monitor support in Linux is also ONE of the reasons that I still have to use XP.

So I was just wondering if there is going to be any improved support in Intrepid for multiple monitors. 

Thanks,

xeddog

---

### Post by dro0g on 2008-09-24
I'm using II and the dual monitor support is definitely improves vs. Hardy. That having been said, it's still not as automatic as I'd like (I'm using it on a laptop that's sometimes in a dock, sometimes by itself and sometimes using the internal screen and an external monitor)

For a desktop, the multi-monitor support seems pretty damn good. I haven't used it with the proprietary ATI or NVidia drivers though so I don't know if there are any caveats there.

---

### Post by xeddog on 2008-09-24
That's good to hear.  So now the question is, how do you implement it.  It isn't just a simple matter of connecting the second monitor because I tried that just to see what would happen.

Thanks.

xeddog

---

### Post by dro0g on 2008-09-24
In my case, I just had to hook it up, go to System -> Preference -> Screen Resolution and uncheck "Mirror Screens".

You can also do the same thing with xrandr on the command line. running "xrandr" with no switches should show you all the displays hooked up and the resolutions they support.

---

### Post by xeddog on 2008-09-24
Hmmmm.  I'm running the KDE 4.1 desktop so I need to find something like that.  Nothing I see regarding screen resolution gives me any options like you mention.  Myst be around someplace . . . . .

xeddog

---

### Post by xeddog on 2008-09-24
OK, I think I have it resolved.  I used Adept and installed the nvidia settings app.  That almost made it easy to set up dual monitors.  I have tried both the Twinview (where x thinks there is only one monitor attached), and Xinerama mode (where each monitor is considered a totally separate display).  Just a couple of things left to figure out and then actually use them to see which one I like better.

One of the things I need to figure out is this.  The two monitors I am using are from two different computers.  I just take the video cable loose from machine "A" and connect it to a cable extension running to the second video port on machine "B" (I am testing this on machine "B" running Intrepid/KDE).  I am trying to set it up so that the monitor attached directly to machine "B" is the primary monitor with the panels etc., but it ALWAYS goes to the monitor that was connected to machine A".  I have tried switching primary displays using the nvidia application, and even switched the cables on the video card itself, and it still insists on using the monitor from machine "A".  I suppose that wouldn't be so bad except for the fact that monitor "A" is on another desk and is behind me.

The other thing I need to figure out is how to move windows between displays when using Xinerama.  I hope this doesn't turn out to be a case where I have to direct the application to a specific display when launching and then am unable to move it to the other.  That would suck.  

But anyway, I'm having fun again.

xeddog






P.S.  If you do choose to install the nvidia-settings application, you cannot just simply run it from the menu.  You need to run it from a terminal as "sudo nvidia-settings".  Then it works.

---

### Post by nanog on 2008-09-24
nvidia-settings works fine from the menu for me.

---

### Post by RAOF on 2008-09-24
You probably want to be using TwinView rather than Xinerama.  Apart from the fact that the -177 drivers (*finally*) don't suck at dual head with dynamic TwinView, using Xinerama will disable any cool desktop effects you might want to enable.

---

### Post by xeddog on 2008-09-25
Desktop effects are not really an issue with me.  I have tried them and find most of them more of an annoyance than anything else.  But there are a couple of things I would like to keep.  

I still haven't figured out how to move application windows from one monitor to the other with Xinerama yet.  I haven't looked either because I have been doing other things.  If you can tell me how it is done you could save me some time looking for it.  :-)


Thanks,

xeddog

---

### Post by RAOF on 2008-09-25
> **xeddog said:**
> Desktop effects are not really an issue with me.  I have tried them and find most of them more of an annoyance than anything else.  But there are a couple of things I would like to keep.  

I still haven't figured out how to move application windows from one monitor to the other with Xinerama yet.  I haven't looked either because I have been doing other things.  If you can tell me how it is done you could save me some time looking for it.  :-)


Thanks,

xeddog

Using TwinView rather than Xinerama will make this Just Work.

---

### Post by lancest on 2008-09-26
Good news about .177 Nvidia driver doing 1024,800 twinview dynamically. My notebook doesn't get the correct EDD's from my work's projector. I've not been able to get Twinview at the right projector resolution since Feisty after it stopped working correctly, and I couldn't quite get the xorg Twinview settings correct. Has been torture -since I know alot of people did.

---

### Post by nanog on 2008-09-26
Dual head does work better on the typical monitor but EDID problems on projectors are still a *big* problem. Nvidia-settings does not allow you to manually set resolution when it gets a bogus EDID. (And yes twinview works when I manually edit my xorg to contain correct resolutions -- but who has time to do that with an audience waiting.)

To get the projector to work I typically shrink my laptop screen to 1024x768 and use fn F8 to clone. (At least this works in recent kernels.) Its just so DAPPER to still be doing this.

---

### Post by Josh04 on 2008-09-26
xrandr is excellent at solving dual display problems I have found. A simple

xrandr --output VGA --auto --right-of LVDS

puts the second monitor at the correct resolution to the right of my laptop monitor, with the laptop monitor unaffected. Run xrandr without any options to see the names you should be using instead of LVDS and VGA.

This is on the intel driver however, I'm assuming that xrandr works with the nvidia driver.

---

### Post by nanog on 2008-09-27
xrandr works fine if the edid parser reports the correct resolution. the problem is that linux either does not read edid 1.4 settings correctly or the manufacturer screws them up. this is especially true with lcd projectors. The inflexibility of plug and play in linux is a huge problem. i have no doubt that eventually this will be the way to go but like gvfs it is at the cost of basic functionality.

/rant off

---

### Post by RAOF on 2008-09-28
> **Josh04 said:**
> ...
This is on the intel driver however, I'm assuming that xrandr works with the nvidia driver.

Your assumption would be (annoyingly) incorrect.

---

### Post by lancest on 2008-09-28
Sorry to ask. Can some one give me a current Hardy xorg.conf for using Twinview? Asus notebook with Nvidia 7300. Yea I use nvidia-settings and can only get 640x480 dynamically on the projector.

---

### Post by RAOF on 2008-09-29
My current (Intrepid) xorg.conf:
```

Section "Device"

#       Option          "NoAccel"       "True"
    Identifier     "GeForce 7600Go"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "GeForce 7600Go"
    Monitor        "Inbuilt LCD"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    SubSection     "Display"
        Virtual     3000 2000
        Depth       24
    EndSubSection
EndSection

```

---

### Post by lancest on 2008-09-30
Thanks. I'm afraid to try Intrepid with my NVidia card again (yet), so will plug this into Hardy.

---

