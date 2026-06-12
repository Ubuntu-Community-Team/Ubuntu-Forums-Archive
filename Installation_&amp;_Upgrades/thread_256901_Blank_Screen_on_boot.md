---
title: "Blank Screen on boot"
date: 2006-09-13
forum: Installation &amp; Upgrades
---

### Post by milans on 2006-09-13
Hello,

Windows user, experienced developer, trying to build linux skills.

Using Ubuntu disk 6.0.6, I boot my PC - after splash screen, the monitor just goes blank. I have tried two different monitors - a Dell 19" LCD and a Sony Trinitron 17" CRT. On the Sony, the power light starts blinking. Also, the keyboard doesn't seem to have been recognized - I have tried a couple. I see from the other threads that I should see some Function key descriptions at the bottom of the screen. 

Video card is a Number Nine S3 Trio/64.

The machine has Windows XP running fine on it.

Incidentally, Knoppix LiveCD and Red Hat Enterprise 3 have the same problem with the screen going blank - the saving grace is that the keyboard seems to work.

I have dug for 2 days now, and while I see lots of threads talking about similar sounding problems, I haven't yet seen a resolution. 

Thanks in advance for any help you can provide.

Milan

---

### Post by orb9220 on 2006-09-13
Try booting with second option safe graphics mode. If that still fails then it is most likely your video card not supported.

Search forum on vga option on boot maybe a workaround.
Sorry don't have forum links myself.

---

### Post by milans on 2006-09-14
> **orb9220 said:**
> Try booting with second option safe graphics mode. If that still fails then it is most likely your video card not supported.

Search forum on vga option on boot maybe a workaround.
Sorry don't have forum links myself.

Thanks - I searched the forum. As far as I could tell, I was supposed to download the alternate CD. I did that, and it has the same problem - no keyboard control during splash screen, and then the monitor just goes blank from there.

The one bit of good news is that I downloaded damnsmalllinux (DSL), which booted beautifully. I am thinking that the next step for me is to figure out how DSL configures the video system, and then somehow duplicate the config on a normal install. Of course, I have no idea how exactly to do this. 

Again, any pointers would be great.

Milan

---

### Post by K.Mandla on 2006-09-14
I don't know if this would work, but you could install a server (which is an option on the alternate/install CD), and try to duplicate the DSL configuration that way. But as I understand you, you're losing video immediately after booting the disc ... ?

Also, any chance you have an onboard video port that's claiming the signal, and ignoring the S3 card?

---

### Post by d-train3054 on 2006-09-14
By chance is that a USB keyboard or any other USB devices plugged in. I posted this as a response to another thread but not sure if it's related.

"Check to make sure you don't have any USB storage devices plugged in to the computer (flash drive, ext hard drive, or other USB device). Sometimes during the boot process the computer waits for responses from those devices but never gets one."

---

### Post by milans on 2006-09-14
> **K.Mandla said:**
> I don't know if this would work, but you could install a server (which is an option on the alternate/install CD), and try to duplicate the DSL configuration that way. But as I understand you, you're losing video immediately after booting the disc ... ?

Also, any chance you have an onboard video port that's claiming the signal, and ignoring the S3 card?

Thanks for the response. As you point out, I never get keyboard control, even to try and select a non-default option from the splash screen. 

My MB doesn't have onboard video, however, it does have an AGP slot but my video card is a PCI card.

Regards,

Milan

---

### Post by milans on 2006-09-14
> **d-train3054 said:**
> By chance is that a USB keyboard or any other USB devices plugged in. I posted this as a response to another thread but not sure if it's related.

"Check to make sure you don't have any USB storage devices plugged in to the computer (flash drive, ext hard drive, or other USB device). Sometimes during the boot process the computer waits for responses from those devices but never gets one."

Standard, not USB, keyboard and mouse. I don't have anything plugged into the USB port.

Milan

---

### Post by mdb444 on 2006-09-16
I am having the same problem.  Frustrated.

Its an old Compaq box that I thought I'd flip to Linux just to check it out.  I have a decent knowledge of Windows, but can't get anywhere with Ubuntu.  After the boot lists all processes as OK, I get a blank screen and the monitor goes to standby instantly.  Ctrl+Alt+F1 will get the monitor out of standby and get me a text login, and I can login.  Someone suggested to try apt-get update.  I did, but that fails to execute properly.  (I get several security errors and other sundry failure notices.)  Ctrl+Alt+Bkspace will turn the monitor back on for a split second, but then it goes to standby again.  So I'm stuck.  Please help me escape from Windows!

900 MHz P III
128MB RAM (I installed with an alt-i386 downloaded CD)
S3 Vid Card

Thanks for any help,
mdb

---

### Post by skutterdan on 2006-09-19
It sounds like a very similar problem to what i had when booting from the  live cd. It seems the problem, (well for me at least),  is that your xorg.conf file is set with the wrong frequencys for the monitor. Thats why  your monitor keeps switching off. I've only ever had this problem with Ubuntu.  

Do a search for "**     Blank Screen on LiveCD"** on these forums. I have put how i solved this problem in that thread. Hope it is of some help. 

Or alternitvely [http://www.ubuntuforums.org/showthread.php?t=259575&highlight=Blank+Screen+LiveCD](http://www.ubuntuforums.org/showthread.php?t=259575&highlight=Blank+Screen+LiveCD)

---

