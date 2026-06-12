---
title: "WideScreen Notebook"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by adolph on 2007-04-19
Hi Everyone;

Need some help with the setup of my wide screen, I have a Acer TravelMate 4202WLMi notebook.
I have read some of the pages on the forum that goes through the process of updating the /etc/X11/xorg.conf file's resolution and modeline without any luck.
My Notebook has a INTEL Mobile 945GM display card, which has been installed without much of a fuss... just the screen looks terrible!!! PLEASE HELP...
Adolph.

---

### Post by Flavian on 2007-04-21
I have a problem as well with my widescreen... If I set the resolution to: 1280x800 the screen looks  weird. It seems as if it mirrors what's on the left side, to the right side in an awful way.
I changed the resolution only through system - pref - screen res. not manually in the xorg.conf
My Graphics card is an ATI X700 Mobile, I am using a laptop. 
xorg.conf says that it uses the "ati" driver.

Can anyone help me?

That's how it looks like:

---

### Post by pillu on 2007-04-21
> **adolph said:**
> Hi Everyone;

Need some help with the setup of my wide screen, I have a Acer TravelMate 4202WLMi notebook.
I have read some of the pages on the forum that goes through the process of updating the /etc/X11/xorg.conf file's resolution and modeline without any luck.
My Notebook has a INTEL Mobile 945GM display card, which has been installed without much of a fuss... just the screen looks terrible!!! PLEASE HELP...
Adolph.

This is what worked for me
```
sudo apt-get install 915resolution
```

This patches the xorg.conf file to the required resolution. For my laptop it added the 1280x800 resolution to the list of available resolutions. Earlier the max resolution was 1024x768 and now it is 1280x800 which is the max available for my laptop. After installing this patch, just reboot and then change your resolution to 1280x800 in System -> Preferences -> Screen Resolution.

Hope this helps

pillu

---

### Post by Flavian on 2007-04-22
Hi :)
Does anyone have a solution for me, cause 915resolution only works for intel graphichips!
And I have an ATI graphicscard.

Thanks in advance
Flo

---

### Post by Flavian on 2007-04-22
Got it up and running, now :)

---

