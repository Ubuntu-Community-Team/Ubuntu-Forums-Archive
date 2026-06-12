---
title: "Install Intrepid on Virtual PC with Nvidia 8400M GS FAILS!!"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zxed on 2008-10-18
first of all., why cant they just put the noreplace-paravirt option in the GUI ??!

So i downloaded the ISO., im using Virtual pc 2007., i have created the vdisk., attached the iso., i boot., i select english.,  
leave selection on try......
select safe mode, 
remove quiet splash 
add vga=791 noreplace-paravirt
it starts booting.... after a few minutes get a
Ubuntu is running in low graphics mode, screen and graphics card coud not be detected
anyway, you can either choose a dif config, or trouble shoot... if i trouble shoot and open the xconfg, its pretty much blank., not much in there, just the basic tags,. trying to create a new config makes everything just hang...

I am new to linux/ubuntu., never used it before (as you can see).... my only frustration (so far).. is that regarless of how shitty m$ has been., after 4 - 5 hours i have been able to get it installed, starting from ver 3.1 :)

i am pretty sure it has to do with my nvidia gfx card., im booting from the ISO... i am thinking/read that i should install envy., is there a way i can do it with the live cd? with boot?

i would install 8.4 instead of 8.10 but im pretty sure the problem exits there as well?

---

### Post by Steveway on 2008-10-19
1. Ubuntu is not seeing your real hardware, only the emulated hardware.
2. Use a real virtual-machine like virtualbox, wich has far better support for other Operating-systems than windows.

---

### Post by zxed on 2008-10-19
> **Steveway said:**
> 1. Ubuntu is not seeing your real hardware, only the emulated hardware.
2. Use a real virtual-machine like virtualbox, wich has far better support for other Operating-systems than windows.

does it need glasses ;)?

ill give virtual box a try

---

