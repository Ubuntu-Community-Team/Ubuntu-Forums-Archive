---
title: "Such bad luck..."
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by davidpm0 on 2008-04-26
So let me preface this with the background necessary so you aren't wondering WHY i'm doing what I'm doing. 

I accidentally dropped my VISTA powered laptop a few days ago.  I'm pretty sure that I busted up the hard drive as it now tells me that it can't detect an operating system nor the hard drive itself.  So i figured I'd use an external USB hard drive as a temporary fix.  I figured I'd install Ubuntu onto it and use it as my primary hard drive until I can get a replacement for the one I busted.  

So I pop in the Ubuntu installation CD and I don't get the normal load up like I did for my PC (more on that in a second)  It starts telling me about various SRST error (Error: -19) and then proceeds through initializing various components before it freezes up and the CD ROM just stops spinning and the installation ends there.**  That's my problem number 1.**

So I decide that I'll use my desktop PC to load the operating system onto the external hard drive.  I plug it in, the installation works beautifully,  and I restart my PC.  Now my PC is giving me a GRUB error 21 and stops there without loading anything.  Usually it would load to the Ubuntu boot menu and ask if I wanted to load Ubunutu or Windows XP (which exist on separate Hard drives in my PC).  I can only get into my PC now by using the installation boot up disc to run it off the CD.  **That's my problem 2**

Finally, I plug my USB external drive into my laptop and I get an MBR error 3 followed by MBR error 1, then "Please enter a floppy disc" MBR error 2 which repeats when I press any key.  **That's my problem 3**

I'm in a world of hurt here.  If anyone can help me out with any of these problems, I'd greatly appreciate it.  Thanks!

D

---

### Post by davidpm0 on 2008-04-26
I kind of figured out one of my problems.  The second problem with the PC giving the GRUB error 21 does not happen when the USB drive is connected to my PC.  It is looking for this to load the boot menu and is giving the error message when it can't find it.  How can I make it so that this drive is not set as the default location to search for this menu?

---

### Post by obidose on 2008-04-26
There are 2 parts of the Grub from what I gather. One is on the bios and the other is saved on the hard disk /boot/grub
By removing your hard disk from the pc you prevent it accessing /boot/grub so it has no info of the OS's available
On the other hand the laptop does not have the bios component to start grub.

I am not very experienced in this matter but that is what I think is happening.

I believe that running super grub cd would help on the pc and maybe the laptop.
On the pc also you could use easyBCD to restore the vista bootloader and also set it up to dual boot ubuntu and vista using that.

---

### Post by davidpm0 on 2008-04-26
Ok, Super Grub has helped me get my PC up and running again.  It auto loads into XP again  Thanks for that.

Also, I am pretty sure that my laptop will not run the version of Ubuntu that is on the external drive because it wasn't installed via the laptop.  All of the directories that are written for loading are unknown because they were written on the PC.  This makes sense.

So the only issue that I have now is that when I put the installation CD into my laptop, I get the following error message:

[ 48.088000] ata1: SRST failed (errno=-19)

this repeats but with different numbers at the start (ie 58.092000)

this happens 5 times followed by two
[191.268000] sd 2:0:0:0: [sda] Asuuming drive cache: write through

then there are 3 more of the original SRST message then it takes me to a command prompt (initramfs)

Is it possible to load Ubunutu to run on the external USB drive on a laptop that currently has no other detected hard drive?

Thanks!

---

### Post by obidose on 2008-04-26
I think it should be possible, but form what i gather you can't get the live CD up and running. Making it difficult to install.

Perhaps the boot order in your laptop is ignoring the cd and proceeding to try and boot from the hard disk. Make sure your primary boot device is set as the CD drive in your bios settings.

Access bios settings usually by pressing del at start up.

---

### Post by davidpm0 on 2008-04-26
Actually, it loads up to the start up menu where i can select what i would like to do (ie start or install ubuntu, start ubunutu in safe graphics mode, etc) then when I select start or install Ubunutu, it "loads linux kernal, then a quick line comes up that "BIOS BUG #83" exists then it goes to the Ubuntu loading screen with the bar moving back and forth...

After that it goes to the SRST error messages.  On my PC it just loaded to the desktop off the CD so I could install onto the hard drive.

---

### Post by obidose on 2008-04-26
It is beyond my understanding then. The only thing I could think of (and this is just pure unfounded speculation) is that maybe the cd sees the hard disk but when it tries to load it failure follows.

I would try to disable or unplug the internal hard drive to test the theory out, but I do not actually know much about it and someone else will probably give you a better solution/answer.

Good luck.

---

### Post by davidpm0 on 2008-04-26
somewhat new update.

I took out the faulty hard drive and just tried to get the CD to boot up with no hard drive.  I didn't get the SRST error messages anymore.  After I hit enter on the installation screen to "Load or Install UBUNTU", it took me to a terminal like screen where it stated what it was loading and said "OK" then it went to a weird screen that looked like fog rolling in from the edges of the screen slowly and I couldn't get it to do anything else.  Any idea what that means?

---

### Post by davidpm0 on 2008-04-26
bump

help please

---

