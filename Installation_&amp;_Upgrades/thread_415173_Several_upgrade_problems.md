---
title: "Several upgrade problems"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Fuzzy Logic on 2007-04-20
Hello fellow Ubuntu users!

I upgraded Ubuntu yesterday from Edgy to Feisty, since then I experienced few problems where I'm not really happy with.

When I upgraded, the upgrade program asked me to reboot, so I did that. While loading, I immediatly saw something strange. The GRUB showed me really lot of kernel versions I could choose from. To be precise, these:
2.6.20-15-386
2.6.20-15-lowlatency
2.6.20-15-generic
2.6.17.11-generic
2.6.17-10-386
2.6.17-10-generic
memtest86+

This was strange to me, but I tought the best would be to choose the newest 386 version, so I did that. But when it booted, I didn't get the graphical login window but the classic Linux terminal. I logged in and typed 'startx', this gave me an error. Booting the old kernel, that I used before upgrading, gave the same result. So I edited the xorg.conf file and changed the name of the video driver from 'nvidia' to 'nv'. Xorg finally booted.

When I logged in, I noticed my internet didn't work. As well as Beryl. So I booted to the old 386 kernel and there internet worked but Beryl still didn't. When I type 'beryl-desktop' i get the following error:
> fuzzy@FUZZNET:~$ Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
I have to use the normal Gnome Dekstop Manager in order to be able to have a desktop manager.

Can anyone please help me with these problems? My PC is really important in my daily life, so I need to have it working without any problems.

Much thanks in advance!

---

### Post by rich.bradshaw on 2007-04-20
Have you tried System/Administration/Restricted Drivers to install your nvidia graphics card?

THis might sort you out...

I think the old Envy script if you used it can mess things up... maybe someone else knows... Try that for now...

---

### Post by anachreon_ on 2007-04-20
Fuzzy, are you using an nVidia graphics card?  If so, do you have the "envy" script installed on your system (it can be used to automatically download the nVidia driver and configure it).

I've found that when using a proprietary graphics driver, upgrading some base packages related to the X server basically overwrites your xorg.conf and will break things like beryl.  When that happens, I reinstall the graphics driver and reconfigure xorg.conf.  

Recall that when you installed beryl the first time, you probably had to insert some special lines into your xorg.conf, right?  Those probably aren't there any more, causing your beryl not to work.

---

### Post by Fuzzy Logic on 2007-04-20
Wow, you people are awsome, in less than 5 mins 2 answers. Much thanks, I installed the restriced drivers. Now i have to reboot, I will tell you how it went.

---

### Post by Fuzzy Logic on 2007-04-20
Too bad, I installed the nVidia driver as rich.bradshaw suggested, but when I wanted to boot the old 386 kernel hanged on an empty black screen. So I edited the xorg.conf file again because the driver I installed changed the name of the driver from 'nv' to 'nvidia'. And now I go to System > Administration > Restriced Drivers Manager the program says that the two nVidia drivers I chose aren't used at the moment.

So the problem of the whole thing is the nVidia driver I guess. Altough I don't really get it why my GRUB list is so big while I just need the newest 386 kernel that preferrably WORKS. But that is not the case.

I will now try to install envy as anachreon_ suggested, but I don't have hope it will work.

Can anyone please help me? This sucks...

**EDIT:** I could not find envy in the Synaptic Package Manager, is there other way to install it?

---

### Post by madcow72 on 2007-04-20
Just a quick suggestion:  if you can't get in to X, you will probably want to disable Beryl.  I assume Beryl is set to  startup when you log in, but if your graphics drivers aren't working then it could cause your system to hang.  When turn on your computer and it loads up, do a 
CTRL+Alt+F1 to get to a terminal.  
Log in.
```
sudo aptitude remove beryl emerald-themes
sudo /etc/init.d/gdm restart
```
(If you're using Kubuntu, change "gdm" to "kdm" in that last line)  and see if this helps you to get into your Desktop session.

---

### Post by madcow72 on 2007-04-20
No, envy isn't in the repositories.  You could do this:
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.2-0ubuntu1_all.deb
sudo dpkg -i envy_0.9.2-0ubuntu1_all.deb
sudo envy
```

Alberto Milone wrote and distributes [envy]("http://albertomilone.com/nvidia_scripts1.html") from his server.

---

### Post by Fuzzy Logic on 2007-04-20
I can't get it working, it says i need to install dependencies, and when I try to install them I get this message:
> The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
Do you really think this will solve my problem? Becuase I have the feeling that it won't.

---

### Post by madcow72 on 2007-04-20
You should just be able to do:
```
sudo aptitude install build-essential
```
and then try running envy again.  Any time you get an unmet dependency, you should be able to install it just like above.

First, however, I would try uninstalling beryl and logging back in.  Did you try that yet?

---

### Post by anachreon_ on 2007-04-20
By the way, fuzzy, if you end up using Envy, you will have to get the "unstable" version that actually supports Feisty.  When I initially upgraded to Feisty and couldn't load into KDE, I tried using the old Envy, but it complained about not supporting my version of the OS.  So I restarted, selected the previous (edgy) Kernel and installed the new version of Envy from there.  Then, when booting Feisty I logged into the command prompt and did "sudo envy" and uninstalled / cleaned my previous installation, then re-installed the driver.  Keep in mind that if you ever get a blank screen you probably just need to select your terminal with ctrl+alt+f1.

Here's where you can get the script.

[http://albertomilone.com/wordpress/](http://albertomilone.com/wordpress/)

---

### Post by Fuzzy Logic on 2007-04-21
Thanks people, I appreciate your help.

I installed Envy, but while installing the nVidia driver I got the following error:
> Bad luck, the kernel headers for the target kernel version could not be found and you did not specify other valid kernel headers to use.
Is this maybe because of the fact that I'm running the old kernel right now? (it says that i'm running feisty dough). If that is the case, then I first have to solve the internet problem on the new one before I plan to use it. Does anyone have ideas why that doesn't work? I'm using Intel Pro Wireless 3945...

---

### Post by Fuzzy Logic on 2007-04-21
Well.. I'm glad to tell you that i got the new kernel working, the problem was that I didn't have internet because I didn't have the packages for the restricted drivers program installed, so I connected to a wired connection, installed the package and enabled the wireless drivers, now everything works. I still have to figure out why Beryl doesn't work, but the nVidia driver works now fine.

I think I just have to edit Xorg.conf file like I did when I first installed beryl, like anachreon_ suggested. I will get to that when I solve a little problem with VMware that is on my to-do list for a while now.

Thanks for everything guys, you are wonderful.

---

