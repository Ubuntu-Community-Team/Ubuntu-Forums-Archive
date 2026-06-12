---
title: "Purple screen of death after upgrade to 11.10"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by Halibutt on 2011-12-04
I was happy with my 11.04 for quite some time, it worked a charm on my desktop. Lately, a pop-up appeared urging me to upgrade to 11.10. I used to have problems with upgrading Ubuntu in the past (well, it actually never worked), but for some reason I decided to give the update a try. 

The installation process went just fine (with some minor problems with Apache, but that shouldn't cause problems, should it). I rebooted and... nothing. Black screen. Or rather Ubuntu's dark purple screen. No chance to switch to console, log in, nothing. 

So I downloaded and burned 11.10 to a cd, booted it up and decided to go with the upgrade from disc. Same result. Any ideas?
Cheers

P.S. I'm dual-booting with Windows 7x64

---

### Post by MAFoElffen on 2011-12-05
> **Halibutt said:**
> I was happy with my 11.04 for quite some time, it worked a charm on my desktop. Lately, a pop-up appeared urging me to upgrade to 11.10. I used to have problems with upgrading Ubuntu in the past (well, it actually never worked), but for some reason I decided to give the update a try. 

The installation process went just fine (with some minor problems with Apache, but that shouldn't cause problems, should it). I rebooted and... nothing. Black screen. Or rather Ubuntu's dark purple screen. No chance to switch to console, log in, nothing. 

So I downloaded and burned 11.10 to a cd, booted it up and decided to go with the upgrade from disc. Same result. Any ideas?
Cheers

P.S. I'm dual-booting with Windows 7x64
What is your graphics card? (Instructions will go from that info.)

---

### Post by Halibutt on 2011-12-05
> **MAFoElffen said:**
> What is your graphics card? (Instructions will go from that info.)Hell, forgot my specs, sorry about that. Nvidia GeForce 9600GT (512MB) - Asus P5Q SE/R - Intel Core2Duo E8400 3000MHz 
Cheers

---

### Post by MAFoElffen on 2011-12-05
> **Halibutt said:**
> Hell, forgot my specs, sorry about that. Nvidia GeForce 9600GT (512MB) - Asus P5Q SE/R - Intel Core2Duo E8400 3000MHz 
Cheers
Either hold the shift key down during boot and select the safemode/low graphics to boot into a GUI -or- use this method using " nomodeset " as a kernel boot option:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**[/SIZE][/COLOR][/SIZE][/COLOR]

I would tell you to just go to Additional Driver and install your drivers (nvidia-current) ***BUT*** it sounds like you had drivers loaded and something went aerie with them... So do this instead:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1][**Installing NVidia Packaged Drivers**]("http://ubuntuforums.org/showpost.php?p=11467050&postcount=797")[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by kio_http on 2011-12-05
When you see this purple screen does CTRL + ALT + F1 give you a full screen console also does recovery mode work?

Have you in the past used drivers from the Nvidia website?

---

### Post by Halibutt on 2011-12-05
Thanks for your help gentlemen. Sadly, no success so far. 

Argh! Something changed, must've fiddled around with boot settings or the reinstall did something. In any way, normal boot now shows some text instead of purple screen of death, but hangs on "Checking for running unattended-upgrades   [OK]". 

> **MAFoElffen said:**
> Either hold the shift key down during boot and select the safemode/low graphics to boot into a GUIDoesn't work. It hangs on "Checking battery state... [OK]". 

>  -or- use this method using " nomodeset " as a kernel boot option:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**[/SIZE][/COLOR][/SIZE][/COLOR]

Interestingly, the "nomodeset" is already there. The line looks slightly different as it doesn't include "quiet splash" nor "vt.handoff=7" parameters. 

It's more or less like this:
```

linux /vmlinuz-3.0.0-14-generic root=UUID=blahblahblah ro recovery nomodeset _
```

> **kio_http said:**
> When you see this purple screen does CTRL + ALT + F1 give you a full screen console also does recovery mode work?I don't see it now, but it didn't work yesterday. As to recovery mode, it kind of works. It shows me the graphic window with options to resume, fsck, remount or root. Shell prompt fires up just fine. 

> Have you in the past used drivers from the Nvidia website?I can't remember, though I believe I might have tried those when trying to (unsuccessfully) force Ubuntu to recognize my other screen for XBMC to run on my TV. 
Cheers

---

### Post by oldtimer7777 on 2011-12-05
Did you do an upgrade of your entire system via WiFi connection instead of a trustworthy hardwired ethernet connection?

If you did you might have hosed it with a bad connection. I don't know why Ubuntu doesn't advise their users about that fact, but that would be a good suggestion at the very least. 

> **Halibutt said:**
> Thanks for your help gentlemen. Sadly, no success so far. 

Argh! Something changed, must've fiddled around with boot settings or the reinstall did something. In any way, normal boot now shows some text instead of purple screen of death, but hangs on "Checking for running unattended-upgrades   [OK]". 

Doesn't work. It hangs on "Checking battery state... [OK]". 



Interestingly, the "nomodeset" is already there. The line looks slightly different as it doesn't include "quiet splash" nor "vt.handoff=7" parameters. 

It's more or less like this:
```

linux /vmlinuz-3.0.0-14-generic root=UUID=blahblahblah ro recovery nomodeset _
```I don't see it now, but it didn't work yesterday. As to recovery mode, it kind of works. It shows me the graphic window with options to resume, fsck, remount or root. Shell prompt fires up just fine. 

I can't remember, though I believe I might have tried those when trying to (unsuccessfully) force Ubuntu to recognize my other screen for XBMC to run on my TV. 
Cheers

---

### Post by Halibutt on 2011-12-05
Quick update: got the PSoD again. I tried to follow the instructions on installing nvidia drivers linked above. This time the "quiet splash vt.handoff=7" part was there, so I replaced it with "--verbose single", saved and taddah! Here it is. Ctrl+alt+F1 doesn't work, no reaction for a looooong time. 

Rebooted again, tried the "nomodeset" - and the computer hanged on Checking battery state (what the heck, it's a desktop). 

> **oldtimer7777 said:**
> Did you do an upgrade of your entire system via WiFi connection instead of a trustworthy hardwired ethernet connection?

If you did you might have hosed it with a bad connection. I don't know why Ubuntu doesn't advise their users about that fact, but that would be a good suggestion at the very least.Nope. First installation (failed) was wired, the second (also failed) from a dvd (also downloaded through a wired connection). 
Cheers

---

### Post by MAFoElffen on 2011-12-06
> **Halibutt said:**
> Quick update: got the PSoD again. I tried to follow the instructions on installing nvidia drivers linked above. This time the "quiet splash vt.handoff=7" part was there, so I replaced it with "--verbose single", saved and taddah! Here it is. Ctrl+alt+F1 doesn't work, no reaction for a looooong time. 

Rebooted again, tried the "nomodeset" - and the computer hanged on Checking battery state (what the heck, it's a desktop). 

Nope. First installation (failed) was wired, the second (also failed) from a dvd (also downloaded through a wired connection). 
Cheers
if you can get it to a tty text console by using the "--verbose single " boot switches then you could install the packaged driver via the link in my last post.

The hanging at "*checking battery state*" through the "*checking for system V compatibility*" messages usually points to the graphics drivers- either not loaded because theiir not there, mis-configured, or there are multiple versions of drivers (or fragments of) that are conflicting with each other.

One thing you might try first is to boot off a LiveCD and find the /etc/X11/xorg.conf on your installed sys and rename if to xorg.conf.bak then try to start with " nomodeset ".

If you look in the instructions I linked to, it has instructions their to remove both binary or packaged drivers, as well as ensure the correct pieces are present before you install your new driver. (It has all the latest workarounds).

If it happens that you have something out-of-the-ordinary and is different- I want to know.  I maintain the Graphics Resolution Sticky here in this forum and all it's tutorials.  I've had a lot of practice working out X-Windows issues since 1988, with Unix and later Linux. It's something I like doing.

If you go to my sticky:
**[B]Sticky:**[/B]                         [COLOR=#008C00]**[all variants]**[/COLOR] [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

Go to post 2, which is a "Table Of Contents" with links to most of the tutorials and workarounds... Things that Ii found myself explaining repeatedly. 

The plan- you need to install new drivers, while cleaning out any old fragments.

How? - I'm thinking 3 ways off the top of my head...
1. Using a " nomodeset " boot parameter by editing the grub menu and starting the GUI tio get to the Additional Drivers applet to install a new driver... Since this was an upgrade when the problem happened, I would go to a terminal session and use my instructions.
2. Boot "recovery" and go root prompt or edit the grub menu to boot TTY text console to get to a CLI..- to install as per the instructions...
3. Boot from a LiveCD, mount and chroot the installed system. That way you can install from a GUI to the mounted system...

All the instructions for all those possibilities are linked from that post.

---

### Post by kio_http on 2011-12-06
> **oldtimer7777 said:**
> Did you do an upgrade of your entire system via WiFi connection instead of a trustworthy hardwired ethernet connection?

If you did you might have hosed it with a bad connection. I don't know why Ubuntu doesn't advise their users about that fact, but that would be a good suggestion at the very least.

There is nothing so risky about a WIFI connection.

---

### Post by Halibutt on 2011-12-06
I specifically mentioned that verbose single gets me the PSoD, so no, no text console there. I tried the same from text console in recovery mode. But "sudo apt-get update" gets me nowhere, lots of Failed to fetch "could not resolve 'archive.ubuntu.com'" errors. Also "unable to write to /var/cache/apt" and "The package lists or status file could not be parsed or opened". Argh, will post more info once I log back to Windows. 
Cheers

EDIT/ Partial success aka I gave up trying. After countless reboots I simply decided Ubuntu is not worth my efforts and decided to install it once again over the previous 11.10 installation, overwriting all, instead of simply updating (aka breaking the working installation). This created some conflict with Grub apparently, as on the first Grub screen I have to chose "Windows 7" and only then the second Grub screen appears where I have to chose ubuntu, but at least the system loads now. Not the cleanest solution I guess, but it would have to do. 

Thanks for all the efforts guys, apparently I'm not tech-savvy enough to use this linux for the people. Or perhaps I'm not one of the people this linux is meant for. 
Cheers

---

### Post by MAFoElffen on 2011-12-06
> **kio_http said:**
> There is nothing so risky about a WIFI connection.
At this point, what does matter is that it is hosed and the OP needs to get back up and going...

---

### Post by kio_http on 2011-12-06
> **Halibutt said:**
> I specifically mentioned that verbose single gets me the PSoD, so no, no text console there. I tried the same from text console in recovery mode. But "sudo apt-get update" gets me nowhere, lots of Failed to fetch "could not resolve 'archive.ubuntu.com'" errors. Also "unable to write to /var/cache/apt" and "The package lists or status file could not be parsed or opened". Argh, will post more info once I log back to Windows. 
Cheers

EDIT/ Partial success aka I gave up trying. After countless reboots I simply decided Ubuntu is not worth my efforts and decided to install it once again over the previous 11.10 installation, overwriting all, instead of simply updating (aka breaking the working installation). This created some conflict with Grub apparently, as on the first Grub screen I have to chose "Windows 7" and only then the second Grub screen appears where I have to chose ubuntu, but at least the system loads now. Not the cleanest solution I guess, but it would have to do. 

Thanks for all the efforts guys, apparently I'm not tech-savvy enough to use this linux for the people. Or perhaps I'm not one of the people this linux is meant for. 
Cheers

I would recommend backing up and doing a fresh install using the manual partitioning option (install t and format current ubuntu partition) . If you are technical enough you may prefer the alternate install option.

---

### Post by MAFoElffen on 2011-12-06
> **kio_http said:**
> I would recommend backing up and doing a fresh install using the manual partitioning option (install t and format current ubuntu partition) . If you are technical enough you may prefer the alternate install option.
If the OP does a fresh intall, he/she will most likely end at a the same point until the graphics drivers are loaded.

He could backup, install fresh, install his drivers as I suggested before and end up clean... without any apache errors.. Reinstall any apps, he had before, reinstall any data he wanted back on there...

Or he could install his drivers on what he has.... And reinstall Apache. His call.

I do both for various customers.  The first option is more time intensive and a bigger bill. 

If this OP is doing this himself. We can provide him with clear understandable instructions for whatever he decides is best for him and his resources.  I know for me, I have Servers and Terabites to back off to (to play with)... Average users have to figure out what resources they have and hopefully be clear on what they need help with.

Right?

---

### Post by Halibutt on 2011-12-06
Thanks, I reinstalled the system (overwriting 11.10 with 11.10) from a dvd and Ubuntu works just fine, proprietary drivers installed from within the system. I have another problem though. I repaired grub (the problem mentioned in my last post) and it works just fine for Ubuntu or recovery mode or memtest. However, Windows 7 option is there, but doesn't work at all...

I posted a [new thread about it here]("http://ubuntuforums.org/showthread.php?p=11518777#post11518777"). 
Cheers

---

### Post by Halibutt on 2011-12-07
Yesss! It worked a charm, thank you very, very much gentlemen. Now the option to boot to Windows 7 properly invokes the right Boot up screen (with two options, to boot to Windows and to Ubuntu). While this still is somewhat messy (first a grub window with all 5 options, then another window with two), it works, which is all I wanted. 

Thank you once again. 
Cheers

---

