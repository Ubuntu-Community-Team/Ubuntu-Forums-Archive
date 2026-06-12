---
title: "Ubuntu Studio/Remix_OS dual boot"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by whitetrashkillbot on 2011-07-03
I'm running Ubuntu Studio 11.4 off my laptop and I found this cool little distro called remix_os and I installed it on an external hard drive.  I did a live cd off an 8GB flash drive, ran the installer and installed remix-os onto a 500gb external hard drive.  Everything works, but I think it deleted the grub off my computer.  what I thought was going to happen was when I started my computer and hit F2 to set it to boot off the usb hdd then it would load the remix_os, and when I set it to load off my computer's hard drive it would load into ubuntu studio like normal.

What actually happened was the installer set up remix_os and ubuntu like a dual boot, it goes into the remix menu and I can still load ubuntu studio but I have to have the external hard drive plugged in.  If I unplug it then I just get the black screen saying "30025454hiwe or whatever my hard drive is called" doesn't exist and a line that said "recover grub".  Is there a way to get the grub back up for ubuntu studio without reinstalling everything?  If I had a dual boot set up I want ubuntu to be the default or priority and load off my computer's hard drive, then either select the usb hdd if I want it, if not ubuntu will load and do it's thing. I'm open to scrapping remix_os and maybe trying a different installer, ultimately I just want ubuntu studio to load. I'm bad at explaining things, it makes sense to me as I'm writing this but if I can clarify anything let me know.  Any help would be greatly appreciated.  

(what happens is I have a crap internet connection and I get ubuntu all set up, start messing with reaper and wine and various installs and command line things and I screw something up, I don't want to mess with ubuntu, I got it just the way I want it.  I thought I could run that remix_os off the external and it wouldn't effect my main operating system but it looks like it jacked my grub)

---

### Post by Remixer on 2011-07-04
You installed Grub on your external HDD, when installing Remix_OS. 
Login to Ubuntu Studio, unmount and unplug your external HDD, reinstall Grub form Synaptic and reboot.

---

