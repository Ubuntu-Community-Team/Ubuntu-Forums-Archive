---
title: "Install seems good, but boot is bad"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by Resurrection on 2006-02-20
Ok, this is my first post, trying to get ubuntu to work.  Not new with computers, and I have some programming experience with Unix systems, but only a tiny bit of experience with Linux.  This is first time installing it myself.

After some install problems, turns out I just had a badly burned .iso and reburned and it installed fine.  Or so I thought.

System is set up as a dual boot with two hard drives.

First drive is WinXP Pro.

Second drive is Ubuntu.

Second drive was completely clean and formatted during installation.  System boots fine in XP, but when Grub trys to load Badger, It hangs.  If I choose the kernel (recovery) option, Grub will load system all the way to root prompt and then I don't know what to do from there.  

So my question is why is the root prompt working but not the happy shiny GUI?

Edit:  Learning more as I go along, at the root prompt I type "startx" and it cuts to an all black screen.  Nothing there, not even a cursor.  A problem with the Gnome install?

---

### Post by Resurrection on 2006-02-20
Well I did a Gnome install from the root prompt at after starting the kernel in (recovery) mode from Grub.

When the root came up, I typed "sudo apt-get install ubuntu-desktop"

Gnome seems to install fine, so I type "startx" and it gives me some error codes.

After researching the website it says to try:
[http://wiki.x.org/wiki/FAQErrorMessages]("http://wiki.x.org/wiki/FAQErrorMessages")

I find out that:
> Message: "No devices detected"
You get an error message like:

(EE) No devices detected.

Fatal server error:
no screens found

It is very likely that your xorg.conf file doesn't contain the correct driver(s) for the chipset(s) in your system or that your chipset isn't supported by any of the drivers.

So I decide to pull my nVidia card from the system and do a clean reinstall of Ubuntu.  Will see if the graphics card was the problem.  Going to use my standard on-board Intel graphics in the meantime.  Hopefully that will work.

---

### Post by Coelocanth on 2006-02-20
If you think it's the nVidia card, you could try using the vesa drivers (instead of the nv ones) and then update to the proper nVidia drivers after. I had troubles with my install due to my card as well and had to go about it that way.

---

### Post by Lord Illidan on 2006-02-20
I had the same problem myself with an NVIDIA card. Don't re-install. Just change nv in /etc/X11/xorg.conf to vesa.

And then, you can install the nvidia drivers through synaptic when you are in a gui.

---

### Post by Resurrection on 2006-02-20
Too late, As I type I am at 83% of Installing Packages after the reboot during install.  So almost done.  Besides, would rather know that I have a clean install that works, before trying to tweak things.  If my install doesn't work, then I will know that my card wasn't the problem, and I may have some other compatibility hardware issues.  I have plenty of time to experiement.  Thanks for the info about the nvidia drivers, I am sure I will have to do something like that when I try to use the card again in the future.

Edit:  Success!!!!!!!!!  Right now I am looking at a pefectly functioning install of Ubuntu with at the "desktop".  Pulling the graphics card was the only change.  That and this time I stopped being lazy and plugged in a internet connection and setup that up during the install.  But I don't think the internet connection would have affected this.  Now its time for me to play some and see what this distro can do.
Thanks for the help.

---

