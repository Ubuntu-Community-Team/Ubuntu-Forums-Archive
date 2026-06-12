---
title: "nvidia drivers.."
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by keewong on 2011-04-03
I'm sorry - Total and Complete Noob here. Although total and complete mean the same thing, I needed it to hit home the fact I am an utter moron when it comes to this ubuntu and linux in all its entirety. 

That being said, I can't figure out how to install the nvidia drivers for my nvidia 8800 GT video card. I've followed some other posts and all the posts seemed either incomplete, or led me down a path of which eventually broke my installation, that I needed to reinstall the entire ubuntu system.

Again, it may not have been broken, i just didnt know how to get back in to the gui version of ubuntu, the instructions took me to the console terminal

So now,

1.) I've installed the ubuntu 10.10 64bit for i386 in an oracle virtualBox.. 

2.) downloaded from nvidia.com "NVIDIA-Linux-x86_64-260.19.44.run"

3.) Stuck don't know what to do.

any help or point in the right direction would be greatly appreciated, as I have an assignment due needing to use this for Thursday.

---

### Post by Hedgehog1 on 2011-04-03
You are running Ubuntu as a guest OS in Vbox? I am guessing the host OS is Windows (host OS it not really important, just curious).

Here is the thing: The only nvidia drivers you need are the ones in Windows - Vbox has it own set of video and mouse 'drivers' and the .iso to load them is already on your PC.

Fire up the Ubuntu Vbox, and select the 'install guest additions' once it is running:

[IMG]http://img855.imageshack.us/img855/9451/vboxuseradd01.png[/IMG]

This load the iso as a virtual 'cd'.

Next, use the 'places' menu to mount the CD:

[IMG]http://img189.imageshack.us/img189/2020/vboxuseradd02.png[/IMG]

The run the install:

[IMG]http://img845.imageshack.us/img845/5472/vboxuseradd03.png[/IMG]

After it completes, reboot the vbox.

***The Hedge***

:KS

p.s. Once this is done, you can resize the Ubuntu screen and the mouse will work better.  If you want to do 3d-effects, I will show you how to turn those on (Requires Vbox 4.0.4).

---

### Post by Hedgehog1 on 2011-04-03
> **keewong said:**
> That being said, I can't figure out how to install the nvidia drivers for my nvidia 8800 GT video card. I've followed some other posts and all the posts seemed either incomplete, or led me down a path of which eventually broke my installation, that I needed to reinstall the entire ubuntu system.

I missed that you had broken it - you will need to redo the installation from the Ubuntu .iso,  This is much faster than fixing the damaged install.

Once you have a working version, you can choose 'export virtual appliance' and save a snapshot of the system.  I do this before I experiment in case I mess things up.

My Vbox control panel:

[IMG]http://img219.imageshack.us/img219/455/vbox01.png[/IMG]

This is a very powerful tool!

***The Hedge***

:KS

---

### Post by keewong on 2011-04-04
That was perfect! Thanks so much, Hedge!!!

I will also take your tip to take a snapshot.. I will likely mess things up quite a bit!

Kee

---

### Post by fudoki on 2011-04-04
Kee - in Virtual Machine installations the Nvidia drivers must be installed and working correctly on the host (physical) machine.  They will then work automatically and correctly in the virtual machines, regardless the virtual OS installed.  Virtualbox handles this.  You will need to allocate some memory in your virtual machine if you need to use hardware acceleration; but if this is the case running in a virtual machine is only going to slow and impair your productivity.  If you need high performance graphics, run in native mode (no virtual session).

The main purpose of Virtualbox is 1) testing and evaluating an OS or product, and 2) Hosting websites and web servers.  Neither of these functions require high end graphics.

Set up the Nvidia drivers on the host, then configure Virtualbox as recommended in the very through and easy to use instructions.  You will need to find out how much video memory you have, and the other details about your hardware.  If you don't maintain the computer, get the person who does to give you a hand the first time and you will save a lot of time and trouble.

---

