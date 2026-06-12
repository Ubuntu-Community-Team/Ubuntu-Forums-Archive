---
title: "No X after installation (ATI HD 2600)"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by narcotico on 2008-11-11
I've been trying to solve this myself but I can't think of anything new.

```
n@santabarbara ~ $ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 2600
OpenGL version string: 2.1.7412 Release
```

Guys, it's impossible to run Ubuntu 8.10 Live CD. The screen goes black and slowly seems to go white with the default xorg.conf driver, "ati". Even if I change it to vesa the X server just to refuses to accept the monitor configurations, complaining about none screen found. 
The same happens when upgrading from 8.04, even if I lock the X, preventing it to update to 7.4 (I guess). 

I've been reading topics, tutorials, everything ...

---

### Post by bvtd092 on 2008-11-11
Narcotico,

I've had the same problem, underneath the link how I solved the problem.

[http://ubuntuforums.org/showthread.php?p=6152916#post6152916](http://ubuntuforums.org/showthread.php?p=6152916#post6152916)

Greetings,

---

### Post by narcotico on 2008-11-11
> **bvtd092 said:**
> Narcotico,

I've had the same problem, underneath the link how I solved the problem.

[http://ubuntuforums.org/showthread.php?p=6152916#post6152916](http://ubuntuforums.org/showthread.php?p=6152916#post6152916)

Greetings,

I'm used to my wireless connection. If I plug the wire will I connect automatically before X? I guess I already tried to connect but nothing happened. So I won't be able to apt-get update, right?

Anyway, thank you! I feel like I am closer. lol

---

### Post by bvtd092 on 2008-11-11
Narcotico,

Yes, when you are wired to the network, you can use your network before x is started! In my situation that works!

Greetings,

---

### Post by narcotico on 2008-11-11
> **bvtd092 said:**
> Narcotico,

Yes, when you are wired to the network, you can use your network before x is started! In my situation that works!

Greetings,
Thank you again!
I'm writing this post from 8.10 and it works just great. I was just about to give up!

---

### Post by luxorvan on 2008-11-12
Please read all this you may find some answers!When I tried to install the driver version 8-10 I did this ctrl+alt+F1 (then login) cd to the location the file is at then instead of using sh I chmod +x the file then login as root (you get graphical interface with more support and it will report errors to you)I shut down x then I sudo the file. However please note I've encountered several problems 1. glibc needs to be version 2.2 or 2.3 "Only"! You can't use glibc-source or ati installer says it's 2.1 and I still haven't figured out how to build and install it from source or even fix the problem! 2. xorg-xserver is reported as a base(generic) xorg7.1 and it says you must download/build from source and install the 7.1 full or greater from their website [www.xfree86.org](www.xfree86.org) to have the full xorg-xserver like is required. Other packages required are libstdc++, libgcc, fontconfig, freetype, zlib, gcc, gnu make(make or automake) you should probably add libc6-dev if it isn't added already. I guess build-essential includes most of them but probably not all of them! Again I'm sharing this because I feel it may help in your quest! And another tip if you restart to a white screen hit ctrl+alt+F1 then login and type this command that is included in the readme: aticonfig --initial -f     Then hit ctrl+alt+del it will restart and you should be able to login as normal! You will also need to enable posix by typing this into a terminal: sudo gedit /etc/fstab
then enter this into the fstab line(gedit window): tmpfs /dev/shm tmpfs defaults 0 0     And save it then close it!
then typing this: sudo mount /dev/shm
and this: sudo mount | grep "shm"
That's as far as I get but glib and xorg still stand in my way! If anybody could help beyond that I'd appreciate it as well! Best Wishes!

---

