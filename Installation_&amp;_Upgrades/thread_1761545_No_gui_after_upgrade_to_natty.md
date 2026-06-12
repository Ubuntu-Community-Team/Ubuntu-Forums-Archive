---
title: "No gui after upgrade to natty"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by GK N on 2011-05-18
Good day all,
i have (after several effort) upgrade my system to natty and no more gui.
When i try to boot on a graphical mode It ask for low resolution and after that the screen is blinking making it un readable.
Only the console mode is available.

What should I do to have the GUI back.
Thank in advance

---

### Post by lads on 2011-05-18
Hi GK N,

I just upgraded today and I'm running into similar problems. In my case, if I choose the boot option with kernel 2.6.38-8-generic X starts without problems.

It seems that the 2.6.38-8-generic-pae kernel left as default boot option at GRUB by the upgrade has some sort of trouble with graphical things.

Good luck,

Luís

---

### Post by dino99 on 2011-05-18
from a terminal:

sudo rm /etc/X11/xorg.conf
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

reboot then check graphic driver activation

---

### Post by Blasphemist on 2011-05-18
There is a real good post on this kind of problem. Please see this.
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by GK N on 2011-05-18
Good day dino99,
thank for your reply but for me it is not working

---

### Post by GK N on 2011-05-19
After the whole night sleepless and following this [http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html](http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html) it try to start in no resolution but i can not log the screen in blinking

Desperately needing help

---

### Post by Blasphemist on 2011-05-19
GK N, I'll work on this with you if you'd like. I'm assuming you have an SiS gpu but please run these and paste the results back in.
```
lshw -class Display
```
```
xrandr -q
```
Did you download and run the script from Martin's April 30 post?
Please follow this flow and post back what happens and any questions you may have.
> **General **
Yes, with every new release of a distribution of Ubuntu, there seems to be similar and reoccurring problems that arise with "graphics" when trying the run a LiveCD and after the initial install and fist boot. These are my notes that have help people through the last 5 releases of Ubuntu, up through Ubuntu Natty Norwhal 11.04. 

Basically, we want to make sure that the Grub menu boots. then verify that the kernel is booting, then that the Xwindow Session starts and displays.

**Troubleshooting Flow Chart** 
This is to break this down into steps:
_Step 1_. Do you have a Grub Menu?
- Yes: Go to step 2...
- No: Whiie booting, Press shift key (don't hold down) multiple times to see if the Grub menu will come up
- - If yes on Menu, go to step 2
- - If no, comment out /etc/default/grub/ GRUB_HIDDEN_TIMEOUT=00. and rerun grub-update (from a LiveCD)
- - - If yes on Grub Menu go to Step 2
- - - If No, reinstall grub and Start Step 1 from Beginning... Becuase it seems that Grub is not booting.

_Step 2_ "Does the Linux Kernel Boot?" At Grub Menu, go into edit mode and boot into a text console (see instructions below)
- Yes. Go to Step 3
- No. Messages will be verbose on what is loading, what are warnings and what are error messages. Shortcut keys will start to work as the kernel modules load. If if stops at an error, you will be able to use the shortcut navigation cuts to review the errors. Depending on the error, if it is a kernel error, you may be able to reinstall or renew the kernel image. If it is a device module, at least you have somewhere to go to reload that device module or driver.,,, Goal is to get a "booting kernel."

_Step 3_. From the Grub Menu, try to boot in Rescue mode/low graphics.
- If Yes, look for addtional drivers and install recommended driver.
- If No, goto Step 4 to verify that linux kernel will boot.

_Step 4_. Can you boot a graphical Xseesion from a text console session? From the command line type 
```
sudo service gdm start
```
- Yes No black screen/No problem... should boot straight from the grub menu.
- No. Reboot and start testing and changing gfx_modes and kernel boot graphical modes, still booting into the text console before you try to start an Xsession. Going this way, you will have more of a possible chance to be able to toogle between a graphical session or text terminal session (sometimes). ...and at a text console, at least you have the abilty to install files and make changes to config files. And if you can get back into a command prompt, you could then stop the gdm service that is locked.

You can stop the gdm service via
```
sudo service gdm stop
```


---

### Post by GK N on 2011-05-19
Good day Blasphemist,
thank you for your reply and of course your help is welcome
here is the results of the command.
```

lshw -class Display
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:fdee0000-fdefffff ioport:dc00(size=128)


```
```

xrandr -q
Screen 0: minimum 640 x 480, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1024x768       60.0  
   800x600        60.0  
   640x480        60.0  


```

Regarding the gdm while installing the necessary to compile the driver the gdm was installed. After the installation the gdm start again but i have recovery console and user Defined Session which give me 2 small terminal

---

### Post by GK N on 2011-05-19
it is ok now
i have finish the upgrade. This upgrade fails due to an erreor in python.
Happy to see gdm again.
the only thing is that unity is not working on my computer.
 
Thank you very much for your help

---

### Post by Blasphemist on 2011-05-19
Good to hear of progress! These two things will tell us more about not having Unity.
```
/usr/lib/nux/unity_support_test -p
/usr/lib/nux/unity_support_test -p --compiz
```
And, did martin's script run without error's and did it help?

---

### Post by GK N on 2011-05-20
Thank,
here is teh result of the commands

```

/usr/lib/nux/unity_support_test -p

[COLOR=Black]OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:      [COLOR=Red]**no**[/COLOR]
Not blacklisted:                 yes
GLX fbconfig:                    yes
GLX texture from pixmap:  [COLOR=Red]**no**[/COLOR]
GL npot or rect textures:    yes
GL vertex program:           yes
GL fragment program:       yes
GL vertex buffer object:     yes
GL framebuffer object:       yes
GL version is 1.4+:            yes

Unity supported:                **[COLOR=Red]no[/COLOR]**
[/COLOR]
```

```

/usr/lib/nux/unity_support_test -p --compiz

OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:      **[COLOR=Red]no[/COLOR]**
Not blacklisted:                 yes
GLX fbconfig:                    yes
GLX texture from pixmap:  **[COLOR=Red]no[/COLOR]**
GL npot or rect textures:    yes

Compiz supported:             [COLOR=Red]**no**[/COLOR]


[COLOR=Black][/COLOR]
```



regarding the script i think it work (even if some checking were not ok f77 for example) but no sound when I boot with the kernel 2.6.38 and i have the sound i the kernel 2.6.35. Why ? this is the $ 1 000 000 question.

---

### Post by Blasphemist on 2011-05-20
It doesn't look like to me that you will be able to run Unity 3D but should be able to run Unity 2D. I get this from a 72 page thread that Martin has been working in. 
[http://ubuntuforums.org/showthread.php?t=958967&page=72](http://ubuntuforums.org/showthread.php?t=958967&page=72)
Here is a quote from him in that thread in recent pages.
> Unity-2D will run well with SIS, just don't forget to enable Metacity compositing through gconf-editor. So you can at least enjoy a bit with shadow etc 
You can install Unity 2d from synaptic package manager or, 
```
sudo add-apt-repository ppa:unity-2d-team/unity-2d-daily

sudo apt-get update

sudo apt-get install unity-qt-default-settings
```
See this page. [http://www.ubuntugeek.com/install-ubuntu-unity-2d-using-ppa-in-ubuntu-11-0410-10.html](http://www.ubuntugeek.com/install-ubuntu-unity-2d-using-ppa-in-ubuntu-11-0410-10.html)

---

### Post by GK N on 2011-05-20
well thank for your 72 page thread reading.
i have install unity-2d (and i love it) i'm now trying to update all the package.
I still have an issue with the sound in the kernel 2.6.38 and when i lauch banshee to play a file :D it crash and log me out.
I think i will make all my update and if it continue create a new thread as this one is solved.
Thank you very much Blasphemist

---

