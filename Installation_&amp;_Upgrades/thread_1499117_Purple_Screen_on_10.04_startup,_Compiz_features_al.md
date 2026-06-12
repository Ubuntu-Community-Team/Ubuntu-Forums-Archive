---
title: "Purple Screen on 10.04 startup, Compiz features all switched off"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by captain_conrad on 2010-06-01
Im almost sure other people must be experiencing what I am experiencing, lots of people use the compizconfig visual effects, especially the famous desktop cube....

I just recently upgraded to 10.04.

Now when I start up i get that dreaded purple ubuntu screen and the text reads as follows:

An error ocurred while mounting /proc/bus/usb
Press s to skip mounting or m for manual recovery

So I hit S and it logs in just fine and I arrive on my desktop just fine.

(by the way I searched for that file in those directories, it just isn´t there)

But now all my compizconfig visual effects are all switched off.

So I right click on the desktop, select change desktop background, then go to the visual effects tab, and the ¨NONE¨ option is what is currently selected. 
Well i select the ¨EXTRA¨ option, and all goes fine.

Then I go into compizconfig settings manager (system, preferences).
I switch on my desktop cube, set it to 6 desktops so I get a hexagon, enable viewport switcher, cube rotate, window decorations, cube gears, 3d windows, animations, all kinds of stuff I normally have switched on. (I really make thorough use off all of compiz´s things). 

And all is well and everything works perfectly, and off I go doing everything I normally do, everything running perfectly the way I want it to, no problems. :)


But...

](*,)

When I switch off or restart my computer...

the whole process starts again. ](*,) 

Every time. ](*,) Hrmfphhh....

Purple screen, select s for skip, login, Change desktop background, visual effects, select extra, open compiz, enable everything, bla bla  bla bla eeeeuuuurrgghh i do not wanna do this every time I login! ](*,)

Please Help!?

---

### Post by captain_conrad on 2010-06-04
:(
Is *Anybody* having the same problems at all?

The purple screen claiming /proc/bus/usb
OR 
compiz not remembering that everything was switched on when you restart or shut down and start computer again?

Anyone at all?

Or does anybody even have the feintest idea where or in which direction i can go and poke my nose around for more information?

---

### Post by davidmohammed on 2010-06-04
may be [this thread]("http://ubuntuforums.org/showthread.php?p=9204265") will work for your usb mounting issue...

---

### Post by davidmohammed on 2010-06-04
... and maybe [this is similar]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/453912") to your compiz issue.

It suggests you need to rename you .local file in your home directory i.e.

mv .local .local_backup

then reboot.

---

### Post by captain_conrad on 2010-06-17
An error ocurred while mounting /proc/bus/usb
Press s to skip mounting or m for manual recovery

[B]SOLVED.
[/B]

In 9.04 the usb would not work in virtualbox and there was some hack found where u had to open up the fstab file and type an additional line into it.

I solved it by opening the terminal and typing

sudo nano /etc/fstab

then i deleted the entire last line of text, the one after the line containing ¨# for usb access with virtualbox¨

After doing that, I got a bit stuck because i have no clue what im doing in the terminal, so I was like OK what now?

that ¨ ^ ¨ symbol represents the Ctrl button. So I hit Ctrl+X

I then closed the terminal, and that solved the problem of the purple screen of death saying An error ocurred while mounting /proc/bus/usb
Press s to skip mounting or m for manual recovery

AWESOME!

PS: Virtualbox has apparently sorted itself out regarding USB, but u have to have the version of virtualbox that matches your version of ubuntu. This means you can delete the ¨hack¨ line without disabling the USB in virtualbox. I downloaded the version of virtualbox that matches the version of ubuntu that I have, and all is working fine again.

---

### Post by captain_conrad on 2010-06-17
My compiz issues however are NOT solved :confused:

Every time i start up my computer, when i reach the desktop, I have to right click, select the change desktop background, then go to the visual effects tab, and then the ¨none¨ option is selected, so I gotta select ¨extra¨, wait for it to find available drivers, select keep settings when it pops up and asks if i want to keep the settings, and then I have to go into compiz config settings manager and switch on all my cool effects again.

Every time. ](*,)

Its so annoying. I did read up on the links suggested. I tried unistalling compiz completely, then reinstalling it. Didn´t work. I tried going into synaptic package manager and marking compiz for re-installation, and it did its thing, but it still did not fix my problem.
I tried renaming the .local folder in the home folder, that didn´t work either.

Any suggestions, any help please?

---

### Post by captain_conrad on 2010-06-18
Compiz switched off every time i start up, cube not on, cube rotate not on, window decorations not on, etc etc.

**SOLVED.**


> **andrea000 said:**
> This sounds like one of the compiz bugs open ccsm go to
the workarounds plug in and put a check in the legacy
full screen support and reboot this fixed mine and should
yours to.



> **BillyG123 said:**
> Here's what worked for me:

1. compiz --replace
2. System > Preferences > Startup Applications > Options > Remember Currently Running Application


I don´t know which one of these is the one that actually made it work, but I did both and then restarted, and **PROBLEM SOLVED!!!**

:mrgreen: \\:D/   WOOHOO!!! \\:D/ :mrgreen:

---

