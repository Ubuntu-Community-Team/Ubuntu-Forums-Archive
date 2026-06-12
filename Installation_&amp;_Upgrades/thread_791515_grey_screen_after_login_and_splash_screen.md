---
title: "grey screen after login and splash screen"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by cazmatazzz on 2008-05-12
hello, after upgrading to hardy on an old computer (256 mbram) i ran into the following problem. i can boot up and get to the computer login screen, after logging in the splash screen (with the xubuntu running mouse) comes after which the screen goes a light shade of grey blank. 

i had this problem  before and it turned out to be a problem with selecting the wrong session in the log in screen. now this does not seem to be the problem. 

however, in the grey screen i am for example still able to use alt+f2 and run programs such as evolution. the entire menu and background seem to have disappeared and the mouse button doesnt work either. 

i have looked through various forums and thought it might be a graphics problem, because there also is a large black bar at the side of the screen

if anyone can help me that would be great, it seems a lot of people seem to be experiencing 'grey screen' problems.

---

### Post by hermes0710 on 2008-05-12
I suggest creating a new user and login to see if this keeps happening. If not then probably some settings stored in your home folder from previous release keep messing up hardy

---

### Post by cazmatazzz on 2008-05-12
how do i create a new user? i can only use terminal in xterm safe mode

---

### Post by cazmatazzz on 2008-05-12
also when i enter grub before login there are five options i can choose from, two safemodes of the same version, two normal modes of the same version and on memtest

---

### Post by Jarramundi on 2008-05-15
I am also having the same problem, my desktop is gone replaced by a blank grey screen. but, when I try to fix broken packages in recovery mode, it says it can't resolve [www.medibuntu.com](www.medibuntu.com) or something, but there is no mention of medibuntu in my /etc/apt/sources.list, so why is it trying to source packages there? I need to sort this out, I am stuck working with a windows machine while my ubuntu is down, which I hate. Please help!

---

### Post by rotundrory on 2008-12-16
I have been using Hardy for several months now, but a few days ago, I got stuck on this gray screen that is normally only up for a 1 or 2 seconds when I log in.

This all started when Rhythmbox tried to play what I guess was a corrupted mp3, causing Ubuntu to freeze up. When I restarted, I got an unmoving gray screen.

When I hit Ctrl-Alt-F1, I see that there is some error with GNOME Display Manager (duh), and then I get the following output over and over. 

[Please note the numbers in brackets I've written on the left are in this instance random and are strictly increasing from one line to the next.]

```

[39.58784]   ata1.00: status: {DRDY ERR}
[39.59125]   ata1.00: error: {UNC}
[39.59230]   ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[39.59598]   ata1.00: BMDA stat 0x25
[39.59125]   ata1.00: cmd c8/00:08:4e:e6:2c/00:00:00:00:00/e6 tag 0 dma 4096 in

```

Again, these error messages repeat, and I'm unable to enter any commands.

A single time, I was able to Ctrl-Alt-F7 it, and my desktop picture came up, but I wasn't able to do anything.


I can log in with the "safe terminal" mode. After an inconsistent amount of time, though, I've noticed that sort of freezing up.

Someone help me, because Windows is awful.

HELP!

---

### Post by rotundrory on 2008-12-16
> **rotundrory said:**
> HELP!

fyi this still applies

---

### Post by Diecutter on 2008-12-16
I am also getting a GRAY or blank screen after successfully logging in. This is my first eXPerience with UBUNTU 8.10 and I'm trying very hard to stay positive about this O/S. I've done a fresh install of Ubuntu a couple of times but I get the same result, it's the only O/S on my machine. I've checked the distribution disk for errors and it's clean. I'm using an HP Evo DC5000SFF desktop (100% dedicated to Ubuntu) 2GB of Ram, 80GB HDD. Any help????

Thanks
Blair

---

### Post by mrbiggbrain on 2008-12-17
adding a user via the terminal 

sudo useradd newusername
sudo passwd newusername

you will of course need to know the root password to do this, or on ubuntu, the password of a high privileged user.

---

### Post by mrbiggbrain on 2008-12-17
> **Diecutter said:**
> I am also getting a GRAY or blank screen after successfully logging in. This is my first eXPerience with UBUNTU 8.10 and I'm trying very hard to stay positive about this O/S. I've done a fresh install of Ubuntu a couple of times but I get the same result, it's the only O/S on my machine. I've checked the distribution disk for errors and it's clean. I'm using an HP Evo DC5000SFF desktop (100% dedicated to Ubuntu) 2GB of Ram, 80GB HDD. Any help????

Thanks
Blair

have you tried using failsafe mode? does this work or not? did u ever get anything other then a grey box? or is this all you have recived since installing.

---

### Post by pieje on 2011-11-11
Sorry to bump up this old thread, but I have this problem after restarting xubuntu 1.10 for the third time.

---

### Post by matiash on 2011-12-08
Hi, just press ctrl+alt+F2 then type sudo apt-get install xfce4-panel, then reboot, then install from software center xfce desktop and reboot again.

---

