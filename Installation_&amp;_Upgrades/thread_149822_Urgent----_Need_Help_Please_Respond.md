---
title: "Urgent---- Need Help Please Respond"
date: 2006-03-24
forum: Installation &amp; Upgrades
---

### Post by scrfceyeyo on 2006-03-24
After I install it from the cd, it reboots and starts to install, then after picking resolution size, it just turns into all this messed up screen. What should I do to install this correctly I have tried many times.

---

### Post by eriefisher on 2006-03-24
Picking a resolution??? What res did you set it at. I don't remember picking a res during the install, I thought it was detected.

eriefisher

---

### Post by aysiu on 2006-03-24
It sounds as if you're picking the wrong resolution or don't have your video settings configured properly.

[This link](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) has a plethora of resources.

---

### Post by scrfceyeyo on 2006-03-24
the thing is, it doesn't finish the install, and when it loads up again, it goes to the same screen. (Keep in mind that this is after I have installed everything from the cd and am installing from the HD,) Also, Before installing Ubuntu, I had windows xp x64 bit edition on the HD i tried to install ubuntu on. (I have 2 hds, first one with regular windows. second had 64bit windows. Even though I formatted the second harddrive, windows 64bit still shows up as an option to boot from, could that be the problem?? Please respond quickly :D i need this fixed.

---

### Post by axelbjel on 2006-03-24
Exactly the same happens to me but I have no solution.

---

### Post by axelbjel on 2006-03-24
Well, I try in many ways, but the computer lock up every time during installation. This is hopeless!

---

### Post by scrfceyeyo on 2006-03-24
any other "vets" know, this is my first "real" attempt at linux, so I am a nub.

---

### Post by Mustard on 2006-03-24
[QUOTE=scrfceyeyo]any other "vets" know, this is my first "real" attempt at linux, so I am a nub.[/QUOTE]
Can you get to a command line at all?

Try hitting ctrl + alt + f1 (or any of the functions keys up to f6)

---

### Post by scrfceyeyo on 2006-03-24
During the installation?

---

### Post by Mustard on 2006-03-24
[QUOTE=scrfceyeyo]During the installation?[/QUOTE]

When the installation fails, I mean.

---

### Post by scrfceyeyo on 2006-03-24
and then what?

---

### Post by Mustard on 2006-03-24
Well, if you are at the command line, we can try a temporary fix to get a GUI going until such a time as you can install some drivers for whatever graphics card you might be using.

If you get a login prompt, then login using your username and password that you set up in the install process.

I'm going to try to get you to switch to the 'vesa' drivers and pick a resolution setting that is pretty standard, by reconfiguring your xorg.conf file.

To reconfigure your xorg.conf file try this command..

```
sudo dpkg-reconfigure xserver-xorg
```

It will start a dialog up asking you some questions about your settings.  For the most part you should choose the default answers that are already there, but when it comes to choosing your graphics drivers, choose the 'vesa' option.  Don't try to set up any fancy resolutions just yet.  Go for the default options it shows when it asks about which resolutions to use.

When the dialog finishes it should write a new xorg.conf file.

Now you need to try starting your display from the command line. Try either of these commands...

```
startx
```

or

```
sudo /etc/init.d/gdm restart
```

Any error messages you receive along the way, you should write them down and post them in here, so we can troubleshoot further.

---

