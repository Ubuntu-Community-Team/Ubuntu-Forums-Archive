---
title: "Grub configuration"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by mac173 on 2010-06-04
I am running Ubuntu 10.04 as a dual boot on my laptop next to Win 7. I installed using all defaults, as I am pretty much a novice user. I also put 10.04 on my desktop at home, but did not install. I am running that machine ON the Win 7 partition. 

My problem is that on my desktop, I get a boot option of Windows or Ubuntu from the MBR, and Windows is the default. If I choose Ubuntu, I then get the Grub menu which defaults to Ubuntu (fine, I already chose that). 

On my laptop (where I did the full install on its own partition) Grub takes over, which would be fine but for Ubuntu being the default. I really want the default to be Win 7. 

I have read several posts, and a tutorial on changing the boot order in Grub, but when I try to access the file mentioned (etc/default/grub) I get an error "Permission Denied". I have made myself Administrator, so I should have access to everything. 

I know I need to change the line GRUB_DEFAULT=0 to GRUB_DEFAULT=6 to make this work, but I cannot open the file. 

Is there an easier way of doing this? Honestly, if you want novice users to try out Ubuntu, sending them to command line is NOT the way. The great majority of people that might be willing to try Ubuntu will run for the hills at the simple suggestion of command line. Most everything else you do is handled by an app, why not this?

Ok, /rant off

Can someone help me get this file changed?

---

### Post by darkod on 2010-06-04
For GUI control of basic grub setings like default OS, timeout, etc, install the package startupmanager. You have few ways: Software Center, Synaptic, or simply in terminal:

sudo apt-get install startupmanager

After installation I think it's in System-Preferences or System-Administration (I don't use it myself).

For editing the /etc/default/grub you can do in terminal:

gksudo gedit /etc/default/grub

gksudo is used instead of sudo for GUI application like the editor gedit. Even though you are the main user and administrator, the sudo (or sometimes gksudo) is necessary for added protection, I guess that's why you got the error.

You should be OK with typing a command or two in terminal now and then, it's really a good thing. Take care. :)

---

### Post by mac173 on 2010-06-04
Thanks, I think I got it. Apparently the lack of sudo or gksudo was the problem. The tutorial tells you to change the file, but did not explain how to OPEN the file in gedit. 

I know command line will not kill me, but I have a little experience with Linux and have at least a vague idea what is going on. Most people will not. 

I will try that startupmanager package. Although I will not need it now, if I get friends to try Ubuntu out, I will load that for them. 

I would suggest to Ubuntu that they give that as an option, or even make it the default on installs. 

Thanks again.

---

### Post by darkod on 2010-06-04
Actually I am using gedit with sudo myself, and it works OK. But the recommendation is if you are opening program with graphical interface, and gedit is one of them, to use gksudo. So recently I started with gksudo too.

---

### Post by darkod on 2010-06-04
Another "operation" I do to make the grub menu more user friendly, I put windows on top and because the latest ubuntu kernel is always first from the kernels, you have only one key stroke up or down to select between windows or ubuntu.
There are also many ways to do that, but if you have single windows and single ubuntu installation, I prefer:

Copy the 30_os-prober file into a new one starting with 06:

sudo cp /etc/grub.d/30_os-prober /etc/grub.d/06_os-prober

Disable the executive bit of the original file:

sudo chmod -x /etc/grub.d/30_os-prober

Disable executive bit for memtest if you already haven't, you don't do memtests every boot:

sudo chmod -x /etc/grub.d/20_memtest86+

Recreate new grub.cfg:

sudo update-grub

You should see windows first, the latest ubuntu kernel second, etc. So there is one key stroke up or down between them. And because with kernel update the latest kernel will again be first from the kernels listed, no changes in grub files are needed.

Of course, if you do the above again you have to modify your /etc/default/grub and put for default OS the value 0 for windows, or 1 for ubuntu.

---

### Post by sgosnell on 2010-06-04
Being an administrator does not automatically let you do anything you want.  You still have to use 'sudo' and provide a password in order to change any files owned by anyone but you.  That's for your protection.  It's possible to set a password for root, and then log in and run as root, but it's a bad, bad idea and you shouldn't do it.  Just use sudo for the operations you need to do.  Being logged in as root opens all sorts of security holes and lets you make bad changes without thinking about them.  You'll get used to using sudo, and that's the way it should be done.

There are several good tutorials on configuring grub2, but you should be aware that mistakes can make your system unbootable, so be careful about what you do, and be prepared to correct them.  Have an external boot disk of some type available until you're sure things are working.

---

