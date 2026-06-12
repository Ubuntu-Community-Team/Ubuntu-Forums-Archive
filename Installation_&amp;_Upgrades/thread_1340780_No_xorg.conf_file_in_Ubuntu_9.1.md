---
title: "No xorg.conf file in Ubuntu 9.1?"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by SNYP40A1 on 2009-11-29
I don't see an xorg.conf file in Ubuntu 9.10.  Was it moved someplace else?

```

ubuntubox@compy:/etc/X11$ ls
app-defaults             fonts    xinit       Xsession          XvMCConfig
cursors                  rgb.txt  xkb         Xsession.d        Xwrapper.config
default-display-manager  X        Xresources  Xsession.options

```

I want to add some configuration options for my video card.  Do I just create a new xorg.conf file and place it in the directory above?  Does it need to be linked in someplace?

---

### Post by livigagl on 2009-11-29
As far as I know you can use a previous xorg.conf (if you have one for that pc that works well) or create a new simple one similar to this:

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "dri"
    Load    "GLcore"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "vesa"
EndSection
```Obviously you should change the driver using the right one for your video card (e.g. intel, radeon, nv, etc...) and you might also want to add other sections like:

```
Section "Monitor"
    HorizSync       30.0 - 85.0
    VertRefresh     55.0 - 75.0
    Identifier     "Monitor"
    Option         "DPMS"
EndSection

Section "Extensions"
    Option         "DAMAGE" "Enable"
    Option         "Composite" "Enable"
    Option         "RENDER" "Enable"
EndSection
```**Do not use my HorizSync and VertRefresh values if you're not sure that they are correct for your monitor!**

Depending on what you need (e.g. improve 3D performance), you can find many samples on internet.

---

### Post by SNYP40A1 on 2009-11-30
Thanks, I'll try it.

---

### Post by kritostar on 2009-12-03
Hi! I've installed kubuntu 9.10 and have the same problem, no xorg.conf file. Did it work to make the file in /etc/X11 ???

---

### Post by Braveheart1980 on 2009-12-13
> **kritostar said:**
> Hi! I've installed kubuntu 9.10 and have the same problem, no xorg.conf file. Did it work to make the file in /etc/X11 ???

Same here!

---

### Post by igorek93 on 2009-12-14
Please help!
I need to change the color depth in 9.10 server.
I understand that there is no xorg.conf.
Can any1 tell me where and how i can change the color depth?
I'm new to unix so please make it step by step.
Also i can bearly see the console so if you please write the all the commands.
Thank you!

---

### Post by Stabbin Jed on 2009-12-14
Same problem here.  I have an older Toshiba Satellite with a Trident video card on it and the only fixes I've been able to find consist of editing the xorg.conf file which doesn't appear to be present.  I'm pretty new; this is my first install and I really could use some help.

Thanks

---

### Post by bryonak on 2009-12-14
Hi everyone!
Ubuntu 9.10 has sourced out the setting from the xorg.conf, which can be considered obsolete and is due to be phased out in the coming years.
However that won't happen quickly, so if you create one and paste your old configuration into it, it will get parsed and the options will be honored.

You can leave away the input devices sections, X will configure them automatically.
Input and media devices are now controlled by HAL, video settings are preferably managed by your driver (for example through nvidia-settings if you have a NVidia card... I don't know the utility for, say, Stabbin Jed's Trident card).
But there is absolutely no harm in still using the xorg.conf, and I guess it will still work several years from now on ;)
Just to say "no xorg.conf" is a feature, not a bug. It marks the "bullet-proof" stability of the recent X server releases as compared to earlier versions, which required a flawless and complete xorg.conf in order to work.

---

### Post by Stabbin Jed on 2009-12-15
At the risk of sounding really dumb, I have no idea how to "create my own."  Would anyone be willing to give me a step by step?  Would I be creating an xorg.conf file (even though it's obsolete) or some other type of file?  I guess I'm still a little lost here.  

Thanks!:)

---

### Post by audiomick on 2009-12-15
Hallo Jed.
You don't sound dumb, we all had to learn.

Yes, you are creating a xorg.conf file. Although it is obselete, it still gets taken into account if it is there. It needs to be in /etc/X11


First of all, I believe there is a man page for xorg.conf.
In the terminal, do
```
man xorg.conf
```
and it should appear.

Then there is this:
[https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)

And this:
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)
which has a link to a Trident trouble shooting page.

To create a file, do
```
gksu gedit /etc/X11/xorg.conf
```

This will open the editor gedit with root priviliges.
I think if you do it like that, it knows you want to create a file, but I am not completely sure.

 If it says "file doesn't exist" or something of that nature, you need to navigate to the directory /etc/X11 (note that this is case sensitive. It is a capital X) and open the editor there, then save there. I can't try this out right now, as I am not at home.

To navigate,
```
cd /etc/X11
```
will move you to the right directory.

Then
```
gksu gedit
```
to open the editor with root priviliges.

Write what you need into the file. I hope you know what to write from your research. I would have to look it up myself.

I think you should only need something along these lines:

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Synaptics Touchpad"
EndSection
```
where the "device" section refers to your video card, i.e. you must put the name and driver in there.

Once again, I am not sure about it. The last time I had to deal with this was about 3 years ago.

I hope this helps you a bit.

---

### Post by rjdaggett on 2010-03-10
This is the only way to go..

In order to generate xorg.conf you need to switch to one virtual console using the key combination CTRL + ALT + F1.

Now execute the following commands:

**user@ubuntu ~# sudo service gdm stop**

This command will stop the X.
Now we need to generate the xorg.conf file:

**user@ubuntu ~# sudo Xorg -configure**

This has generated the file in ~/xorg.conf.new.
We need to make the X using it so we have to put this file inside /etc/X11/

**user@ubuntu ~# sudo mv ~/xorg.conf.new /etc/X11/xorg.conf**

After moving this file to the proper location you can start the X again and see what happens:

**user@ubuntu ~# sudo service gdm start**
 
Good Luck!

---

### Post by zigmo on 2010-05-10
Thanks. This was perfect.
I knew I had to create the Xorg.conf file, but didn't realize I had to stop gdm (or even know that it existed).
It looks like it's working fine.

---

