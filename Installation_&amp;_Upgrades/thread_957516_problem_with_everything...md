---
title: "problem with everything.."
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by CrazyEye941 on 2008-10-24
Hey, I'm really new to Ubuntu and its completely different from windows.

I can connect to the internet right.

Boots correctly

Sounds are good

Graphics - SLOW (I have an XFX 8800GT *new* with 2gb of DDR2 Memory so I dont know why its running slow on the internet and .gifs)


Flash player doesn't work, I tried installing but the install was a .deb, I googled it and was told to open the terminal and type "dpkg -i filename.deb" and with filename i put the location of the file. 

Random Crashes.

I would really like some help with ubuntu because I know that if I learn more about this OS I would like to stay here rather then go to windows.

---

### Post by ammikulka on 2008-10-24
For your graphics card you probably need to install the correct driver

go to 

system >> Administration >> Hardware Drivers

and check the box next to your graphics card name

edit* with .debs all you need to do is double click on them then it will open up a program to install it

---

### Post by CrazyEye941 on 2008-10-24
> **ammikulka said:**
> For your graphics card you probably need to install the correct driver

go to 

system >> Administration >> Hardware Drivers

and check the box next to your graphics card name

edit* with .debs all you need to do is double click on them then it will open up a program to install it

I get this error "ERROR: Wrong architecure'i386'"

I clicked hardware drivers and it says "NVIDIA accelerated graphic driver (latest cards)" but I already had that installed and its still messing up and showing artifacts (Open up firefox it flashes static for a brief second) I went to the nvidia website to download the drivers but when I dbl click the .run file it says "choose a program" and from the desktop it says "could not open the file /home/crazyeye/Desktop/N&#8230;Linux-x86-177.80-pkg1.run."

I'm doing something wrong aren't I -.-"

---

### Post by ammikulka on 2008-10-24
uh.. I'm sorry to say but i have no clue...:confused: hopefully someone else will spot this thread and help you out

---

### Post by CrazyEye941 on 2008-10-24
> **ammikulka said:**
> uh.. I'm sorry to say but i have no clue...:confused: hopefully someone else will spot this thread and help you out

Alright, well thanks for helping me out. I hope someone does come and rescue me from this linux trap lol

---

### Post by Bender2k14 on 2008-10-24
First off, congratulations on leaving Windows :)

I use EnvyNG to install the correct Nvidia driver for my graphics card.  I believe EnvyNG is in Applications->System Tools.

After the correct driver is installed, you can edit your display settings by running the command

```
sudo nvidia-settings
```

in the terminal.  The terminal is somewhere it the Applications menu as well.

As for flash, a quick Google search returns this [flash install tutorial]("http://www.psychocats.net/ubuntu/flash").  There are still some flash problems even after installing the plug-in.  Firefox still crashes for me sometimes when loading a page that uses flash.  Adobe recently released a new flash plug-in that should fix some (if not all) of the crashes, but I think it came after the feature freeze for Ubuntu 8.10.  It will be an update soon enough.

.deb is the extension for packages in Ubuntu.  Packages are like install files.  The name comes from Debian, the distribution from which Ubuntu is based.  i386 basically means 32 bit.  Is it possible that you installed the 64 bit version of Ubuntu?

> Random Crashes.

What is crashing?

---

