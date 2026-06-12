---
title: "[SOLVED]  Desktop Effects on EeePC 1000H"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dirtylobster on 2009-03-23
I switched from EeeBuntu to Jaunty Alpha6 a few days ago and couldn't enable desktop effects (which I had before with the array kernel). I found that the solution was found in xorg.conf. By removing the following lines I got the effects enabled and everything seems to be running smoothly:

```
        SubSection "Display"
                Virtual 2048 2136
        EndSubSection

```

Oh, and it's the Intel 945GME Chip.

---

### Post by sprintrjm on 2009-03-23
how do you like the new os?


I have a 1000ha and am curious about trying it out.

Any other things to look out for?


Currently running intrepid 8.04

With Wicd network manager,and the eeepc kernel fix, to enable wifi.

Thanks

---

### Post by Westmeath on 2009-03-23
Desktop effects worked out of the box for me on my 1000h.

---

### Post by Westmeath on 2009-03-23
> **sprintrjm said:**
> how do you like the new os?


I have a 1000ha and am curious about trying it out.

Any other things to look out for? Currently running intrepid 8.04

With Wicd network manager,and the eeepc kernel fix, to enable wifi.

Thanks
Wifi worked out of the box for me. I haven't needed Adam's kernel. 

I am running standard Jaunty but changing the default font sizes to 8 instead of 10 (System > Appearance > Fonts) is a big improvement.

---

### Post by dirtylobster on 2009-03-24
Wifi works fine out of the box, bluetooth on the other hand doesn't. Haven't really needed it so I haven't looked for fixes.

Firefox 3.07 kept randomly locking X (forced me to Ctrl-Alt-F2 and reboot)*, Epiphany did the same although a bit more rarely but since I installed FF 3.1b3 (two days ago) the system has been 100% stable.

*) 'sudo /etc/init.d/gdm restart' didn't change anything

---

### Post by DeeZiD on 2009-03-24
> **Westmeath said:**
> 
I am running standard Jaunty but changing the default font sizes to 8 instead of 10 (System > Appearance > Fonts) is a big improvement.

Agreed, fonts look amazing (compared to any other linux distribution) when set to 8.


Dennis

---

