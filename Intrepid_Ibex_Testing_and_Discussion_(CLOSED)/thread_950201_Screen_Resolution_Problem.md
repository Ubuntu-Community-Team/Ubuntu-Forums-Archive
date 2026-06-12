---
title: "Screen Resolution Problem"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Istonian on 2008-10-16
I just installed Ibex and it is not recognizing my native resolution. In Hardy I typed in displayconfig-gtk and changed it from there, but that option is no longer there for Ibex. Any ideas on how to get is to 1440x900? It's as 800x600 now. The monitor is an Acer 1916w widescreen LCD 19". Nvidia 7300 gs for graphics. Help is appreciated.

---

### Post by Istonian on 2008-10-17
bump

---

### Post by sdowney717 on 2008-10-17
did you run that nvidia-settings command?

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-t.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-t.html)

---

### Post by Istonian on 2008-10-17
I think I did, but I will try again.

---

### Post by davidw89 on 2008-10-17
Same problem with Radeon 9000 ......

Same issue in 8.04.1

Why still not a fix yet?

---

### Post by Istonian on 2008-10-17
The Nvidia settings did not work. Any other suggestions?

---

### Post by Istonian on 2008-10-17
bump

---

### Post by Istonian on 2008-10-17
bump x2

---

### Post by Istonian on 2008-10-17
bump again

---

### Post by Istonian on 2008-10-17
Wow, no one knows

---

### Post by Istonian on 2008-10-18
bump...again

---

### Post by amano on 2008-10-18
Try to rename the xorg.conf in /etc/X11/ to test.conf or something else and reboot. The system should be able to boot without it with the current X (new feature). And then try to set the resolution values within the normal GNOME resolution switcher. Try nvidia-settings just if that doesn't work.

Good luck. ;)

---

### Post by Istonian on 2008-10-18
No luck, same result

---

### Post by andrewabc on 2008-10-18
Don't bump so often. It wastes screen space when I'm browsing the thread.
Proper etiquette would be to not bump more than once per 24 hours.

Best thing to do is have a nice descriptive thread title so those that can help know to look into the thread. And you do have a nice thread title.

---

### Post by SilverGoldBronze on 2008-10-18
You know, you can't expect a forum to know everything. Ask around, google search, etc.

---

### Post by Istonian on 2008-10-18
I have googled. I have looked everywhere. I am just being persistent. Maybe by bumping someone will see the thread and know the solution. I will limit bump time to 24 hours.

---

### Post by andrewabc on 2008-10-18
My only suggestion would be to somehow manually set resolution in your xorg.conf

Note that doing so could screw up your resolution to the point where you have to use command line to edit it back, or reinstall.

I had problems with resolution in gutsy which made it impossible to set to native monitor resolution of 1680*1050

---

### Post by wgrant on 2008-10-18
What does /var/log/Xorg.0.log say about the EDID? What do you get if you install read-edid and run 'sudo get-edid | parse-edid'?

---

### Post by nanog on 2008-10-18
this post has come up a gazillion times in testing. 

nvidia does not play well with xrandr and its quite possible that your monitor's edid settings are defective. typically you can still force another resolution in nvidia settings (choose the manual option) but occasionally this does not work.  you need to manually add the proper resolution to your xorg.conf. 

For example in screen section:


SubSection "Display"
Depth 16
Modes "1440x900" "1280x800" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" "1280x800" "1024x768" "800x600" "640x480"
EndSubSection

---

### Post by Istonian on 2008-10-19
I have tried both of those suggestions to no avail. I do think the EDID is faulty though.

---

### Post by Zyphrexi on 2008-10-19
I just upgraded yesterday from hardy and I don't seem to be encountering any issues. I remember at one time setting it to read the configuration from nvidia-settings. If both your monitor and video card can handle that resolution, I don't see how you can't set it up in xorg, I think though that intrepid changed the way things worked in that area since hardy, but I don't recall specifics.

for problems like this, try thinking like a computer, that usually works for me.

EDIT: ah yeah here we go

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

as you can see, for modes it uses "nvidia-auto-select"

---

### Post by Istonian on 2008-10-19
So what can I do to change this? Just delete it?

EDIT: I just looked at my xorg.conf file and it does not have an option for auto nvidia-select.

---

### Post by Zyphrexi on 2008-10-19
w00t there ya go. just make sure nvidia-settings is set up right ftw.

---

### Post by Istonian on 2008-10-19
It still doesnt allow me to change my resolution to what it needs to be. I am so confused.

---

### Post by Zyphrexi on 2008-10-19
It's a pain since I can't see what you're doing, so what do you mean, like in the resolution drop-down menu, your desired resolution isn't coming up?

2. after making changes did you click [apply] and [Save to X configuration file] ?

Sorry to sound like some lame windows tech, but I gotta rule that stuff out, since info like that goes a long way to reasoning your way out of problems like this. Just think like a computer and you'll be good.

---

### Post by Istonian on 2008-10-19
Yeah, my resolution does not come up. I tried to apply a different resolution to see how it worked, but it wouldn't save. It said it failed to parse and then it couldnt create a backup. I was going to save it anyway and then put my resolution in the xorg.conf manually, but it won't save.

---

### Post by Zyphrexi on 2008-10-19
did you invoke sudo?

all the stuff in that area is root stuff, so you'll need to be root.

```
sudo gedit /etc/X11/xorg.conf
```

```
sudo nvidia-settings
```

EDIT: also wow, i get all kinds of crazy resolutions. I mainly just use 1024 X 768 though. Refresh rate is the real kicker though, manually setting that up is a pain.

---

### Post by Istonian on 2008-10-19
Yeah, I always use root to edit everything.

---

### Post by Zyphrexi on 2008-10-19
I'm totally out of ideas. Anything I have is just from experience and encountering my own set of issues. I am unfamiliar with the changes with Intrepid and really haven't encountered any problems. All I can say for now is to wait until the stable release. 

If it's a bug that has been reported several times, I'm sure there will be a fix for it eventually. Sorry I couldn't be of more use. Be glad that you have X running though, In the *n* years (where *n* is a number) I've been running linux, I've seriously borked quite a few systems. I eventually came out on top the wiser of course, but it's still a pain if you don't really know the *cause* of the problem

---

### Post by Istonian on 2008-10-19
Thanks for all of your help. Maybe the final release will have a fix for it.

---

### Post by nanog on 2008-10-19
Try removing the other resolutions and restarting x. 


SubSection "Display"
Depth 16
Modes "1440x900"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" 
EndSubSection

---

### Post by Istonian on 2008-10-19
That is the only resolution. Still no luck. Makes absolutely no sense to me.

---

### Post by Zyphrexi on 2008-10-19
have you tried this?
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Istonian on 2008-10-19
Yeah, I have tried that.

---

### Post by iClouseau88 on 2008-10-20
Hi all,

Same story.  Initially I upgraded from Hardy to Intrepid without any problem.  However my screen resolution started going downhill after the recent 100+ upgrades along with the new kernel 2.6.27-7 generic. I tried everything from "displayconfig-gtk" which no longer exists in Intrepid, to "sudo dpkg-reconfigure -phigh xerver-xorg", to "sudo gedit /etc/X11/xserver.org".  Nothing works.  Refer to my thread in Absolute Beginners forum.

I am getting frustrated. With this many users reporting the same screen resolution
problem, one would hope that this get resolved very very soon.

---

### Post by mickbuntu on 2008-10-20
It can only gets worse displayconfig-gtk was removed. It was only way to get my monitor to work. It seems like if it does not work it will not work. You can bug report it, if your lucky someone will fix your monitor issue. One of my PC's have same exact monitor (including a always on pixel got bit better). But Ubuntu selects 800 by 600 default go figure!  No way to change it.

---

