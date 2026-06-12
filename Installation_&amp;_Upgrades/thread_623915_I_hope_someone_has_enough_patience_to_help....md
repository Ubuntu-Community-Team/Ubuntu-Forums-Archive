---
title: "I hope someone has enough patience to help..."
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by bueller on 2007-11-26
Edit - 

Problem solved. Thanks Squishy!

---------------------------

I am a liniot. Please understand that if you try to help. You WILL need to spell it out for me.

Thank you in advance.

I downloaded the latest version of Ubuntu last night. I want to learn something new. I do NOT want to end in dismal failure like I did years ago trying to install Redhat that I never got running.

So I burned the Ubuntu ISO image to a CD. I installed it in the CD drive of the target machine, an AMD Athlon XP running at 1533 Mhz with 1/2 gig of ram. It is unfortunately equipped with an Nvidia GeForce 2 MX 400 video card, which seems to be the source of my complications. The disc checks fine. When I go to install it starts up, I tell it to start or install Ubuntu, it reads the disc, thinks for a while, and then I get the "out of scan range" message from my monitor as Ubuntu changes video resolution and/or refresh rate. From that point on I can't do anything but shut the machine off and start over.

What are the specific steps for getting around this problem?

---

### Post by Therion on 2007-11-26
I don't have a solution for you, but it appears you're not the only one experiencing problems with Ubuntu and the MX400.  The simple solution would be to simply install a different video card.  For $30 or $40 you could drop in something like an nVidia FX-5500 or FX-6200 video card that would, most likely, resolve the problem straight away.

If that's not an option, you could *try* using the text-based Alternate-Install CD to at least get Ubuntu installed.  From there you'd need to install the nVidia legacy drivers, but from what I've read, even then your problems wouldn't be over, and the solution for getting around them far more complex than I can explain.  Hopefully someone else with more technical expertise will post a better work-around for you.

---

### Post by Sqwishy on 2007-11-26
when your monitor starts messing up, press ctrl+alt+f1... you SHOULD see a bunch of text, if not then try it again... and again... repeat for 1 min or until it works...

Once you see about 50 lines of white text or something, and the stuff everywhere stops dumping lines of text everywhere, try to login with the username ubuntu and no pasword, i think. If the terminal there is not prompting you for a login press ctrl+alt+f2, that terminal should be prompting for a login.

One you login type (and it's case sensitive btw)
```
sudo nano /etc/X11/xorg.conf
```
This will open a file that controls your display.
There are two sections that are important atm, but i think all we need to deal with is the refresh rate, right? The refresh rate is to high/low and the monitor is messing up right? If it isn't then you can shoot me, but if it is here's what you do.
Look though the file (use the arrow keys or press pagedown/pageup) and find the part that talks about your monitor
it should look somethign like...
```

Section "Monitor"
	Identifier   "Your monitor brand and model"

```
```

Section "Monitor"
	Identifier   "Generic Monitor"

```

Then look down the section and find the part that talks about your monitor range.
```
	HorizSync    Some numbers in here
	VertRefresh  Some more numbers in here
```
If you know the specs of your monitor's normal refresh rate and stuff put those in. For those numbers
Then press F2 to save (you'll probobly hafta press y or somethign to confirm overwriting)
And type 
```
sudo /etc/init.d/gdm restart
```
if you don't switch to the GUI automaticly press ctrl+alt+f7 
if you see an error please reply with the info :(

---

