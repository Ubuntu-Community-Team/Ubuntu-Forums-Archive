---
title: "Install problems."
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by mike_a on 2008-06-19
Hi all.

Well I tried to install Ubuntu 7.xxx, from a dvd that came with
“A Practical Guide to Ubuntu Linux(R)” 
By Mark G. Sobell  
The self test on the dvd is OK.
If I try to run Ubuntu off the dvd it hangs on the video.
If I try to install the command line all seems to go 
well up until I get to the option of which hard drive
to mount it on.   It seems like the install wants 
to use all three hard drives?   I can’t find the option
that will let me pick the one I want ubuntu mounted on.
I will just unplug the other hard drives and try that.

Any way if I get the command line up and running 
how hard will it be for me to get the desk top up?

With the dsl modem on the installer tells me it see the 
network ok.

Oh I tried making an iso dvd and no soap, system boots
the windows.    If I unplug the hd with vista on it system says
none boot in dvd drive. 

I will try the command line install this weekend.

Mike.

---

### Post by ktrnka on 2008-06-19
By command line install, do you mean you are install ubuntu-server? Ubuntu-server installs just the minimum to get up and running. 

It's very easy to install the ubuntu desktop after a successful install of ubuntu-server.

```
sudo apt-get install ubuntu-desktop
```

once that's done just type

```
startx
```

and there's your GUI

---

