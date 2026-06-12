---
title: "NVIDIA 173.08 v Legacy 96.43"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by goslings on 2010-03-16
Under 8.04 & 8.10 & 9.04  I managed to use 173... Nvidia drivers as I got compiz (3d Cube & wobbley windows) & Avant to work
 
Now under 9.10 (after a few graphic clitches) when I try and install 173.08 Nvidia reports that I must use Legacy 96.43.xx 

I think that this version (96.43.xx) does not support compiz or Avant 
(using an old GeForce 4 Ti 4600 - but it did work before)
regards

---

### Post by mikewhatever on 2010-03-16
A quick look [through supported cards]("http://packages.ubuntu.com/karmic/nvidia-glx-173") reveals that for nvidia-173, the game starts from GeForce 5. What can you do? Time goes, hardware gets old, that's life. I hope compiz works with 96.43.., and if you only use it because of Avant, try another dock instead.

---

### Post by goslings on 2010-03-20
such is life - all things get oldier - to be far my vaio was brough out 2003/4. 
just would be good to have the basic functionality of compiz & avant
linux prides it self on resurecting "old" machines 
i'll have a play, if it works expect 9.10 will be it last major upgrade

---

### Post by 5735guy on 2010-03-20
Nvidia-graphics-drivers-96 (96.43.13-0ubuntu6) source package in Ubuntu 9.10 Karmic Koala
[https://edge.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.13-0ubuntu6/+build/1309137](https://edge.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.13-0ubuntu6/+build/1309137)

---

### Post by goslings on 2010-03-20
thanks 
can you remind me just what I need to do with these and which ones I actually need. Currently i'm just at low res graphics after recovering from an apparent broken system 
many thanks 
Ian

---

### Post by goslings on 2010-03-20
> **5735guy said:**
> Nvidia-graphics-drivers-96 (96.43.13-0ubuntu6) source package in Ubuntu 9.10 Karmic Koala
[https://edge.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.13-0ubuntu6/+build/1309137](https://edge.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.13-0ubuntu6/+build/1309137)

used synaptic to install this 
using system -sdmin - nvidia x server setting 
it shows I have a silicon Graphics GDM-5411 & GEForce4 Ti 4600  - correct 
I can set res to 1792x1344 is good for this monitor but when i save to x-config (&merge) file it will not let me
I assume it is because I am not root?
must I do this via terminal sudo ?
but what is the name of the prog sudo ???????
hence when I reboot I loose all my settings 
Does anyone know if 96.43. will work with compiz & Avant
i.e give me the at least the cube desktop (as per 9.04)   
thanks

---

### Post by goslings on 2010-03-21
used sudo nvidia-settings 
and can change res t what I want 
on saving will not remain after reboot
note also that it is for screen 0 and not screen 1 which I cant change 
anyone any thoughts

---

### Post by realzippy on 2010-03-21
"*on saving will not remain after reboot*"


...have you hit:

"Save To X Configuration File"

in nvidia-settings?

If so,is there a file "*monitors.xml*" in your /home/youruser/.config/ directory?

Delete this file;it is generated when setting resolution with system/settings/Display and conflicts with NVIDIA....

---

### Post by goslings on 2010-03-21
> **realzippy said:**
> "*on saving will not remain after reboot*"

Delete this file;it is generated when setting resolution with system/settings/Display and conflicts with NVIDIA....

BINGO! :KS
This has worked
I really wanted to get back to a nvidia driver that supports compiz & Avaqnt under 9.10, it did in 9.04 and 8.10
(GeForce 4 Ti 4600, which is circa 2004 and 3D enabled.

Each time I try system - pref - appearances extra it all goes peared shaped. 

I thought under the days of 173.xxx you had these drivers as 3rd part drivers ?

have you any experience of this?

thanks again 
Ian

---

### Post by realzippy on 2010-03-21
..maybe compiz-check helps:

[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by goslings on 2010-03-21
I know that it ran under 9.04 (and the compiz scripts you suggests say it should)
Just that for 9.10 the drivers for nvidia & my  card seem to have been reverted back to legacy one 96.43.xxxx which suggest while the machine can nvidia have decided not to support it.
Boo!

---

### Post by realzippy on 2010-03-22
Have you tried to install the 173.xx driver manually?

---

### Post by brucel on 2010-03-22
> **realzippy said:**
> Have you tried to install the 173.xx driver manually?

Have you tried using EnvyNG to install the nvidia drivers? I've been using it for close to three years and it's magic. It's now included in the Ubuntu repos

---

### Post by realzippy on 2010-03-22
> **brucel said:**
> Have you tried using EnvyNG to install the nvidia drivers? I've been using it for close to three years and it's magic. It's now included in the Ubuntu repos


As I understood,NVIDIA 96.xx is running.
Would be suprised if envy would give more options (the 173.xx he wants) than restricted driver manager...but who knows.

Remember ancient times,Ubuntu 6.10,I also ran 96.xx and had full running 
Compiz (*used to prefer Beryl;RIP*;*different story* ;))

....so,have you installed compiz,all plugins,ccsm correctly?

---

### Post by goslings on 2010-03-24
Thanks realzippy & brucel
I only get to try this at weekend as I am away all week
> brucel yet to try EnvyNG - how do i do this ?
> realzippy I have compiz & Avant installed but when I try system - prefs - appearances - extra it all locks up

---

### Post by goslings on 2010-03-24
> **realzippy said:**
> Have you tried to install the 173.xx driver manually?
If you mean via the Nvidia script & terminal all I get it a message saying that I should install 96.43 
Is there another way, if so please can I have some instructions
cheers. Can only try at the weekends as away during the week.
Ian

---

### Post by realzippy on 2010-03-25
*yet to try EnvyNG - how do i do this ?*

Install via synaptic:

**envyng-core**

There is a GUI for it somewhere in the menue after install...
-------------------------------------------------------------------------

*I have compiz & Avant installed but when I try system - prefs - appearances - extra it all locks up*

..have you installed **compizconfig-settings-manager** ?

--------------------------------------------------------------------------

*If you mean via the Nvidia script & terminal all I get it a message saying that I should install 96.43 *

Yes.No other way.Try envyng,but think it will not work...

---

### Post by goslings on 2010-03-27
Installed EnvyNG, rebooted (jic)
tried Application - System Tools - EnvyNG
- nothing  - no GUI ??

BTW compizconfig-settings-manager is installed 

hmmmm

---

### Post by Helkaluin on 2010-03-27
Try running ```
envyng -t
```in text mode instead.

Another random point: If you're just using Compiz for the compositing for Avant, and you don't really need all the eyecandy of Compiz, why not enable compositing in Metacity instead? (Or even change to another dock, but I won't push.) No more driver conflicts?

---

### Post by goslings on 2010-03-28
yes got there in the end, but EnvyiNG suggest 

 ```
+-----------------------------------------------------------------------------+
 | Number | Candidate Version  | Installed Version  | Compatible | Recommended |
 |-----------------------------------------------------------------------------|
 | 0      | 185.18.36-0ubuntu9 | -                  | -          | -           |
 |-----------------------------------------------------------------------------|
 | 1      | 173.14.20-0ubuntu5 | 173.14.20-0ubuntu5 | -          | -           |
 |-----------------------------------------------------------------------------|
 | 2      | 96.43.13-0ubuntu6  | -                  | +          | +           |
 +-----------------------------------------------------------------------------+
Please select the number corresponding to the desired driver and press ENTER 
(or type another number and press Enter to go back to the previous menu):
```

There is clearly a switch over in 9.10 wrt 9.04 re using the old legacy nvidia drivers for my machine/card, (GeForce 4 Ti 4600.
machine/card was capable in 9.04 to run Avant & Compiz(wobbly windows and cube desktop selection) 
maybe I'' drop an email to EnvyNG to see what they think

---

