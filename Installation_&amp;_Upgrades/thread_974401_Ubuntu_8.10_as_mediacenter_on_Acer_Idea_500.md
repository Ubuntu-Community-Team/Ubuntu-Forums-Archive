---
title: "Ubuntu 8.10 as mediacenter on Acer Idea 500"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by Ronald Hightower on 2008-11-07
Hi

I'am new in using Ubuntu but after running it for a couple of months stable on my workstation and afterwards on my laptop i can no say i am a big of ubuntu.

my mediacenter is the next taget for me to convert to ubuntu the machine is an Acer Idea 500 connected to an LG plasma by HDMI.

the problem i am facing is that after booting from the cd the screen stays black
I have tried the same procedure with an monitor connected to the machine but still no go.

after burning multiple copy's ( incase the install cd was damaged) still no luck. how ever if i use the windows Harddisk back in the machine i can see that everything works fine hardware wise.

i wonder if anybody has come across the same issue or using the same machine and managed to get ubuntu working. 

for me ubuntu is the way forward and hopefully i can get it working soon with your help.

thanks

---

### Post by Jupp3 on 2008-11-07
> the problem i am facing is that after booting from the cd the screen stays black.
I have tried the same procedure with an monitor connected to the machine but still no go.
VGA or HDMI?

There sure have been some issues with HDMI lately. When I couldn't get HDMI output during installation, I just connected a monitor via VGA and after installing the OS, installed propietary drivers and upgraded all packages. After that HDMI output (video only, no sound yet) worked just fine untill today, and I am now trying to get it working again.

If everything else fails, you can get the alternative install CD, which works in text mode.

> after burning multiple copy's ( incase the install cd was damaged) still no luck.

If you ever doubt that ubuntu install CD is faulty, you can select "check disc for errors" from the boot menu (rather than waste empty discs for reburn)

Oh, and next time tell the graphics card too (although I think that in this case you don't have many choices) - it seems to have Intel chipset, which means it has open source drivers (which in turn means you shouldn't need to install them manually separately, like with nvidia and newer radeon cards)

---

### Post by Ronald Hightower on 2008-11-07
Hi thanks for your quick response and good to know i am not the only one who is struggling. I managed to install the machine using "safe graphics mode" from the boot menu.

I'am using HDMI by the way, which works after the installation of 8.10.
what i didn't manage to do jet is increase the resolution to something higher the 800x600. 

i have found some tweaks for the x server but no luck jet, i'll keep trying

during my google adventures i noticed the audio is a challenge on it's own.

regards

---

