---
title: "Ubuntu system on a flash drive. NOT the demo."
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by Maxepr on 2011-06-13
FYI. I don't know if anyone out there has done this but I thought that I'd add my discovery to the forums. I have put a complete Ubuntu operation system on a flash drive. It is NOT the demo version. It is a complete operating system.

I have a HP dv4-1551 laptop. I made sure that it will boot from a flash drive. I simply removed the hard drive and loaded Ubuntu onto the flash drive from a disk. Ubuntu thinks it's simply another hard drive. Since my original hard drive is not there, it doesn't rewrite the boot sector of the hard drive. It will write a boot sector on the flash drive that looks like the menu on a dual boot system but it doesn't affect the hard drive on the PC. If I remove the flash drive, the PC is completely normal. Even with the flash drive in, I can still boot from either the flash drive or the hard drive by simply selecting which drive to boot from within the PC's normal menu system.

I have not tried it on another PC yet but it should work. My other PC is a dinosaur and won't boot from the USB. I used a 4 GB flash drive and Ubuntu uses about 2.5 gigs on the flash drive. It's a little slower than a regular hard drive but it is acceptable and still much faster than a disk and I am happy with the performance.

---

### Post by Maxepr on 2011-06-14
It's me again. FYI. I've tried the Ubuntu Flash drive on two other PC's. It works great! I can't stress this enough. It is not the demo version of Ubuntu. It is a fully loaded operation system that you would normally see on your PC hard drive. It is so cool to be able to keep my operating system in my pocket and work with it away from home and not worry about bringing a virus home.

---

### Post by eaonflux on 2011-06-14
Nice one.

I tried this once with another distro.
reformatting a flash drive into 2 partitions and installed a distro on it.

But it has it downsides, just think about the specific hardware you maybe got.

example: i have nvidia but when i try to start it with a box with out it, i get problems in the gui.

after many hours/days thinkering i fallback to a live cd solution so it is more compatible with each new box/pc i try

but i like to hear how you handle the difference in hardware on your project.

---

### Post by Herman on 2011-06-14
My favorite home desktop PC has an nvidai graphics card while my work PC has an ATI card and I like to use dual monitors at work.

Although of course I have hard disk installed Ubuntu installations, there are times when I want to be able to use the same Ubuntu OS at work and take my work home with me to carry on in the environment of my choice. (There's no place like home).
I also use Ubuntu in a USB sometimes when I have to travel.
I also use USB Ubuntu disks for repairing computers belonging to friends and collegues.

My experience is Ubuntu will boot and run very well in almost all PCs, but if you have special graphics requirements, for example some games or google earth, or if you just want improved graphics you may need to install the proprietary driver.
Google Earth is important to me and in some PCs it crashes without the proprietary video driver.
Unfortunately I don't think it's possible to have both ATI and Nvidia drivers in the same Ubuntu installation at the same time and reverting back to the defaults has not been automated either. You need to boot into safe mode and find the option for reconfiguring the xserver, only takes a minute, but still not as convenient as having some extra software built into the OS that might do that for us.

There's a thread that already discusses ways to try to automate the video driver switching here, **     [[COLOR=#980101][B][ubuntu]**[/COLOR] Can you boot from a flash drive?  ]("http://ubuntuforums.org/showthread.php?t=1714456")[/B]It contains links to other threads too.

---

### Post by Maxepr on 2011-06-14
Ubuntu forum people,

I did not partition the flash drive. It has ONLY Ubuntu 10.10 on it. I have only tried this flash drive operating system on two other PC's besides my laptop. The only hardware problem was on my laptop itself. I needed the proprietary drivers for my wireless card. That was a weird one. I had to plug in a cable to get on the Internet so Ubuntu could download the proper drivers so I could get on the Internet. I only had to do that once.

One of the other PC's was my gaming desktop. I use it exclusively for gaming. It has an HIS 4670 video card. It is the fastest AGP card that I could find. It worked but I didn't test it out that much. Gaming from a flash drive would be foolish. As far as other graphic intense programs, I will have to do a little more research. 

The other PC is one of those little notebook laptops with an 8 inch screen. I had no hardware problems with it either. Everything worked. Those things are only good for simple Internet access anyway.

My only intention with this type of situation is to be able to carry my work around in my pocket. Ubuntu works great for what I want it to without having to dual boot my laptop. It is an easy thing to do. At least if you don't like it, you don't have to format the entire hard drive on your PC to get rid of it. This is simply something that no one on the forums (at least that I know of) has ever done and I think it has some merit and can be very useful to some people. As to all the hardware out there, I do not know. I will keep trying other PC's and find out.

The bottom line.....I think that having a traveling operating system in your pocket has many uses. Are far as hardware problems. I will have to keep working with it on more PC's. Maybe it's not practical. Time will tell. Like I said, it's easy enough to get rid of if you don't like it.

---

### Post by C.S.Cameron on 2011-06-14
On versions of Ubuntu 8.04 and before there was a file named xorg.conf that loaded your "restricted" video drivers.
There is a program named switchconf that lets you switch between conf files at start up.
You could switch between Nvidia and generic video drivers when using your flash drive to boot different machines or between machines with multiple monitors.
You could do likewise with ATI and generic but I never could get both ATI and Nvidia drivers on the flash drive at once.

If you don't load proprietary drivers the flash drive should work on most machines that boot flash).

---

### Post by dforionstar on 2011-06-15
I was able to full-install (not demo) Ubuntu 8.10 on a 4 GB flash drive with no problem.

But when I tried with 11.04, the installation GUI insists I have 4.4 GB which I don't have, so the install will not proceed.

I tried the ubuntu-11.04-alternate-i386.iso which does NOT require 4.4 GB. However this has failed every time to install from USB. I found some workarounds, but it now stops when it can't connect to the internet because 1) it fails to properly configure my adapter and and 2) then I can't connect through my wireless without a browser to insert username/password. 

I will burn an actual CD and try that.

---

### Post by dforionstar on 2011-06-16
I decided to waste a CDR and burn the Alternate iso to CD. They I tried a cold install by restarting and booting from the CD.

I got an error because the installer could not connect to the internet. Not supprising since the installer had not yet installed any adapter interface software. I choose to continue without connecting to the internet.

About 40 minutes later and 85% into the Software installation, the Installer failed. No error details or reason were provided.

I chose to return to the main menu and tried to install GRUB. This also failed - again, no error details or reason were provided.

My guess is Ubuntu is only testing this alternate CD in a VM with Host connectivity to the internet. They are not testing it as a cold install directly from CD.

---

