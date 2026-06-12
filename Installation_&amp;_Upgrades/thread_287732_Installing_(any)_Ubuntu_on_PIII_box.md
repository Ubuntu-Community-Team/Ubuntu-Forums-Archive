---
title: "Installing (any) Ubuntu on PIII box"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by NT4usB on 2006-10-29
So, after a successful first attempt at building a Linux box, I dug an old PIII 550 SE440BX (.P17 bios) 768mb ram and am trying to install Ubuntu on it.
Tried: xubuntu-6.10-desktop-i386, xubuntu-6.10-alternate-i386, 6.06 LTS Dapper Drake, and 5.10. 
They all get to the part about detecting the cdrom and the install stops installing at "Loading module 'ide-cd' for 'linux ATAPI CD-ROM'" (always at 86%.) 
Googled around and found lots of similar troubles with some fixes but none have worked... pci=noacpi, acpi=noirq, acpi=off, noapic nolapic, hdc=noprobe hdc=cdrom, hw-detect/start_pcmcia=false, etc. 
The box was running with NT4 on it. Put 2K on it and it worked fine.
Swapped out the cdrom with another (known working) drive. The install finds it in the very beginning and even gets the name right... LTC-48161H.
One attempt with the 5.10 disk worked but I jacked the partitioning and after starting over, I haven't got that far since.
The easy solution is put 2K back on it but I'd rather use Ubuntu.
Any other suggestions on how to get passed the cdrom problem?

ed: The final fix:
 Pulling the cards allowed me to install but soon as I put them back in, it locked up.
The problem was in the bios config. The ports were set to 'Standard' or something so it's allocating resources during post and leaving nothing for the hardware.
Changing them to 'Auto' holds off on assigning resources until the hardware requests it. Works good now.

---

### Post by gn2 on 2006-10-29
> **NT4usB said:**
> So, after a successful first attempt at building a Linux box, I dug an old PIII 550 SE440BX (.P17 bios) 768mb ram and am trying to install Ubuntu on it.
Tried: xubuntu-6.10-desktop-i386, xubuntu-6.10-alternate-i386, 6.06 LTS Dapper Drake, and 5.10. 
They all get to the part about detecting the cdrom and the install stops installing at "Loading module 'ide-cd' for 'linux ATAPI CD-ROM'" (always at 86%.) 
Googled around and found lots of similar troubles with some fixes but none have worked... pci=noacpi, acpi=noirq, acpi=off, noapic nolapic, hdc=noprobe hdc=cdrom, hw-detect/start_pcmcia=false, etc. 
The box was running with NT4 on it. Put 2K on it and it worked fine.
Swapped out the cdrom with another (known working) drive. The install finds it in the very beginning and even gets the name right... LTC-48161H.
One attempt with the 5.10 disk worked but I jacked the partitioning and after starting over, I haven't got that far since.
The easy solution is put 2K back on it but I'd rather use Ubuntu.
Any other suggestions on how to get passed the cdrom problem?

If the 5.10 install disc can give you a working installed system, you can upgrade  to 6.06 on-line using the Software Updater, then add Xubuntu-desktop via Synaptic.

That's how I got my P3 500 192mb RAM Portege 3440CT laptop sorted.

6.10 is out, but for me it's too soon yet......

---

### Post by Craigus on 2006-10-29
This could be a RAM problem - have you tried running memtest86+ on the box?

---

### Post by markusf21 on 2006-10-29
I am having almost the same problem with 6.10 My cd is detected fine but it freezes on the floppy.

---

### Post by markusf21 on 2006-10-29
I decided to just unhook the floppy drive and tried again.
Seems to be working now.

---

### Post by dbott67 on 2006-10-29
The other thing to try is to re-burn the image at a slower speed (less than 8x).  My first foray into Ubuntu was with a Warty CD burned at 48x and it kept giving me problems.  I re-burned at 4x and it went beautifully.

At present, I've got Dapper w/ Gnome installed on 3 computers:
- Pentium 2-300 MHz with 256 MB RAM (works great, albeit a little sluggish)
- P4-1.8 GHz - runs great
- Intel Core Duo T2400 - runs great

---

### Post by NT4usB on 2006-10-29
> **dbott67 said:**
> The other thing to try is to re-burn the image at a slower speed (less than 8x)...

The 5.10 and 6.06 disks both worked fine when I build the first system.

ed: Recalling other posts about burn speed causing problems, I originally burned the 6.10 at 8x.
I'll try one at 4x and see what happens...

---

### Post by NT4usB on 2006-10-29
> **Craigus said:**
> This could be a RAM problem - have you tried running memtest86+ on the box?
I ran memtest for a half hour or so. Got bored watching it run. Didn't find any problems before I quit it.
How long does it take to finish?

---

### Post by NT4usB on 2006-10-29
> **markusf21 said:**
> I decided to just unhook the floppy drive and tried again.
Seems to be working now.
I thought about that old Windows trick of pulling all the cards and unplugging everything not vital to the system to try to get through the install but that seemed so *windowish* (and a lot of bother.*g*)

---

### Post by NT4usB on 2006-10-29
> **gn2 said:**
> If the 5.10 install disc can give you a working installed system, you can upgrade  to 6.06 on-line using the Software Updater, then add Xubuntu-desktop via Synaptic.

That's how I got my P3 500 192mb RAM Portege 3440CT laptop sorted.

6.10 is out, but for me it's too soon yet......

**If** I could get it to go again, I'd be in fat city. Just wish I could remember which combination of those obscure command line switches I used that got it to run the first time.*g*

---

### Post by Craigus on 2006-10-29
> I ran memtest for a half hour or so. Got bored watching it run. Didn't find any problems before I quit it.
How long does it take to finish?

It loops forever - basically if it gets through all 8 tests without any errors, all is probably OK. I generally leave it go overnight, just to be sure.

---

### Post by NT4usB on 2006-10-30
The fix was to pull all the cards except the nic and video, and unplug the floppy. (Creative sb live, motorolla modem, avermedia tuner.)
I'm guessing the sb live was fscking with the interrupts...

ed: now to see what happens when I put the cards back in.

---

