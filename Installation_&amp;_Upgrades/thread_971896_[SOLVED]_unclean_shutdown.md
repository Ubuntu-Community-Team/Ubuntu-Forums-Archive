---
title: "[SOLVED] unclean shutdown"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by waylow on 2008-11-05
Hey guys

Just upgraded to 8.10 and I'm having a few issues

This is one of them

when I shutdown or restart - it takes a very long time and it is always unclean
every time I restarted it - it needs to check the partition because it was an "unclean shutdown"


anyone had the same issue?

---

### Post by lores on 2008-11-05
Hi. I've fresh-installed 8.10 on two machines and one of them (an HP 6720s notebook) does either not shut down at all or it does it flawlessly, every boot it's different. I don't know the reason for which it decides to power down or not, but it is very disturbing, as I have to force hard power off if it doesn't succeed... I've installed the system twice and in both cases I've had this issue.

---

### Post by waylow on 2008-11-06
Mine does it every time

and it doesn't matter what kernal I boot into

so it takes me about 7mins to boot/reboot my machine :(

---

### Post by cbonar on 2008-11-10
Hi, I've quite the same problem, except it's only happening approximately one out of two reboots.

Only since I upgraded to intrepid...

I also noticed the action on the power button is not set anymore (was : shutdown).

---

### Post by waylow on 2008-11-10
Yeah - it's quite annoying

I have tried rebooting and shutdown from the command line
but this didn't work either

---

### Post by waylow on 2008-11-11
Bump.....

anybody found a solution?

---

### Post by waylow on 2008-11-15
I may have solved it

```
sudo apt-get autoremove
```

looks like there as an old package causing problems
I have done 3 restarts and it has worked fine


hope it helps

---

### Post by CX15 on 2008-11-15
Running Ubuntu 8.10 on PC.

Above code sorted out the problem!

Thanx

---

### Post by CX15 on 2008-11-15
Dang!

One day later and the problem is back!

PC does not restart or shutdown at all.
Have to use the reset button.

Any other ideas out there?
:confused:

---

### Post by waylow on 2008-11-15
Bummer- It's back with me too

I thought it might be something to do with the Network Manager - that is what I completely removed

but now I think it's something to do with acpid

---

### Post by waylow on 2008-11-15
It's hard to tell what other problems are related to this one 

but these are the issues I am having with 8.10 (maybe you have the same)

I did have a sound problem (now fixed - as I can hear sound but it might still be causing issues)
and I am having major issues with my networking (which could be related)

---

### Post by CX15 on 2008-11-17
This seems to have sorted out my Restart and Shutdown problem.

Just to recap: The symptoms were as follows:

1. Ubuntu 8.10 fresh install
2. Whenever I restarted or Shutdown the following:
Black Screen with flashing cursor.
Shutdown or Restart then only happens after 2 to 7 minutes.

This solution found in the sticky about known bugs in the General Help forum.



>  Re: Known Intrepid Ibex bugs and workarounds
Shutdown hangs at the ALSA modules:

Basically you have to shut down networking before the ALSA stuff is shut down. "Workaround" originally from:

[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/274995](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/274995)

open terminal

Code:
  sudo gedit /etc/init.d/alsa-utils

scroll down to where you see "stop"

insert this line right after the stop :

Code:
  ifconfig eth0 down

or if you use wireless/both at times, insert this instead/in addition:

Code:
  ifconfig wlan0 down


Save the file and exit.


Hope this works for all.
Please mark as SOLVED if it does

---

### Post by waylow on 2008-11-17
So it looks like both the networking and the sound were causing the problem

OK So it looks like it is sorted for me too
(just rebooted twice with no issues)

Except - my network is set-up differently

I use the Ndiswrapper for my wireless with WPA2 - I do not have Network Manager (or any manager) installed

so the code to bring my network down is 

```
 ifdown wlan0 
```

instead of 

```
 ifconfig wlan0 down 
```

Problem solved:

but I still have issues with my wireless, graphics card and the sound

but that's for another thread

---

