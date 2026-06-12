---
title: "Check out the new update manager. Bit wacky at the moment."
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-09-22
It is already much improved I'm sure it will only get better.

---

### Post by celticbhoy on 2009-09-22
What am I supposed to be seeing?

---

### Post by philinux on 2009-09-22
Well it is very different behaviour from the previous. Much better.

---

### Post by LKjell on 2009-09-22
It behave like?

---

### Post by Longinus00 on 2009-09-22
Besides it getting wider for some reason, I don't see any difference?

---

### Post by celticbhoy on 2009-09-22
Sorry, but already up to date so cant tell from behaviour.

---

### Post by philinux on 2009-09-22
Compared to Jaunty. It checks if there are updates before it asks for password. Also the package download is way diff.

---

### Post by celticbhoy on 2009-09-22
Will check it out tomorrow. 

ps comiserations on the footy.

---

### Post by jpeddicord on 2009-09-22
It uses aptdaemon behind the scenes instead of Synaptic now, so it's a little more streamlined.

---

### Post by philinux on 2009-09-22
I like it. Everything is getting much snappier.

---

### Post by MacUntu on 2009-09-22
Is it normal that I have to choose a user before being able to enter a password? That's not so nice.

---

### Post by LKjell on 2009-09-22
> **philinux said:**
> Compared to Jaunty. It checks if there are updates before it asks for password. Also the package download is way diff.

So it does sudo apt-get update without asking for password?

---

### Post by Squonk07 on 2009-09-22
> **philinux said:**
> Compared to Jaunty. It checks if there are updates before it asks for password. Also the package download is way diff.

I noticed that, too. The password deferral is much appreciated--the old way, frankly, was sort of annoying (I can understand asking for a password for an install, but just to check?). The package download eschews giving individual repo progress (which never seemed very useful) and instead gives a running total of the combined download size.

Also (correct me if I'm wrong) it seems like it's now smart enough to know when the repos haven't changed without having to download the information every time.

Overall, a change for the better, though the download size info is kind of useless as the target amount ramps up as the check progresses, making the progress bar's position useless. Also, the "Applying changes" window lacks a dedicated icon (it uses the GNOME "No icon" graphic).

---

### Post by oztrailrider on 2009-09-23
I prefer the way update-manager behaves now. It definitely makes more sense for it to only ask for a password when installing. The progress bars don't seem to behave quite normally yet but I am sure it will get fixed.

---

### Post by novafluxx on 2009-09-23
> **jacobmp92 said:**
> It uses aptdaemon behind the scenes instead of Synaptic now, so it's a little more streamlined.

Ah ha! Thats why aptd crashed when I was trying to use Update Manager. Makes perfect sense now. I like the changes though.

---

### Post by Squonk07 on 2009-09-23
> **novafluxx said:**
> Ah ha! Thats why aptd crashed when I was trying to use Update Manager. Makes perfect sense now. I like the changes though.

Ah, the joys of deduction. I agree that the changes are good.

---

### Post by rajeev1204 on 2009-09-24
It keeps asking for password twice before going forward.

---

### Post by novafluxx on 2009-09-24
> **rajeev1204 said:**
> It keeps asking for password twice before going forward.

Same issue here, not sure why it asks twice. May be intentional (can't believe that) or a bug.

---

### Post by rajeev1204 on 2009-09-24
and there is a broken icon on the window.

---

### Post by philinux on 2009-09-24
Just thinking about it why cant synaptic just open without a password. It only needs one if you change something etc.

---

### Post by jpeddicord on 2009-09-24
> **philinux said:**
> Just thinking about it why cant synaptic just open without a password. It only needs one if you change something etc.

That's why PolicyKit (what aptdaemon uses) came around. You can still launch a regular Synaptic as non-root, but you can't apply anything.

---

### Post by philinux on 2009-09-24
> **jacobmp92 said:**
> That's why PolicyKit (what aptdaemon uses) came around. You can still launch a regular Synaptic as non-root, but you can't apply anything.

It asks for a password straight away here. Wont run without.

---

### Post by joey-elijah on 2009-09-24
I've not actually noticed a difference... but then my wifi connects automatically so i have little reason to poke around at it. 

Has it had the "visual refresh" that was proposed in the karmic blueprints?

---

### Post by go7Ul1ai on 2009-09-24
> **joey-elijah said:**
> I've not actually noticed a difference... but then my wifi connects automatically so i have little reason to poke around at it. 

Has it had the "visual refresh" that was proposed in the karmic blueprints?

It certainly does :)

[IMG]http://img136.imageshack.us/img136/4210/screenshotyd.png[/IMG]

Lee

---

### Post by MacUntu on 2009-09-24
Sorry for being off-topic: OMG those icons look so homogenous - this can't be our Ubuntu. Now it lost all its charm. :D :D :D

---

### Post by james9876 on 2009-09-24
> **MacUntu said:**
> Sorry for being off-topic: OMG those icons look so homogenous - this can't be our Ubuntu. Now it lost all its charm. :D :D :D

I think that might be that particular icon set Humanity which is the one i use too.

---

### Post by jpeddicord on 2009-09-24
> **philinux said:**
> It asks for a password straight away here. Wont run without.

Alt+F2. Type `synaptic`.

---

### Post by joey-elijah on 2009-09-24
> **lee.jarratt said:**
> It certainly does :)

[IMG]http://img136.imageshack.us/img136/4210/screenshotyd.png[/IMG]

Lee

Yay! :D 

I only just noticed that my network manager has changed (obviously.) how long has this update been out?!

---

### Post by Slug71 on 2009-09-24
I like the new icons but im not sure about Update Managers behaviour yet.

---

### Post by rburkartjo on 2009-09-24
yea not sure if i like the add/remove options moved to admin but as long as i can access it i really dont care

---

### Post by Slug71 on 2009-09-24
> **rburkartjo said:**
> yea not sure if i like the add/remove options moved to admin but as long as i can access it i really dont care

Well its just there as a back-up im thinking. Ubuntu Software Store is to replace Add/Remove.

---

### Post by joey-elijah on 2009-09-24
> **Slug71 said:**
> Well its just there as a back-up im thinking. Ubuntu Software Store is to replace Add/Remove.

Correct. In fact i hadn't even noticed add/remove in the admin menu!

---

