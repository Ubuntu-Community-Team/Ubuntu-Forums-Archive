---
title: "Login screen - resolution problems"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by prospectofdeath on 2005-02-15
I'm not sure if this is the right forum for this question so I apologize in advance if I'm wasting your time.

My setup is fairly standard AMDXP 3000/Nvidia 5600xt system running Warty with the latest universal patches. Ubuntu installed without any problems and after following the instructions on ubuntuforums.org I was able to get the Nvidia drivers installed. I've got my desktop resolution set at 1280x1024 and things look great.

Here's the crux of my problem:

The Ubuntu the login screen is set at a resolution of 1024x768 (I'm guessing here, how can I tell what the actual resolution is?). When I log into my account the screen changes to 1280x1024. When I log back out the resolution is gets reset incorrectly for the login screen. It appears that it's keeping the screen 'size' but changing the resolution. As a result the black bar at the bottom, containing Shutdown & Restart 'buttons', are off the screen.

I can log in after logging out and I can restart & shutdown using the Alt key so this isn't a very serious problem, just one that I've never encountered before.

Ideas? Help? Am I making any sense?

---

### Post by now_acc on 2005-02-20
I have the same problem.

Where is setting to change resolution of logging screen?

---

### Post by bored2k on 2005-02-20
[QUOTE=now_acc]I have the same problem.

Where is setting to change resolution of logging screen?[/QUOTE]

i dont have that problem, but maybe login in as root and changin res. from there :roll: 

for that ud hav to trick sudo to 
sudo su; passwd su  :wink:

---

### Post by wallijonn on 2005-02-20
You may want to try a different GDM. 

[http://art.gnome.org/themes/gdm_greeter/](http://art.gnome.org/themes/gdm_greeter/)
[http://www.gnome-look.org/index.php?xcontentmode=150&PHPSESSID=4189b8bd2973d93465f21c0cae90a5da](http://www.gnome-look.org/index.php?xcontentmode=150&PHPSESSID=4189b8bd2973d93465f21c0cae90a5da)
[http://www.customize.org/list/ggdm](http://www.customize.org/list/ggdm)

I'm hoping that by changing the GDM it will force a resolution "keep" on logout and log back in.

---

### Post by crane on 2005-02-20
What does your XF86Config-4 have listed in it about resolution? Should be under the monitor settings I believe.

---

