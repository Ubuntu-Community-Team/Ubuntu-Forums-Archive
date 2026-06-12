---
title: "Can I uninstall an ATI Restricted driver if it causes problems?"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by PiggiePaul on 2008-03-01
I need to ask this, and I need to know 100% if this can be done before I attempt it.

Just to give some history before I ask my question:
About 3 weeks ago when I 1st installed Ubuntu on my system, I said yes to the restricted drivers to go with my ATI X800 pro card.
After installing, the card was (for some reason) overheating which after a few mins gave green snow/interference on screen before the display started blacking out.

This caused me to wipe the HDD clean and try again, and this time I used ENVY to install them, and the same thing happened again..

Now, I understand new ATI drivers have just been released.

So I need to ask two VERY IMPORTANT things:

1: What is the best way to install these latest drivers from ATI ?

2: If I do install them, is there a sure fire way to remove them and go back with the default drivers you just get when you install Ubuntu and say NO to the restricted drivers.

Otherwise, it means I will have to wipe my system again.

Oh, and of course, is anyone running an X800 ATI card fine?

Thanks.

---

### Post by kevinatkins on 2008-03-01
Hi,

Yes, you can reinstall the original driver, no problem. This should get you out of jail any time an X configuration goes wrong - here's how:

1. Switch to a text terminal by pressing <Ctrl>-<Alt>-<F1> together.

2. Enter you username and password.

3. You need to shut down any X sessions that are running. Do this by typing:

```
sudo /etc/init.d/gdm stop
```

at the command prompt (this assumes you're using Gnome with the gdm desktop manager. If you're using Kubunu, substiture 'gdm' with 'kdm')

4. Now you need to reconfigure X. At the command prompt, type

```
sudo dpkg-reconfigure xserver-xorg
```

Then follow the instructions. When it comes to choice of video driver, make sure you *don't* select fglrx, which is the ATI proprietary driver. I think the standard open-source driver is called 'aty' or similar. Choose the defaults for everything else, and go for 'simple' configuration of monitor.

5. Once you've finished, it's probably best to reboot the system. Just type

```
sudo reboot
```

at the command prompt, and hopefully your machine should reboot successfully back to a standard desktop.

Bit puzzled why your card is overheating though...

---

### Post by PiggiePaul on 2008-03-01
Thank you for the advice.

If you just go to Google and type in "X800 Ubuntu Overheating" you will see I'm not alone.

I don't really understand what drivers come with Ubuntu if (like me) you say NO to any RESTRICTED DRIVERS.

Even without these, Compiz runs fluid and smooth, Cube, Reflections, Paint with fire, water droplets all smooth and fast.

I've not run any 3D games, and I just installed Google earth and that's the 1st thing I've tried that slow and choppy as hell.

As I say, I have a ATI X800 pro card on a AMD64 3200+ system.

What happened twice (with fresh installs) was after about 15 mins (approx it did vary) I got some green speckles/noise appearing on screen, also my cards fan went to full speed (which it NEVER does - only during VERY intensive 3D gaming)

The screen went off, then back on, then off, and if I did not shut down by the 3rd or 4th time, I'd loose the display totally, and my PC had no graphics (even in the BIOS) until I turned the PC off for a few mins.

Everything points to overheating. (or rather the card being overclocked)

I don't know what version of the ATI drivers they were.

If I use ENVY and say install manually I get to choose 3 versions:

In the order listed in ENVY, they are:

8-01
8.40.4
8.28.8

I don't know what these numbers mean, what is the latest, and which I may have installed last time when I just let it do it automatically.

---

### Post by PiggiePaul on 2008-03-01
Oh well.....

I knew I was going to regret this (and I am regretting it)

Using ENVY I installed the 8.40.4 drivers.

With these drivers I was not able to enable the "Custom Desktop Visual Effects" and also Google Earth just froze upon loading.

So went back to ENVY and did the auto install, which installed the latest ATI drivers:
8-01-x86.x86_64.run

Rebooted, and YES, I was then able to use the Custom Visual Effects, and also Google Earth ran, albeit buggy, as only whilst the Google earth graphics were actually updating was there anything to see in it's window, as soon as the image (or the earth) stopped updating, the window went black. Even moving the mouse around was enough to make it show, but stop the mouse and the screen went black.

Ok, so that aside, I started setting Compiz again, then after about 10 / 15 mins I noticed the green snow/interference start to show on the screen again, so I had to shut down quick before I lost my display.

Turned PC off, and back on again, and had NOTHING on screen at all. Not even a BIOS screen a dead display.

So held power switch and turned PC off for a couple of mins before turning on again, and back into Ubuntu, then used ENVY to remove the ATI drivers.

Another Reboot, and back up and running again, though, guess what.

Yup, I can't enable the Custom Visual Effects now (I had them working perfect before)

Oh poo, dammit, blast etc etc............ :(

---

### Post by PiggiePaul on 2008-03-01
Just an update - (Talking to myself really!!!!)

But good to keep track of things........................

As I said, uninstalled ATI driver via ENVY but then I was left with a HORRID end result.

I don't know what Ubuntu gave me when I installed it as a video driver, but whatever it gave me, I had lovely and smooth Compiz Effects. Now, (after using ENVY to remove the ATI drivers) I had a horrid, slow, clunky desktop.

Really rotten, and not a hope in hell of Compix running, even moving a window around the screen was jerky.

OH WHY DID I TOUCH THIS IN THE 1ST PLACE !!!!

So, went back to SYSTEM / ADMINISTRATION and ticked the Restricted Drivers option, it installed some drivers (no idea what, but they were not the same ATI ones that Envy got as they were a lot quicker to download and I did not recognize the version number of the filename.

Rebooted, and back with smooth moving windows again.

Just waiting to see if I get my green noise/pixels appear on screen in the next 5 to 10 mins.

If I DO get the noise back, I wonder, if there is anyway to get back to the drivers I had before I started?

They were super fast and smooth for ANY of the Compiz effecte, Cubes, Fire on screen etc etc. Even the 3D screensavers, all fast and smooth.

They were just no good for something like Google Earth and I guess 3D games.

I can live without Games and Google Earth !!!!

---

