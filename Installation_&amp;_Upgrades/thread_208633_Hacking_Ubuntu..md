---
title: "Hacking Ubuntu."
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by sketchman on 2006-07-03
I have a problem.
I have an older computer that I want to put Ubuntu on. Before anyone says it, I don't care if it runs slowly and I'm limited to low res. I'm sick and tired of M$'s buggy excuse for an OS(Win98), so Ubuntu is going on my computer. 
Now, here's the problem. There is absolutely NO way to run Ubuntu as a liveCD distro. Not because the PC can't boot from a CD, but because it is so slow when it does.
So, summary. I need to hack the CD somehow, to get Ubuntu on my HD manually.
What have I tried so far? I copied EVERYTHING from the CD to my 20gig HD, and set up GRUB to boot the partition that Ubuntu now sits in and made the partition bootable. I then rebooted, and no go.
Then I looked around the files and found a *.cfg file. I looked it over and saw that it created a ramdisk on boot and set it as root. So, I changed it to set the HD as root and have no ramdisk. Another reboot, and now some results. GRUB finds the kernel and everything starts to work. But, then, I see an error message.
[COLOR="Red"]Kernel panic: No init found.  Try passing init= option to kernel. [/COLOR]
Any suggestions?:(

---

### Post by sketchman on 2006-07-03
Oh, I forgot to add. Yes, I already checked the init= line in menu.ls of GRUB boot folder. It's there.

---

### Post by jISh on 2006-07-03
Use the alternate install CD instead of the LiveCD.
it has a text-based installer.
You won't have any luck trying to copy the files over.

---

### Post by sketchman on 2006-07-04
Thanks. I'll try that.

---

### Post by lordlollo on 2006-07-04
Give a try to Xubuntu.
It's lighter than Ubuntu (and Kubuntu, of course), as it features the Xfce window manager.
If your pc is really old, anyway, I'm not going to suggest you to use such distros. The world is plenty of small and fast Linux distributions. I have personally tried Damn Small Linux and VectorLinux, as examples.
You could think to give'm a look, if you're not lucky with your work and Xubuntu isn't for you.

---

### Post by sketchman on 2006-07-04
Well, there's no way I can download Ubuntu. 600+megs would take years on my 1kbs dl speed connection. (No, that's not a joke. Sometimes I get as high as 2kbs, but mostly 1.)

There must be a way to do what the GUI installer does, but by hand.
I have a few more ideas before I give up, but I have to admit, this is getting old fast. 

At least I have Puppy Linux if this doesn't work out. So, all is not lost.

---

### Post by atoponce on 2006-07-04
[quote=sketchman]Well, there's no way I can download Ubuntu. 600+megs would take years on my 1kbs dl speed connection. (No, that's not a joke. Sometimes I get as high as 2kbs, but mostly 1.)

There must be a way to do what the GUI installer does, but by hand.
I have a few more ideas before I give up, but I have to admit, this is getting old fast. 

At least I have Puppy Linux if this doesn't work out. So, all is not lost.[/quote]
You can order Ubuntu (or xUbuntu) CDs from the [Ubuntu Shipit program]("https://shipit.ubuntu.com").  They are completely free, even shiping, and take about 6 weeks to show up.  That 6 weeks might be faster than your downloading a 1K/sec. :)

---

### Post by sketchman on 2006-07-07
I did that, but the disk they sent me is the liveCD version, and my PC will not run it. Only 64mb ram and a 350mhz processor. It takes 10 minutes, at least, to get to the the desktop. 

The panel never comes up and all I see is dark red.

---

### Post by atoponce on 2006-07-08
Only 64MB of RAM?  There is problem #1.  If you want the GUI, you need an absolute minimum of 128MB, and you need to install Xubuntu or Fluxbox; not Gnome or KDE.  They are far too bloated and resource intensive.  Even Xubuntu may give you problems.  I would recommend [Damn Small Linux]("http://www.damnsmalllinux.org/") for a system with those specs.

---

### Post by 3rdalbum on 2006-07-08
I think Puppy requires 128 megs these days, but I'm not certain. I think the only thing you can do is install more RAM (so you have 256 megs), or run DSL. DSL should be pretty good on that machine.

I'm running Ubuntu 5.10 with Enlightenment on a 333MHz iMac with 128 megs... it's painfully slow.

---

### Post by sketchman on 2006-07-08
No, Puppy still runs on a PC with as low as 64mb of RAM, as long as it has a swap partition. It runs on the PC in question, so I'm not trying to be arrogant, I just know it to be fact. It has a 500mb swap.

The problem with Ubuntu, I'm guessing here, is that it has to use a whole lot of that swap partition to run so it runs really slowly.

But, if the entire OS didn't have to be in RAM, like if it were on a hard drive and only running programs were in RAM, I think it might work. Maybe not blindingly quickly, maybe not even tolerably quickly, but if it ran at all, I'd be happier than I am now.

Oh, by the way, does anyone know if Ubuntu has problems detecting hardware through USB ports on a PCI card? That's part of the reason I want a different Linux distro than Puppy. Puppy won't, and I'd like to be able to use my USB thumb drive if at all possible.

---

### Post by ubuntu27 on 2006-07-08
> **sketchman said:**
> No, Puppy still runs on a PC with as low as 64mb of RAM, as long as it has a swap partition. It runs on the PC in question, so I'm not trying to be arrogant, I just know it to be fact. It has a 500mb swap.

The problem with Ubuntu, I'm guessing here, is that it has to use a whole lot of that swap partition to run so it runs really slowly.

But, if the entire OS didn't have to be in RAM, like if it were on a hard drive and only running programs were in RAM, I think it might work. Maybe not blindingly quickly, maybe not even tolerably quickly, but if it ran at all, I'd be happier than I am now.

Oh, by the way, does anyone know if Ubuntu has problems detecting hardware through USB ports on a PCI card? That's part of the reason I want a different Linux distro than Puppy. Puppy won't, and I'd like to be able to use my USB thumb drive if at all possible.

I haven't saw any problems with USB Thumbdrives in Ubuntu. When I insert my USB Drive/Thumb Drive it is mounted automatically.


Edit: I think the best solution will be to Buy a new RAM.

[http://www.newegg.com/ProductSort/Category.asp?Category=17](http://www.newegg.com/ProductSort/Category.asp?Category=17)

---

### Post by pravuil on 2006-07-08
The best option is to reinstall Ubuntu, but instead of choosing the LiveCD method of install try using the text mode option. It doesn't rely on graphics so if you're familiar with the debian installer then you shouldn't have too much trouble. If your really having problems with graphics in the long run you might as well choose the server install method which will install only the base linux os without any desktop. (It won't install apache so don't worry about the term used for this method) Once it's installed use apt-get or aptitude to install the xubuntu desktop. About the RAM, you will have some problems but maybe with the appropriate graphics driver installed it might work a little bit better. 64 is only recommended for the server install with 256 being recommended for the desktop. Get more RAM it will help especially when you can get 512 MB RAM for 40 bucks nowadays. Hope that helps.

---

### Post by sketchman on 2006-07-15
> **ubuntu27 said:**
> I haven't saw any problems with USB Thumbdrives in Ubuntu. When I insert my USB Drive/Thumb Drive it is mounted automatically.

Yes, but is the USB port you are inserting your drive into built in to the PC or on a PCI card? Puppy will detect my drive no problem if it's in a built in port. But mine are on a PCI card that I bought and installed, so it won't let me use it.

---

