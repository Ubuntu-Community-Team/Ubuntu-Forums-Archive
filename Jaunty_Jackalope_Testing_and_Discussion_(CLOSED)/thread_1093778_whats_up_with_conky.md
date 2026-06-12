---
title: "whats up with conky?"
date: 2009-03-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by deathsshadow77 on 2009-03-11
every time I start up my computer conky loads then the desktop loads on top. Anyone else see this? Is this a bug? And if so, how should it be reported?
I want to say its startup applications but it might be conky itself. Im just not sure

---

### Post by Technoviking on 2009-03-11
With compiz, you need to delay the start of conky for about 60 after login.

---

### Post by Nullack on 2009-03-11
Its just another thing compiz breaks until we get proper GPU memory management.

---

### Post by Ng Oon-Ee on 2009-03-12
> **deathsshadow77 said:**
> every time I start up my computer conky loads then the desktop loads on top. Anyone else see this? Is this a bug? And if so, how should it be reported?
I want to say its startup applications but it might be conky itself. Im just not sure
It is not a bug, per se. What conky does is write to the root window. Conky is lightweight and fast, so it does that pretty early (just about immediately after you enter your password). Compiz, the big beast that it is, takes much longer (10s of seconds) to load, and once it does it takes over the root window (another term for the base desktop). So basically you have to wait till compiz loads before loading up conky. A simple sleep may do the job, but if you're anal-retentive like  I am and want it to load AS SOON AS it can, then follow my instructions in [this thread for guiding beginners to conky]("http://ubuntuforums.org/showpost.php?p=6809184&postcount=29").

---

### Post by Nullack on 2009-03-12
> **Ng Oon-Ee said:**
> It is not a bug, per se.[/URL].

So requiring custom setup and timing on boot isnt a bug its a feature? :)

---

### Post by deathsshadow77 on 2009-03-12
im not running compiz, just metacity's compositor. I also didnt have this issue with compiz in intrepid.

---

### Post by Ng Oon-Ee on 2009-03-13
> **Nullack said:**
> So requiring custom setup and timing on boot isnt a bug its a feature? :)
No its not a feature, but no its not a bug as well.

Conky assumes the environment is ready for it, so it writes to the root window. Which then gets taken over by compiz.

This is the nature of software, its not possible for all software to be aware of/interact properly with all other software. In this case its a mere timing issue, and guides abound as to how to do this properly. If you feel strongly enough about it, then do submit a patch (and will you submit it to conky or to compiz? or to Gnome?). Myself, I'd prefer the devs to work on something more urgent which can't be solved/worked-around by a simple (sleep 30s) in my startup code.

---

### Post by jjgomera on 2009-03-14
if you use gnome, and nautilus draw desktop with icon, wallpaper, etc, conky must start later from nautilus, thats is not a bug, is more a "incompatibility" with the manner gnome draw desktop, in other DE and WM thats problem dont exist.
You must aply delay to conky start

---

### Post by aldeby on 2009-03-14
A delay of about 30 seconds is enough for my desktop to load compiz and conky. Of course it all depends on CPU & HDD speed.

---

### Post by Nullack on 2009-03-14
> **Ng Oon-Ee said:**
> No its not a feature, but no its not a bug as well.

Conky assumes the environment is ready for it, so it writes to the root window. Which then gets taken over by compiz.

This is the nature of software, its not possible for all software to be aware of/interact properly with all other software. In this case its a mere timing issue, and guides abound as to how to do this properly. If you feel strongly enough about it, then do submit a patch (and will you submit it to conky or to compiz? or to Gnome?). Myself, I'd prefer the devs to work on something more urgent which can't be solved/worked-around by a simple (sleep 30s) in my startup code.

I see it as a bug. The problem is the architecture, rather thank conky itself.

Hopefully in time video will be properly sorted out in Linux so these sorts of ugly hacks with sleep wont be needed.

---

### Post by Ng Oon-Ee on 2009-03-15
Wonder if the problem really is video. I'd think this is simply an issue of differring rendering taking place. But yes, I agree it shouldn't be necessary to hack out such things. I actually think the responsibility should be shared between the DE and the WM, that the DE should 'hold' apps which wish to draw on the desktop till the WM announces its done.

---

### Post by nyarnon on 2009-03-15
> **Nullack said:**
> I see it as a bug. The problem is the architecture, rather thank conky itself.

I would agree with you if conky wouldn't be a console app. Maybe someday it will become a true windowed app and we can (or not) have this discussion again :-)

---

### Post by Ng Oon-Ee on 2009-03-15
> **nyarnon said:**
> I would agree with you if conky wouldn't be a console app. Maybe someday it will become a true windowed app and we can (or not) have this discussion again :-)
Its a console app? Sorry to sound ignorant, but I really was not aware of that. What's a console app doing drawing to a graphical desktop?

---

### Post by nyarnon on 2009-03-15
> **Ng Oon-Ee said:**
> Its a console app? Sorry to sound ignorant, but I really was not aware of that. What's a console app doing drawing to a graphical desktop?

Yeah well sometimes I'm a bit blond :-) I stand corrected.

---

