---
title: "Can't start any GUI on Lenovo y510p"
date: 2013-06-16
forum: Installation &amp; Upgrades
---

### Post by RegginKrad on 2013-06-16
[This]("http://shop.lenovo.com/us/en/laptops/ideapad/y-series/y510p/index.html") is the laptop I just bought.

4rth gen Haswell
Nvidia GT 750M
UEFI (secureboot disabled, legacy on)

I can't get either gdm or lightdm to run.

On Ubuntu 13.04 64bit I did get a GUI running, but the windows were upside down (not rotated) while the actual click boxes remained where they normally would be, and the window borders were glitched to hell.

On Lubuntu 64bit I got a GUI that could only run on 640x480 (but external monitors could run any their normal native resolutions)

I have to use "nomodeset" on grub just to get a command line

This is where the loading process usually ends:
```

* Stopping System V runlevel compatibility                  [Ok]
* Starting                  [Ok]
* Starting                  [Ok]
* Stopping                  [Ok]
mountall: Plymouth command failed
mountall: Disconnected from Plymouth

```

but I can ssh in 

The error from "sudo xinit"
```

Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX


Fatal server error:
no screens found
(EE)
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional info                                   rmation.
(EE)
Server terminated with error (1). Closing log file.

```

This leaves the laptop with a blinking underscore in the top left corner

Google said to do a lot of random things with xorg.conf and .Xauthority (nothing ever came of that)

```
$ sudo service lightdm
startstart: Job failed to start
```


```
$ sudo service gdm start
gdm start/running, process 2032
```
nothing happens

During Ubuntu 13.04 install: GUI seems to work perfectly fine (with "nomodeset", else blank screen)

After install, "nomodeset" doesn't work by itself, but I can only get a basic terminal, no GUI.


--------------------------------------------
```

[COLOR=#000000][FONT=Ubuntu Mono] GRUB> vbeinfo
error: can't find command 'vbeinfo'.

```[/FONT][/COLOR]



I went through the sticky about blank screens, none of the solutions worked, and some solutions just led to more questions.



Any advice on what distribution I should try or what logs I should post?

---

### Post by bmwerks on 2013-06-21
Try finding out from the IRC channels. 
I ordered one of these as well so if you find the solution please post it.

---

### Post by cj100570 on 2013-07-31
I was facing a similar issue. The fix.... Hold the function button and up arrow to turn up screen brightness. By default it launches turned off.

---

