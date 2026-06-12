---
title: "Gnome Desktop Enviroment don't show up"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by Libertario on 2011-04-05
Hi all,

I have a problem with Live CD and installation of Ubuntu Maverick over my PC.

When I run Live CD the system seems load successful but, after listen start session sound, only show up background. I never see Desktop Enviroment. I can run terminal tty and work over it.

After this I installed Ubuntu Maverick thinking that perhaps this were the solution but not were.

The system load properly but, after logged me in (I can work with login screen), I only can see background but not Gnome Desktop Enviroment. I can run terminal tty and work over it.

What can I do?

Intel Core 2 Duo 1,80 Ghz, MSI 7293 v2.0 (bios upgraded v2.4c) and 2x 1GB RAM modules.

Only plugged keyboard and mouse USB and SmartCard Reader USB.

Thanks,
Bruno.

---

### Post by Dutch70 on 2011-04-05
I'm not sure I understand your problem clearly, but see if this helps...
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by iiiears on 2011-04-05
Hello, 

I see that you are new here. As another Ubuntu user..  Welcome!


Maybe the panel is there and you can see it?  
Change settings on your monitor? Did that work?

What desktop window manager are you using?  Gnome Ubuntu, "KDE" Kubuntu, XFCE Xubuntu. 

in a terminal "start gnome-panel" for  Ubuntu's gnome,
KDE is different i do not know the desktop "panel" name.
Okay, Did that work?

Try this to give more information about your system.
 man lspci, man lshw. if you want more information 
 before running a terminal command.

sudo lspci 
sudo lshw

man grep can help. 


sudo lspci | 

sudo lspci | grep vga 


Linux is much easier than learning a second language 

Best Wishes.

---

### Post by Dutch70 on 2011-04-05
> sudo lspci | grep vga

That command has to have upper case "vga"...
```
sudo lspci | grep VGA
```

---

### Post by MAFoElffen on 2011-04-05
> **Libertario said:**
> When I run Live CD the system seems load successful but, after listen start session sound, only show up background. I never see Desktop Enviroment. I can run terminal tty and work over it.

After this I installed Ubuntu Maverick thinking that perhaps this were the solution but not were.

The system load properly but, after logged me in (I can work with login screen), I only can see background but not Gnome Desktop Enviroment. I can run terminal tty and work over it.

MY translation of this is that you started the LiveCD and heard the startup sound of Ubuntu (ala Lion King) but you said the Desktop never loaded... BUT with the desktop not loaded, you wouldn't have been able to see the menu itiem to get to the terminal nor the desktop icon to install... which you said you were using right?

Then you said you installed(?) IMHO- Not a good option if you you were already having problems running and displaying the LiveCD.

From the LiveCD, there are different video modes that you can start from... You didn't mention what kind kind video you are using, which might help others here be able to help you.

Once you get the LiveCD running right on your PC. You can then use those tweeks to help configure the full install.  If you are not sure of what video and video modes your PC supports:
```
sudo hwinfo --framebuffer
```will display what your system is using for video hardware and what video modes it supports.  You can use these modes as a kernel boot option... (which would need further explanation for you to implement).

Please clarify what is going on and what your PC uses for video.

---

### Post by Libertario on 2011-04-06
> **Dutch70 said:**
> I'm not sure I understand your problem clearly, but see if this helps...
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

Thanks for reply.

I read this thread but there isn't help to my problem. The system load but doesn't show up Gnome Desktop Environment (toolbox, icons, etc) and I can't use hotkeys to run, for example, "Run application" Box.

---

### Post by Libertario on 2011-04-06
Thanks for reply.

As said MAFoElffen Gnome Desktop Enviroment don't show up. I installed Ubuntu Maverick using Live CD menu loaded before load entire system that allow you launch Live CD, install entire system, check CD, etc.

This is the ouptup of *lpci | grep VGA*

02:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]

I ran Ubuntu (Recovery Mode) and I selected *failsafe xmode (low  graphics mode)* and the system loaded successfully.

This is the output of *hwinfo --frambuffer*

[http://paste.ubuntu.com/590297/](http://paste.ubuntu.com/590297/)

How can I change video mode before load system?

Thanks for your replies.

---

