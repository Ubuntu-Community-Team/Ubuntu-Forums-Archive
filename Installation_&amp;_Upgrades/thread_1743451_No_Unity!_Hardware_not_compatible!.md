---
title: "No Unity! Hardware not compatible!"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by pooja on 2011-04-29
After upgrading to Ubuntu 11.04, I am told that the hardware is not compatible with Unity, therefore the system boots immediately into a normal, compiz-less OS.
I managed to install CompizConfig Settings Manager but after I chose "Wobbly Windows" it still won't show any sings that it's using compiz.
Remember when all we used to do was:

System &#9656; Preferences &#9656; Appearance &#9656; Visual Effects

Well, there's no "Visual Effects" tab. How to move on?
I'd like to understand why I'm not even offered the chance to choose between Unity and Ubuntu Classic.
Also, what happened to all the Visual Effects? How do I enable them?

thanx.

---

### Post by MAFoElffen on 2011-04-29
> **pooja said:**
> After upgrading to Ubuntu 11.04, I am told that the hardware is not compatible with Unity, therefore the system boots immediately into a normal, compiz-less OS.
I managed to install CompizConfig Settings Manager but after I chose "Wobbly Windows" it still won't show any sings that it's using compiz.
Remember when all we used to do was:

System &#9656; Preferences &#9656; Appearance &#9656; Visual Effects

Well, there's no "Visual Effects" tab. How to move on?
I'd like to understand why I'm not even offered the chance to choose between Unity and Ubuntu Classic.
Also, what happened to all the Visual Effects? How do I enable them?

thanx.
At the GDM login screen, after you clck on a user and the password boxx comes up.... > you will notice an item on the bottom bar mid-way across that says what  you want to boot into (Unity, Ubuntu, Ubuntu Classic, Kubuntu, Xubuntu... etc, if installed or capable.)  Anyways, yes, it checks your hardware (video) and sees if your drivers and hardware can run 3D Unity.  Many people during testing had to configure things in Classic, then try it booting into unity.  

If after all you try and it still says your video combination can't run it...  There is a 2D version of Unity that you can try in the repositories. (Synaptic)  You would have to go to synaptic to download and install that.The "Classic," is still there if nothing else.

---

### Post by KegHead on 2011-04-29
Hi!

For classic;

system...admin..login..chose classic..reboot.

KegHead

---

### Post by pooja on 2011-04-29
[QUOTE='MAFoElffen']after you clck on a user and the password boxx comes up.... > you will notice an item on the bottom bar mid-way across that says what you want to boot into [/QUOTE]

Haven't noticed anything like that. Will try right away. Have enabled Nvidia drivers (recommended versions). Attaching 3 screen-shots of Nvidia drivers and present Desktop.

---

### Post by pooja on 2011-04-29
[QUOTE='KegHead']Hi!

For classic;

system...admin..login..chose classic..reboot.[/QUOTE]

I really would like to try Unity rather than classic. Want to try new things

---

### Post by MAFoElffen on 2011-04-29
> **pooja said:**
> Haven't noticed anything like that. Will try right away. Have enabled Nvidia drivers (recommended versions). Attaching 3 screen-shots of Nvidia drivers and present Desktop.
What Nvidia "card" are you using? I have various here, which some of my older ones won't run 3D unity (even though those older cards ran 3D successfully in older versions of Ubuntu), but those older ones will still run 2D Unity.  

I'm using the same driver that you have highlighted on "this" box here with 2 Geoforce 6800 GTX Ultra's in SLI.

---

### Post by sikander3786 on 2011-04-29
Can you please post the output of this command.

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by perettigiuliano on 2011-04-29
> **pooja said:**
> After upgrading to Ubuntu 11.04, I am told that the hardware is not compatible with Unity, therefore the system boots immediately into a normal, compiz-less OS.
I managed to install CompizConfig Settings Manager but after I chose "Wobbly Windows" it still won't show any sings that it's using compiz.
Remember when all we used to do was:

System &#9656; Preferences &#9656; Appearance &#9656; Visual Effects

Well, there's no "Visual Effects" tab. How to move on?
I'd like to understand why I'm not even offered the chance to choose between Unity and Ubuntu Classic.
Also, what happened to all the Visual Effects? How do I enable them?

thanx.


Same here!
I am trying on 2 different hardware: a desktop and a netbook where previously 10.10 was working great!
I am gonna say tha this version is a mess..

If someone has info about please spread all over, many many peoples are damning 11.04

---

### Post by KegHead on 2011-04-29
Hi!

From what I can gather, Unity is not supporting some video cards.

If I incorrect, please correct me!

KegHead

---

### Post by whitefort on 2011-04-29
> **perettigiuliano said:**
> 
If someone has info about please spread all over, many many peoples are damning 11.04

I know.  i hate it.  I installed it on a computer that was running Compiz with no problems, now I can't even get compiz again, never mind Unity.  And on my other PC, not even the live CD would run.

I guess 11.04 is for the 'elite' who happen to have the right graphics cards!

---

### Post by nexus9k on 2011-04-29
> **sikander3786 said:**
> Can you please post the output of this command.

```
/usr/lib/nux/unity_support_test -p
```

Is it possible to run this script or a similar Unity compatibility check tool *before* upgrading to 11.04 (from 10.10) and exploring Unity?

---

### Post by sikander3786 on 2011-04-29
> **nexus9k said:**
> Is it possible to run this script or a similar Unity compatibility check tool *before* upgrading to 11.04 (from 10.10) and exploring Unity?
I think you can try an Ubuntu 11.04 Live CD (even the classic GNOME session). Not sure about older releases though.

---

### Post by MAFoElffen on 2011-04-29
> **KegHead said:**
> Hi!

From what I can gather, Unity is not supporting some video cards.

If I incorrect, please correct me!

KegHead
@KegHead

Yes... We found that out in testing.  This sticky should help out for some with the graphics issues:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

But 3D Unity is "requiring" specific hardware requirements.  Remember in testing?  There was a lot of discussion of "if not, then install 2D Unity..."  I have quite a few cards I tested that did compiz and 3D fine in earlier version of U, but will not run 3D Unity. But when we got from beta1 to beta 2.. RC... Release-- some graphics issues that existed before still changed with updates to the current drivers.

I'd expect that these other driver changes and updates are still coming and will carry through with some of the "lower than" hardware... but they're still going to have to draw the line somewhere.  In the meanwhile, there's still Unity 2D, Gnome Desktop 3.x and Classic.

---

### Post by pooja on 2011-04-29
> **sikander3786 said:**
> Can you please post the output of this command.

```
/usr/lib/nux/unity_support_test -p
```

This is what I get:

```
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce Go 7400/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```

From what I have gathered so far, we need to do a clean install for this release, then things will work flawlessly, others have tried. Meanwhile I have installed Unity 2d from Synaptic: that's the closest you can get to using Unity on Natty. Totally disappointed with this version of Ubuntu.

*If only Compiz worked!*

---

### Post by KegHead on 2011-04-29
Hi!

I've heard/read this for quite awhile.

Unity seems to be cool if you're machine is up to date with a lot of goodies!

I'm stuck with a dell mini 9, self made atom 330 desktop and two old laptops!

That's the reason for 11.04/classic!

KegHead

---

### Post by sikander3786 on 2011-04-30
> **pooja said:**
> This is what I get:

```
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce Go 7400/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```

From what I have gathered so far, we need to do a clean install for this release, then things will work flawlessly, others have tried. Meanwhile I have installed Unity 2d from Synaptic: that's the closest you can get to using Unity on Natty. Totally disappointed with this version of Ubuntu.

*If only Compiz worked!*
Your graphics card is capable of running Unity but it has been blacklisted due to some problems that other users faced. Still, there is a workaround.

[http://ubuntuforums.org/showpost.php?p=10731067&postcount=2](http://ubuntuforums.org/showpost.php?p=10731067&postcount=2)

---

### Post by bluevoter on 2011-04-30
One of my Ubuntu installations is a virtual appliance on my MacBook Pro running VMware Fusion 3.  The machine has an NVIDIA GeForce graphics card, so I thought that the 3D Unity GUI would come up.

After the standard upgrade came up with GNOME instead of Unity, I ran Synaptic, selected Unity 2D, then downloaded and installed the 2D Unity with the associated libraries.  When I restarted my Ubuntu instance, the Unity 2D interface was the default startup choice, and everything came up just fine.

I think that it's just a matter of time before VMware upgrades Fusion or creates a new virtual appliance for Natty.  For now, though, the 2D Unity solution is the best alternative

---

### Post by pooja on 2011-04-30
From the link you've given:
[QUOTE='mikewhatever']Nvidia 7300/7400 go cards had been blacklisted because of problems people had with them. You can override the blacklisting by adding UNITY_FORCE_START=1 to /etc/environment. For more info, see the bug report:
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/728745](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/728745)[/QUOTE]

So I tried this command from Terminal:
```
sudo gedit /etc/environment
```

And this is what I get back:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

So the question is: where should I type "UNITY_FORCE_START=1" ?

---

### Post by pooja on 2011-04-30
I've found this [link]("http://http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity") therefore I have changed to nvidia version 173 (see attachment) and will try rebooting. Let's see, keeping fingers crossed.

---

### Post by pooja on 2011-04-30
Not working!
Through Synaptic I removed the Unity 2D package and then rebooted. When asked what system I'd like to start up, I chose Ubuntu thinking it would show me to Unity 3D but no, it's Ubuntu 11.04 with the 3 menus Applications, Places, System. 
Did I do something wrong? Should I have written "UNITY_FORCE_START=1" at the end of "PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games" " instead of the beginning?

Compiz still not working!

---

### Post by horace on 2011-04-30
> **pooja said:**
> Not working!
Should I have written "UNITY_FORCE_START=1" at the end of "PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games" " instead of the beginning?


Just add it on a new line.
hth

---

### Post by pooja on 2011-04-30
OMG! OMG! I got it!
It's awesome!
I just installed Compiz Fusion (the only Compiz package I had not yet installed) then loaded it. A blue cube with an arrow appeared on the top right corner of the desktop. I right-clicked on it and opted for "Reload Window Manager" and then puff! It all fell in the right place. Now I have the three menus AND the sidebar of Unity 3D!
BTW, I used Gedit to save the "/etc/environment" file because "sudo **nano** /etc/environment" was not saving the edit. I did "sudo gedit /etc/environment", added the new line and saved it, as stated initially.

It works now! Don't know if it will stay on reboot though.

SO to summarize it all:
1. I installed Compiz Window Manager (yesterday)
2. Changed the Nvidia Driver to version 173 (System>Administration> Additional Drivers> Nvidia 173, requires reboot)
3. Through Terminal I gave ```
sudo gedit /etc/environment
``` and added  "UNITY_FORCE_START=1", then saved and closed Gedit. (Today)
4. I installed Compiz Fusion through Ubuntu SW Centre, enabled it and Reloaded the windows manger.
That's it!
Check out my new desktop. 
Hope it stays on my next reboot!
Will let you know.

---

### Post by hackie on 2011-04-30
Installed 11.04 just now. Was disheartened to see the same error. Will try your steps pooja.

Hope it works. Thanks :)

---

### Post by pooja on 2011-04-30
Unfortunately on reboot, Compiz Fusion's effects, disappear. Any ways to get it working at start up? Otherwise I have to manually load Compiz Fusion (Applications> System Tools > Compiz Icon) everytime.

---

### Post by hoboy on 2011-04-30
> **pooja said:**
> OMG! OMG! I got it!
It's awesome!
I just installed Compiz Fusion (the only Compiz package I had not yet installed) then loaded it. A blue cube with an arrow appeared on the top right corner of the desktop. I right-clicked on it and opted for "Reload Window Manager" and then puff! It all fell in the right place. Now I have the three menus AND the sidebar of Unity 3D!
BTW, I used Gedit to save the "/etc/environment" file because "sudo **nano** /etc/environment" was not saving the edit. I did "sudo gedit /etc/environment", added the new line and saved it, as stated initially.

It works now! Don't know if it will stay on reboot though.

SO to summarize it all:
1. I installed Compiz Window Manager (yesterday)
2. Changed the Nvidia Driver to version 173 (System>Administration> Additional Drivers> Nvidia 173, requires reboot)
3. Through Terminal I gave ```
sudo gedit /etc/environment
``` and added  "UNITY_FORCE_START=1", then saved and closed Gedit. (Today)
4. I installed Compiz Fusion through Ubuntu SW Centre, enabled it and Reloaded the windows manger.
That's it!
Check out my new desktop. 
Hope it stays on my next reboot!
Will let you know.

Nmmmmmmmmmmm this is not working for me :(

---

### Post by dyetheskin on 2011-04-30
i get this but no go for me.

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

if i login the panels dont load and a drive icon on desktop flashes every now and then which basically is a total freeze

---

### Post by SeaWeedz on 2011-05-06
So very strange....  Same error here.  

1) The error even pops up looking pretty old-school and ugly.  

I don't understand..  at least have that error screen show something informative..  maybe a checklist of what requirements aren't being met.  The way it works now feels entirely broken.

I have a hp dv8000, ssd hard drive.. geforce go 7400.  Things should be beautiful :(  not all glitchy.  

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no


2) So when I go to start the install sequence, the Ubuntu boot screen shows up looking beautiful.  Then, once it's installed and booting from my hard drive, it's like the fact that I'm using nVidia then starts to cause all of these glitchy oddities.  

3) Same with shutdown..it's not even a shutdown screen - its like a console log with some dots being displayed.

4) In the "Additional Drivers" section it states
"Required if you want to run Unity" and
"You need to install this driver if you wish to use the Unity desktop..."

this isn't even accurate

---

### Post by mobabur94 on 2011-05-07
> **dyetheskin said:**
> i get this but no go for me.

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

if i login the panels dont load and a drive icon on desktop flashes every now and then which basically is a total freeze

i have the same results as you; i too have a fx5200
i'm experiencing the same stuff too. this sucks :(

---

### Post by calande on 2011-05-08
Hi guys, my Unity bar is black with no icon, has one of you had this problem? Do you know how to solve it? Thanks! :)

---

### Post by sagir42 on 2011-05-10
Hi friend.
I just failed to install Ubuntu 11.04 with unity. My graphics card is GF 9500GT 550M 1GB DDR2 TV DVI PCI-E. I tried to install nvidia-current and nvidia open source 3d driver. But always I failed. My ubuntu is not opening. Finally I got a red screen and there have nothing to do. Please help me friend. I am waiting for your advise.

---

### Post by shonick on 2011-06-28
~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no




I have NVIDIA on my machine (using it on OS windows 7), why do I see Mesa here when I run this code? 

Can I change to NVIDIA and have Unity?

Thanks

---

### Post by shonick on 2011-06-28
> **pooja said:**
> OMG! OMG! I got it!
It's awesome!
I just installed Compiz Fusion (the only Compiz package I had not yet installed) then loaded it. A blue cube with an arrow appeared on the top right corner of the desktop. I right-clicked on it and opted for "Reload Window Manager" and then puff! It all fell in the right place. Now I have the three menus AND the sidebar of Unity 3D!
BTW, I used Gedit to save the "/etc/environment" file because "sudo **nano** /etc/environment" was not saving the edit. I did "sudo gedit /etc/environment", added the new line and saved it, as stated initially.

It works now! Don't know if it will stay on reboot though.

SO to summarize it all:
1. I installed Compiz Window Manager (yesterday)
2. Changed the Nvidia Driver to version 173 (System>Administration> Additional Drivers> Nvidia 173, requires reboot)
3. Through Terminal I gave ```
sudo gedit /etc/environment
``` and added  "UNITY_FORCE_START=1", then saved and closed Gedit. (Today)
4. I installed Compiz Fusion through Ubuntu SW Centre, enabled it and Reloaded the windows manger.
That's it!
Check out my new desktop. 
Hope it stays on my next reboot!
Will let you know.

How do you keep the top bar on your screen,

Which program do you use to have the bar at the bottom?
[http://ubuntuforums.org/attachment.php?attachmentid=190499&d=1304161876](http://ubuntuforums.org/attachment.php?attachmentid=190499&d=1304161876)

---

### Post by Fajer on 2011-07-31
after: /usr/lib/nux/unity_support_test -p
```
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no
```

I have HP Pavilion dv6331 notebook GeForce GO 7400

Do I have any chance to run Unity 3D?

---

