---
title: "NVIDIA Driver.  I've wasted all stinkin' day on it."
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by xl_cheese on 2007-06-03
Still cannot install it.

I have an 8600 gt card.  I've tried installing the beta driver per nvida instructions as well as these:
[http://www.nvnews.net/vbulletin/showthread.php?t=92479](http://www.nvnews.net/vbulletin/showthread.php?t=92479)

The later process will actually start, but complains about my nvidia kernel and then quits.

This driver on vista took about 5 minutes to install...

What a pain.

---

### Post by lazyart on 2007-06-03
Did you get the recent kernel upgrade?  That might have something to do with it.

Reboot and when you get to the grub screen hit escape.  You might have six different options there to boot into.  Select the third Linux related option  in the list.  If that gets you in then we can comment out the new kernel entry.

---

### Post by xl_cheese on 2007-06-03
> **lazyart said:**
> Did you get the recent kernel upgrade?  That might have something to do with it.

Reboot and when you get to the grub screen hit escape.  You might have six different options there to boot into.  Select the third Linux related option  in the list.  If that gets you in then we can comment out the new kernel entry.

Thanks for your reply, but I'm not sure what you're telling me to try?

I think I have the .16 generic kernel.

I'm not even sure what the kernel does.

---

### Post by lazyart on 2007-06-03
when you first power up the machine you get the usual start up stuff and then it screen will go black and it will mention GRUB 1.5.

Hit ESC at that point (before the ubuntu logo).

You can pick a kernel to boot with, recovery mode for each kernel, a memory test, etc.  This will be text only.

The first option is the default and could very well be the new kernel which some people are having trouble with.  Below that will be recovery mode for that kernel, but we don't want that either.  You may have another kernel listing-- the .15 version.  Select it and see if it gets you into your desktop.  If it does we know the culprit and can attack it from there.

---

### Post by Beamerboy on 2007-06-04
Hi,

I just found a fix for this.  there is a problem with the NVidia.Com installer in that it doesn't update the module dependencies.  To fix this problem boot your machine and let xorg fail then hit ALT+CTRL+F1

Login using your username and password the type the follow:

sudo depmod -a

then type sudo reboot

This should fix your problems but if it doesn't you need to do the following:

sudo nano /etc/default/linux-restricted-modules-common

add the following line

DISABLED_MODULES="nv"

press CTRL+X and save the file.

Reboot.

Everything should now work.

Paladine
[Edit] Thanks to ROAF for the fix

---

### Post by xl_cheese on 2007-06-04
> **Beamerboy said:**
> Hi,

I just found a fix for this.  there is a problem with the NVidia.Com installer in that it doesn't update the module dependencies.  To fix this problem boot your machine and let xorg fail then hit ALT+CTRL+F1



Paladine
[Edit] Thanks to ROAF for the fix

Ok, I tried this, but I didn't see a change.

Here's the log file.

Using: nvidia-installer ncurses user interface
-> You appear to be running in runlevel 1; this may cause problems.  For exampl
   e: some distributions that use devfs do not run the devfs daemon in runlevel
   1, making it difficult for `nvidia-installer` to correctly setup the kernel 
   module configuration files.  It is recommended that you quit installation no
   w and switch to runlevel 3 (`telinit 3`) before installing.
   
   Quit installation now? (select 'No' to continue installation) (Answer: No)
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
ERROR: Unable to connect to download.nvidia.com (unknown host)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by Kuoi on 2007-06-04
As Lazyart says , it could be (and I too guess it is ) a kernel problem.

Do you see the .15 kernel in your grub , and if so , did you tried to boot this one ?

Kuoi

---

### Post by xl_cheese on 2007-06-04
I looked into installing a libc package

[http://ubuntuforums.org/showthread.php?t=452746&highlight=libc+header](http://ubuntuforums.org/showthread.php?t=452746&highlight=libc+header)

However, the install says I already have that version installed.

---

### Post by xl_cheese on 2007-06-04
> **Kuoi said:**
> As Lazyart says , it could be (and I too guess it is ) a kernel problem.

Do you see the .15 kernel in your grub , and if so , did you tried to boot this one ?

Kuoi

yep.  I was originally using that one, but installed ubuntu updates which changed it to .16.

I went back on the original suggestion and tried it on the older kernel, but did not see a change.

thanks for your help!

This is kind of a bummer.  I was pretty excited to try a linux OS on my home pc.

---

### Post by xl_cheese on 2007-06-04
fyi - I installed the libc-dev stuff suggested by another thread I found and the nvidia driver installation now works.

Catch is that now my Xserver is broken?!

---

### Post by Kuoi on 2007-06-04
Try to stay in the .15 kernel , do not use .16 , because there are many problems with it.

Now , maybe you can try to install the videodriver using [Envy]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.4-0ubuntu6_all.deb").
First uninstall your driver using the tool , and then install the correct diver with the tool .

If you can't boot after it , just boot in "recovery console" , and type there > dpkg-reconfigure xserver-xorg , but normally , using  Envy should work well.

Kuoi

---

### Post by xl_cheese on 2007-06-05
Thanks everyone for the help.  These forums are a great resource.

After some more determination I have things working.

I reinstalled unbuntu so I could start from a clean slate.  I deleted all the nvidia kernerl stuff recommended on one of the other threads.

I then ran Envy and installed a driver other than the beta version.  

I did not upgrade to .16 this time.  

Next I did:
/etc/init.d/gdm restart

Then:
installed the nvidia beta driver.

And finally 
/etc/init.d/gdm restart to get back to the window environment.



to get higher screen resolution I manually edited the xorg.conf and added the correct resolution.

---

### Post by topsites on 2007-06-05
Just wanted to add my little .002 after spending closer to a week dealing with this, for the third time!

How to do it right lol:
1)  Get the Ubuntu 6.06 Iso CD, insert, re-boot and boot from CD.
2)  When it boots, Re-install but manually configure the partitions CAREFULLY!
 > In my case, I put the Desktop and Documents directory elsewhere.
3)  Re-install.
4)  Once you can boot, BURN Desktop / Documents to a CD-Rom (actually, I have a DVD-Rw, it fits 4GB)
 > You might have to let it upgrade / install packages, I did.
5)  Re-install again, this time re-partition everything back to one drive.
6)  Once you can boot, let it upgrade / install packages.
7)  Then, go into Terminal and upgrade > Edgy > Feisty.
8}  Once you can boot, dump your DVD's contents back onto the Desktop.
9)  Download Envy, install
10)  Uninstall the driver
11)  Auto Install (option 1, I think).
12)  Re-boot, and let the xserver crash (LOL how did we know?)
13)  Go into dos mode, and type Envy -t
14)  Uninstall current driver (option 2, I think)
15)  Install Manually as such:
 > You HAVE to know which driver is for your card, charts for this exist, in my case it's 9631
16)  Reboot xserver

voila, you might can manually install direct from the GUI, but in my case the above is how I did it.

p.s.:  It helps if you have some spare time, like a few days, but most of it is automated, just takes time.

And trust me, I tried everything else, I had 50-odd pages of detailed how-to's and step by steps, none of that worked for me.

Other notes:  Do NOT install anything on your working system that you do not need!
No, really, don't install it, period.  If it works, don't install anything at all from Synaptic.

Now I got a working system.

---

