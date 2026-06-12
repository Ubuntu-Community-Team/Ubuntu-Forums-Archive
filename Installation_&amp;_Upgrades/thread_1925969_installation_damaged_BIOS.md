---
title: "installation damaged BIOS"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by canucksailor on 2012-02-15
Acer Travelmate 620 (PIII, 256 RAM, 20Gb hdd - yes, it's old, that's why I tried Lubuntu) I started install from ISO CD lubuntu-11.10-desktop-i386.iso -- clean install, reformatted to 6Gb / , 2 Gb swap, 12 Gb home, all ext4.  It was still copying files (from CD, but LAN cable with internet access was plugged in as requested during set up) and status bar at about 75% when it suddenly shut down - no apparent reason, no warnings, I was actually watching the screen.

Tried rebooting.  It won't even get as far as BIOS or Acer splash screen - computer appears dead.  Fan goes on, blank screen, 4 beeps, power and fan go off.  I've done all the "reset power" operations (remove cord and battery, hold power switch 30 secs, replace battery) with no success.

Acer tech help useless ("out of warranty" yup, it is) and won't tell me what 4 beeps means.  I can't believe that this is a hardware failure, too much of a coincidence that it happened during an installation "crash".

Help, suggestions warmly welcomed - many thanks.

---

### Post by Mark Phelps on 2012-02-15
If if it HAD worked, you experience trying to use 11.10 on a P3 256MB PC is going to be abysmal.  

You would much better, with that underpowered a PC, trying something less resource-demanding like Lubuntu.

And, what could have happened, since recent Ubuntu kernels have a known bug that contributed to laptops overheating, is that your attempt to install 11.10 overtaxed the PC resources, driving the demand up so hign that it overheated and crashed.

---

### Post by canucksailor on 2012-02-15
> **Mark Phelps said:**
> If if it HAD worked, you experience trying to use 11.10 on a P3 256MB PC is going to be abysmal.  

You would much better, with that underpowered a PC, trying something less resource-demanding like Lubuntu.

I agree :)  Please read my post, I was installing Lubuntu, with an "L".

---

### Post by coldraven on 2012-02-15
I got this from here: [http://www.pchell.com/hardware/beepcodes.shtml](http://www.pchell.com/hardware/beepcodes.shtml)

It says that fix for 4 beeps is much the same as 2 beeps.
>  Your computer has memory problems. First check video. If video is working, you'll see an error message. If not, you have a parity error in your first 64K of memory. First check your SIMM's. Reseat them and reboot. If this doesn't do it, the memory chips may be bad. You can try switching the first and second banks memory chips. First banks are the memory banks that your CPU finds its first 64K of base memory in. You'll need to consult your manual to see which bank is first. If all your memory tests good, you probably need to buy another motherboard.

---

### Post by drmrgd on 2012-02-15
I'm not sure that I agree that the install damaged your BIOS.  It's more likely that you had a hardware failure during the install, and the beep codes are telling you something.  Could be any number of things, but I would guess memory.

Actually, I may have to take that back.  Check this out here...page 69.

[http://tim.id.au/laptops/acer/travelmate%20620.pdf](http://tim.id.au/laptops/acer/travelmate%20620.pdf)

>  Battery critical LOW
In this situation BIOS will issue 4 short beeps then shut down 
system. No message will show\


Does this seem likely / relevant?

---

### Post by canucksailor on 2012-02-15
[drmrgd]("http://ubuntuforums.org/member.php?u=1288128") suggested battery; thanks, I'll double check, but voltage is showing 14.6v with the "charge pins" shorted, and it was at 100% charge before I deleted WinXP this morning. The battery is only a couple of months old and I'm operating with a good power adapter plugged in.  Also, trying an external DVD player on USB, there's enough voltage to open/close the tray multiple times quite normally during the few seconds while the machine is beeping.

As to memory suggested by [coldraven]("http://ubuntuforums.org/member.php?u=993657"), this is **perhaps** more likely.  Before I started the Lubuntu install, I used the "Memory check" utility that comes with the ISO install (seemed like a good idea.)  Since then I've been told that some "new" mem checks are not good for older 133 SODIMM memories.  No way of checking apart from replacing ...

Maybe??? I'm out of pocket $32.99 plus postage -- but at least I can probably upgrade from 256 to 512 for the same price.  And all my other Ubuntu machines are running great - two servers and three desktops :)

---

### Post by canucksailor on 2012-02-16
New memory was needed.  I still don't know if it was pure coincidence that it failed during installation, or whether the memory check utility that comes with the .iso had anything to do with it.

Anyway, Lubuntu 11.10 now up and running.

Thanks to all who responded.  Now, I've got to find the way to mark [SOLVED].

---

