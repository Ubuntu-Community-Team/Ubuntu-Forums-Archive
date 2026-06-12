---
title: "Adobe Flash crashes with Youtube"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by pooja on 2012-05-26
Hi everyone,
I've just clean-installed Ubuntu 12.04. First of all, my audio was out so I fixed it following Steps 1 to 3 of this [guide]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure") and updating the ALSA drivers from [here]("http://www.stchman.com/alsa_update.html"). Secondly, I installed Cinnamon and 2 of its themes from Terminal following a guide I googled. Now however everytime I try to play a video on YouTube, Adobe Flash player crashes (see picture attached). What can I do to fix this problem and be able to view youtube videos?
Thank you.

---

### Post by jadtech on 2012-05-26
not really a crash so much as you need to install flash , go to the software centre and install flash for Mozilla   this will work with firefox and for chrome  once its installed even though it not requested do a reboot  and you should be set .. 

i was getting the same message when I first set up 12.04  and installed flash the reboot fixed everything haven't had any trouble since  ..

if your using fire fox this to can help 
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

this also is great no need for flash 

[http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by pooja on 2012-05-26
Hi there!
I tried both the things (installed Adobe Flash plugin from Ubuntu Software Centre + installed Flash-aid plugin by Mozilla): problem persists, even after reboot.

---

### Post by jadtech on 2012-05-26
have you updated completely check software updater

---

### Post by Curtis6767 on 2012-05-26
Look at post #3

[http://ubuntuforums.org/showthread.php?t=1983218](http://ubuntuforums.org/showthread.php?t=1983218)

---

### Post by pooja on 2012-05-26
> **jadtech said:**
> have you updated completely check software updater

You mean Update Manager? Yes, tried that too, didn't work.


[QUOTE=Curtis6767 ]Look at post #3

[http://ubuntuforums.org/showthread.php?t=1983218](http://ubuntuforums.org/showthread.php?t=1983218)
 [/QUOTE]

I'm gonna try. Will let you know.

---

### Post by pooja on 2012-05-26
Tried that too - worked for 5 seconds then it crashed again.

Actually, thinking it backwards, Adobe flash player was working all right the first time around, then I had that sound problem I was mentioning above. After fixing it, I tried (un)installing a number of applications. Then I tried playing a YouTube video and started having this problem. I gave up for some time, came back and installed Cinnamon (I like it very much with Ubuntu 12.04). Checked for Updates but was still having trouble starting a YT video because Flash Player crashes everytime.

---

### Post by darkod on 2012-05-26
Did you uninstall the previous tries to make flash work? Remove the flash-aid and the other package you installed.

Also, there is the possibility that there is conflict with flash from the (un)installing of packages you did.

Otherwise, the option with copying the libflashplayer.so file works 100%.

Remove all packages you installed for flash with apt-get remove --purge so that the settings are also removed.

---

### Post by pooja on 2012-05-26
> **darkod said:**
> Did you uninstall the previous tries to make flash work? Remove the flash-aid and the other package you installed.

That's the first thing I did, got rid of Flash-Aid and that method did work, only for too little a time. Then it crashed. I can't make things right. Hope it's not Cinnamon. Or Nvidia drivers.

Plugins (including Shockwave) are all updated, according to mozilla FF. (See my 2nd post, for a list of all plugins)

---

### Post by pooja on 2012-05-26
Perhaps I should uninstall Mozilla FF completely? Say like 
```
sudo apt-get remove --purge mozilla
```
(Is it even correct?)
Then repeat the same precudure with ```
flashplugin_installer
```

---

### Post by darkod on 2012-05-26
If you want to try it would be:
sudo apt-get remove --purge firefox

But I'm not sure that would sort it. I can't tell what the problem is.

I only know I am using the method with just copying the file for years, and it always worked fine.

---

### Post by pooja on 2012-05-27
Still not working. Perhaps I should try re-installing the system? After all, what have I got to lose? I've already made a backup of important files.

---

### Post by darkod on 2012-05-27
That is up to you. But I think there is some conflict.

If you decide to install new, immediately after that don't try to install anything about flash. Just copy this libflashplayer.so file in the /Home/.mozilla/plugins folder and check to see if it works. I am sure it will.

You can keep this file you have now and use it, no need to download from adobe again and unpack. Just copy this libflashplayer.so to a usb stick or where ever and you can use it any time you want.

---

### Post by pooja on 2012-05-27
OK. Thanks everyone for your input.

---

