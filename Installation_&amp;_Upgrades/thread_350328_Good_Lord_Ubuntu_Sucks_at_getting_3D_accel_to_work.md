---
title: "Good Lord Ubuntu Sucks at getting 3D accel to work!"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by skenagle on 2007-01-31
I have tried for days now to get 3d Acceleration to work. I have Radeon X600  and have used this same exact card on SuseLinux and was running beryl fine.

So i switch to Ubuntu because people say it is the next big thing and its easy to work with. ARE YOU KIDDING ME??

I have followed about 10 different walkthroughs all over the forums, ive installed Fglrx, vesa, etc.. everythign i can think of to either circumvent or update this issue. 

My current xorg.conf says i am using fglrx, but when i "glxinfo |grep direct" it shows "direct Rendering : NO.

Ive done this over and over again for hours now, i am frustrated and overwhelmed and have no where else to go.

Can someone who has some idea of where i am going wrong please help me?

No matter what i do, i cant get Direct REndering to work...

Even in a forum posting that says "this worked for my x600" etc...


PLEASE HELP....

i want to use Ubuntu and give it a shot, but lets be honest, without Beryl, Linux isnt as fun and productive.

---

### Post by skenagle on 2007-02-01
surely there is someone here who knows...

im still reading through the forums 12 hours later.

please help.

---

### Post by The_Architect on 2007-02-01
> **skenagle said:**
> surely there is someone here who knows...

im still reading through the forums 12 hours later.

please help.
The Good Lord knows :D

---

### Post by spockrock on 2007-02-01
sorry but this is a problem with crapptastic ati drivers......

---

### Post by aberry5555 on 2007-02-01
I had the EXACT same problem as you, and it's easy to fix, as long as you don't try doing it the Ubuntu way :p. switch back to the open-source "radeon" driver for now and completely uninstall (by right clicking on the package and clicking completely remove, rather than just remove) the fglrx drivers and then go to the ati website and follow their instructions. simple as that the acceleration worked for me. I think it's a broken package in the Ubuntu repository. I warn you though, Beryl tends to suck a bit with ATI, at least it does with me. The GLX drawing of the desktop is a bit dodgy.

---

### Post by skenagle on 2007-02-07
yes i took your advice, tried that.. and badabing...

nothing.. :(

it still tells me that i am running a mesa driver..

im am so lost..


I did this same thing in Suse 10.2 and it was fine.

I recently installed fiesty herd 3 to see if the new ATi drivers built in to the new system would help.
It just comes up after the initial boot option splash screen with that "cannot display xserver" eror all of us ATI people get at bootup.


anyone know how i can get mesa driver to stop showing up and get my ati radeon x600 video card to GLX info to Render=yes??


Ill pay someone in kind gestures and perhaps send them an ecard, if they can help me.


thank you.

---

### Post by cstrippie on 2007-02-07
Your best bet for fglrx install instructions is here: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

As for your no direct rendering issue, it sounds like you did not disable the composite extension.  Instructions for modifying compositing in x11.conf are near the top of the link I gave above.  **IF USING FEISTY DO NOT USE 8.33.6 DRIVER**

---

### Post by skenagle on 2007-02-07
i appreciate all teh help i am getting, yes i do have the Composite Ext disabled.

I am goign to go through that wiki you posted there, see if i can do this right .
(for the 10th time) (literally)

oh, i decided to reformat back to edgy since feisty didnt make it easier...
(i learned that trick from years of using windows)


.. off to follow the wiki.... the wonderfull wiki of oz...

(im losing my mind)

---

### Post by Drezliok on 2007-02-07
Buy Nvidia Card.

If thats not an option, try Envy from, I think I has ATI drivers in it.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

When last using it I remember it asking if I wanted ATI or Nvidia. Follow the instructions and see if it works.

---

### Post by skenagle on 2007-02-08
I am so happy i tried that Envy script...

IT WORKED!!!
I AM RUNNING X600 DRIVERS FROM ATI!!!!

WOOHOO!

thank you very much Drezliok for the tip....

i have been working on this for ever...

i ran this envy script before too adn it didnt work..

i think i had an older version..


thank you all for your help...

now to get beryl working..


see you guys later most likely in my newest post entitled "How the hell do you get beryl to work in ubuntu" hehe!


i appreciate all your concerns and support..

peace!

---

### Post by warkro on 2007-02-08
this is why I love the Ubuntu community.

---

### Post by Drezliok on 2007-02-09
Feels good to be helpful.:popcorn:

---

### Post by Dexter. on 2007-04-21
Envy worked at getting fglrx running but I still have no direct rendering...

glxinfo | grep direct says:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

Help?

---

