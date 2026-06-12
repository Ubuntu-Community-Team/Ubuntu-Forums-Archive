---
title: "How do i upgrade Xfree86?"
date: 2004-10-26
forum: Installation &amp; Upgrades
---

### Post by brschmid on 2004-10-26
i want to upgrade to the latest, but i don't know how. i don't even know what is included in Ubuntu :(

help

---

### Post by cseg on 2004-10-26
Ubuntu currently uses XFree86 4.3.0 but has stated that in the next release they will move to x.org.

To get the latest x.org build, start here:

[http://www.freedesktop.org/XOrg/CvsPage](http://www.freedesktop.org/XOrg/CvsPage)

---

### Post by brschmid on 2004-10-26
[QUOTE=cseg]Ubuntu currently uses XFree86 4.3.0 but has stated that in the next release they will move to x.org.

To get the latest x.org build, start here:

[http://www.freedesktop.org/XOrg/CvsPage](http://www.freedesktop.org/XOrg/CvsPage)[/QUOTE]
 what is the difference, how do i uninstall xfree and install x.org then?
and i have this video device, is it supported?  Intel 82552/82855 GM/GME

---

### Post by HiddenWolf on 2004-10-26
X, at the moment, is really an 'if it works, leave it' package.

I don't know how much experience you have with linux, but the differences between XFree and X.org are at the moment not very big.

If the ubuntu patched XFree works for you now, I'd advice you strongly to leave it. 
X.org is a fork of an XFree version, and as such is not very different yet.

XFree is dead, so it will get replaced eventually, and for the future X.org has some great plans, to improve looks and speed, and ease of use, but as for now, there is little to gain beyjond the knowledge you're cutting-edge.

---

### Post by brschmid on 2004-10-26
[QUOTE=HiddenWolf]X, at the moment, is really an 'if it works, leave it' package.

I don't know how much experience you have with linux, but the differences between XFree and X.org are at the moment not very big.

If the ubuntu patched XFree works for you now, I'd advice you strongly to leave it. 
X.org is a fork of an XFree version, and as such is not very different yet.

XFree is dead, so it will get replaced eventually, and for the future X.org has some great plans, to improve looks and speed, and ease of use, but as for now, there is little to gain beyjond the knowledge you're cutting-edge.[/QUOTE]
 ok, i was just curious because my screen on my laptop is blurry and i am unsure how to fix it.

---

### Post by HiddenWolf on 2004-10-26
Wish I could help. 

There is an option in XFree86config for LCD displays, to improve the way it looks, but I am no expert, so I really can't advise you on it.

Best of luck.

---

### Post by brschmid on 2004-10-26
[QUOTE=HiddenWolf]Wish I could help. 

There is an option in XFree86config for LCD displays, to improve the way it looks, but I am no expert, so I really can't advise you on it.

Best of luck.[/QUOTE]
 where is that option, do you know?

---

### Post by HiddenWolf on 2004-10-26
Try backing up your Xfree86 config file, then running XFree86config

It should present you with a question regarding LCD displays.

However, chances are that X doesn't work if you choose the wrong awnser somewhere during config, so make sure you can always put your original config back.

---

### Post by brschmid on 2004-10-26
[QUOTE=HiddenWolf]Try backing up your Xfree86 config file, then running XFree86config

It should present you with a question regarding LCD displays.

However, chances are that X doesn't work if you choose the wrong awnser somewhere during config, so make sure you can always put your original config back.[/QUOTE]
 ok, newb here, where is the config file at? how do i back it up? and what command to run the config util??

---

### Post by HiddenWolf on 2004-10-26
config file is  /etc/X11/XFree86config

to back it up, just copy it
cp <file> <different file name>
That will copy the file, to a file with the different file name

so if you want to copy /etc/X11/XFree86config, do this
cd /etc/X11
cp XFree86config XFree86config-backup

Then run XFree86config

Don't hold it against me if it's not 100% correct, but that's the idea.

---

### Post by normnmiles on 2004-10-26
XFree86 saves it's configuration file under ```
/etc/X11/XF86Config-4
```, side note for the next release, xorg saves it's config file in the same location but calls it ```
/etc/X11/xorg.conf
``` instead.  You can find the various XFree86 configuration tools under /usr/X11R6/bin.  I would start xfree86config from the terminal by using ```
$sudo /usr/X11r6/bin/xf86config
```

---

### Post by brschmid on 2004-10-26
[QUOTE=HiddenWolf]config file is  /etc/X11/XFree86config

to back it up, just copy it
cp <file> <different file name>
That will copy the file, to a file with the different file name

so if you want to copy /etc/X11/XFree86config, do this
cd /etc/X11
cp XFree86config XFree86config-backup

Then run XFree86config

Don't hold it against me if it's not 100% correct, but that's the idea.[/QUOTE]
 close enough, thanks :)

---

### Post by brschmid on 2004-10-26
[QUOTE=HiddenWolf]config file is  /etc/X11/XFree86config

to back it up, just copy it
cp <file> <different file name>
That will copy the file, to a file with the different file name

so if you want to copy /etc/X11/XFree86config, do this
cd /etc/X11
cp XFree86config XFree86config-backup

Then run XFree86config

Don't hold it against me if it's not 100% correct, but that's the idea.[/QUOTE]
 there is XF86Config-4 but i can't execute it.

---

### Post by normnmiles on 2004-10-26
That's the configuration file...make a backup copy of that as those are your current settings for XFree86.  
```
$sudo cp XF86Config-4 XF86Config-4.Ubuntuconfig
```
then run the configuration tool to create a new /etc/X11/XF86Config-4 file
```
$sudo /usr/X11R6/bin/xf86config
```

---

### Post by Julius on 2004-10-26
[QUOTE=brschmid]ok, i was just curious because my screen on my laptop is blurry and i am unsure how to fix it.[/QUOTE]
 What screen resolution are you using? With LCD monitors, the screen seems blurry when the "wrong" screen resolution is used.
I mean, if your monitor supports 1280x1024 (or higher), use it, it can really help.

"Big" (17'', 19'') LCD monitors will work better using high screen resolutions, I think. I don't use a LCD monitor myself, but I have two in my house and they look blurry when windows is starting. They look normal when windows starts at the highest resolution supported.

---

### Post by brschmid on 2004-10-26
[QUOTE=Julius]What screen resolution are you using? With LCD monitors, the screen seems blurry when the "wrong" screen resolution is used.
I mean, if your monitor supports 1280x1024 (or higher), use it, it can really help.

"Big" (17'', 19'') LCD monitors will work better using high screen resolutions, I think. I don't use a LCD monitor myself, but I have two in my house and they look blurry when windows is starting. They look normal when windows starts at the highest resolution supported.[/QUOTE]
 this is a laptop with native resolution of 1024x768

---

### Post by brschmid on 2004-10-26
[QUOTE=normnmiles]That's the configuration file...make a backup copy of that as those are your current settings for XFree86.  
```
$sudo cp XF86Config-4 XF86Config-4.Ubuntuconfig
```
then run the configuration tool to create a new /etc/X11/XF86Config-4 file
```
$sudo /usr/X11R6/bin/xf86config
```[/QUOTE]
 thanks :)

---

### Post by FLeiXiuS on 2004-10-26
The only differences that I know of are  because of licensing/copyright issues...

---

### Post by brschmid on 2004-10-26
[QUOTE=FLeiXiuS]The only differences that I know of are  because of licensing/copyright issues...[/QUOTE]
 running thru the config

---

### Post by daniels on 2004-10-28
Try editing /etc/X11/XF86Config-4, and removing the HorizSync and VertRefresh lines from the Monitor section.

I strongly, strongly urge you not to upgrade to X.Org.  We have about 300,000 lines of patches (more these days, I think) on top of XFree86, and it is a very highly customised build.  Building X from source is incredibly complicated and only likely to end up with a lot more pain.

---

### Post by brschmid on 2004-10-29
[QUOTE=daniels]Try editing /etc/X11/XF86Config-4, and removing the HorizSync and VertRefresh lines from the Monitor section.

I strongly, strongly urge you not to upgrade to X.Org.  We have about 300,000 lines of patches (more these days, I think) on top of XFree86, and it is a very highly customised build.  Building X from source is incredibly complicated and only likely to end up with a lot more pain.[/QUOTE]
 hmm, i will try that.


edit: did that and it is a little better now :) thanks, i just commented them out though.

---

