---
title: "RE: Installing Ubuntu 18.04 LTS on HP Spectre x360 Convertible"
date: 2018-12-06
forum: Installation &amp; Upgrades
---

### Post by jabrilm on 2018-12-06
I am trying to install Ubuntu 18.04 LTS on a new HP Laptop (Spectre x360 convertible with NVIDIA GeForce). I am installing from a USB drive, and trying to install it as a dual-boot system with Windows 10. I find that it hangs at the splash screen (the one with the dots), which I've encountered in the past when installing Ubuntu on other machines. However, this time the solutions I've used in the past are not working. Most suggestions online say to edit the grub boot options, finding the line with [FONT=courier new]quiet splash[/FONT] and adding [FONT=courier new]nouveau.modeset=0[/FONT] and booting from there, and later installing the NVIDIA drivers. That's not working, though. It still gets hung up after making a bit of progress. The last message before freezing up is about the dbus message bus starting, and it has status [OK]. Nothing happens after that.

I've also tried variants such as [FONT=courier new]nomodeset[/FONT], or [FONT=courier new]nvidia.modeset=0[/FONT], or [FONT=courier new]nv.modeset=0[/FONT]. I've also tried deleting [FONT=courier new]quiet splash[/FONT] or leaving it. What should I try next? Does the ordering of the arguments matter? Can I do the installation in a low-resolution mode? I saw a recommendation to use [FONT=courier new]grub_gfxmode=1280x1024x24[/FONT] but that has not worked either.

I've now tried installing 18.10 as well and am getting errors. First some ACPI errors that I can fix by setting[FONT=courier new] acpi=off[/FONT] in the grub settings. And then an error "[FONT=Menlo][FONT=courier new]MODSIGN: Couldn’t get UEFI db list[/FONT]". 

[/FONT]Secure Boot has already been disabled in BIOS. I also updated the BIOS to the newest version.

---

### Post by balalrumy on 2018-12-07
[COLOR=#1A1A1A][FONT=&amp]I dual boot mine with windows 10 and 18.04.1.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp][https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/how-to-install-ubuntu-18-04-alongside-with-windows-10-or-8-in-dual-boot.html](https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/how-to-install-ubuntu-18-04-alongside-with-windows-10-or-8-in-dual-boot.html)[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]No major issues. The speakers do not work correctly and its a known issue.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp][https://bugzilla.kernel.org/show_bug.cgi?id=189331](https://bugzilla.kernel.org/show_bug.cgi?id=189331)[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]I have tried version up to kernel 4.18.3.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]My computer is a HP Spectre x360 convertible 13-ae0xx which is also a [**[COLOR=#222222][FONT=Verdana]best laptops for engineering students[/FONT][/COLOR]**]("https://technicalustad.com/best-laptops-for-engineering-students/")[/FONT][/COLOR]

---

### Post by jabrilm on 2018-12-07
Did you have to change your grub settings at all when installing, e.g. using nomodeset?

I was able to get past these errors by adding [FONT=courier new]noapic noacpi nosplash[/FONT] in place of [FONT=courier new]quiet splash [FONT=arial]in the grub boot settings.[/FONT] 

[FONT=arial]The touchpad and touchscreen are not working, but I'm hoping to get them working with the right drivers. [/FONT][/FONT]

---

### Post by collectionofatoms on 2019-02-12
Were you ever able to get this Ubuntu install fully working on your machine?
Has the Dual Boot treated you well since?

I ran into the same freeze on the splash screen that you did, but haven't tried futzing with  but may be better off returning this computer if nobody knows how to get the touch pad working.

---

### Post by collectionofatoms on 2019-02-12
For posterity:  

I got this all working and it wasn't easy. 

tl;dr Enable legacy, update Kernel.

I'll preface this by saying that I started this endeavor with the intention of creating a solid React.JS project development environment.  First I tried Virtualization of Ubuntu using VirtualBox and found the virtualized machine just couldn't keep up with the screen resolution.  Everything was laggy and terrible, and it definitely wasn't a place where I would want to spend all of my time working my day job.  I tried setting up a standard Windows environment for React.JS.  Our project wouldn't compile, so I decided to try a dual boot on my machine, and that process was the biggest pain of them all.  But right now I'm writing this from inside of a smooth working Ubuntu environment, so I figure I'll pass the knowledge down the line.  

The trick here is to go into the BIOS (by pressing ESC during startup) and change the setup so Legacy is enabled.  Note that in doing this, you will trip a security setting in windows and so you should make sure that you have your BitLocker hard-drive key on hand, or else you will get locked out of your Windows machine.  If you did all the login stuff with your microsoft account you should be able to access them online on your Microsoft account ([Help Docs for that]("https://support.microsoft.com/en-us/help/4026181/windows-10-find-my-bitlocker-recovery-key")).

After legacy mode was enabled, I was able to proceed with the install option.  It looked like it wasn't doing much when I told it to start the installation and gave me a spinning circle for my cursor for several minutes, before it was ready to actually start the install.  

During install tell it to install those sweet sweet proprietary graphics drivers.  The install process took about an hour, but that might be because I told it to do an update during install, and the network connector is mega bad.  More on that now:

So if you get this far, you'll be like: "Great everything is running mega smoothly and I'm happy!  Time to start installing software and getting set up.  Oh wait, why is the Wifi so slow?"  And the answer is this: your network card is too new and Ubuntu's stable release is 6 months behind the times and you need a newer Kernel version to get your networking to not suck terribly. [Here's a Reddit PSA about running Ubuntu on machines with this network card]("https://www.reddit.com/r/Ubuntu/comments/a61qq1/psa_for_owners_of_intel_wirelessac_9260/").  At this point you are either going to want to find a way to hard-wire a connection to your machine, or get access to another computer and a drive, because until you change the Kernel your internet will be unbelievably slow, so even downloading the new one will take a whole day.  (I was getting ~20kbps at best before updating.)  

[Here is a resource about changing your kernel.]("https://wiki.ubuntu.com/Kernel/MainlineBuilds")  You'll have to download some files from that site and run some ```
[FONT=courier new]sudo apt-get install ./<package name>[/FONT]
```.  But be warned: first I downloaded the newest kernel (4.20.something) and while that fixed my networking issues, it broke my trackpad and mouse.  I ended up installing [Version 4.19.8]("https://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19.8/") and that did the trick. 

After that I was able to get my dev environment up and running as intended.  Hope this helps somebody down the road.

---

### Post by jabrilm on 2019-04-10
Thank you for all the info. During your initial installation, did you have to edit your grub settings at all, or was enabling the legacy settings all that you needed to get it installed?

---

### Post by jabrilm on 2019-04-11
[SIZE=2][FONT=garamond]In case this helps anyone with similar issues, this is the grub line that ended up getting Ubuntu installed and the touchpad working on my spectre laptop. I replaced[/FONT] [FONT=courier new]quiet splash[/FONT] [FONT=garamond]with[/FONT] [FONT=courier new]noapic noacpi nosplash i8042.reset i8042.nomux=1 i8042.nopnp i8042.noloop [FONT=garamond]in the grub settings. 

[/FONT][/FONT][FONT=garamond]However, the touchscreen still does not work. I will update the thread if I get it working. [/FONT]

[FONT=garamond]I did **not** have to enable legacy mode in the BIOS as an earlier comment suggested. [/FONT][/SIZE]

---

