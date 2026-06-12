---
title: "installation successful but....."
date: 2006-04-24
forum: Installation &amp; Upgrades
---

### Post by sahirb on 2006-04-24
so I work at this place and there was a conference for ubuntu promoting it or something, then i had a conversation with this nice gentleman and he gave me the installation and live cd of ubuntu linux 5.10 , I installed it into my desktop and select the option erase the hard drive and install, it unpacked all the files then ejected the cd to reboot, after rebooting the ubuntu splash screen comes up and loads modules etc then goes to a blank screen then a typing cursor on the top left corner of the screen, the cursor blinks and then it freezes after a few seconds and it doesnt go any further from there. restarted several times and re installed several times, same result!! Frustrated! I am a complete newbie in linux, please help me out.

---

### Post by Sef on 2006-04-24
Could you tell us what your system specs are, please:  x GHz (or MHz), ram, video card, anything else that you know.

---

### Post by sahirb on 2006-04-24
its quite old, 633 mhz, 320 MB RAM, 32MB Geforce 2 Grafic card, it had Windows xp Home installed which I formatted and trying to install Linux. Help please.

---

### Post by lenehey on 2006-04-24
I have had similar problems with my laptop. I think you have successfully installed Ubuntu, but the graphics user interface (X, xorg, X11) is not properly setup.  In my case, Ubuntu defaulted to the external monitor port rather than the LCD screen.  If you have a TV out or second port on your video card, you could be having the same problem.  The only way that I know of correcting the problem is by booting in safe mode, and editing the xorg.conf file, which is located in /etc/X11/.  I don't know what you need to put into the file to correct the problem, but the easiest way to edit is to type the following when you get the root prompt on safe boot:

cd /  [note a space must precede the slash]
cd etc
cd X11
nano xorg.conf

(by the way, you can view folder contents by typing "ls"; go up one level by typing "cd .." (space before ".." is important); and return to the root by typing "cd /".)

That will bring up a user-friendly text editor and allow you to edit the file.  Typically a very simple change to the file is needed to fix whatever problem you are having, but finding the simple change you need to make is the tough part.  I did a little web searching for you and found that you may need to add a line in the "Device" section of your xorg.conf file.  The following is an example.  Note that the double quotes are important.  Try not to change anything but add the 'Driver' line if it is missing.  Good luck.  

```

Section "Device"
  Identifier "nVidia Inc. GeForce2"
  Driver     "nvidia"
  VideoRam   65536
EndSection
```

If that doesn't help, I suggest you look for other possible problems online, post a bug in the Wiki and/or try another distribution.

---

### Post by sahirb on 2006-04-25
ok that problem is solved. now another one, it says ""the xserver (graphical interface) is not setup properly, press yes to see the diagnose of the problem" so after that it gives me a command prompt to login. I am really frustrated at this point.

---

### Post by Sef on 2006-04-26
Try this at the command prompt:

sudo dpkg-reconfigure xserver-xorg

It will allow you to change your monitor settings.

---

### Post by BCRailrodder on 2006-04-27
[QUOTE=Sef]Try this at the command prompt:

sudo dpkg-reconfigure xserver-xorg

It will allow you to change your monitor settings.[/QUOTE]
ThankyouThankyouThankyou...

I just swapped my old AOC monitor for a new Dell LCD and could not get past the login screen.  By following your advise I was able to reconfigure X11.

Much appreciated - I hope that sahirb has as much success.

---

### Post by sahirb on 2006-04-27
i get the same problem, i am guessing that i should enter the correct pci slot for me grafic card, i have intel grafic card on the board and a seperate pci grafic card wich is nvidia tnt2 32mb. in the configuration it asks about the pci slot for the grafic card which i dont know the number of, it is the bottom most slot though, can i get some help on that?

---

