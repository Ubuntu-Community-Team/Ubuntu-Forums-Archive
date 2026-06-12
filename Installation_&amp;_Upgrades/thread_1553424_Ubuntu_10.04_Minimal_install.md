---
title: "Ubuntu 10.04 Minimal install"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by Gorilllanobaka on 2010-08-15
[FONT=Arial]Right ..Looks like my Linux-fu skills are not as good as i thought they are..:D

I am currently working on a minimal install for my underpowered 7 years old laptop..

I had tried the to do the same thing before but using a server install cd instead....Worked perfectly but no sounds....

After a lot of reading i found out that the servers are not supposed to have sound and all that (Which make a lot of sense ) ,so back to the square one!!

Again I have  installed  on  my low-spec'ed computer a minimal install using Ubuntu 10.04   Minimal CD Image this time  and here is what i did so far: 

As soon as i had the CLI Ubuntu installed i went trough this steps:


sudo apt-get update

sudo apt-get install xorg xterm  icewm menu  gksu synaptic --no-install-recommends rox-filer my seamonkey browser , flash  conky alsa-base alsa-utils alsa -oss linux-sound-base

Afterwards i sudo usermod -a -G audio myself

And i tried to run alsaconf (Spoiled by Puppy Linux) of curse it did not worked and after doing some serious reading i found out the reason why...

I run a alsamixer un-muted everything  pop-ed up the volume to the max (On all the devices)

I sudo alsactl init  then rebooted and tried to test my sound..No joy...:(

Right now i am kinda stuck I have no other idea what do do next in order to get the sound working...

Looks like there is something i do wrong but i`ll be damn if i understand what..

(Reading the effing manual it did not helped in my case as my gorilla brain is just to thick to make make it work...:D)


So... the million $ question is ..what I am doing wrong ???


Thanks in advance


PS: I would really like to make it work because i love how little RAM this setup uses..

Here`s a screen shot ...Please ignore the messed up conky (I am still working on it..)
Look instead of the uptime, load, and the ram usage and you will see why i would really like to make it work..

Cheers!


[IMG]http://i36.tinypic.com/m9vt5y.jpg[/IMG]

[/FONT]

---

### Post by Gorilllanobaka on 2010-08-16
[SIZE=6]/BUMP[/SIZE]....[SIZE=5]?[/SIZE][SIZE=6]?[/SIZE]

[I]Really....??? You`ve got to be kidding...

On all this this huge Ubuntu forum (multinational one..meaning people from all over THE PLANET post ) there is no one who`s got **ANY** idea at all??

No one has got any idea on what i am doing wrong and why my sound is not working??

[/I]> 
Ubuntu is a linux distribution focus'ed on making things simple and easy for new comers and experts alike.


[I]
Oh well, there always Slackware`s net installs (At least there i do not have to go creative about adding my start up scripts in  /etc/rc.d/rc.local and the services make a lot more sense...)

[/I]

---

