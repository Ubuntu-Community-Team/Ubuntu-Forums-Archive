---
title: "First time user. Installed Ubuntu. Failed right after installtion when I restarted.."
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by rzzzz on 2011-02-19
Hey,
 
First time Linux user, pretty disappointed. Seems like a lot of people having problems with Ubuntu. Looking for Windows substitute, not so sure anymore...may have to stick with the dark side...
 
Still, don't want to give up just yet.
 
Burned ISO image on CD. Booted CD, installed Ubuntu, no problem.
 
Right after installation, update manager asked to download about 225mb's in updates. Did so. Restarted "to complete updates".
 
Froze when checking battery state (did not get to graphics interface). Restarted. Took me straight to DOS looking prompt (not sure what it's called). Logged in. Cannot get to graphics/windows interface. Typed gdm, didn't work. Some sort of security failure?
 
Only way to get to windows/graphics interface is to start in safe mode. Which works fine. But didn't switch to linux to start in safe mode each time.
 
Help?

---

### Post by Sean Moran on 2011-02-19
> **rzzzz said:**
> Hey,
 
First time Linux user, pretty disappointed. Seems like a lot of people having problems with Ubuntu. Looking for Windows substitute, not so sure anymore...may have to stick with the dark side...
 
Still, don't want to give up just yet.
 
Burned ISO image on CD. Booted CD, installed Ubuntu, no problem.
 
Right after installation, update manager asked to download about 225mb's in updates. Did so. Restarted "to complete updates".
 
Froze when checking battery state (did not get to graphics interface). Restarted. Took me straight to DOS looking prompt (not sure what it's called). Logged in. Cannot get to graphics/windows interface. Typed gdm, didn't work. Some sort of security failure?
 
Only way to get to windows/graphics interface is to start in safe mode. Which works fine. But didn't switch to linux to start in safe mode each time.
 
Help?
I'm sorry.  I've had a few problems before with my nVidia drivers when I try to install proprietory software before HDD installation but never had troubles with reboot after an update. Maybe something in your hardware that is not fully recognised, but overall, Ubuntu can do better than that.

DOS-looking prompt is colloquially known as 'command line' or 'cli' or (if you have a GUI running), 'terminal'.

To find the cause of the problem, do you see any error messages if you press CTRL+ALT+F1?   Also, another way to get back to the GUI is 'startx' although that's not helping the normal automatic GUI login, but maybe if 'startx' gets you to your desktop, we can be sure that something is working okay on your graphics driver, and backtrack from there.

This is not the usual, so that's why I want to sort it out quicksmart.

---

### Post by Rubi1200 on 2011-02-19
What graphics card do you have installed?

Was this a regular install or via Wubi?

If you still have Windows on the machine are you able to boot into it normally?

---

### Post by rzzzz on 2011-02-19
Thanks guys, I think you got it. Definitely graphics card related. 

I'm not sure what wubi is, so I think I installed it regularly. Windows boots just fine. I do have an NVIDIA graphics card 

When I click Crtl + Alt + F1 it says something about Nvidia configuration failure.

When I am in the terminal and type gdm it says something about "failed to acquire org.gnome.displaymanager"

I click Nvidia X Server settings (while in safe mode) and it says "does not appear to be using Nvidia X Driver. Edit X config file and restart x server"

I type xstart (in terminal) and says something about no screens found.

So all signs point to monitor/graphics card. At least we know what the problem is!

Any suggestions on what to do next? Sorry if this is obvious to you guys, but I'm realllllly out of my comfort zone. I would appreciate any help!

---

### Post by dino99 on 2011-02-19
ok, lets go for a try :)

into a terminal:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo rm /etc/X11/xorg.conf

sudo apt-get install nvidia-current
sudo apt-get install nvidia-common
sudo apt-get install nvidia-settings

(the 3 commands above are allowed with all ubuntu but natty)

sidenote: its a good idea to give the exact config when you ask for help: which ubuntu: maverick ? i386 (32bits) or amd64 (64bits) ? which desktop: gnome, kde, xfce, lxde ?
well everything usefull but blah blah

---

### Post by rzzzz on 2011-02-19
umm you rock.

Did all that, restarted, logged in just fine. Graphics were a bit off. Restarted again, seems to be working fine for now. THANKS!

Noted, will be more specific next time for sure!

---

### Post by rzzzz on 2011-02-19
Hmm although now there is no sound, there was though.

I installed the 32 bit version, not sure what desktop. I downloaded and installed yesterday off the ubuntu website (desktop version)

---

### Post by rzzzz on 2011-02-19
Gnome desktop

---

### Post by dino99 on 2011-02-19
about sound:

- check hardware detection: menu -> system pref sound

if your hardware is well detected, then check that everything is unmute; install (with synaptic) gnome-alsamixer

then goto: applications sound & video alsamixer, and set sound levels for your needs, mute/unmute as you like

then into a terminal:

sudo dpkg-reconfigure pulseaudio

good luck :)

---

### Post by rzzzz on 2011-02-19
Oh wow. This is wayy too complicated for me haha...

cannot even find the "system pref sound", no clue what synaptc is...

I do know everything is muted...

Thanks for the help buddy, but I'm pretty close to giving up, this is far from user friendly, certainly not for first time users anyway

---

### Post by rzzzz on 2011-02-19
I mean unmuted

---

### Post by rzzzz on 2011-02-19
i mean unmuted

---

