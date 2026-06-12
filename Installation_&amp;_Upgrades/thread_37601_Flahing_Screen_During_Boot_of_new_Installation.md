---
title: "Flahing Screen During Boot of new Installation"
date: 2005-05-27
forum: Installation &amp; Upgrades
---

### Post by misterben on 2005-05-27
My problem:
I am attempting to install Ubuntu 5.04 onto my pc. The install goes fine, but when the system boots up the screen fills with bright coloured boxy characters which flash. Sometimes it starts out black and white before turning coloured. There is no response from keyboard or mouse. When I press the power button on my pc to turn it off, the screen clears and I see a text login prompt for the half second before the pc turns off. 

My attempts to solve it:
I tried to install kubuntu, but have the same problem.
I was originally trying dual boot (w/ XP pro), but disconnected the XP drives and just tried installing as if I would only have 1 OS.
I searched the forums and documentation but couldn't find anything relevant.

My computer:
MB: P4C800-E Deluxe 
Processor: P4 2.8 w/HT
Ram: 1GB
Video Card: nVidia GForce FX 5900  (128mb version)
Harddrive: Maxtor (older 16 gig) 

Much thanks.

---

### Post by 23meg on 2005-05-27
does this happen as soon as the kernel has booted (for example 10-15 seconds from hitting the power button), or when everything else is loaded and gnome is about to start?

---

### Post by misterben on 2005-05-27
after everything has loaded. The first time it booted, it went through the list of packages it was updating/installing

---

### Post by 23meg on 2005-05-27
you probably have a problem with your xorg configuration. and did you try booting in recovery mode?

perhaps you should post the contents of your /etc/X11/xorg.conf file here, but i'm wondering how i can get you to do that since you get stuck in startup. i'll just think out loud here, maybe this will help you but i'm not sure. you should try hitting ctrl+c several times at startup to prevent gnome from starting, and then type "sudo nano /etc/X11/xorg.conf" to see the contents. if your internet connection is working, you should be able to install the text-only Links browser by typing "sudo apt-get install links", and you can then use links to visit the forum and send the contents of the file, but i'm afraid you'll have to copy it line by line; i don't think copy/paste works in the console (or does it somehow?). if this is the case, and you have enough patience, just try typing in the "Device" section first. or find some other means of capturing what's in there and sending it here.

i also don't know if virtual consoles are an x feature; if they're not, you can use multiple consoles to make the work easier by hitting ctrl+alt+f1 to f6.

---

### Post by misterben on 2005-05-27
I will try that and then post back here
thanks

---

### Post by sparx on 2005-05-27
Just an idea..
After it loads up and gets stuck ctrl+f1 to get to a terminal then try 'sudo dpkg-reconfigure xserver-xorg'

---

### Post by misterben on 2005-05-27
ok, sparx idea worked, kind of (thank you much though). Now when it boots up I don't get the flashing screen, but x doesn't load either. Just the text login (ctrl-altf1-f6 work)

xorg.conf device section 

```
Section "Device"
               Identifier            "NVIDIA Corporation NV35 [GeForce FX 5900]"
               Driver                "nv"
               BusID                 "PCI:1:0:0"
               VideoRam              128
               Option                "UseFBDev"                "true"
EndSection
```

---

### Post by sparx on 2005-05-27
Any error messages? What happens if you try to run 'startx' from the command line?

---

