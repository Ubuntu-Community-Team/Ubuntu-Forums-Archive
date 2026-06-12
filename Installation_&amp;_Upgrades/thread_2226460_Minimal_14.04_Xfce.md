---
title: "Minimal 14.04 Xfce"
date: 2014-05-27
forum: Installation &amp; Upgrades
---

### Post by Andrew_Lucas on 2014-05-27
Hi all,

This is more of a 'check I'm on the right lines' rather than 'fix my problem' thread.

I'm a bit of a perfectionist, and have decided that _buntus comes with  too much 'junk' installed (packages that I don't need or want).

Having  looked into Arch, and deciding that the effort/skill required to  maintain it is beyond me, I've come round to the idea of setting up a  minimal installation. This lets me have to have an 'Arch-like'  experience (i.e. only packages I want will be installed), but once set  up, I shouldn't have to worry about the rolling release cycle breaking  things, as well as saving me from learning the nuances of another package manager. (I've also tried Bodhi, and I like everything about it apart from Enlightenment - unfortunately, Bodhi *is* E17). I'm also hoping this is something of a learning experience, and that I'll gain knowledge of my chosen packages. There's a great line in the 'Package Management' section of LFS, about how some people use *no* package management, because they know their system intimately. Whilst I'm a long way off that, it's fun to dream...

My DE of choice is Xfce. What I want after installation of the following packages is a desktop (with the Whisker menu) and some basic administrative utilities, but as little else as possible (call this 'Stage 1', where installing the minimal iso is 0, applications is 2, configuration is 3). The list will be installed with the **--no-recommends** argument.

Package list:

```
thunar
xfce4-mixer  
xfce4-panel
xfce4-session
xfce4-settings
xconf
xfdesktop4
xfwm4
xfce4-notifyd
[B]xserver-xorg
xinit[/B]
gtk3-engines-xfce
xfce4-power-manager
thunar-archive-plugin
thunar-media-tags-plugin
xfce4-artwork
xfce4-battery-plugin
xfce4-clipman-plugin
xfce4-cpufreq-plugin
xfce4-cpugraph-plugin
xfce4-datetime-plugin
xfce4-dict
xfce4-diskperf-plugin
xfce4-fsguard-plugin
xfce4-genmon-plugin
xfce4-mount-plugin
xfce4-netload-plugin
xfce4-quicklauncher-plugin
xfce4-screenshooter
xfce4-sensors-plugin
xfce4-systemload-plugin
xfce4-taskmanager
xfce4-terminal
xfce4-volumed
xfce4-xkb-plugin
xfce4-power-manager-plugins
xfce4-whiskermenu-plugin
lightdm
lightdm-gtk-greeter
 xdg-user-dirs
dkms
light-locker
light-locker-settings

```

Note: I do realise xfce4-artwork is just eyecandy, but since this list was created with the help of the dependencies listed on the Ubuntu package search site, I've stuck it in here. The same applies to the plugins - I've already discarded ones I think I won't use.

Questions:
1) Are there any obvious ***necessary*** packages missing (necessary not in so far as dependencies - I know apt will pick these up - but in so far as functionality)?

2) The two bold packages, I'm unsure about - xinit I've read in one place isn't needed since LightDM will handle starting X, whereas another source said it was needed. With xserver-xorg, logic dictates that it is of course needed, but unless its so far down the dependency chain I've not seen it, I can't find it listed as a dependency for the Xfce packages (e.g. xfce4-session, xfwm4, xfdesktop4). LightDM only *recommends* the xserver-xorg package too.

3) As part of the minimal installation, I've disabled root (so will be controlling the system with sudo). Do I need to manually add myself to the sudoers group, or would that be done already (i.e. as a consequence of root being disabled)?

4) Aside from installing packages, and fiddling with settings in the GUI to get things how I want them, are there any tasks which are automatically done by the 'normal' _buntu installer but not by the minimal one, that would need doing manually? This is really more of a generalisation of (3).

Ta!

---

### Post by Bashing-om on 2014-05-27
Andrew_Lucas; Hi ! My Welcome to the forum.

I run minimalistic install with xfce4 as the DE. You are making this much more complex than what it is.
What I suggest that you do ( highly suggest), once you have the core install completed:
```

sudo apt-get install xorg
sudo apt-get install xfce4

```
Install similarly your choice of a web browser ->
and you are done with the basic set up. You do have a fully functional desktop installation with most everything on your list.

As you are seeking the minimal, I would not even install lightdm, or a desktop manager ( start the gui desktop from terminal -> startxfce4 ).
Once you are done with the core installation
installed xorg
installed xfce4
installed a web browser
I suggest ya take a look at what you have now, then see what you may want to add.
Consider what changes you want to make in the basic config , and take your time doing so.

xfce4 is highly configurable and customize-able. Just a matter of finding what file does what/where.
I boot in @ 5 seconds and this setup is very fast - even on my "older" hardware.

When you are ready to consider, we will discuss package management, updates and upgrades, and system housecleaning, all simple and easy - just needs to be done routinely.

[INDENT][INDENT]I agree,
[INDENT][INDENT][INDENT][INDENT]simple is better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by PJs Ronin on 2014-05-28
Add me the the 'interested bystanders' list.   I have an old lappie that I'm trying to resurrect and like the OP have settled on an X brand buntu with xfce starting with a mini.iso and building up from there.   TBH, I think there is a good demand for this concept and hopefully in the process will teach an old dog (moi) a new trick or two.

---

### Post by Bashing-om on 2014-05-28
PJs Ronin; Hi ! Welcome to the club.

OK, if one knows what they are doing, and seeking the smallest footprint, one may do a number like:
```

apt-get install --no-install-recommends xorg xfce4

```
to have a very very minimal install. It is on you to install any of the amenities of a modern day desk top. It can be fun figuring out what is missing - say for instance 'anacron'; so log-rotate functions.

You may find that you must set up DISPLAY and XAUTHORITY variables from the environment of #a running X application, for example the XFCE panel or another application #that surely are running on the system. As you may find permission issues for a number of other processes, it will indeed be a learning experience.

Patience and tenacity are virtues -> I generally avoid the hassle of
[INDENT][INDENT][INDENT]re-inventing the wheel; someone has already "configured" what these basic necessities are
[/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-05-28
*Thread moved to **Installation & Upgrades**.*

> **Bashing-om said:**
> 
I run minimalistic install with xfce4 as the DE. You are making this much more complex than what it is.
tion

^^^
This. And this:
> **Bashing-om said:**
> 

OK, if one knows what they are doing, and seeking the smallest footprint, one may do a number like:
```

apt-get install --no-install-recommends xorg xfce4

```


I would add 'synaptics' to that command then install whatever you like through that or a terminal (you could also add 'lxterminal' or another terminal, but xfce4 will drag one in from memory). 

I only use the minimal install with xfce4 and a select handful of my favourite and/or required apps. Good luck. ;)

PS: A good tip would be to *just* make a list of the apps you want/or need and don't worry about the rest. Installing xfce4 will take care of most of the other stuff on your list and what it doesn't you can worry about if there's a problem, which there probably won't be. I've never had one and never installed half the stuff on your original list.

PPS: When you get to the section of the minimal install that asks if you want the machine set up with a profile of some kind, e.g. server, audio, etc., don't choose anything. Once the kernel is installed you will reboot to a cursor for log in. Once in, run the 'sudo apt-get install ...' line and reboot when it's done.

---

