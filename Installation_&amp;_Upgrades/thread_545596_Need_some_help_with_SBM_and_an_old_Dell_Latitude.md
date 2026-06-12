---
title: "Need some help with SBM and an old Dell Latitude"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by ltcarter47 on 2007-09-07
Hi, 

I'm trying to get Ubuntu(or Xubuntu) onto a Pentium 133 Dell Latitude. The BIOS will only allow booting to a floppy, so I have that attached externally with a serial cable(I think it's serial, it works in any case...). I have tried to follow the instructions from linux.simple.be/tools/sbm, but the disk I get ends up not working. The Dell immediately says "SBMK Bad!".

Any thoughts?

Thanks,
LtCarter47


PS, I'm very new to Linux, this is my first attempt at installing it on anything other than a modern PC that boots and runs the live CD without issue.

---

### Post by K.Mandla on 2007-09-07
I used SBM a couple of times, and followed the wiki instructions here.

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

Are there settings in the BIOS for boot sequence, etc.? Usually when I used SBM I had to refresh the boot list a couple of times before the CDROM would appear. I don't know if that helps at all. :-k

And by the way, both Ubuntu and Xubuntu are going to run dog-slow on that. Were you planning on using the full desktop, or just install a minimal environment? The latter would be a better idea.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by ltcarter47 on 2007-09-07
I did go through that page the first time someone told me about SMB, but I got confused at this part:

Then use rawrite command: rawrite -f sbm.bin (rawwritewin.exe sbm.bin)

Is this a command that is typed into the command line?  I ended up just opening rawrite and using the program's interface to make the disk, and maybe that's not the right way to do it.  I got the same error...

---

### Post by ltcarter47 on 2007-09-07
> **K.Mandla said:**
> And by the way, both Ubuntu and Xubuntu are going to run dog-slow on that. Were you planning on using the full desktop, or just install a minimal environment? The latter would be a better idea.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Hmm...Just noticed this part.  This machine originally ran windows 95 and eventually 98.  I thought maybe linux would be a better choice as far as speed when I set about making it useful again.  I don't know anything about the minimal environment.  would that be a text based thing?  Maybe it's just time for it to be retired.

---

### Post by Pumalite on 2007-09-07
You can make Linux run on a dime if you apply yourself. You were given an excellent link. Just don't give up so easily.

---

### Post by K.Mandla on 2007-09-08
> **ltcarter47 said:**
> Hmm...Just noticed this part.  This machine originally ran windows 95 and eventually 98.  I thought maybe linux would be a better choice as far as speed when I set about making it useful again.  I don't know anything about the minimal environment.  would that be a text based thing?  Maybe it's just time for it to be retired.
Not necessarily. Installation would definitely be text-based, but what you add to it after that is up to you.

On a machine that old, Ubuntu is going to be a little sluggish. That's not anyone's fault, it's just the nature of the OS and the hardware; in conjunction, they're a bit slow.

I did the same trick about a year ago on a [120Mhz]("http://ubuntuforums.org/showthread.php?t=259901") machine and then on a [75Mhz]("http://ubuntuforums.org/showthread.php?t=294292") machine. They're both completely usable systems, but you have to be very, very picky about what you install. Even now, with a year's experience, I would never tackle those machines the same way. 

However, if you're conservative and you know what you want out of it, you can definitely make it work under Ubuntu. In retrospect, I would choose a version of Linux that's a little lighter, but Ubuntu is a good starting point. Don't retire it! It still has life in it!

---

### Post by logos34 on 2007-09-08
> **ltcarter47 said:**
> I did go through that page the first time someone told me about SMB, but I got confused at this part:

Then use rawrite command: rawrite -f sbm.bin (rawwritewin.exe sbm.bin)

Is this a command that is typed into the command line?  I ended up just opening rawrite and using the program's interface to make the disk, and maybe that's not the right way to do it.  I got the same error...

Open the Run box and type **cmd**.  This brings up the DOS window.  Enter the rawwrite command at the prompt.

If you still get the error, try making the SBM floppy the linux way.

Boot the ubuntu live cd, insert the floppy, then open a terminal (menu>accessories>terminal) and type:

> [B]sudo mke2fs /dev/fd0
dd if=/cdrom/install/sbm.bin of=/dev/fd0[/B]

---

### Post by logos34 on 2007-09-08
> **K.Mandla said:**
> However, if you're conservative and you know what you want out of it, you can definitely make it work under Ubuntu. In retrospect, I would choose a version of Linux that's a little lighter, but Ubuntu is a good starting point. Don't retire it! It still has life in it!

Maybe the itcarter47 shoould consider DSL, Puppy or even Deli linux?  Those are almost guaranteed to work on legacy hardware.

K. Mandla,

I read your second link...Very entertaining!.  About this part:
> 
"P.P.S.: I think this is about the bottom of the barrel for me. It's getting amazingly hard to find a working, complete system that predates this generation. Perhaps if you have an old 66Mhz Packard-Bell 486DX in the garage you can give it a try, but for myself, I'm out."

Hah! I have exactly that! Well, *had*, and not exactly the same but awfully close: a 66MHz 486SX Compaq Presario loaded up with a whopping 53MHz RAM and 3.8GB hard drive!  1994 vintage.  I could still surf the web dialup until 2005 (printer-friendly pages only)!  Alas, the monitor was giving out and it was forever locking up on me (dying PSU probably), so finally had to throw it out.  The thing was so old it had no USB ports, no RJ-45, just 2 isa slots.  But I wish I had kept it for a while longer if only to try Deli linux on it.  It might have worked (Deli claims to be able to run on 16mb ram i think).

---

### Post by K.Mandla on 2007-09-10
Excellent! Too bad it had to go. I know Deli supposedly can run on 16Mb, and DSL works on 486 machines (there are photos on their Web site) and there's Minix3 too, which will supposedly run on a 386 with 8Mb, if I remember right. 

I always keep my eyes open for old, throwaway machines because occasionally, there's something worth picking up in them.

---

