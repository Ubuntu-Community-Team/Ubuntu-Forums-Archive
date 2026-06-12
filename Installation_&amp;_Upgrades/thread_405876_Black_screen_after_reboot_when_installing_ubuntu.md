---
title: "Black screen after reboot when installing ubuntu"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by uthman on 2007-04-10
Hi people

Hope you can help with this problem
I've tried into install unbuntu (6.10) on my laptop (HP Pavilion Entertainment PC) using a live dvd.
I go through the install process step by step.  When the install finishes reboots the machine, the machine boots backup up until the unbuntu loading bar finished and then I get a black screen.  Nothing happens.

I've tried entering ctrl-alt-f1 to get a console prompt but this does not work.

I've also changed the driver in xorg.conf to "vesa", "ati" ,"nvidia", "radeon" and none of these worked.  The actual graphic card I have is "nvidia".

Could anyone please help me to see what the problem is.  I'm new to linux and really want to try ubuntu.

Thanks a lot
Uthman

---

### Post by bulldog on 2007-04-10
If you have a nvidia graphics,your driver should be listed as 'nv'.

Try to boot in recovery mode which provide you a console with root privileges.
We are going to install your graphics driver.
First we install the restricted modules,but you have to know which kernel you have.
Type in console ```
uname -a
``` which will return something like "Linux AMD64 2.6.20-14-generic #2 SMP Mon Apr 2 20:37:49 UTC 2007 i686 GNU/Linux
bulldog@AMD64:~$ "
Now type in console ```
aptitude install linux-restricted-modules-2.6.20-14-generic
``` you need of course your kernel instead of mine.

When done type```
aptitude install nvidia-glx
``` which will install your graphics driver.
When done type ```
nano /etc/X11/xorg.conf
``` which will open the xorg.conf file.
Scroll down and find the driver section,make 'nv' into 'nvidia' and hit Ctrl-x to close and enter to save the file.

Reboot and see what happens.

---

### Post by uthman on 2007-04-10
Thanks alot for your help.

I did what you said but got the following problem.  When x tries to start I get a blue screen detailing x server error.

Failed to load module "nvidia" (module does not exist,0)
No drivers available

When I ran the aptitude commands I got the result "... 0 packages updated".  This was for both commands.

This is very strange.

---

### Post by bulldog on 2007-04-10
Are you sure you typed the commands **exactly** with spaces and - and of course your kernel?

The restricted modules aren't installed by default so you have to do it your self and you need them for your graphics to install.

Is it an old graphics or recent one?

---

### Post by uthman on 2007-04-10
Thanks for sticking with me!

First I start in recovery mode type 
uname -a which gives the response

Linux sandbox 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i 686 GNU/Linux

Next I type
aptitude install linux-restricted-modules-2.6.17-10-generic
which gives the response no packages will be installed, upgraded, or removed
0 packages upgraded,0 newly installed, 0 to remove and 0 not upgraded.

The spec says the card is Nvidia GeForce Go 7500 graphics.

I'am not really concerned about getting the graphic car working (unless I need to be?).  I just want to get unbuntu working.

---

### Post by bulldog on 2007-04-10
Hmm,and ```
aptitude install nvidia-glx
``` does nothing too?

**EDIT**
I think I know the problem,you haven't enabled the multiverse and universe repositories.

Type in your terminal ```
nano /etc/apt/sources.list
```
Look for the lines with multiverse and universe and remove the # in front of it.
Close the file with Ctrl-x and save it with enter.

Now type```
sudo aptitude update && sudo aptitude upgrade
```
And try now the restricted modules again and the nvidia-glx after that.

---

### Post by uthman on 2007-04-10
It does nothing!

I'm pretty sure the iso I downloaded is up to date.

---

### Post by bulldog on 2007-04-10
Look at my edit in previous post.:)

---

### Post by uthman on 2007-04-10
Ok its till not working.  It gives "No packages...".  By looking at the source.list I think it because I'am not connected to a network right now.

Really dumb question but do you need to be connected to a network to get this installation working?

---

### Post by bulldog on 2007-04-10
Well it sure helps,to install anything,updates or new packages,you'll need to be connected to the internet.
Otherwise you can't update anything,and in your case you need some packages to be updated.

Normally when you install ubuntu,it checks for updates during install and replaces the old packages with the newer ones.

So if possible,get your connection to work,cause you need it badly.

---

### Post by uthman on 2007-04-11
Ok got the internet connected and installed everything. Only now when I boot up I get this problem /bin/sh: can't access tty; job control turned off (initramfs)

Is this a related problem or something different?


Edit!
Just so you know more about my system. it is based on AMD Turion64 X2.  Does this help at all?

---

### Post by bulldog on 2007-04-11
I don't know if it's related or not.
Can you hit Ctrl -d and continue the boot process?
It's possible you need some updates which will be available after the log in.

When you can log in and receiving the updates,keep an eye on the packages to see if there are any kernel upgrades.
If you get the message to reboot after the update process,you can be fairly sure there was one.

So it is possible you get the same X-fault again with the new kernel.
If so just install the restricted modules for the new kernel which name you can find with the  uname -a command.
Reinstalling your nvidia driver isn't necessary.

---

### Post by uthman on 2007-04-12
Hi 

I managed to install the linux-restricted-modules and the nvidia drivers add "nvidia" to the driver section of the xorg.conf file.  When the finishes booting up I head the ubuntu "roar" sound when it finishes (I didn't head this before) but the screen is still black and pressing Alt-ctr-f1 doesn't open a console!

Its as if it finishes loading but doesn't display anything.

---

