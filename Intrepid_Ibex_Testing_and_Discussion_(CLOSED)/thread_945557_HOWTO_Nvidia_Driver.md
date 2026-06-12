---
title: "HOWTO: Nvidia Driver"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by AdrianVeidt on 2008-10-12
There have been a number of important changes in the X server that Intrepid users need to be aware of. One is that unless you're using a proprietary xorg driver, you don't need the xorg.conf file anymore. Two is that if you are using Nvidia or ATI's proprietary driver, you need to alter your xorg.conf to be more in line with the new format -- take out all of the module and input stuff.

Why should you use Nvidia's proprietary driver? Because it is the one and only way to get hardware-accelerated OpenGL 2.1 on Linux. ATI doesn't have it, neither does Intel. If you're not using this driver, "direct rendering" means "software rendering". Incidentally, the 180 series, which is scheduled for release this quarter, will provide hardware-accelerated OpenGL 3.

You can use the Restricted Drivers Manager (jockey) to install the Nvidia driver I suppose. If that worked, then you probably aren't looking at this post. If it didn't work, then I can get your Nvidia driver working for you. Jockey didn't work for me a month ago, but it has obviously been worked on in that time, so maybe it works now. I get a lot of questions in IRC about the Nvidia driver, so I suppose Jockey isn't perfect yet.

Anyway, if Jockey didn't work for you, read on.

We're going to go step by step so there are no mistakes. First, determine what Nvidia card you have. If you know, great. If not, open a terminal and run:
> lspci
That will give you lots of information. Look for the word Nvidia. Here's what I get:
> 01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
GeForce 8800 -- got it? Good.
Now, in Intrepid, there are two Nvidia drivers that can be used with Nvidia hardware (two proprietary ones, anyway) -- 177, and 173. Which driver applies to you? They actually support some of the same hardware, but the 177 driver has improvements in 2d acceleration over the 173. **Only use the 173 driver if you have a GeForce 5xxx card.** Here's the list of cards supported by the 177 driver: Geforce 6xxx, 7xxx, 8xxx, 9xxx, GeForce GTX 260, GeForce GTX 280 and possibly others. Certainly anything built within the past couple of years.

Now you know which driver you want. Ideally, all you should need to do now is open a terminal or Synaptic and install the nvidia-glx-17x package. If you're in a terminal and you want to install the 177 package, the command would be:
> sudo apt-get install nvidia-glx-177
Afterwards, alter your xorg.conf file as described below and reboot.

If this does *not* work -- if you reboot and don't get to a gui, then more work is required. If your xorg.conf file contains information that the X server can't apply, then you'll get to a screen that will demand to know what you want to do about it. You can continue in low graphics mode, you can delete your xorg.conf file and reboot -- which should give you a gui through an open source driver, or you can just go to a virtual console through ctrl-alt-f[1-6]. It's up to you.

**DKMS**
Another major change in Intrepid is that restricted graphics drivers are now built and rebuilt for each new kernel update through a process called DKMS. You can thank Dell for it. Here's what it does. Every time your kernel is updated or upgraded, DKMS automatically (and silently) builds and installs the restricted driver into the new kernel. In a perfect world, you'd never see DKMS doing its job. If DKMS has for some reason not built and installed the driver, you can force it to do so.

Run the following command in a terminal:
> dkms status
And that will produce something like:
> nvidia, 177.80, 2.6.27-6-generic, x86_64: installed
Keyword -- "installed". That means the driver is in the kernel and available to be loaded (assuming you've got a good xorg.conf file, you're in good shape).
If on your system the result is "added", or "built", then you need to force DKMS to go further. Let's start with "added":
> sudo dkms build -m nvidia -v 177.80 -k 2.6.27-7-generic
The syntax of this command should be pretty obvious. The -m switch means the name of the module, the -v switch means the version, and the -k switch means the name of the kernel you're using -- that information can be retrieved using the "uname -r" command. Note -- You need the *nvidia-17x-kernel-source* and *linux-headers-generic* packages at the very least in order to build the module into the kernel. These should be installed automatically when you select the *nvidia-glx-17x* package.
After the build finishes, tell DKMS to install the module:
> sudo dkms install -m nvidia -v 177.80 -k 2.6.27-7-generic
When that finishes, re-run the "dkms status" command to confirm the driver is "installed".

**XORG.CONF FILE**
One way or another, you now have the Nvidia driver available to drive your card. Now we must address the xorg.conf file. I guess the easiest thing to do would be to use mine. Here it is:
> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
        Driver          "nvidia"
        VendorName      "NVIDIA Corporation"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        Option          "PixmapCacheSize" "5000000"
        Option          "AllowSHMPixmaps" "0"
EndSection
This file is located at /etc/X11/xorg.conf. You can edit yours using the command:
> gksu gedit /etc/X11/xorg.conf

Note: for those of you who tried running the nvidia-xconfig command, you have created a parochial xorg.conf file that needs to be replaced. That command is out of date and should be ignored until it's updated.
Note 2: The two "Option"s at the end apply to the 177 series only. If you have a GF 5xxx card and are using the 173 driver, delete or comment out those lines.
Note 3: If you don't have lots of VRAM (I have 512) you'll probably want to reduce the PixmapCacheSize value from 5000000 (25MB) to 1000000 (5MB). This reserves video RAM for pixmaps, but also takes away video RAM from OpenGL.
There's one more 177 tweak. Nvidia recommends running the following command after starting X:
> nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1
...however...I find that AWN and other things don't work well unless the InitialPixmapPlacement value is 1. I use Gnome and I have this command set up as a session script (System > Preferences > Sessions). I don't know how it would be done on KDE4.
Once your xorg.conf file is set and the tweaks are in place, restart. If after all of these steps, the Nvidia driver still won't load for you, run the *dmesg* command for information about why -- it could say you don't have the right hardware, for instance.

Important note for those with old hardware: The Nvidia 96 and 71 drivers do not work with the new X server and won't until and unless Nvidia updates them. Yes, they appear in the Intrepid repositories *but they don't work.* You could try the unsupported Nouveau drivers in [[COLOR="Blue"]RAOF's ppa.[/COLOR]]("https://launchpad.net/~raof/+archive") Or you could live without Compiz...or you could use Hardy until Nvidia updates the old drivers.

References:
[[COLOR="Blue"]Nvidia's performance tweaks for the 177 series[/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?t=118088")
[[COLOR="Blue"]DKMS usage[/COLOR]]("http://www.linuxjournal.com/article/6896")

---

### Post by plun on 2008-10-12
Great, just a proposal

As big as possible...:)

**[SIZE="6"]Menu System > Administration > Hardware Drivers[/SIZE]**


I have laborate with this and something seems to brakes if a user is doing it on "free hand"... in my case I totally broke my install with Nouveau.
(now I knows the secrets how get the driver back from tty)


Envyng is also a supported method.  (within Intrepids repo)

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=envyng](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=envyng)

---

### Post by nanog on 2008-10-12
> now I knows the secrets how get the driver back from tty

I think there should be a test before allowing someone to download or upgrade prior to at least the RC stage. Don't know how to chroot -- well then no alpha5 for you!

---

### Post by joepotter on 2008-10-12
There is a bug. 

The nVidia drivers do not work with GeForce 6100. 

See:

 [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/282214](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/282214)

In fact; the 6100 has never worked using nVidia with Intrepid that I am aware of; and it looks like it will not work at release either. (a hunch)

---

### Post by plun on 2008-10-12
> **nanog said:**
> I think there should be a test before allowing someone to download or upgrade prior to at least the RC stage. Don't know how to chroot -- well then no alpha5 for you!

(I needed to chroot around Alpha 2 but since then it has been stable.)

In this case its about to switch to a tty.

A user also gets the new maybe confusing choices for **failsafe management**.

And you cannot switch to a tty until the failsafe driver is loaded. GDM
cannot be stopped

"Please wait"  > Login screen or crash

Then you can switch over to a tty..... 
 
A total "big bang crash" is better for you can directly swith to tty 

But.. I am rather sure that Alberto, Martin and all Xorg guys nails this challenge...:)

---

### Post by nanog on 2008-10-12
> And you cannot switch to a tty until the failsafe driver is loaded. GDM cannot be stopped


I believe that TTY1 should be available independently of the status of gdm. I'm hopeful they'll fix the failsafe mode bugs by release.

---

### Post by plun on 2008-10-12
> **nanog said:**
> I believe that TTY1 should be available independently of the status of gdm. I'm hopeful they'll fix the failsafe mode bugs by release.

Sorry, this is the case if a user wants to install a downloaded driver.

nvidia-installer checks if GDM is running and the failsafe driver must be fully established then gdm can be stopped and so on..

A tty switch just for normal update or package install is no problem. 

but... a tty is something really abstract for mostly all users so its
better to remove this challenge complete  :)

---

### Post by shane19174 on 2008-10-12
AdrianVeidt,
Thanks for the useful post. Brings together a lot of info to one place and presents it in a very understandable manner.

---

### Post by philinux on 2008-10-12
Backed up my "barebones" xorg.conf and used the OP's and glxgears has gone from 3500 to 5200 same as Hardy. Cheers.

What does this bit do?
Option          "PixmapCacheSize" "5000000"
        Option          "AllowSHMPixmaps" "0"

---

### Post by AdrianVeidt on 2008-10-12
> AdrianVeidt,
Thanks for the useful post. Brings together a lot of info to one place and presents it in a very understandable manner.

I'm glad someone thinks so. I was tired of repeating this stuff in IRC over and over again. From now on I'm pointing people at this post.

---

### Post by philinux on 2008-10-12
With compiz on glxgears goes back to 3600 fps.

---

### Post by PinkFloyd102489 on 2008-10-12
This guide worked on my 8600M GT.

Very helpful post. Thanks man!

---

### Post by subixonfire on 2008-10-12
Sorry but actually there are 4 Nvidia propetary drivers!
You have 2 more legacy drivers, 96.xx is the important one, because with this driver compiz is working on some really old cards like gforce2.
**This driver dos not work curently,** because of the Xorg used in intrepid , a loot of peoples are waiting for nvidia to release it! 

I know my english is a litle bad, sorry!

---

### Post by Hoppiesbox on 2008-10-13
Thanks loads Adrian! Everything was A-OK as far as I could tell, so I replaced my xorg.conf with yours, rebooted, and nvidia-settings worked like magic. Both screens are working now.

Thanks again,
Justin

---

