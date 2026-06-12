---
title: "compiz broken after this morning (Oct7) updates"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tact on 2008-10-06
After this morning's update compiz is broken on my machine...  before I report - anyone else experienced same today?

---

### Post by deathsshadow77 on 2008-10-07
yes same here along with many other new problems
-compiz will not start up
-not all windows show up in the panel
-wallpapers are acting weird
-the resolution manager no longer recognizes the names of my monitors

---

### Post by macarpen on 2008-10-07
Same here. I noticed a bunch of compiz packages got updated, but also xserver-xorg-core. Any idea which update is to blame?

---

### Post by dabl on 2008-10-07
Check ```
glxgears
```

My broken compiz turned out to be a broken Nvidia driver installation.  Reinstalled and all was well again.

However that was with last night's updates.  Today I see there is a new kernel coming, plus the official 177.80 Nvidia driver is now available, so I think it's going to be another long evening ....  :lolflag:

---

### Post by macarpen on 2008-10-08
My problem ended up being that the radeonhd driver was being used instead of the ati driver. My xorg.conf is very generic and doesn't specify any drivers or other settings. After explicitly configuring the device section to use ati I was able to run compiz again. Not sure why ati had been the default at first and then radeonhd became the default after the update.

---

### Post by ubername on 2008-10-08
Same thing.

When I check System>Administration>Hardware Drivers

it says 'No proprietary drivers are in use on this system'

However I have an nvidia card installed and nvidia-glx-177 installed.

If I do System>preferences>Appearance and choose the visual effects tab, then select the 'extra' option I am told that visual effects cannot be enabled.

---

### Post by ger_macaco on 2008-10-09
In my case, KDE Windows Decorator and Kwin are in use when I boot and I have to reload Window Manager to make compiz work.

Compiz and Emerald are default, but after Oct7 updates I have to go through this to get them running.

Any guess about this?

PS: nvidia-glx-177 in use (this is/should be OK)

---

### Post by vgrisham on 2008-10-09
I have an Intel 915GM graphics card that worked fine with gutsy and hardy. It started off well with Intrepid, but after last night's update, I'm having similar problems. Compiz loads, but I can't see the tops of the windows to minimize, maximize or close. 

Anybody file a bug report on this yet? If so link?

---

### Post by kfries6 on 2008-10-09
> **vgrisham said:**
> I have an Intel 915GM graphics card that worked fine with gutsy and hardy. It started off well with Intrepid, but after last night's update, I'm having similar problems. Compiz loads, but I can't see the tops of the windows to minimize, maximize or close. 

Broke?  Exploded into a worthless pile of junk is more like it.

I run a Latitude D620 with the Intel video chip, and Apt keeps getting stuck on configuration issues (I have not let it sit and work on a 30 second problem for 2 hours, so its not that I am not waiting long enough), and I too have no windows decorations.  Emerald is just no willing to run.  And nothing is showing up in /var/log/messages

And this problem is on top of the network manager problem they still have not fixed.

I have run pre-releases before, and this one seems to be seems less stable at this point than pre-releases in the past.  Is anyone else feeling that way also?

---

### Post by Locke_99GS on 2008-10-09
Recent copmiz update (today) fixed alot of odd issues I was having recently; Cube deformations weren't working, cube transperency wasn't working, and the ever popular titlebar glitch, were all introduced lately and they all seem to be repaired now.

There was a nm update also, but the ugly ifupdown hack has been working well enough for me, so I don't know if the update fixed anything.

While I did have many problems fighting with the new X, it accepted my nVidia drivers without a hitch.

---

### Post by smartboyathome on 2008-10-09
Have any of you tried enabling "Window management" in compizconfig? This solved the titlebar issue for me (of course, I haven't restarted yet after getting these updates, so I don't know if it will come back).

---

### Post by quazi on 2008-10-09
Update today broke compiz for me.  I made the mistake of clicking the partial upgrade button when it came up and after restarting every window kept flashing (appearing and disappearing).  After disabling compiz and restarting, the flashing windows were gone, but reappeared when I re-enabled compiz.

Disaster.

---

### Post by tghe-retford on 2008-10-09
I mentioned this elsewhere, but the latest updates which came through a few hours ago for compiz-fusion-plugins-main has broken the animations plugin. You now have to type in the animation you want as opposed to the easier to use drop down menus in previous versions. Even if you do change the animation to a valid one (ie. animations:Skewer or animations:Fade) the animation doesn't change to what the user requests but uses the default one.

compiz-fusion-plugins-extra and compizconfig-settings-manager with some other packages are still the old version in the repositories (0.7.7+git20080807-0ubuntu1), whilst others have been upgraded (0.7.8-0ubuntu1).

---

### Post by Locke_99GS on 2008-10-09
I still have dropdowns in the animation plugin, and they still work for me.

---

### Post by tghe-retford on 2008-10-09
> **Locke_99GS said:**
> I still have dropdowns in the animation plugin, and they still work for me.
I do now that the settings manager and python-compizconfig updated - it must have been something in one of those packages not being able to update which caused the drop down boxes to disappear. Compiz is now fully upgraded to 0.7.8 for me.

---

### Post by BARlotta on 2008-10-09
> **tghe-retford said:**
> I mentioned this elsewhere, but the latest updates which came through a few hours ago for compiz-fusion-plugins-main has broken the animations plugin. You now have to type in the animation you want as opposed to the easier to use drop down menus in previous versions. Even if you do change the animation to a valid one (ie. animations:Skewer or animations:Fade) the animation doesn't change to what the user requests but uses the default one.

compiz-fusion-plugins-extra and compizconfig-settings-manager with some other packages are still the old version in the repositories (0.7.7+git20080807-0ubuntu1), whilst others have been upgraded (0.7.8-0ubuntu1).

Seeing that here as well

---

### Post by tghe-retford on 2008-10-09
> **BARlotta said:**
> Seeing that here as well
Try updating the repositories and ensuring that the latest compizconfig-settings-manager (0.7.8-0ubuntu3) and python-compizconfig (0.7.8-0ubuntu1) are installed. This worked for me.

---

### Post by ykpaiha on 2008-10-09
> **tghe-retford said:**
> Try updating the repositories and ensuring that the latest compizconfig-settings-manager (0.7.8-0ubuntu3) and python-compizconfig (0.7.8-0ubuntu1) are installed. This worked for me.

it worked again after uninstall and reinstall the whole compiz 0.7.8
...thanks

---

### Post by BARlotta on 2008-10-09
> **tghe-retford said:**
> Try updating the repositories and ensuring that the latest compizconfig-settings-manager (0.7.8-0ubuntu3) and python-compizconfig (0.7.8-0ubuntu1) are installed. This worked for me.

That works...thanks.
Is anyone else missing some animations that were there previously (like Leaf Spread)?

---

### Post by tghe-retford on 2008-10-09
> **BARlotta said:**
> That works...thanks.
Is anyone else missing some animations that were there previously (like Leaf Spread)?
You have to enable the Animations Add On plugin under Effects for the more spectacular effects, including Leaf Spread.

---

### Post by shane19174 on 2008-10-10
My animations are broken after today's updates. I checked and compizconfig-settings-manager (0.7.8-0ubuntu3) and python-compizconfig (0.7.8-0ubuntu1) are installed, so that's not the problem. In fact, the "open" animation (set to Glide 1) works, but not "close" or "minimize." It doesn't matter what I set them to, they just don't work. I noticed, however, that the so-called "minimize effect" (the independent effect which disables "animations") works. Seems weird to me. Any ideas?

Shane

---

### Post by plun on 2008-10-10
Test this, there was a "transient breakage" yesterday when all packages went out to repo.

```

sudo apt-get install compiz
```


How it looks

```
plun@plun:~$ sudo apt-get install compiz
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome
The following NEW packages will be installed:
  compiz compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 3791kB/3897kB of archives.
After this operation, 18.8MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by shane19174 on 2008-10-10
Nope:

[INDENT]shane@shane-desktop:~$ sudo apt-get install compiz
[sudo] password for shane: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
The following packages were automatically installed and are no longer required:
  libavutil1d libpostproc1d libx264-57 libswscale1d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/INDENT]

By the way, how do you box in code on this forum?

Thanks,

Shane

---

### Post by shane19174 on 2008-10-10
I tried to reinstall all compiz packages in synaptic, but that didn't help. Then I did a complete uninstall of compiz, followed by an install. Nothing at all has changed: I still have the glide animation when a window is opened the first time, but no animation on minimize or close.

Anyone else experiencing this?

Shane

---

### Post by dngpng on 2008-10-10
> **shane19174 said:**
> I tried to reinstall all compiz packages in synaptic, but that didn't help. Then I did a complete uninstall of compiz, followed by an install. Nothing at all has changed: I still have the glide animation when a window is opened the first time, but no animation on minimize or close.

Anyone else experiencing this?

Shane

It's interesting, I have no animation for open/close, but the ones for focus/shade/minimize/ are fine. Reinstall compiz packages didn't solve the problem for me either. :(

See [Bug #281001]("http://launchpad.net/bugs/281001")

---

### Post by plun on 2008-10-10
> **shane19174 said:**
> I tried to reinstall all compiz packages in synaptic, but that didn't help. Then I did a complete uninstall of compiz, followed by an install. Nothing at all has changed: I still have the glide animation when a window is opened the first time, but no animation on minimize or close.

Anyone else experiencing this?

Shane

Animation is split within version 0.7.8

Compiz runs faster and all "special animations" are moved.  Just a good idea from the compiz-fusion project.

Please read this developer message

[http://forum.compiz-fusion.org/showthread.php?t=9628](http://forum.compiz-fusion.org/showthread.php?t=9628)

:)

---

### Post by dngpng on 2008-10-10
> **plun said:**
> Animation is split within version 0.7.8

Compiz runs faster and all "special animations" are moved.  Just a good idea from the compiz-fusion project.

Please read this developer message

[http://forum.compiz-fusion.org/showthread.php?t=9628](http://forum.compiz-fusion.org/showthread.php?t=9628)

:)

Thanks for the link. After reset the open/close animation, they work fine again. :)

---

### Post by vgrisham on 2008-10-10
> **smartboyathome said:**
> Have any of you tried enabling "Window management" in compizconfig? This solved the titlebar issue for me (of course, I haven't restarted yet after getting these updates, so I don't know if it will come back).

How do I get to compizconfig?

Edit: Never mind. I found the command by googling. For anyone else, the command to access compizconfig is ccsm

---

### Post by plun on 2008-10-10
> **vgrisham said:**
> How do I get to compizconfig?

Please take a look at this Tombuntu article

[http://tombuntu.com/index.php/2008/03/27/custom-compiz-effects-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/27/custom-compiz-effects-in-ubuntu-804/)

Its the same for Intrepid.

simple-ccsm or ccsm, ccsm can be confusing with tons of settings.


You can also use Add/remove for install or Synaptic.

---

### Post by vgrisham on 2008-10-10
[quote=plun;5939646]Test this, there was a "transient breakage" yesterday when all packages went out to repo.

```

sudo apt-get install compiz
```

Reinstalling Compiz fixed everything. Thank you. Now I can use avant window navigator again!

---

### Post by ameseisch on 2008-10-10
reinstalling all compiz packages helped fix most of my problems, but I still cant move or resize any windows... and many windows appear up at the top left corner with the title bar under the gnome pannel. any thoughts on that?

as far as Nvidia drivers I have been using the 173 one instead of the 177 which was labled "(recommended)" on my machine, 177 didn't work for me before. is the 177 driver really recommended now that it has been updated?

on a positive note, recent upgrades got my wireless card working!

---

### Post by quazi on 2008-10-10
Compiz is still completely broken for me, even after removing all the compiz-related packages in synaptic and then running "sudo apt-get install compiz".  Here's the output from a compiz --replace

```

Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3840x1200) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3840x1200) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
present. 
Checking for Xgl: not present.

```

Compiz was working perfectly before I decided to partially upgrade on Oct 9 (I've since learned that was a stupid thing to do).  Synaptic also updated my nVidia drivers to 177.80 at the same time, so that might have something to do with it as well.  I made a new xorg.conf file with nvidia-settings and that did nothing to help.  Any suggestions?

---

### Post by shane19174 on 2008-10-10
I still can't get close or minimize animations to work, but I have to admit I don't know what is meant by "resetting" the animations (as mentioned in plun's link and according to which dngpng got things working). Any help would be appreciated.

By the way, compiz was working fine until yesterday (Oct 9) for me too. Mine is not the result of a partial upgrade, though. I got the problem through synaptic with the compiz updates.

---

### Post by dngpng on 2008-10-10
> **shane19174 said:**
> I still can't get close or minimize animations to work, but I have to admit I don't know what is meant by "resetting" the animations (as mentioned in plun's link and according to which dngpng got things working). Any help would be appreciated.

By the way, compiz was working fine until yesterday (Oct 9) for me too. Mine is not the result of a partial upgrade, though. I got the problem through synaptic with the compiz updates.

I assume you already have the ccms (CompizConfig Settings Manager). Open it and go to the "Animation" section, click through the buttons with yellow brush where things don't work for you. This was what I've done and it worked out pretty well. 

Just be careful that the settings you added before by your own may get lost if you don't back them up or note them down.

---

### Post by shane19174 on 2008-10-10
> I assume you already have the ccms (CompizConfig Settings Manager). Open it and go to the "Animation" section, click through the buttons with yellow brush where things don't work for you. This was what I've done and it worked out pretty well.

Just be careful that the settings you added before by your own may get lost if you don't back them up or note them down. 

Hey, thanks! That was exactly the point I was missing. Worked perfectly.

---

### Post by quazi on 2008-10-10
> **quazi said:**
> Compiz is still completely broken for me, even after removing all the compiz-related packages in synaptic and then running "sudo apt-get install compiz".  Here's the output from a compiz --replace

```

Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3840x1200) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3840x1200) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
present. 
Checking for Xgl: not present.

```

Compiz was working perfectly before I decided to partially upgrade on Oct 9 (I've since learned that was a stupid thing to do).  Synaptic also updated my nVidia drivers to 177.80 at the same time, so that might have something to do with it as well.  I made a new xorg.conf file with nvidia-settings and that did nothing to help.  Any suggestions?

So after looking around a bit, the Xgl not present is apparently not the problem since I'm using the nvidia driver.  When I run compiz, I get that message about 16 times and simultaneously all the windows and taskbar flash in and out (disappear and then suddenly reappear) until it eventually fails with this message 

```

Checking for texture_from_pixmap: 
** ERROR **: Can't create CORBA main-thread wakeup pipe
aborting...
Aborted (core dumped)
present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 8: No modules found:
No builtin or dynamically loaded modules were found.
PangoFc will not work correctly.
This probably means there was an error in the creation of:
  '/etc/pango/pango.modules'
You should create this file by running:
  pango-querymodules > '/etc/pango/pango.modules'
Window manager warning: Log level 16: failed to find shape engine, expect ugly output. engine-type='PangoRenderFc', script='latin'
Window manager warning: Log level 16: failed to find shape engine, expect ugly output. engine-type='PangoRenderFc', script='common'
Comparing resolution (3840x1200) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 

** ERROR **: Can't create CORBA main-thread wakeup pipe
aborting...
Aborted (core dumped)
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 16: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: cannot open shared object file: Too many open files
Window manager warning: Log level 8: No modules found:
No builtin or dynamically loaded modules were found.
PangoFc will not work correctly.
This probably means there was an error in the creation of:
  '/etc/pango/pango.modules'
You should create this file by running:
  pango-querymodules > '/etc/pango/pango.modules'
Window manager warning: Log level 16: failed to find shape engine, expect ugly output. engine-type='PangoRenderFc', script='latin'
Window manager warning: Log level 16: failed to find shape engine, expect ugly output. engine-type='PangoRenderFc', script='common'


```

---

### Post by zoomy942 on 2008-10-10
mine is borken too.  mimizing closes the window

---

### Post by Efros on 2008-10-10
Have the old decorations missing problem, Nvidia .80 driver failed to install on 2 of my systems, but one of them still has a working compiz installation...go figure. I really like this piecewise upgrade, every morning is a new adventure sometimes at the terminal sometimes in a GUI. If I follow my normal pattern I go through all this piecewise updating and then install afresh when the final release is available, guess I'm a masochist!:)

---

### Post by quazi on 2008-10-10
I fixed my problem by starting with a new compiz settings file.  It's kind of annoying how long that took me to figure out.

---

### Post by [Neurotic] on 2008-10-10
I just updated, and realised that several effects seem to be missing, most notably 'Beam'.  Not a huge deal, but anyone know where they went?

Could possibly be the cause for these other issues, not sure.

---

### Post by tghe-retford on 2008-10-10
> **'[Neurotic] said:**
> I just updated, and realised that several effects seem to be missing, most notably 'Beam'.  Not a huge deal, but anyone know where they went?
You need to activate the Animations Add On plugin in CCSM.

---

### Post by smartboyathome on 2008-10-10
> **'[Neurotic] said:**
> I just updated, and realised that several effects seem to be missing, most notably 'Beam'.  Not a huge deal, but anyone know where they went?

Could possibly be the cause for these other issues, not sure.

Enable "Animation Addons" and then restart compizconfig (not compiz).

---

### Post by jerrylamos on 2008-10-11
On IBM Thinkpad R31, Compiz since Alpha 5 has been broken i.e. hangs up the R31 altogether, power off time.  

Either use Alpha 5 AND DON'T UPDATE COMPIZ! or else Xubuntu or Kubuntu.

Jerry

---

### Post by BARlotta on 2008-10-11
> **'[Neurotic] said:**
> I just updated, and realised that several effects seem to be missing, most notably 'Beam'.  Not a huge deal, but anyone know where they went?

Could possibly be the cause for these other issues, not sure.

The more cpu/gpu intensive animations moved to a separate plugin.  It is called "Animations Add-On"

EDIT: Whoops I just saw this was already answered, sorry for the dup.

---

### Post by radiobuzzer on 2008-10-19
I also have an Intel graphics card and the title bars are missing after the upgrade. No minimize maximize etc.

> **smartboyathome said:**
> Have any of you tried enabling "Window management" in compizconfig? This solved the titlebar issue for me (of course, I haven't restarted yet after getting these updates, so I don't know if it will come back).

What do you mean. I get a whole plugins category with Window Management. And half of them are already enabled. I added, removed, but still titlebars missing. Any clue?

I also removed the compiz with --purge and reinstalled it but nothing. HELP!

---

### Post by ameseisch on 2008-10-20
i finally fixed my problem with no window borders and not being able to move them or resize them by re-enabling some things in the compiz settings manager. 

- window decorator
- move
- resize

i don't understand why these setting were reset but most of the others weren't, and the reason it took me so long to figure out is because i had never had these effects turned off so i guess i didn't really understand the role they played in compiz.

---

### Post by radiobuzzer on 2008-10-25
> **ameseisch said:**
> i finally fixed my problem with no window borders and not being able to move them or resize them by re-enabling some things in the compiz settings manager. 

- window decorator
- move
- resize


Can you help me find these settings? Are they plugins in the CompizConfig settings manager? I can't find them either.

EDIT: It's ok! I found it! I had to instal compiz-gnome that was removed previously.
```
 sudo apt-get install compiz-gnome
```
These plugins were disabled, so I had to enabled them again.  Title bars are back now and everything seems to work. Hopefully

---

