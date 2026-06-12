---
title: "Clock Applet not loading"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by EricLorenz on 2010-10-16
I had the Clock Applet installed in my panel up through 10.04- when I did the upgrade to 10.10, it was removed (with no explaination). Now, when I try to put it back into the panel, I get the following error message-

"The panel encountered a problem while loading OAFIID:GNOME_ClockApplet"

and asks me if I want to leave it anyway, or remove it. Regardless of what I select, it does not appear.

I like the clock applet. Has anyone else had this issue? Would this be classified as a bug, or is it already a known issue? I have not searched Bugzilla yet.

Would this have any relation to the issue I am having with being unable to re-install evolution (Which was also removed during upgrade)?

Thanks,
Eric

---

### Post by EricLorenz on 2010-10-18
ANYONE know of a way to fix this? Could this be tied a larger problem I have been having with my applet bar that goes back to probably 9.04, where my icons/applets in the right corner of my applet bar disappear/get lost/overrun each other? 

Not sure what to do with this...

Thanks for the help.

Eric

---

### Post by EricLorenz on 2010-10-20
Am I posting this question in the wrong forum?

---

### Post by Old_Grey_Wolf on 2010-10-20
I can not reproduce your problem. 

I entered 
> "The panel encountered a problem while loading OAFIID:GNOME_ClockApplet" 
and 
> Ubuntu "The panel encountered a problem while loading OAFIID:GNOME_ClockApplet" 
into Google and got some results.

However, I can not determine if any of them will work; because, I can't reproduce your problem.

---

### Post by EricLorenz on 2010-10-21
Thanks for trying...not sure what to do at this point...both of these issues (this, and my evolution disappearing) seem to stem fro  a 'failed' upgrade. Apparently the upgrade I did from 10.04 to 10.10 using the alternate CD did not go well...it ended (ran it overnight) then I ran update manager to get any updates...that's when I got the Partial Upgrade message. I said OK, that's when it wanted to take the Clock applet and Evolution away.

Maybe I just need to backup the /home folder and reload 10.10 from scratch? What a pain.

If I do that, do I need to remember what all apps I have installed, and re-install them manually again after the inital install? Do I then just copy my backed up /home folder over the new one?

Thanks.

---

### Post by Sickpuppy87 on 2010-10-22
Just so you know you are not alone here.... i updated from 10.04 to 10.10 and am having the same issue...

Entry from .xsession-errors:
```

** (gnome-panel:1730): WARNING **: panel-applet-frame.c:1273: failed to load applet OAFIID:GNOME_ClockApplet:
System exception: IDL:Bonobo/GeneralError:1.0 : Child process did not give an error message, unknown failure occurred
```

i have tried reinstalling gnome-panel/gnome-applets/gnome(i think lol)  also tried a new user and clearing out the preferences in my home drive..... 

meh i think i am just going to give up on the clock applet and see if i can find another one but ill let you know if i find an answer.

---

### Post by kanamor on 2010-10-28
Same here :(

---

### Post by kanamor on 2010-10-28
I found a solution.

I know that is not the best, but it has worked.

Clearly, then you will need to reconfigure the desktop, but at least they work properly.

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

---

### Post by Old_Grey_Wolf on 2010-10-28
> **kanamor said:**
> 
rm -rf .gnome .gnome2 .gconf .gconfd .metacity

That is a scary command. Remove files recursively from .gnome .gnome2 .gconf .gconfd .metacity.

I don't think I would try it!

---

### Post by kanamor on 2010-10-28
Yes, that's exactly what it does, restart the gnome default settings. Command is not as dangerous ... if you know what you do.

You can always make a backup of those folders...

I did and I'm still alive ....

---

### Post by Old_Grey_Wolf on 2010-10-28
> **kanamor said:**
> Yes, that's exactly what it does, restart the gnome default settings. Command is not as dangerous ... if you know what you do.

You can always make a backup of those folders...

I did and I'm still alive ....

People should be told that that command will set their desktop back to the defaults. They will need to redo the changes they made.

---

### Post by kanamor on 2010-10-28
I did, back to copy what I put above, if you read me.

> **kanamor said:**
> I found a solution.

I know that is not the best, but it has worked.

[COLOR="Black"]_Clearly, then you will need to reconfigure the desktop, but at least they work properly._[/COLOR]

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

---

### Post by CharlesA on 2010-10-28
It would be a good idea to have them use ***rm -ri*** instead of ***rm -rf***.

One typo and they wipe out something they don't want removed.

---

### Post by EricLorenz on 2010-10-30
When you say "...need to reconfigure the desktop" what exactly will I have to 'reconfigure'?

Thanks,
Eric

> **kanamor said:**
> I found a solution.

I know that is not the best, but it has worked.

Clearly, then you will need to reconfigure the desktop, but at least they work properly.

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

---

### Post by CharlesA on 2010-10-30
Reconfigure as in wipe out all the desktop settings and start from scratch.

---

### Post by EricLorenz on 2010-10-30
Again, not trying to sound stupid here...just wanting to make sure I understand...will this essentially take the desktop back to the way it is after you first install Ubuntu?

So basically, back up any files I have directly on the desktop, and note any shortcuts I made? I assume it will also take out any menu items for programs installed after initial installation? So thos would all have to be re-created? Is there a file I can save that would preserve everything in the applications menu?

Thanks!

> **CharlesA said:**
> Reconfigure as in wipe out all the desktop settings and start from scratch.

---

### Post by CharlesA on 2010-10-31
I don't know tbh, I don't know what all is stored there, but it would be a good idea to back everything up.

---

### Post by Old_Grey_Wolf on 2010-10-31
> **EricLorenz said:**
> Again, not trying to sound stupid here...just wanting to make sure I understand...will this essentially take the desktop back to the way it is after you first install Ubuntu?

Use your file browser to look at  the contents of /home/*username*/.genome2, /home/*username*/.gconf, and /home/*username*/.gconfd. I have never run that command, I looked at the command and saw what it would delete.

---

### Post by EricLorenz on 2010-11-01
Let me ask this...is the issue the applet itself, or something else in the system that is making it appear as if the applet is bad (or not allowing it to load). Is it such that just deleting it from whereever it is stored and copying in a fresh copy would fix the issue?

Thanks,
Eric

---

### Post by Sickpuppy87 on 2010-11-01
> **kanamor said:**
> I found a solution.

I know that is not the best, but it has worked.

Clearly, then you will need to reconfigure the desktop, but at least they work properly.

rm -rf .gnome .gnome2 .gconf .gconfd .metacity


Tried that and no luck for me...

> Again, not  trying to sound stupid here...just wanting to make sure I  understand...will this essentially take the desktop back to the way it  is after you first install Ubuntu?

So basically, back up any files I have directly on the desktop, and note  any shortcuts I made? I assume it will also take out any menu items for  programs installed after initial installation? So thos would all have  to be re-created? Is there a file I can save that would preserve  everything in the applications menu?

Thanks!

for me it did not remove my shortcuts just any settings in my panels .... and my background....

Also no your installed programs will not be removed from your menus

---

### Post by EricLorenz on 2010-11-05
Tried the command suggested...I now have a fresh new desktop, but still no clock applet. It is apparently part of the default configuration, and as the desktop came up after logging in, got the same error message.

So again...could my clock applet have gotten corrupted somehow, and is there a way to delete and reload a new, fresh, hopefully non-corrupt copy of just the clock applet from somewhere else?

Thanks!

Eric

---

