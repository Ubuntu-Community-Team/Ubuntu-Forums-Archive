---
title: "Compiz/Unity issues after 11.04 upgrade"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by afrodeity on 2011-05-01
Moving from a completely working installation to a partially working installation after the Natty upgrade is probably par for the course. 

I am experiencing the following issues:

Default Ubuntu session fails to invoke Unity.

No working compiz under Classic. None of the usual workarounds seem to work, eg. deleting **.compiz**. Metacity is all that works.

Have manually reinstalled the Nvidia driver several times.

Some performance issues. Am wondering if this has anything to do with the latest kernel. I am running kernelcheck's candela kernal, which was perfect under Maverick, but now the system is slow.

Some errors reported while upgrading. 

Have tried reconfiguring the applications:

dpkg --reconfigure -a

Test to show support for unity:
```

/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 8400 GS/PCI/SSE2
OpenGL version string:  3.3.0 NVIDIA 270.41.06

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

```

any help appreciated.

---

### Post by afrodeity on 2011-05-01
This saved me

```

gconftool --recursive-unset /apps/compiz-1
gconftool --recursive-unset /apps/compizconfig-1

```

Now if only I can figure out the performance issues.

---

### Post by afrodeity on 2011-05-02
To fix the kernel performance issue I did:

```


apt-get install --reinstall linux-generic

```

I also uninstalled the nvidia-nouveau and did a manual install of latest nvidia driver to avoid conflict see [here]("http://translate.google.com/translate?sl=auto&tl=en&u=http://ubuntulife.wordpress.com/2011/05/01/solucionar-problemas-con-las-tarjetas-nvidia-en-ubuntu-11-04-natty-narwhal/").

```


apt-get remove xserver-xorg-video-nouveau


```

The new unity ubuntu session is working but suffering from artifacts.

The classic ubuntu session can only handle metacity. 

Any help appreciated.

---

### Post by afrodeity on 2011-05-02
duplicated
Any help appreciated.

---

### Post by rtimai on 2011-05-02
afrodeity

No Compiz here either with open source driver for ATI M880G [Mobility Radeon HD 4200] video on an HP Pavilion dv6 laptop. I tried installing the proprietary AMD/ATI driver but had severe usability problems (obscured dropdown menus.)

HP-dv6-3012he:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD RS880
OpenGL version string:  2.1 Mesa 7.10.2

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

When I initially rebooted in Recovery Mode, I did see a windowed warning that my hardware was not compliant with advanced graphic features, and advised to use Classic Ubuntu (Metacity) desktop.

Unlike most others, however, I'm happy with Metacity. Not much for eye-candy, and didn't find the new Launcher on the left screen edge very useful. I thought it hid too many selections. I prefer to see full task menus. 

Thanks for the Unity test command, though. That was interesting, though obviously reporting WRONGLY.

Sat 2011 Jun 11
My Unity desktop troubles began after I installed themes from the Gnome3 PPA. Purging the Gnome3 PPA and removing those themes did not fix my "blank wallpaper syndrome."

I've been using Synaptic Package manager to "completely remove" Unity on each "Ubuntu" desktop login failure (to remove any residual configurations,) and re-installing every few weeks after seeing Compiz or Gnome updates. Twice no changes ("Ubuntu" desktop was blank wallpaper,) third time the charm -- the Unity desktop is now functioning! 

Hopefully others who have upgraded and have graphics systems that support Unity and still had problems with the Unity desktop may try reinstalling "Unity" (if they, like me, uninstalled it.)

I still have a problem with the "Ubuntu Classic" desktop, however. It now displays both the old Gnome Panel at the bottom and the new (non-configurable) top panel -- AND the Unity Launchbar, which should not be loading in the classic desktop. I am not going to fool around and try to fix it -- too many times I've found that changes I've made in one desktop affected other desktops, so I'm leaving well enough alone. I'll wait for this to be fixed by automatic updates.

Anyway, Unity appears to be making progress in fixing its Gnome3 theme issues. I am determined to give myself some time in it to get accustomed to it.

---

### Post by afrodeity on 2011-05-04
This works for the classic desktop. The absense of desktop effects tab in System >> Preferences >> Appearance should provide a clue. Compiz needs a basic set of plugins activated in order to work, they are Composite, OpenGL, Window Decoration, Move Window & Resize Window. You can turn them on using CCSM. 

Then: in the terminal 
```

compiz --replace ccp &

```
to launch compiz and 
```

gtk-window-decorator --replace & 
```
to get window decorations.

---

### Post by rtimai on 2011-05-30
afrodeity!

I found Kernel Mode Setting (KMS) was turned off when I reverted from the proprietary ATI/AMD fglrx driver to the open source Gallium driver, and fixed it by removing the extra parameters -- esp. 'nomodeset' -- added to /boot/grub/menu.lst.

I succeeded in activating the Unity desktop, and as a result, opened up a whole new can of worms.

As I stated earlier, I had a blank desktop (wallpaper only) when logging into the "Ubuntu" desktop... I logged out and back in to the Ubuntu Classic desktop which was fully functional, and created desktop launcher icons for gnome-terminal and gnome-control-center.
THEN I logged out of "Ubuntu Classic" and logged into "Ubuntu," used the newly-created desktop icon to open Control Center and verified Unity Plugin was activated, plus the other required items (Window Decorations listed unity-decorator, I changed it to gtk-window-decorator.) 

At this point I couldn't close the big Control Center panel, because there were no window controls, and the Terminal icon was hidden behind it. So I used Ctrl-Alt-Bkspace to restart Xorg, and used the icon in the bottom right corner to restart. I once again logged back in to "Ubuntu," used the second desktop icon to run Terminal, and ran (as you suggested):

compiz --replace ccp & ##don't know what the ccp does
 and
gtk-window-decorator --replace &

Both commands appeared to hang with the cursor on a new line with no userid. I had to Ctrl-C to stop each process. But, at this point the Unity desktop appeared! And the window decorations and functional buttons!

Wow, I thought, will it be preserved next time I log in? I restarted, logged into the "Ubuntu" desktop -- and once again, it was an empty wallpaper with no panel or launch bar. I repeated the "replace" processes again with the same result, a fully-function Unity Desktop. And again, a blank on logging back in.

THEN I found out that logging in to the "Ubuntu Classic" desktop logged me into the UNITY desktop -- PLUS the Classic (Metacity,) a HYBRID desktop with elements of both! I had moved the bottom panel of the Classic desktop to the left edge to make it "parallel" the Unity layout -- and now I had both the Gnome/Metacity panel overlapping the Compiz/Unity launch bar.

The "Ubuntu Classic (No Effects)" desktop looks (so far) like the normal Metacity-driven desktop, don't know if video acceleration is turned off or not. And the "User Defined" desktop is also the UNITY desktop -- so far.

What's infuriating is I MADE THE CHANGES ONLY WHILE LOGGED IN TO THE "UBUNTU" DESKTOP. But all the desktops appear to have switched places or combined. 

I may have to completely remove-autoremove Unity and Compiz before it drives me crazy. Unity has too many duplicated settings at different locations that overlap and conflict. 

I will keep trying different sequences, and will let you know the results. But meanwhile, I'm thinking about switching to a more SANE distro. Any suggestions? I'm thinking about a plain vanilla Debian.

Tue 2011 Jun 14
Just wanted to report here that Gnome and Compiz updates that have been successively released in the past weeks have gradually fixed all the bugs that I described earlier in the different desktop logins. Ubuntu (Unity,) "Classic Ubuntu" (Metacity,) Classic Ubuntu (no effects,) Unity 2D (I installed it,) are all functioning as expected. I think my symptoms occurred because I installed Gnome3, which I later found installed themes that overwrote parts of the Unity configuration. The Ayatana Team knows what they're doing, I think, and they deserve kudos for fixing those unforeseen incompatibilities. Maybe communication with Gnome has declined with Canonical moving away from Gnome3 to create its own direction in desktop functionality. Anyway I expect that Oneiric will have a much more stable desktop.

---

### Post by cejack on 2011-06-01
Check out the following video:

[https://public.me.com/cejack](https://public.me.com/cejack)

Hate to rub it in but maybe I'm just lucky. 

I loaded up compiz settings manager and fusion icon and then just set up some eye candy and it started working after a while.  

I have a "non-unity" card (geForce FX 5900XT) see below.  As you can tell, I get application switching, wobbly windows, desktop cube with 3D, and cover page window switching.  

This is a brand spanking new install with X86 ShuttleX (sn41g2) that I am re-purposing from an old Windows XP install.  

This is fairly old crusty hardware.  (Note:  I am NOT using the built-in NForce 2 graphics to drive the monitor.)  Athlon XP 2200+ single processor with 2gb memory.  

Pretty wimpy stuff but it appears to work.  I do have the same problem as others..."This driver is activated but not currently in use" showing in the additional drivers screen.  


$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5900XT/AGP/SSE/3DNOW!
OpenGL version string:  2.1.2 NVIDIA 173.14.30

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

---

