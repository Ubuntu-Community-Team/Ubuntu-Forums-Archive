---
title: "Noobie Help - Black Screen of Death on Install"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by sorias on 2007-09-28
I would really like to install Ubuntu, but Im concerned about my hardware as I have have a relatively new machine. 

AMD 64x2 5600+
AMD M2n32SLi Deluxe
2 gigs Corsair 800mhz
Creative Soundblaster X-Fi
GeForce 8800GTX

I run a 22inch widescreen monitor with resolution at 1680 x 1050. 

I DL'd the 7.04 64 bit version, but I get the black screen of death immediately after hitting enter for install .

Any suggestions?

---

### Post by sorias on 2007-09-29
Tried the alternate Disk and it seems to be working.I suspect some of my devices were too new for live cd.

---

### Post by PmDematagoda on 2007-09-29
Here are your problems:-

Creative Soundblaster X-Fi
GeForce 8800GTX

But they can be used by installing the latest Nvidia driver for Linux, and installing the newly released X-Fi drivers by Creative.:)

---

### Post by twist2b on 2007-09-29
i had the same trouble.... even after install you will have trouble i believe... when you turn the compy on with the live cd in i pressed F4 and changed the resolution... it worked.... but after dl becuase the resolution doesnt save you cant load.... theres a dl for g-force users

oo and by the way... OMG i have the same crap as you HAHAHA except diffrent resolution

edit- can someone give the link to the g-force thign and the other thing?
thanks

---

### Post by sorias on 2007-09-29
phase 1 of the install went wihtout a hitch, it ejected the disk and prompted for the reboot, but after reboot, i get the black screen again. 

So here is my question, is the fact that I have a 8800gtx and the Soundblaster Xfi goign to prohibit me from doing a clean slate install of Ubuntu?

---

### Post by twist2b on 2007-09-29
im pritty sure your install is fine... but like me your resolution is diffrent including the fact that you have GeForce... did you install the GeForce linux driver? i think that should do the trick or before booting any OS theres C for command crap.... if theres someway to make sure ubuntu starts up at the spacific resolution then that would prob work but i dont know what commands would do that.... :'( im at the same position your at to tell the truth and i havnt been able to dl the geforce kernel yet.... do that 2marrow

---

### Post by sorias on 2007-09-29
IM still in the install process so I havent been able to install drivers yet. I put the Alternate CD for the text install, followed the prompts, did a full drive partition install, it installed all the software fine, ejected the cd, and prompted to reboot, at which point its reboots and its supposed to continue the install process for phase 2. 

Right after the reboot to being phase 2, it says 

GRUB loading stage 1.5
GRUB loading...

It then says at te bottom of the screen 

Kernal Alive
Kernal Direct Mapping ( some numbers appear here but the screen changed to fast for me to get it)

Its at this point I get the black screen.

---

### Post by pbcartwright on 2007-09-29
go to nvidia.com and download the newest Linux driver.. NVIDIA-Linux-....*.run
read the readme and HOW-TO basically :
sh NVIDIA...run
then reboot.
this modifies your /etc/X11/xorg.conf
if you want to run with a minimal driver, go to the video driver sevtion. With nvidia installed it reads like this:
 Driver         "nvidia"

if you want to run a lower 1028X764 res you can change it to:
 Driver         "nv"

then restart x

---

### Post by twist2b on 2007-09-29
oo ok so i think grub was not installed correctly.....
i think theres a way to just boot up windows normally and take grub out of the picture.... if you have vista its prob esc then change boot order...... after that theres actually a way to boot up ubuntu withought grub.... i think..... anyways yea i think your having grub issues

can anyone give me step by step n00b instructions on how to install the geforce linux kernel?? i downloaded it but i dont know how to run it

---

### Post by PmDematagoda on 2007-09-29
To install:-
```

sh "Name of the file of the Driver"
```

You have to stop Xserver to install the driver, I'm not sure of the commands because I installed the driver while in Recovery mode, you can do the same.

After installation start the x-server:

```
startx
```

If after the installation, you face problems, you can try reconfiguring the X-server completely by:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by skopa on 2007-09-29
if you installed the nvidia driver right than it's not your fault
USPLASH IS BUGGY,the developers know it,they just won't fix it(WOOHOO,UBUNTU ROCKS)
go to the entry of what you load on the grub menu,edit it(I think it's the e button) and remove splash at the end of the second line... after editing that second line press b and tell me if it works...

---

