---
title: "Ibex wont boot to GUI"
date: 2008-09-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sjprice on 2008-09-05
So, fairly new linux user, have 8.04 on my main box and decided to dual boot my second box with Vista and Ibex. So I cant boot to Ibex anymore. I get the command line, I can log in no problem, but I never get a gui. I have tried starting X, which it says it cant find. Tried starting gdm, which it says [ok] but im still in a command line. and Also switched displays to tty2-6, with no difference. 

I know to really be good at linux, I need to learn the command line, but cmon, this is ridiculous! :)

Ideas?

---

### Post by ronacc on 2008-09-05
If you are new to linux and not comfortable yet with the command line you probably shouldn't be running a developement alpha thats asking for trouble . I sounds like an update took out your video driver , what kind of video card do you have ? also you might want to install MC  (midnight commander) it runs from the command line and is much like norton commander for dos , it will make it easier fo you to move around and examine things without a gui . after you log in and are at the cmd prompt type    sudo apt-get install mc <return>   enter your sudo password <return>  and that will d/l and install mc then after it is installed just type  mc  (lwr case) <return> at the cmd prompt .

---

### Post by Slug71 on 2008-09-05
Have you tried restarting a few times sjprice? Sometimes i would get that to and then just try restarting a few times and it would work.
If still nothing then try,

Code:
sudo apt-get update

then

sudo apt-get upgrade

and see what happens.

---

### Post by Nullack on 2008-09-05
To restart gdm:

sudo /etc/init.d/gdm retsart

However youd be better off having a look at what your xorg logs say about what the problem is.

---

### Post by ronacc on 2008-09-05
thats why I told him to install mc , he's not up to speed with the cmd line  so that will make it easier to poke around .

---

### Post by sjprice on 2008-09-06
> **ronacc said:**
> If you are new to linux and not comfortable yet with the command line you probably shouldn't be running a developement alpha thats asking for trouble .

This is a sandbox pc, so i just poke around to have fun and learn some things. I think the best way to learn is to break it and figure out how to put it back together. Unfortunately, i dont know what I did to break it.
>  I sounds like an update took out your video driver , what kind of video card do you have ? also you might want to install MC  (midnight commander) it runs from the command line and is much like norton commander for dos , it will make it easier fo you to move around and examine things without a gui . after you log in and are at the cmd prompt type    sudo apt-get install mc <return>   enter your sudo password <return>  and that will d/l and install mc then after it is installed just type  mc  (lwr case) <return> at the cmd prompt .

Nvidia card, and installed MC, it will make it much easier to read logs and see what is going on. Thanks for that.

> Have you tried restarting a few times sjprice? Sometimes i would get that to and then just try restarting a few times and it would work.
If still nothing then try,

Code:
sudo apt-get update

then

sudo apt-get upgrade

and see what happens. 


Restarted numerous times, trying different kernels and recovery options. Problem is that it boots fine, just to a cli.

So I updated and upgraded and rebooted and I got the splash screen then it dropped to a cli again. gdm is running. Where are the xorg logs, maybe that will give me a clue?

Thanks for the help so far...

---

### Post by Nullack on 2008-09-06
use google for basic questions answered quickly

logs are in /var/logs, there is two xlogs

also the debugging wiki has tips for helpiing these sorts of things - look at the intrepid howto in my sig

---

### Post by ronacc on 2008-09-06
ok take a look at your /etc/X11/xorg.conf file and find the section that reads like this . you will need to start mc with sudo to be able to edit xorg.conf  .
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection
 
change "nvidia" to "nv" 
and see if that lets you boot . also as nullack said check your logs and there is also a file  /home/*you*/.xsession-errors   , look at that one too . the . in front indicates a hidden file you will see it from mc but in nautilus you would need to either hit ctrl+h or from the nautilus view menu select "show hidden" to see it .

---

### Post by sjprice on 2008-09-06
Changed the "nvidia" to "nv" with no result. I pulled up the xorg on my main box and it was actually identical. So I dont think thats the problem

Pulled up the xsession-errors and it was quite full, and i couldnt tell which was the most recent, so i deleted the file and rebooted to see if there would be a fresh file. And of course there was no file at all. 

So i try to start x and get:

exec: 5: /usr/bin/X11/X not found
xinit: Server error.
xauth: error in locking authority file /home/sprice/.Xauthority

When I do a gdm status, it is running

---

### Post by ronacc on 2008-09-06
can you boot into failsafe mode ? it should be the next choice under your normal intrepid in grub . since nv don't work we know it is not your video driver .

---

### Post by sjprice on 2008-09-06
> **ronacc said:**
> can you boot into failsafe mode ? it should be the next choice under your normal intrepid in grub . since nv don't work we know it is not your video driver .

Recovery mode? Yea, I can boot into that. at the menu, I have tried dpkg, clean, and continue to boot normally, and everything boots fine again, but just no gui and I cant start it.

---

### Post by Nullack on 2008-09-06
Please post your xorg logs inlcuding the old one showing why it went to bullet proof x

---

### Post by ronacc on 2008-09-06
did you set a root password ? (not your sudo password ) . if so see if you can login as root and startx as root . if you have not yet set a root password from the cmd line type  sudo passwd root *  <return>   where * is the password you want for root , it should be atleast 6 characters .  it will then ask for your sudo password enter that then <return> then logout and back in as root and try to startx .
@ nullack  I don't think he is even getting bulletproofx he's getting no x at all .

---

### Post by Nullack on 2008-09-06
Just use sudo -s to gain root

If x is starting at all, we need to see the x logs

---

