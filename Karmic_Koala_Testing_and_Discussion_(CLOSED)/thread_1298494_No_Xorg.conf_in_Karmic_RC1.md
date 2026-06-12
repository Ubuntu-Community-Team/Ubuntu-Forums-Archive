---
title: "No Xorg.conf in Karmic RC1"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SunnyRabbiera on 2009-10-22
I kind of need it for gamma, my monitor is just too dark without me adjusting brightness via xorg.
My monitor is already at max with its brightness and the screen is still too dark!
I tried generating a new xorg.conf file but nothing.
I have a intel card...
If I manually have to make a xorg.conf file thats fine but it is annoying.

---

### Post by novafluxx on 2009-10-22
I believe Xorg -configure can be used to generate the file you seek

In the latest version of X.org the file is deprecated in favor of auto-detection through hal and/or devicekit, I do believe.

If I am in error, someone please correct me.

---

### Post by SunnyRabbiera on 2009-10-22
> **novafluxx said:**
> I believe Xorg -configure can be used to generate the file you seek

In the latest version of X.org the file is deprecated in favor of auto-detection through hal and/or devicekit, I do believe.

If I am in error, someone please correct me.

no tried that and nothing, no xorg.config file generated.
I want my gamma, there must be a way to do it.
Can I edit devicekit or HAL?

I got this error:
```
sudo Xorg -configure

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help.
```

---

### Post by novafluxx on 2009-10-22
> **SunnyRabbiera said:**
> no tried that and nothing, no xorg.config file generated.
I want my gamma, there must be a way to do it.
Can I edit devicekit or HAL?

I got this error:
```
sudo Xorg -configure

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help.
```


Ahhh, duh, you can't generate one while you're running X! Sorry!

You'll need a way to shutdown X and get to the console, I do not know how to do this in Ubuntu, however I'd love to learn, because I want to experiment with booting to the console and only starting X when I run startx

If you need to create one from scratch, I'd be more then willing to give you mine as a template to edit, so you're not flying blind and typing a lot of stuff, but I'm sure we'll get a resolution. Does the monitor brightness/gama look OK during pre-boot, in your system BIOS?

---

### Post by SunnyRabbiera on 2009-10-22
> **novafluxx said:**
> Ahhh, duh, you can't generate one while you're running X! Sorry!

You'll need a way to shutdown X and get to the console, I do not know how to do this in Ubuntu, however I'd love to learn, because I want to experiment with booting to the console and only starting X when I run startx

If you need to create one from scratch, I'd be more then willing to give you mine as a template to edit, so you're not flying blind and typing a lot of stuff, but I'm sure we'll get a resolution. Does the monitor brightness/gama look OK during pre-boot, in your system BIOS?

Alright, I will log out and do all that.
And no I have no gamma options with my bios.

---

### Post by Rob2687 on 2009-10-22
Stopping X:

Drop to the terminal by doing **ctrl+alt+F1**
Type **sudo service gdm stop**

---

### Post by novafluxx on 2009-10-22
> **SunnyRabbiera said:**
> Alright, I will log out and do all that.
And no I have no gamma options with my bios.
Excellent, let us know how it goes and best of luck to you!
> **Rob2687 said:**
> Stopping X:

Drop to the terminal by doing **ctrl+alt+F1**
Type **sudo service gdm stop**

Thank you!

Question: Why is it gdm being stopped, I thought gdm was just the graphical login manager. So it also controls the whole X session?

---

### Post by SunnyRabbiera on 2009-10-22
> **Rob2687 said:**
> Stopping X:

Drop to the terminal by doing **ctrl+alt+F1**
Type **sudo service gdm stop**

yeh nothing there either.
What nonsense, I even tried to make my own Xorg.conf file but nothing...

---

### Post by novafluxx on 2009-10-22
> **SunnyRabbiera said:**
> yeh nothing there either.
What nonsense, I even tried to make my own Xorg.conf file but nothing...

Go to tty1 and do as he said to stop that service, then run Xorg -configure, whats the output of that when you run it AFTER stopping gdm?

Please post it if possible

---

### Post by SunnyRabbiera on 2009-10-22
> **novafluxx said:**
> Go to tty1 and do as he said to stop that service, then run Xorg -configure, whats the output of that when you run it AFTER stopping gdm?

Please post it if possible

No it gives me more of the same, it doesnt change a blasted thing.

---

### Post by HotShotDJ on 2009-10-22
Have you tried:```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Rob2687 on 2009-10-22
Try booting into recovery mode then running **Xorg -configure** in the root console.

---

### Post by novafluxx on 2009-10-22
> **Rob2687 said:**
> Try booting into recovery mode then running **Xorg -configure** in the root console.

It shouldn't give you the fatal error about the X server already running if its been shut down, and make sure you do sudo Xorg -configure.

Try it the way Rob2687 suggests.

---

### Post by SunnyRabbiera on 2009-10-23
Yeh i got it now, just seemed to crash out there for a bit.

---

### Post by Starks on 2009-10-23
Just start Ubuntu in recovery mode, go into root, type "Xorg -configure".

---

### Post by SunnyRabbiera on 2009-10-23
> **Starks said:**
> Just start Ubuntu in recovery mode, go into root, type "Xorg -configure".

Nono, all fine now.

---

