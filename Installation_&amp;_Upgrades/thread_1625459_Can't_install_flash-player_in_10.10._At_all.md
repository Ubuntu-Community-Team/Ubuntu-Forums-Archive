---
title: "Can't install flash-player in 10.10. At all"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by Antiverminseed on 2010-11-19
I've tried using synaptic, didn't work. Tried completely removing it with the synaptic and then installing it again using apt-get install flashplugin-nonfree. didn't work either. 

I've looked around a lot and I have yet to find anything helpful. 

In synaptic and in terminal i get this: "Sub-process usr/bin/dpkg returned an error code(1)"

I don't really know what it means. 

I read somewhere i should locate libflashplayer.so and copy it to the chromum-browser folder (i use chromium) so i ran 

```
locate libflashplayer.so
``` 

in terminal and got 

```
/usr/lib/chromium-browser/plugins/libflashplayer
```


So it seems it's already in the right place. So i tried using this: 

```
chromium-browser --enable-plugins
```

Which just opened a new default chromium window. No options for enabling plugins. 

i also checked the about: plugins page in chromium. I found the option to disable/enable "VLC multimedia plugin" under which i found "video/flv - flash-video". it was already enabled. 

Well, i just don't know what to do. Any ideas, anyone?

---

### Post by oboedad55 on 2010-11-19
Are you using 64 bit or 32 bit? I just downloaded the flash from Adobe, unzipped it and copied the libflash file over to /usr/lib/mozilla/plugins. If you have 64 bit OS installed make sure that's the one you grab. Normally Chromium picks up the the Mozilla plugins.

---

### Post by Antiverminseed on 2010-11-19
> **oboedad55 said:**
> Are you using 64 bit or 32 bit? I just downloaded the flash from Adobe, unzipped it and copied the libflash file over to /usr/lib/mozilla/plugins. If you have 64 bit OS installed make sure that's the one you grab. Normally Chromium picks up the the Mozilla plugins.

I see. I'm running 64 bit. 

Something's seriously messed up anyway. Now i can't open synaptic package manager. I get this: 

"Error: opening the cache (E: Read error - read (5: Input/output error), E: The package lists or status file could not be parsed or opened.)"

This error message didn't appear until later when i booted the computer (i guess when looking for updates). But except trying to install flash there's really not much i have done since installing ubuntu. I tried installing vlc which worked fine except the flash-problem. I also installed some small, ordinary programs without any problems at all (Wine, spotify, chromium). 

So now i'm REALLY lost. 

FYI: I did use ubuntu earlier this year but because of a lot different reasons i switched to windows 7. Later on my computer completely crashed (still a mystery to me why this happened) and then i decided to try ubuntu again. So i'm not totally new to ubuntu but almost.

---

### Post by dino99 on 2010-11-19
now you need to reboot, then:

sudo dpkg --configure -a
sudo apt-get install -f

with synaptic :
search and remove/purge everything related to flash

then:
you need to install the package: flashplugin-installer (you get it if "canonical partner" repo is enabled into synaptic repo tab (third party)

---

### Post by Antiverminseed on 2010-11-19
> **dino99 said:**
> now you need to reboot, then:

sudo dpkg --configure -a
sudo apt-get install -f

with synaptic :
search and remove/purge everything related to flash

then:
you need to install the package: flashplugin-installer (you get it if "canonical partner" repo is enabled into synaptic repo tab (third party)

Thanks, i'll try that! I'm assuming you mean after doing the commands i'll be able to run synaptic? Cause now it won't run at all.

---

### Post by Antiverminseed on 2010-11-19
> **dino99 said:**
> now you need to reboot, then:

sudo dpkg --configure -a
sudo apt-get install -f

with synaptic :
search and remove/purge everything related to flash

then:
you need to install the package: flashplugin-installer (you get it if "canonical partner" repo is enabled into synaptic repo tab (third party)


I tried the first command you suggested and it didn't work out. I'm running ubuntu in swedish so I can't copy it but, translated, it said somehting like:

```
dpkg: failed to read in buffered copying to copy information file "var/lib/dpkg/available": Input/output error
```

I still tried running the other command you suggested and got (translated): 

```
Reading package lists... Error!
E: Reading error - read (5: Input/output error)
E: The package list or status file could not be parsed or opened
```


So... any other ideas? 

I don't know if it's relevant but i have yet to install any additional driver for my graphics card. I postponed it cause last time I got a lot of problems when i installed the proprietary driver that ubuntu suggested. Maybe i should have fixed that first, i don't know. 

ps. I'm running ubuntu in swedish but most things are still in english. The terminal is using both but  most other places in OS are in english ds.

---

### Post by Antiverminseed on 2010-11-20
I tried thís suggestion (first reply) from launchpad: 

[https://answers.launchpad.net/ubuntu/+source/apt/+question/119654](https://answers.launchpad.net/ubuntu/+source/apt/+question/119654)

The first command failed so I didn't bother with the rest. I'm not the most skilled linux user but i'm guessing the first command is copying some backup list or something. I figured since that simple command didn't work the rest was sort of useless. But what do I know. 

I've been looking around a lot and I can't find anything that works. I guess i could just do a clean install since I *just* installed ubuntu anyway but i'm afraid the problem will return. 

I could try doing the clean install and then try to install flash without f*****g it up this time. And maybe then the synaptic problem won't occur. 

but before i go do that last act of desperation, does anyone has any suggestions?

---

### Post by Antiverminseed on 2010-11-21
What do you know; i simple apt-get update did the trick. So now i'm back to my original problem; flash player!

---

### Post by wojox on 2010-11-21
Put it in 

```
/usr/lib/mozilla/plugins
```

It should work for chromium.

---

### Post by Antiverminseed on 2010-11-21
> **dino99 said:**
> now you need to reboot, then:

sudo dpkg --configure -a
sudo apt-get install -f

with synaptic :
search and remove/purge everything related to flash

then:
you need to install the package: flashplugin-installer (you get it if "canonical partner" repo is enabled into synaptic repo tab (third party)

Can't remove them. I get input/ouput error.

---

### Post by Antiverminseed on 2010-11-21
> **wojox said:**
> Put it in 

```
/usr/lib/mozilla/plugins
```

It should work for chromium.

I doubt it'll work if i don't get rid of all broken flash related stuff i've already got. 

i can't do anything with anything flash-related. I seem to get errors whatever I do. I've tried to remove everything that has to do with flash so I can try doing it all over, it doesn't work; i get input/outpur error.

---

### Post by Antiverminseed on 2010-11-21
I realize now what i did wrong the first time. Now the problem is just about not being able to remove the broken packages. I can't remove them. Whatever I do I get "Input/output error". The same happens when i try reinstalling it.

---

### Post by oldos2er on 2010-11-21
Try [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by Antiverminseed on 2010-11-22
> **oldos2er said:**
> Try [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

Hm, looks interesting. Almost to good to be true. since chromium uses the plugins from mozilla it should work in chromium as well. 

I'll get back to you with results.

---

### Post by Antiverminseed on 2010-11-22
> **oldos2er said:**
> Try [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

Best add-on ever! Can't believe it worked. I have no idea how it could have but it worked. I followed the output in terminal and saw the input/output errors along the way and thought I was screwed but then, somehow, it magically resolved itself. 

Thanks a lot! Never before has one single, lousy firefox add-on been so useful.

---

