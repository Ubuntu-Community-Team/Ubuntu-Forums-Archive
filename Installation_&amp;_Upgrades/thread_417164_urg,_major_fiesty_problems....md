---
title: "urg, major fiesty problems..."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by wallybman on 2007-04-21
ok, dl'ed the fiesty amd 64 iso, burned it, booted off of it to the basic menu, ran the memtest  and the cd checker, both fine.

here's what i have
939 amd 4000+(64) x1
foxconn nforce4 sli mobo x1
evga 7300 gt (256) pci-e x2
40 gig ide hd
1 gig(1gx1)pc3200
xp installed
proview 22 inch widescreen lcd(1680x1050 optimum)


i have windows installed on this machine, so i am going back and forth from the forums to the cd... luckily, this system boots pretty fast.

ok, the problem i have. 

go to basic screen. try live cd boot. get splash screen, hear jungle sounds, cd spins down, and black screen (the monitor still sees a signal though, or it would be shutting off) ok, so i'll try the safe mode. same thing.

i know i'm actually getting into ubuntu, because ctrl-alt-f6 brings up a console, but it has been years upon years since i've done anything in a console. 

i would really like to no longer have to rrun windows on this box. i built it myself about 2 weeks ago, and all of the hardware checks out under windows as fine.

any help would be appreciated...

---

### Post by sauyeeluo on 2007-04-21
please correct me if im wrong but it appears as if your running SLI. your problem could simply be the result of the kernel or xserver freaking out when you boot the live cd. but,  please take this with a grain of salt (if you look at my sig) since im not running exactly the newest hardware.

if your inclined i would probably use the alternate install cd and run the old school debian style installer and then tailor your xserver to your needs as well as install the nvidia driver. 

the nvidia driver (version 1.0-8174 and up) has support for SLI in linux.

---

### Post by wallybman on 2007-04-21
yeah, i'm running sli. i know this isn't the right place to do it, but i don't see the point of standardized drivers not being included by default. they don't actually cost anything, i.e. free, they aren't open, but it is a driver, come on now. /rant

anyways, thanks, i guess i'll try that. i would just rather have an actual graphical install, seeing how ease of use is supposed to be one of ubuntu's features... :(

---

### Post by wallybman on 2007-04-21
actually, what is the name of the driver package? and is there any way to get it from the command line that i can get once ubuntu has loaded(with the ctrl-alt-f6) and what do i need to type to get it and set it up?

---

### Post by sauyeeluo on 2007-04-21
well theres two ways to get the driver

sudo-apt install nvidia-glx (if i remember correctly)

it'lll probably install a few more things that i dont recall. you also have to edit your xorg.conf to use the nvidia driver. check with something like ubuntuguide.org where the instructions are more detailed and accurate then my mindless rambling.  if the command failes...check with packages.ubuntu.com for the correct name of the package you want.

or you could download the driver from nvidia's website.


hope this helps.

---

### Post by Jason_25 on 2007-04-21
If you can get to a console, take a look at the xorg log at /var/log/Xorg.0.log to see why x didn't start.

---

### Post by wallybman on 2007-04-21
ok, i've got 
"sudo apt-get install nvidia-glx nvidia-kernel-common"

that works, and installs the restricted drivers and it says the nvidia kernel is current.

ok, so i then run

"sudo nvidia-xconfig"

and it writes a new config file

so i then run

"sudo startx"

that is where it stops, it won't let me start x because it is already trying to run... urg, i wish i could remember more of how to do this stuff. at least i remember how to move around directories and see what is in there. haven't messed with linux in over 7 years, so i figure i'm doing pretty good so far. thanks for the help, i'll look around more and see what i can find.

---

### Post by wallybman on 2007-04-21
ok, got x running on the live cd. so i figured i'd install. i'm in feisty  now :D

here is the easy way to update everything to get it all running..

"(ctrl-alt-f6)

sudo apt-get install nvidia-glx nvidia-kernel-common

sudo nvidia-xconfig

sudo startx"

if x doesn't start..

"sudo /etc/init.d/gdm restart"

if x shuts down but fails to restart

"sudo /etc/init.d/gdm restart"



and it will bring the most stubborn nvidia sli setup up to speed on the live cd. (amd64 desktop)

i didn't have to restart gnome once  had ubuntu on the hard drive.

now, to install win4lin, or whatever...

---

