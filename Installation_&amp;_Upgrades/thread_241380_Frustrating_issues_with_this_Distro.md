---
title: "Frustrating issues with this Distro"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by jellystones on 2006-08-22
This is where I vent my frustrations with Ubuntu and hopefully find a solution before trying a different distribution.

So I heard of Ubuntu on Digg as a "Linux for Humans" and was intrigued. I have tried Red Hat Linux in the past and was somewhat pleased with it, but always went back to windows due to windows only programs that I needed.

Anyway I tried Ubuntu yesterday and In My Opinion, it seems to have moved backwards rather than forward in ease of use.
[B]
First Issue[/B] EXTREMELY SLUGGISH performance. It takes more than 5 seconds for the terminal to pop up on the screen. This is immediately after a fresh install on a blank hard drive. Using the *top* command shows no significant processor usage.
System Specs:
Asus A7V-133 Socket A motherboard
AMD Athlon XP 1700+ Processor
512MB SDRAM
Creative SoundBlaster Live! Value
250GB Western Digital Harddrive
Nvidia Geforce FX 5200


**Second Issue** What is wrong with the Super User? Trying to log in as *su* at the terminal tells me I have the incorrect password. Logic tells me the password should be the same as my account password that I setup during the install.
[B]
Third Issue [/B] Why is installing Nvidia drivers on this distribution SO COMPLEX??? I found a guide on this forum that required at least 6-7 steps. I remember on redhat all i had to run was SH NVIDIA* in the terminal to begin the setup process, and 5 minutes later all was complete. That was over 2 years ago, I come back and the install has become even more complex?


One improvement I did find over previous linux versions I have installed is the installer. It was very painless and quick. But the 3 issues I have outlined above have me more frustrated now than the first time I tried Linux as an uber noob (now Im just a regular noob). Anyway I downloaded Slackware last night, and am thinking about trying it out tonight, but would be willing to stay with Ubuntu if anyone could suggest some solutions.

---

### Post by gwillh on 2006-08-22
Good Mornin! 

Sorry to hear about your experience to date, but here's some answers:

Sluggish Terminal 
1) Is due to the fact it's using Gnome Terminal, most things 'fancy' seem to be slow (turn on widgets in MS Windows and you get sluggish too). Try making a launcher for a bare xterm, it's lightning quick, for comparison. This is probably your issue all over, which brings me to 2)

2) You need more ram.

Super User:
Due to repeated and varied attempts by users to accidentally harm the system, sudo has been chosen as the method to modify the system, and safely drop you back into the security of user space. To fix it, just issue sudo bash, passwd. 

Nvidia Issues:
Blame nvidia for not producing an open source driver. Their drivers have always been a MAJOR pain in the .... Sometimes easy, sometimes hard to install, and mostly buggy as hell on anything except MS windows, and even then every third one seems to require rolling back to an older one to get away from errors on MS Windows.

Nvidia Fixes: 

 How to install Graphics Driver (NVIDIA)
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable

Taken from:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29")

I wasn't muchly impressed with it over the basic nv driver, but then all I do is python and backend stuff, not much into 3D.

System for comparison:
P4 2.4
1gig RAM
GF6800 with 256.

system works blazing fast at 1280x1024x24, except for Gnome Terminal load time.

Hope this helped a bit. The things you mention are issues, but no more so than the actual bugs that the other distros seem to put in that completely and actually break the system before it's even up. 

Will

---

### Post by wpshooter on 2006-08-22
I sort of disagree.  I think something else is afoot here.  I have several machines with just 512 ram and one with a slower processor than his and my terminal is almost instantaneous.

Is this computer that you are running Ubuntu on also being used for M/S windows ?

How did you install Ubuntu from the DESKTOP cd or from the ALTERNATE cd ?

And did you WIPE everything off of the drive before you installed Ubuntu.  My suggestion would be to WIPE the drive and then use the DESKTOP cd 32 bit to install Ubuntu.

Good luck.

---

### Post by jellystones on 2006-08-22
I will try your method of installing the nvidia drivers tonight.

However the sluggish performance I described is not just limited to Gnome terminal. Immediately after a fresh restart, I cannot access the menus at the top of the screen for at least a minute. My hard-drive is doing nothing either which suggests that Ubuntu has finished loading any files it needs....

As for needing more ram, Im positive I dont need more ram....bloated redhat ran fine on 512mb. Also im not running any applications, so needing more than 512mb of ram just to access the menu "instantly" at the top would be pathetic.

---

### Post by Paul133 on 2006-08-22
Is Dapper really slow when you have a HD installation ona  cheap Dell laptop with 256 M RAM and with XP? If so, I won't bother installing it. I really just want to try an open source OS and learn how to use a CLI, but I have to have Windows for school. Can you reccomend a distro? (I've run a non-verified but correctly burned Dapper as a Live CD, but it's so slow when I try to install it, it hangs.)

---

### Post by wpshooter on 2006-08-22
What do you mean by it hangs ?  Stopping at what point ?

---

### Post by aysiu on 2006-08-22
Use Mepis then.

It's based on Ubuntu, has a graphical installer as well, includes NVidia drivers as part of the installation process, has a root user, and isn't sluggish at all.

That said, my terminal pops up almost instantaneously, and I love *sudo* now instead of root/user.

---

### Post by Paul133 on 2006-08-22
wpshooter, I mean that when I click "install", it freezes.

And aysiu, I'll look at Mepis. So far the only distros I've installed are PuppyOS and Ubuntu (both as Live CD's)

---

### Post by aysiu on 2006-08-22
I like Ubuntu for its community and documentation, but for no-muss, no-fuss Linux that's cost-free and proprietary software-full, Mepis is the way to go. That or PCLinuxOS.

---

### Post by Paul133 on 2006-08-22
But is Mepis free?

---

### Post by aysiu on 2006-08-22
> **Paul133 said:**
> But is Mepis free?
Mepis is cost-free (no money involved), but it contains a lot of non-free (i.e., proprietary) software like NVidia drivers and Flash.

---

### Post by John.Michael.Kane on 2006-08-22
Paul133 sure is free,and as already stated has all codec/drivers

---

### Post by jellystones on 2006-08-23
Well I gave on Ubuntu...kinda.
I installed Mepis instead and it works exactly how I expect linux to work.....not sluggish like Ubuntu at all.

If im correct, Mepis is just Ubuntu with proprietary drivers enabled? I guess the open-source drivers that came with Ubuntu were at fault.

---

### Post by aysiu on 2006-08-23
I'm glad you found something that worked for you. Yes, what works best with NVidia is... NVidia--surprise, surprise.

I always recommend Mepis to those who find Ubuntu too much hard work. You may be back, though. Mepis was my first distro, and a great first distro for a month. Then, I've used Ubuntu ever since (a year and three months now).

---

