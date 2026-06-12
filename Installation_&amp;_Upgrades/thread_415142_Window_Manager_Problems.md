---
title: "Window Manager Problems"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by becominglumberg on 2007-04-20
After upgrading to 7.04 last night, I decided to turn on desktop effects this morning. When I did, outside of the windows disappeared. I tried restarting, to see if x didn't adjust properly, but the problem remains... I can open windows, but there is no window frame.

Now, on context pop-ups (like right clicking icons in the task bar) I get the fade and wobbly, so I assume compiz is working to some degree. Any idea what gives?

---

### Post by rich.bradshaw on 2007-04-20
Hmmmm.... not sure how to fix that, but if you want beryl with borders etc do

sudo apt-get install beryl emerald

then

beryl-manager

This will work better. Sounds like Compiz is missing it's window decorator, though I don't know what that is called...

---

### Post by becominglumberg on 2007-04-20
Yeah, I was hoping to get the standard compiz working... I am pretty sure it is cgwd that is the window manager for compiz, but I don't know how to go about getting it to go.

---

### Post by davidvasta on 2007-04-20
Having the same problem with a new install. I saw this in the beta and RC but figured it would go away in the GOLD version. Guess not. I am trying to make it happen again and get a screen shot of it if I can to post for more help.

---

### Post by ivotedforkodos on 2007-04-21
I am having the same problem. I just upgraded to Feisty, and everything is fine normally, but when I turn on Desktop Effects, the window borders disappear. Note that you can still move the windows using <Alt>, but it's still obviously pretty annoying. The wobbly windows and rain, and other compiz effects do seem to work. 

Is this a window decorator problem? For me, the problem persists regardless of whether I have "Use Metacity theme" checked in the GL Desktop preferences pane. 

I'm have a GeForce 6150 and the nvidia binary driver.

---

### Post by Timokl on 2007-04-21
I have the same problem. I upgraded from Edgy this night, and the upgrade process seems to have been fine - except from the windows-decorator thing.

When I open a window, there is no windows-decoration. When I start GL-Desktop from the System menu, GL-Desktop is not activated, but when I activate it, the windows decoration appear, and everything works smoothly. However, there are no Compiz effects of any kind with activated GL desktop. :confused: And, also there is also only the metacity theme with activated GL desktop although this is not selected. :confused: 

I did have installed Compiz on Edgy using this method: [https://help.ubuntu.com/community/CompositeManager/InstallingCompiz]("https://help.ubuntu.com/community/CompositeManager/InstallingCompiz"). There might be something left that confuses Feisty - but where to look for it?

Greez,
Timo

---

### Post by GButler on 2007-04-21
My friend and I experienced this problem while installing Fiesty on my desktop system. It has to do with the nVidia drivers. I can't be as specific as I want to be, but hopefully someone reading this post will know what I'm trying to tell you and give you the actual terminal command.

You have to add an Option to your screen driver or directory or something that adds in RGB support. Again, hopefully someone will know what that command is exactly.

---

### Post by ahirreddy on 2007-04-21
Simple fix for nvidia users. Just reconfigure the x.org config. 

run

sudo nvidia-xconfig  --add-argb-glx-visuals

It'll back up your current xorg.conf, and create a new one. Just restart X with ctrl+alt+backspace or reboot and your good to go!

---

### Post by Timokl on 2007-04-22
OK, but what about ppl with ATI cards? Install the fglrx driver?

Regards,
Timo

---

### Post by Timokl on 2007-04-23
> **Timokl said:**
> OK, but what about ppl with ATI cards? Install the fglrx driver?

I seem to have found a solution. :popcorn: 

1) I installed the proprietary ATI-driver fglrx

2) I installed Xgl as Composite Manager, as described in [https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")

Now, Window Manager is loaded, my Gdesklets are loaded, Desktop FX work.

I hope it's also some kind of stable now.

Bye,
Timo

---

### Post by peacechicken on 2007-04-27
This worked for me! THANK YOU!! I had windows problems once I got my widescreen monitor resolution fixed. I tried a few other things I found in the forum but to no avail... that one line fixed it though, thanks so much!


> **ahirreddy said:**
> Simple fix for nvidia users. Just reconfigure the x.org config. 

run

sudo nvidia-xconfig  --add-argb-glx-visuals

It'll back up your current xorg.conf, and create a new one. Just restart X with ctrl+alt+backspace or reboot and your good to go!

---

