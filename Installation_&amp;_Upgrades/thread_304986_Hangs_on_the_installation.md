---
title: "Hangs on the installation"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by mazingaz on 2006-11-22
I have tried livecd and alt., install cd but it hang on the installation process.
After choosing the installation method it hang while looking for the devises.

I have 
amd 64 x2 4400
nvidea 258 6800xt sli 
1 gig ddr2 ram
2 sata drive
(1 10,000 rpm raptor, 2nd 7200 samsung)

any solutions?

---

### Post by taurus on 2006-11-22
How fast did you burn the ISO image anyway?  make sure you don't burn it faster than 4x if you can...

---

### Post by mazingaz on 2006-11-22
> **taurus said:**
> How fast did you burn the ISO image anyway?  make sure you don't burn it faster than 4x if you can...

Does it really matter?  I burnt the alt., installtion cd and desktop version at full burning speed and it didn't seem like had any problem. 

hmm I will try to burn them at 4x and give it try.

---

### Post by mazingaz on 2006-11-22
Burning @ 8x and stiill hangs while loading kernel.
I really have no idea why its is doing  this.

---

### Post by Bartender on 2006-11-22
I have a homebrew PC that runs W2K flawlessly day in and day out.  It hangs at "Detecting Hardware" with an Ubuntu LiveCD.  I tried PCLinuxOS and everything went fine.

---

### Post by futz on 2006-11-22
> **mazingaz]I have tried livecd and alt., install cd but it hang on the installation process.
After choosing the installation method it hang while looking for the devices.[/quote]
[QUOTE=Bartender said:**
> I have a homebrew PC that runs W2K flawlessly day in and day out.  It hangs at "Detecting Hardware" with an Ubuntu LiveCD.  I tried PCLinuxOS and everything went fine.
I wouldn't worry too too much about the burn speed thing. Bad burns are not super common these days, as long as your blank media is of decent quality.

What might help (has helped me) on a funky install is installer boot options like noprobe and/or nousb. There are other options too, like noapic and a bunch of others I can't remember. 

Try noprobe for that Detecting Hardware problem. Might not work, but it can't hurt to try it. All it costs is time.

I had one box where I couldn't install Dapper at all without the nousb option. With the option the install behaved perfectly. Only thing is, you can't use a usb keyboard during the install with that option. Just temporarily plug in a spare PS2 keyboard for the install. Once you've finished installing, unplug it and use your usb one again.

---

### Post by mazingaz on 2006-11-23
> **futz said:**
> I wouldn't worry too too much about the burn speed thing. Bad burns are not super common these days, as long as your blank media is of decent quality.

What might help (has helped me) on a funky install is installer boot options like noprobe and/or nousb. There are other options too, like noapic and a bunch of others I can't remember. 

Try noprobe for that Detecting Hardware problem. Might not work, but it can't hurt to try it. All it costs is time.

I had one box where I couldn't install Dapper at all without the nousb option. With the option the install behaved perfectly. Only thing is, you can't use a usb keyboard during the install with that option. Just temporarily plug in a spare PS2 keyboard for the install. Once you've finished installing, unplug it and use your usb one again.


Hmm.. what is the exact command for that?
just noprobe did not work.

---

### Post by cantormath on 2006-11-23
> **mazingaz said:**
> I have tried livecd and alt., install cd but it hang on the installation process.
After choosing the installation method it hang while looking for the devises.

I have 
amd 64 x2 4400
nvidea 258 6800xt sli 
1 gig ddr2 ram
2 sata drive
(1 10,000 rpm raptor, 2nd 7200 samsung)

any solutions?

Are you using the AMD 64 version of ubuntu?

Have you tried the alternative cd(for AMD 64)?

---

### Post by mazingaz on 2006-11-23
i am using alt-installation cd image.
I just noticed this, during kernel boot it is searching for the floppy drive when I don't even have the floppy.  How do I disable searching for the the floppy drive? is it hw-detect/floppy=false?

---

### Post by futz on 2006-11-23
> **mazingaz said:**
> Hmm.. what is the exact command for that?
just noprobe did not work.
Assuming you are using the alternate install disk, at the first menu you first select the install type of your choice, but don't hit Enter yet. Then hit F6 to see the command line for that install. Add a space delimiter and the option(s) to the end of the line before hitting Enter.

---

### Post by mazingaz on 2006-11-24
No good still hangs at the kernel loading.
It is looking for the Fb0 when I don't even have floppy.
What is the exact command for the skipping floppy drive at booting kernel?
:( :( :(

---

### Post by mazingaz on 2006-11-27
Does anyone has the solution to this prob???

---

### Post by Asmodision on 2006-11-27
Have to disabled the floppy in BIOS?

Had the exact same problem with an old mandrake inst. helped to disable the floppy...

---

### Post by Jamie Jackson on 2006-11-27
FWIW, on my older laptop, no CD/DVD installs would work. The CDROM drive just didn't like any of them, and I also didn't get anywhere with boot options.

The installer CDs have a "validate cd" or some similar option which will check the integrity of the CD, that might give a clue as to whether it's a CDROM problem, but it could also give a false negative if it passes.

On that machine I ended up going with a network (Internet) installation, which took a while, but went well. I can't find the directions for it, but I thought it was listed under [advanced]("https://help.ubuntu.com/community/Installation#head-e87f88f2cc723e9cfbd1ce8698de949d31004d2c") installation options. I don't see it anymore, but maybe someone has a link.

UPDATE: I found the [link]("https://help.ubuntu.com/community/Installation/FromWindows"), but now remember that I got things started via Windows. Don't know if this applies to you or if you can adapt it...

Thanks,
Jamie

---

