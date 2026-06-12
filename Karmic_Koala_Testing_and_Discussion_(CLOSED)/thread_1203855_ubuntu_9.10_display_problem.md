---
title: "ubuntu 9.10 display problem"
date: 2009-07-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vijrams on 2009-07-03
Hi 

i just installed ubuntu 9.10 on my box which originally had XP Pro

i have a asus a7n266-vm motherboard with nvidia nforce chipset.

my resolution is set to 800X600(max) and i am not able to see any thing higher in the drop down.

The XP install had a higher resolution ( 1024X768 ) and it used to detect the monitors automatically
 
Is there anything i have to do extra after installing ubuntu to get higher resolution in my configuration?

need help

Thanks
Vijay

---

### Post by tad1073 on 2009-07-04
Open a terminal and post the out-put of:
```
lspci
```This will give who ever wants to help and idea of your video chipset

---

### Post by alphacrucis2 on 2009-07-04
> **vijrams said:**
> Hi 

i just installed ubuntu 9.10 on my box which originally had XP Pro

i have a asus a7n266-vm motherboard with nvidia nforce chipset.

my resolution is set to 800X600(max) and i am not able to see any thing higher in the drop down.

The XP install had a higher resolution ( 1024X768 ) and it used to detect the monitors automatically
 
Is there anything i have to do extra after installing ubuntu to get higher resolution in my configuration?

need help

Thanks
Vijay

If you haven't used Ubuntu or any other Linux distro before, then it isn't a good idea to start with an alpha release, which is in a state of constant flux. Your problem is most likely because your video card is running a lowest common denominator generic vga driver.

---

### Post by autocrosser on 2009-07-04
I would also second a move away from the testing install--if you have limited experience with Linux--this is not the place to be--testing can & will blow-up at any time--Alpha is REALLY prone for it & we are only heading towards Alpha 3 right now--

I would get some linux-miles on with 9.04 (Jaunty)--it works very well & you can explore it's & your limits in relative safety...when you have some time under your belt pick up the testing group--it's wild at times--but you will learn quite a bit about Linux in a short period---Many of us have been doing this for several years now & like the BREAKAGE.....


BRING ON THE BREAKAGE!!!!!!!

---

### Post by Regenweald on 2009-07-05
if even in the 800 by 600 res you can get to System>>Administration>>Hardware Drivers and turn you nvidia drivers 'on' or 'in use', they should be installed and may sort out your problem. 

NB. I'm using the gnome-core environment and can't remember if 'Hardware Drivers' is in administration or preferences :)

---

### Post by meborc on 2009-07-05
after installing nvidia drivers from the place mentioned before, restart and run "nvidia-settings" program... from there it is easy to set up your resolution, dual screens etc...

---

