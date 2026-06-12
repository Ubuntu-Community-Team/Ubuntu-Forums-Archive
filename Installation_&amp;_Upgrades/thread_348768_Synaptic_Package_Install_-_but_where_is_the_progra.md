---
title: "Synaptic Package Install - but where is the programme? :)"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by NonPapa on 2007-01-29
Hi there,

Just installed Ubunto 6.10 this morning, and almost everything is running fine :D 
However, just tried to install a package using Synaptic Package Manager, and the programme
seems to be installed (the box preceding the programme is filled out in a nice green hue). Where do I go from here? How can I start this programme now?

Sorry, this must be very obvious, but the more I read the more I realise that I don't understand much, and I would love to use this programme *now*... :) 

Any hints much appreciated,
NonPapa

P.S. Apologies if this is in the wrong section of this forum. :-(

---

### Post by taurus on 2007-01-29
What is the name of the program?  See if you can start it from a terminal.

Applications -> Accessories -> Terminal
```
**program_name**
```

---

### Post by NonPapa on 2007-01-29
Good hint! That made me crawl to the directory where the programme was installed into (according to Synaptic), and it has a much shorter name than what I was expecting. Found it now,
and it works. How do I get it into the more comfy "Applications" menu? Will it appear automatically on re-start?

Sorry for this stupid questions, but that's my first 3rd party software have installed on Ubuntu. :)

Many thanks,
NonPapa

---

### Post by taurus on 2007-01-29
If the program is in your path, you can run it from anywhere.  Don't have to change directory to where it is first.  What's the name of the program again?  Chances are it would be in the menu somewhere under Applications.

---

### Post by NonPapa on 2007-01-29
Programme is Tintin++ :)
And it was installed into usr/games/ , but that's somehow not my "home" path.
I have checked, and it's in none of the sub section of the Applications drop-down menu.

Many thanks again,
NonPapa

---

### Post by taurus on 2007-01-29
Is that the name of that game on your machine?  It doesn't appear in the Applications -> Games menu at all?  I guess you can create a shortcut in the panel so you click on it to run it unless you don't mind typing the name of that game from a terminal.

---

### Post by lucia_engel on 2007-01-29
Slightly off topic, but I've always wondered about this. 

After installing a program (from apt-get or synaptic), if it's not automatically added to menu and not under /usr/bin/program-name (on those rare occasions where the execute command is different from the program name) how do I find the right path at the terminal? 

I'm thinking something with apt-cache but apt-cache show didn't list that. I know synaptic lets you see all the installation paths when you check the program properties.

---

### Post by taurus on 2007-01-29
```
whereis **program**
-or-
locate **program**
```

---

### Post by NonPapa on 2007-01-29
> **taurus said:**
> Is that the name of that game on your machine?
Surprisingly yes. I was expecting' TinTin++'
> **taurus said:**
> It doesn't appear in the Applications -> Games menu at all?
Correct. It's in non of the 'Applications' at the top of my screen.
> **taurus said:**
> I guess you can create a shortcut in the panel so you click on it to run it unless you don't mind typing the name of that game from a terminal.
I don't mind using the terminal, but it would be good for future reference to know how you can create a shortcut in the panel, as I can't figure out how to do that. :-(

Many thanks for all your help, taurus!
NonPapa

---

### Post by taurus on 2007-01-29
I am home right now but from my memory, here is how you would add a launcher to the top panel.  

Place a cursor in the middle of top panel and click the right mouse.  Pick the Add Applications Launcher or something similar to that.  You can type in the name of your program and in the command field, type the name of your game in a whole path.  For instance, if it's  /usr/games/TinTin++, then you need to put that path thing in.  Save it.

Now, click on the icon to see if you can run it!

---

### Post by NonPapa on 2007-01-31
Thank you very much!
That worked nicely. :)

NonPapa

---

