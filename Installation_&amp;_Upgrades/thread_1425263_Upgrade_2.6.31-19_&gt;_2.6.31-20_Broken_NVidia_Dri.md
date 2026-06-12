---
title: "Upgrade 2.6.31-19 &gt; 2.6.31-20 Broken NVidia Drivers"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by cryptotheslow on 2010-03-08
Hi,

Update Manager just prompted me to update to kernel version 2.6.31-20 which I did.

After the required restart, X went into safe graphics mode and put up an advisory box that NVIDIA could not start and could not load a driver. There was no mouse pointer and keyboard controls didn't work to clear that box. So I ctrl-alt-f2 to terminal and init 0.

Back up in 2.6.31-19 now all is working fine.

I'm just not sure where to start looking to resolve the issue with 2.6.31-20 - any pointers would be gratefully received.

Some details:

Ubuntu 9.10 (karmic)
AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
NVidia GeForce GTS 250
(NVIDIA UNIX x86 Kernel Module  190.53  Tue Dec  8 18:51:41 PST 2009)

v190.53 are the latest NVidia drivers - so I'm not sure how to proceed.

Many thanks,
crypto

---

### Post by peabrane on 2010-03-09
Got very similar problem.

Tried this link? Haven't tried it myself yet.

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2078478.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2078478.html)

Hope this helps

---

### Post by fudoki on 2010-03-09
Same here. Nvidia 7900-GS came up in -20 on my multi-sync (120Hz) monitor in 1024x768@50Hz!!!!!  No alternative choices!!!  Nvidia-settings tool offered 1152x864@63Hz (what the heck???) - ONLY, no choices of higher, non-flicker, freqs; and 1365x768@60Hz - never seen that one before on this 19", high-end, tube!!!

Went back to -19.  Settings still totally borked.  Same "choices"...  Went to /etc/X11/xorg.conf to fix manually.  No info in file.  Cannot even find where configuration takes place/resides.

It's like a M$ system now; automatic, indecipherable, and BROKEN.

I'm too old for this nonsense...  I'd rather have to do it manually and have it work right than have it working right, 1280x1024@60Hz, 1152x864@70Hx, 1024x768@75Hz or 85Hz, and get broken by an "update" that don't work.

Anybody got any ideas how to gain control of the video subsystem in this nice, modern, broken OS?  Surely there is some tool, or configuration files where you can tell the system the parameters of your hardware???  Right??

Oh, my other 2 AMD64 (Phenom 9950 and X2 5600+ w/8Gb each) machines run Debian Lenny flawlessly, and my dinosaur server (Athlon 800 w/384Mb) runs Slack, currently 12.1 without error or problem.  Had decided to try the new Ubuntu to see the cutting edge on this x86 box.  Will give it a few days and see what suggestions come up on here.

This is pretty disappointing after the flawless install and exactly correct setup of my Nvidia card, monitor settings, and HP All-In-One (pain in the rear) printer!  Hopefully, there is a fix for this.

Thx in advance for any info.

---

### Post by cryptotheslow on 2010-03-09
I fixed mine by following the details in this thread:
[http://ubuntuforums.org/showthread.php?t=690557](http://ubuntuforums.org/showthread.php?t=690557)


Quite simply reinstall the NVidia driver. It automatically detects the previous install and removes it, before recompiling itself for the new kernel and installing. It also then offers to update your xorg.conf - which should at least give you something to work with.

You need to boot into the new kernel version then...

Do it through a virtual Terminal:
Ctrl+Alt+F1
username
password
sudo service gdm stop
sudo sh /path/to/driver/NVIDIA-Linux-xxx.run
password
Accept License
Let driver compile the module into your kernel
Let the driver reconfigure your xorg.conf file, then if necessary edit the new xorg.conf: sudo nano /etc/X11/xorg.conf
Once you're done with that:
sudo service gdm start


If you don't have the driver install file you can get it like this.

For 32-Bit:
wget [http://us.download.nvidia.com/XFree86/Linux-x86/190.53/NVIDIA-Linux-x86-190.53-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/190.53/NVIDIA-Linux-x86-190.53-pkg1.run)

For 64-Bit:
wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/190.53/NVIDIA-Linux-x86_64-190.53-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/190.53/NVIDIA-Linux-x86_64-190.53-pkg2.run)

Those are the English (US) language versions.

It seems it is fairly common to have to reinstall/recompile the proprietary NVidia drivers after a kernel patch - so once you get it working keep a copy of the driver install file and your working xorg.conf file somewhere safe for future use ;) . We live to learn :D


Hope that helps!

:D

---

### Post by afspear on 2010-03-09
noob here.  what is a "virtual terminal"?

---

### Post by cryptotheslow on 2010-03-10
A virtual terminal will give you another login prompt.

Ubuntu sets up 7 virtual terminals tty1, tty2, tty3....> tty7

By default the graphical interface you see and use runs on tty7.

To access one of the other terminals just hold down Ctrl and Alt then press a number from 1 to 6 (for tty1 -> tty6). To get back to your graphical interface on tty7 - Ctrl+Alt+7

Very useful to know when your graphics drivers stuff up for whatever reason and you need to get to a command line to repair things.

---

### Post by peabrane on 2010-03-10
Thanks to Cryptotheslow for a good answer. I tried this but unfortunately, to recompile the kernel requires the kernel source to be available - which it is not on my machine.

Far easier to change /boot/grub/menu.lst default so that kernel "19"  is the default boot. Hopefully kernel "21" will have sorted this problem.

This is the lazy way out but I've never had a problem with NVIDIA drivers on a kernel upversion before.

If I understand Cryptotheslow's response, at least he had a gdm running - all I got was a terminal log-in prompt. I have older NVIDIA cards I guess.

If Ubuntu are going to cut support for older graphics cards, the least they could do is warn you. If it was a drop off, then fair enough. If they are going to expect us to recompile kernels for every upversion, I shall consider switching autoupdates off. I want a computer not random hassle.

Thanks for the responses everyone. This has helped me understand the problem.

---

### Post by cryptotheslow on 2010-03-11
> **peabrane said:**
> Thanks to Cryptotheslow for a good answer. I tried this but unfortunately, to recompile the kernel requires the kernel source to be available - which it is not on my machine.
 
Far easier to change /boot/grub/menu.lst default so that kernel "19" is the default boot. Hopefully kernel "21" will have sorted this problem.
 
This is the lazy way out but I've never had a problem with NVIDIA drivers on a kernel upversion before.
 
If I understand Cryptotheslow's response, at least he had a gdm running - all I got was a terminal log-in prompt. I have older NVIDIA cards I guess.
 
If Ubuntu are going to cut support for older graphics cards, the least they could do is warn you. If it was a drop off, then fair enough. If they are going to expect us to recompile kernels for every upversion, I shall consider switching autoupdates off. I want a computer not random hassle.
 
Thanks for the responses everyone. This has helped me understand the problem.
 
 
I'm a bit confused by this reply. I didn't mention recompiling the kernel.
 
Yes the GDM came up but was unusable - I had to fix it from another tty command prompt.
 
I'm also not sure what your reference to Ubuntu cutting support for older NVidia cards is about either. This whole thread revolves around reinstalling the proprietary NVidia drivers. Nothing to do with the Ubuntu open nv drivers. Which are you using?
 
Were I not such a complete noob to Ubuntu, this issue would have taken me all of 5 minutes to fix - just grab the driver and run the install essentially - I was too nervous about breaking something.

---

### Post by peabrane on 2010-03-11
Hi Crypto,

Thanks for the reply.

I suppose I'm no noob as I've been around Unix and Linux for about 20 years. But I keep away from the complicated bits so I do not regard myself as an expert on anything Linux - so count me as a noob.

Here is a fuller explanation of what happened when I tried to follow your instructions.

Boot up, get straight to console so no gdm running. If I try a startx I get Module NVIDIA not found (or similar) message.

I know my terminal is internet sentient because the first thing it asked me after log-in was "would I like to install 3 updates and 1 security update". Ran apt-get update and apt-get upgrade and it duly updates 4 packages. This is information is relevant as the script you suggeste attempts to access the NVIDIA site.

Navigate to the folder containing the NVIDIA-Linux-x86-173.14.12-pkg1.run file which I have already downloaded. Note that I'm on the "173" package - hence the comment about older NVIDIA cards (2 off GEForce 5200s). "173" is what EnvyNG tells me I should be using. Ran this thing with the "sh" command

Got to the "Accept" prompt.

Then got "No precompiled kernel interface was found to match your kernel. Would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site (ftp://download.nvidia.com)?"

Answer yes.

"No matching kernel interface was found on the NVIDIA ftp site. This means that the installer will need to compile a kernel interface for your kernel" (I presume that the script was actually able to access the NVIDIA site?)

Answer "OK"!

ERROR Unable to find kernel source. Please make sure that you have installed the kernel source for your kernel ......   blah ... blah ... blah"

Followed by "FAILED".

Getting to this level of complication is beyond my endurance/understanding./competence so I'll stop here unless anyone has a simple cure for this. Probably I've misunderstood the whole thing and I'm down the wrong path, but either way, my NVIDIAs don't work with kernel "20".

 But thanks again for the response.

---

### Post by slakkie on 2010-03-11
Hi,

to figure out your kernel:

dpkg -l | grep linux-image

You will get output similar to 

linux-image-generic
linux-image-server
linux-image-somethingelse

Then based on this install the correct kernel header package:

sudo aptitude install linux-headers-generic

Then retry the nvidia installer.

---

### Post by peabrane on 2010-03-12
Hi Slakkie,

Thanks for the advice. That worked for me.

I guess my emergency purge on disc contents (based on other threads) went a little too far. Deleting linux-headers-generic is NOT a good idea (for me at least)! This is one of the perils of following other's advice when you don't fully understand what these things are for.

I need a new big disc - but I'll wait until 10.04 is released.

Thanks again!!!

---

### Post by eGelor on 2010-04-29
nada

---

