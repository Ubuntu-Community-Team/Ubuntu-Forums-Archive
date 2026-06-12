---
title: "Ubuntu 8.10 freezes on startup (before login)"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by skutterz on 2008-11-25
Hi all

I'm pretty new to Linux (used it off an on for a while, but never been that knowlegable about terminals and commands etc.), and I've just built myself a new desktop (see spec below). I was hoping to duel boot XP with Ubuntu (something I've done before), using Ubuntu as my main system and XP for those programs I couldn't run on Ubuntu. 

Anyway, XP installed ok, and I went to install Ubuntu 8.10 (64 bit desktop), but it hung on a plain, off white screen (with no mouse cursor) when I booted up the live CD, after the progress bar screen. I got past this by restarting and using the boot parameter 'acpi=off', got a message telling me it was running in low graphics mode: "(EE) RADEON(0): Acceleration initialization failed", and managed to install it ok (and left me with a working system). I then shut the machine down as it was getting late. However, when I booted it back up, I got the same off white screen. I figured this was for the same reason as with the live CD, and added the same boot parameter (temporarily) to Grub, but to no avail.

I thought this might have something to do with Ubuntu trying to use the wrong drivers for my graphics card, but when I tried to update them (from the command line, obtained through grubs recovery mode), it couldn't seem to see an internet connection (which is working, as XP can see it).

There seem to be a lot of other people out there with similar problems, but most of them seem different to mine in one way or another.
Any advice you can give me on this issue would be really appreciated, as I really want to switch to Ubuntu from Windows. I would try installing 8.04, but I really don't want to have to re-install XP again.

My system is:
	Mobo: Asus P5Q-E
	CPU: Intel Q6600 Duo Quad Core
	GPU: ATi Radeon HD 4870 1GB
	RAM: 4GB CAS 4 Corsair
	HDD: 1TB Samsung Spinpoint

Cheers,
Skutterz

---

### Post by rich.bradshaw on 2008-11-27
I'd guess that this is something to do with the graphics card and the 64 bit ness of everything.

You will have problems with using a 64bit system because there isn't a 64bit version of flash, and some ethernet/wireless controllers don't have 64bit drivers. Of course, you need 64 bit to address 4GB of ram.

I'd either try the 32bit version to see ...  Read moreif you get same problem, or boot in low-graphics mode and sort things out from there.

Another random idea might be to check your video memory in your bios - on my old PC I had to change a setting to do with AGP memory to make it higher. Don't know if this will apply for you, but you never know!

---

### Post by skutterz on 2008-11-28
Hey Rich, thanks for the reply.

I'm suprised to hear there isn't a 64 bit version of flash/ethernet since the hardware has been around quite a while now, and although admittedly 64 bit operating systems are fairly new, surely they're not much use to anyone if they can't use flash. Is it not possible to run 32 bit flash on a 64 bit OS?

I will give the 32bit system a try, but that would seem a shame to use permenantly, as like you say, some of my RAM will be wasted (and I really don't want to have to get Vista just to make the most of it). Also, someone told me that the 3Gb RAM that can be used with 32bit systems includes the Graphics card memory. Do you know if this is the case?.

Do you know if theres any way I can re-install Ubuntu without reformatting my whole drive? I've got XP on there too, and it'll be a hassle if I have to reinstall that too (including all the updates, firewall, virus scanner etc.).

Also, you suggest booting in low graphics mode - how do you do this manually? From what I've read, Ubuntu usually seems to do it automatically when it thinks needs to (which it did when I booted from the live CD), but I don't know how to force it to manually. I'd have thought this might help, since as far as I can tell, its the only difference from when it booted from the CD. Plus, once I'm into the system, I can then try different drivers for the card etc.

I've had a look in my bios for graphics card info (I was going to try and get it to use the onboard graphics temporarily, but I found my mobo doesnt have onboard graphics!), but I couldn't find much. I will have another look though.

Cheers again for your advice.

---

### Post by cariboo on 2008-11-28
If you start in recovery mode and drop to a root prompt, you can start networking by typing at the prompt:

```
dhclient eth0
```

assuming that eth0 is what you are using to connect to the netwrok. the previous poster must not have heard that there is a beta version of 64bit flash now available for Linux only.

There is really no reason to use 32bit in place of 64bit as most of the problems that the above poster mentioned have been addressed. The only time you may run into problems with drivers is if you are using bleeding edge hardware, and that probably won't be supported in 32bit either.

Have you tried  starting in recivery mode and using xfix to repair your vjdeo problem? If xfix works you should be able to get back to your desktop where you can load the propitiatory video drivers (restricted). Go to System-->Administration-->Hardware Drivers to load the drivers.

Jim

---

### Post by rich.bradshaw on 2008-11-30
Ah, I assumed that progress must have been made on flash/drivers for 64bit. I haven't actually got a 64bit system so don't have any first hand experience.

I was just suggesting the 32bit to try and isolate what the problem is - obviously if it's more effort than it's worth to install it then don't bother!

---

### Post by skutterz on 2009-01-25
Thanks both of you for your advice. I managed to get it sorted (mostly) in the end by installing the ati drivers from the shell after ativating my ethernet port. I still have a problem with video playback being flickery, which I've temporarily sorted out by disabling desktop effects, but I'll look into that in more detail when I have more time (been really busy recently).

For anyone else with the same problem, I'll write a more detailed report on what I did to fix it when I have the time.

---

