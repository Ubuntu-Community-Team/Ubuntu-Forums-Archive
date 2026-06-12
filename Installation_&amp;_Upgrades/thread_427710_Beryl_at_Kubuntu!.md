---
title: "Beryl at Kubuntu!"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by athenix on 2007-04-29
Okei people.
I need some help here..

I have try many times to get beryl at my pc. I have nvidia grapic card. Geforce go 7600. And the beryl is ******* up mye screen. Top bar just dissaper.. why?

Can some one help me to explain how i can install Beryl for kubuntu? :)

---

### Post by paparucino on 2007-04-30
> **athenix said:**
> 
I have try many times to get beryl at my pc. I have nvidia grapic card. Geforce go 7600. And the beryl is ******* up mye screen. Top bar just dissaper.. why?

Can some one help me to explain how i can install Beryl for kubuntu? :)

Try this 

```
http://doc.gwos.org/index.php/BerylOnEdgy
```

It's written for Edgy but it's valid for Feisty too.

Note. First you MUST remove Installation of XGL/AIGLX and make a copy of /etc/X11/xorg.conf









UAResolved

---

### Post by monstermunch on 2007-04-30
> **athenix said:**
> Okei people.
I need some help here..

I have try many times to get beryl at my pc. I have nvidia grapic card. Geforce go 7600. And the beryl is ******* up mye screen. Top bar just dissaper.. why?

Can some one help me to explain how i can install Beryl for kubuntu? :)

I found that I could start berly when I logged into a failsafe session (e.g. no KDE). I found that if I killed kdesktop first, beryl would start. I didn't my title bars would disappear. I use this script to start beryl inside of KDE (messy but it works):

killall kdesktop
sleep 1
beryl-manager&
sleep 1
beryl&

Make sure you have the following in your xorg "Screen" section:

    DefaultDepth    24
    Option         "DisableGLXRootClipping" "True"
    Option         "AllowGLXWithComposite" "true"
    Option         "RenderAccel" "true"
    Option         "backingstore" "true"
    Option         "XAANoOffscreenPixmaps"
    Option         "AddARGBGLXVisuals" "True"

And this in "Extensions":

    Option         "Composite" "Enable"

---

### Post by Roisen.dubh on 2007-04-30
I found a lot of long winded guides when I was installing Beryl, but one guide I found (that worked) was really short and simple.

first, download envy [here]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.2-0ubuntu5_all.deb"), and run. Download it's recommended driver. (link assumes you have Feisty or Edgy)

second, enter these commands inter a terminal one at a time, pressing enter after each one:
> 
sudo gedit /etc/apt/sources.list

Add the following line to the top of the text file that comes up for editing:

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main

Save the file and quit. Now back on the command line, issue the following four commands, one at a time:

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

sudo apt-get update

sudo apt-get install beryl beryl-manager emerald-themes heliodor beryl-manager

beryl-manager

There should now be a shiny red gem appearing in the notification area (Windows refugees, think "system tray") near the upper right of your screen. Right-clicking that icon gives you several useful options.

Guide taken from [www.pcworld.com/article/id,130923-page,1-c,linux/article.html](www.pcworld.com/article/id,130923-page,1-c,linux/article.html)

---

