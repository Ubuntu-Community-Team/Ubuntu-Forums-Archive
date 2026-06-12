---
title: "I can't install ubuntu on my Dell Inspiron 620"
date: 2012-09-26
forum: Installation &amp; Upgrades
---

### Post by Trackaholics on 2012-09-26
So I made a bootable usb pendrive using universal usb installer. Went and booted my pc from the usb and got to this screen [http://i.imgur.com/QdFVi.jpg](http://i.imgur.com/QdFVi.jpg)

I hit "install ubuntu on a hard disk" and ubuntu did its thing. After a few seconds It gets stuck here [http://i.imgur.com/eN8zu.jpg](http://i.imgur.com/eN8zu.jpg)

and that's that it doesn't do anything else. I installed ubuntu on my laptop using the same usb drive and it worked 100%. 

any help? thanks in advance ):P

---

### Post by bayouoldguy on 2012-09-26
Trackaholics, unless you get some better instructions, I think I would "force shut-down", remove the USB drive, reboot to clear the setup, then go back & try a "run from the USB before installing. I have a Dell D620 running dual Windows Vista & Ubuntu 12.04.1 as I reported below....Good luck... "G"

 Success w/12.04.1
Just completed my upgrade to 12.04.1, from 10.04 LTS using the upgrade in the downloads manager. I tried the 12.04.1 release in a USB stick trial, found that the wireless problems could be corrected & I could connect my network printer...so took the plunge .took approx. 20 min. download @ 1135 mB/s on our fiber network, & about a 1.5 hr. install & cleanup. Reboot was clean into the desktop & wireless was up & running thru my router ..no effort. I encountered a problem getting my network printer to work ,but did a reinstall of the CUPS driver for the Canon MP500 printer & a sub-menu came up to allow me to specify the network printer. I wish to thank all the devs that worked on this version, making it a clean upgrade !.
(Dell D620 old system, 1.66 Ghz, 2G RAM, 80 GB HD shared w. Windows Vista)
Look like more FUN in Ununtu....thanks guys !!!!!!keep up the good work... ........"G"
__________________
"G": Compaq Presario, 1.2 Ghz AMD Athlon,2.2 GB Ram, 40 GB HD, Windows ME/ Ubuntu 10.04 LTS shared,LG 19" Monitor,nVidia GeForce 2 MX, Creative SB Live. ( old box to learn Linux on )

---

### Post by Trackaholics on 2012-09-27
> **bayouoldguy said:**
> Trackaholics, unless you get some better instructions, I think I would "force shut-down", remove the USB drive, reboot to clear the setup, then go back & try a "run from the USB before installing. I have a Dell D620 running dual Windows Vista & Ubuntu 12.04.1 as I reported below....Good luck... "G"

 Success w/12.04.1
Just completed my upgrade to 12.04.1, from 10.04 LTS using the upgrade in the downloads manager. I tried the 12.04.1 release in a USB stick trial, found that the wireless problems could be corrected & I could connect my network printer...so took the plunge .took approx. 20 min. download @ 1135 mB/s on our fiber network, & about a 1.5 hr. install & cleanup. Reboot was clean into the desktop & wireless was up & running thru my router ..no effort. I encountered a problem getting my network printer to work ,but did a reinstall of the CUPS driver for the Canon MP500 printer & a sub-menu came up to allow me to specify the network printer. I wish to thank all the devs that worked on this version, making it a clean upgrade !.
(Dell D620 old system, 1.66 Ghz, 2G RAM, 80 GB HD shared w. Windows Vista)
Look like more FUN in Ununtu....thanks guys !!!!!!keep up the good work... ........"G"
__________________
"G": Compaq Presario, 1.2 Ghz AMD Athlon,2.2 GB Ram, 40 GB HD, Windows ME/ Ubuntu 10.04 LTS shared,LG 19" Monitor,nVidia GeForce 2 MX, Creative SB Live. ( old box to learn Linux on )

I already tried to run ubuntu from the usb. Thanks for the reply though.

---

### Post by critin on 2012-09-27
> **Trackaholics said:**
> I already tried to run ubuntu from the usb. Thanks for the reply though.

Are you saying it does NOT run live from the usb?  Don't try to install it then.  Have you installed this iso into any other machine and have it work, or even run live?

You might try downloading it again,  ---with wired internet---  your copy may be corrupted.  Run it live first and if everything works, install from the live desktop.

---

### Post by Trackaholics on 2012-09-27
> **critin said:**
> Are you saying it does NOT run live from the usb?  Don't try to install it then.  Have you installed this iso into any other machine and have it work, or even run live?

You might try downloading it again,  ---with wired internet---  your copy may be corrupted.  Run it live first and if everything works, install from the live desktop.

No it doesn't run live from the usb. I tried the same usb on my laptop and it installed without any problem. My copy can't be corrupted. I'm really clueless about why it's not working. It must have something to do with my computer. I was hoping the screenshots would help.

These are my specs if they're any help. 
Intel(R) Core(TM) i5-2320 CPU @ 3.00GHz
6GB RAM 
GeForce GTX 550 Ti
1TB hard drive with 199.0 GB of free space.

---

### Post by critin on 2012-09-27
> **Trackaholics said:**
> No it doesn't run live from the usb. I tried the same usb on my laptop and it installed without any problem. My copy can't be corrupted. I'm really clueless about why it's not working. It must have something to do with my computer. I was hoping the screenshots would help.

These are my specs if they're any help. 
Intel(R) Core(TM) i5-2320 CPU @ 3.00GHz
6GB RAM 
GeForce GTX 550 Ti
1TB hard drive with 199.0 GB of free space.

Just to be perfectly clear.  You installed this same iso to the laptop without error?  It wasn't just the same usb with another iso in it?

The boot menu in your link looks like an old version.  Is it 12.04?  Did you download from the ubuntu download site?  The different look may be from Universal, I use unetbootin and get a different screen.

The screenshots don't help me, sorry.  There isn't enough info.

> 
These are my specs if they're any help. I'll take them, thanks!!  lol

That should run anything you give it.

---

### Post by Trackaholics on 2012-09-27
> **critin said:**
> Just to be perfectly clear.  You installed this same iso to the laptop without error?  It wasn't just the same usb with another iso in it?

The boot menu in your link looks like an old version.  Is it 12.04?  Did you download from the ubuntu download site?  The different look may be from Universal, I use unetbootin and get a different screen.

The screenshots don't help me, sorry.  There isn't enough info.

Yes the exact same usb (same iso too) that didn't work on my desktop worked on my laptop. It's the latest version. I downloaded the 32 bit version straight from this page [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

I also tried using unetbootin but the screen froze when I tried to choose any of the boot options such install to hard drive, run from the usb and such.

The one thing I haven't tried is to burn the iso to a cd. I have an old ubuntu 8.10 cd that I got from ubuntu themselves and that one didn't work either. All I got after the loading screen was a command type screen, like when you open up terminal or command prompt on windows.

---

### Post by critin on 2012-09-27
That's really odd.  I have no ideas if it won't run a cd either.  I was going to suggest that.
Someone with more know-how than I have will be along to help, don't give up.

Something on the hardware is definitely balking.

Why don't you try burning it to a cd/dvd anyway?  Your old four-year old cd copy may have problems of its own.

---

### Post by Trackaholics on 2012-09-27
> **critin said:**
> That's really odd.  I have no ideas if it won't run a cd either.  I was going to suggest that.
Someone with more know-how than I have will be along to help, don't give up.

Something on the hardware is definitely balking.

Why don't you try burning it to a cd/dvd anyway?  Your old four-year old cd copy may have problems of its own.

Yeah I'm thinking it definitely has something to do with my hardware. I haven't tried burning it to a cd because I don't have any right now but I will get some probably tomorrow. I doubt my old cd has any problems because I just installed it onto my old desktop.

---

### Post by critin on 2012-09-27
> **Trackaholics said:**
> Yeah I'm thinking it definitely has something to do with my hardware. I haven't tried burning it to a cd because I don't have any right now but I will get some probably tomorrow. I doubt my old cd has any problems because I just installed it onto my old desktop.

Well, that answers that then.  You do know that updates will be a problem on something that old?  I don't know if you can even find them anymore.

---

### Post by Trackaholics on 2012-09-27
> **critin said:**
> Well, that answers that then.  You do know that updates will be a problem on something that old?  I don't know if you can even find them anymore.

Yeah I thought I could just install 8.10 and upgrade to 12.04 haha

---

### Post by JKyleOKC on 2012-09-27
Since the 620 comes with Win7 and a 1-TB drive, the odds are very great that it's using the UEFI-gpt bootloading technique. This means that you cannot use a 32-bit version of Ubuntu, since only the 64-bit versions are compatible with UEFI and if you are dual-booting, both the Windows and Ubuntu systems must use the same bootloading technique. Otherwise, as you've found, it just won't work.

There's still a problem, though: the current installer program on the Live CD/USB often fails to detect that the system is using UEFI, and still installs the wrong kind of bootloader. Read the page at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) to find out how to force the proper outcome, and how to verify which bootloader is present in your system.

Download the 64-bit ISO file and burn it to either a CD or flash drive, follow the procedure in the help page I linked above, and you should find everything working properly. And the "try without installing" should then work, also.

---

### Post by Trackaholics on 2012-09-27
> **JKyleOKC said:**
> Since the 620 comes with Win7 and a 1-TB drive, the odds are very great that it's using the UEFI-gpt bootloading technique. This means that you cannot use a 32-bit version of Ubuntu, since only the 64-bit versions are compatible with UEFI and if you are dual-booting, both the Windows and Ubuntu systems must use the same bootloading technique. Otherwise, as you've found, it just won't work.

There's still a problem, though: the current installer program on the Live CD/USB often fails to detect that the system is using UEFI, and still installs the wrong kind of bootloader. Read the page at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) to find out how to force the proper outcome, and how to verify which bootloader is present in your system.

Download the 64-bit ISO file and burn it to either a CD or flash drive, follow the procedure in the help page I linked above, and you should find everything working properly. And the "try without installing" should then work, also.

I'm gonna try this. I'll let you know how it goes. Thanks for the reply!

---

