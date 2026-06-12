---
title: "Ubuntu for Allwinner A10 ARM processor"
date: 2012-04-12
forum: Installation &amp; Upgrades
---

### Post by jagspaul on 2012-04-12
Hi All,
Allwinner A10 is very powerful ARM cortext A8 processor (ARM v7). I want to port ubuntu in to on this processor. There is low cost hardware MELE A1000 Android TV box available which is build with AllWinner A10 chip. We could build a small size low cost desktop if ubuntu could be ported on this box.

Can any body help me in this regards?

Thanks
jags

---

### Post by mastablasta on 2012-04-12
have you checked this site? :[https://wiki.ubuntu.com/ARM](https://wiki.ubuntu.com/ARM)
 
Debian also has an ARM version. might be even lighter. though i dont' think they have it under debian stable yet.

---

### Post by jagspaul on 2012-04-13
Yes I have gone through Ubuntu ARM page. But there is only support for imx51/53 and OMP.
There is no support for ubuntu on custom ARM board. So all of you are requested to open a wiki for ubuntu on custom ARM board. or at least Allwinner A10 board.

thanks & regards
jags

---

### Post by trobbo on 2012-04-13
have you seen this site?
[http://rhombus-tech.net/allwinner_a10/hacking_the_mele_a1000/](http://rhombus-tech.net/allwinner_a10/hacking_the_mele_a1000/)

it may help a little :)

---

### Post by jagspaul on 2012-04-14
Yes I have seen it.
But as per editor it is not complete project.

It is only for reference not finish yet.
And it only see the welcome screen, couldn't login. 

jags

---

### Post by fouad_jh on 2012-04-25
> **jagspaul said:**
> Hi All,
Allwinner A10 is very powerful ARM cortext A8 processor (ARM v7). I want to port ubuntu in to on this processor. There is low cost hardware MELE A1000 Android TV box available which is build with AllWinner A10 chip. We could build a small size low cost desktop if ubuntu could be ported on this box.

Can any body help me in this regards?

Thanks
jags

Hi Jags

Great project and good start, I am trying to do something similar, but I don't have the same hardware  -A1000-, however, we can get this project going. We will need to do a massive investment in our time, if you are up for it, then we should start with getting the hardware, and start tackling this project with trial and error, and contribute back with guides to others so they might contribute back ideas or even some work if they have the hardware.

Fouad

---

### Post by jagspaul on 2012-04-27
Hi Fouad,

Thanks for your interest. and would be very happy if we complete the project jointly.
What hardware you have?
Actually A1000 is not for mine I brought it from my friend for some days. I Have a A10 based TAB (COBY MID7042). I would like to work on this hardware first, and after that I will purchase one A1000.

Please  let me know how we can start.

Thanks & regards
jags

---

### Post by fouad_jh on 2012-04-27
> **jagspaul said:**
> Hi Fouad,

Thanks for your interest. and would be very happy if we complete the project jointly.
What hardware you have?
Actually A1000 is not for mine I brought it from my friend for some days. I Have a A10 based TAB (COBY MID7042). I would like to work on this hardware first, and after that I will purchase one A1000.

Please  let me know how we can start.

Thanks & regards
jags

I have "7 Tablet, it is similar to yours (512MB RAM in my case), can you tell me about your linux and ARM background? Kernel and Root file systems?

Thank you

Fouad

---

### Post by jagspaul on 2012-04-29
I think we should start the project right now.

Have you any experience regarding this? If yes please share with us.

jags

---

### Post by TeamMCS on 2012-04-29
I'd be willing to support this. Ubuntu on these cheap tablets would be great.

---

### Post by fouad_jh on 2012-05-01
Hi, sorry for late reply, however, here is a link to Ubuntu Core rootfs link: [https://wiki.ubuntu.com/Core]("https://wiki.ubuntu.com/Core")

We will need the boat Loader which can be UBoot, here is some usefull information: [http://rhombus-tech.net/allwinner_a10/u-boot/]("http://rhombus-tech.net/allwinner_a10/u-boot/")
and regarding the Kernel, here is a link: [http://rhombus-tech.net/allwinner_a10/kernel_compile/]("http://rhombus-tech.net/allwinner_a10/kernel_compile/")

Some useful information: [http://rhombus-tech.net/allwinner_a10/]("http://rhombus-tech.net/allwinner_a10/")

I will do my best to contribute soon, as soon as I get it up and running, I will let you know (I have time constrains).

Fouad

---

### Post by brewhoxs on 2013-03-30
It seems interesting, i'll wait your new development to port Ubuntu on AllWinner A10 devices...

---

### Post by MediaBanger on 2013-06-18
Did this ever get anywhere? I have an Allwinner A10 Cortex A8 laptop, and I've been wanting to experiment with loading Lubuntu or something similar. 

I tried to load [THIS VERSION]("https://www.miniand.com/forums/forums/2/topics/1") of Lubuntu, which is made for the MK802 that is very similar to my Allwinner A10 in specification, but it didn't work. Using my work computer (new iMac), I burned the image to an SD card using dd in Terminal, inserted in my laptop's SD card slot while the laptop was off, turned on the laptop, and got a green power light for a moment on my keyboard before it turned off again. After trying to boot again, it seems to always bypass the SD card and goes straight back into the default OS (Android 4.0 ICS).

---

