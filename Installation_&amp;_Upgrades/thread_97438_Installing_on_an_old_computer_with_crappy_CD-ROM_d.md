---
title: "Installing on an old computer with crappy CD-ROM drives"
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by BotBuilder on 2005-12-01
I'm new to ubuntu, although I've tried getting it working on the computer I'm using now (I believe what went wrong is a fatal mixture of AMD 3500+ x64 and an ati X700 (PCI-E), gnome wouldn't start).  Anyway, I'm trying to get a server running on this old comp that will never be used for anything else.

One CD-ROM drive used to work fine but now it's pretty intermittant so getting it working right as the computer starts up is a challenge.  the drive below it is a 'HP CD-writer-plus 9100 series".  I've tried to boot up with the boot disk in this drive, however I get this

(Amazing how hard it is to take a picture of a black screen)

The bios managed to boot to the CD but it appears to have some problems recognizng itself right after that. Or something.

Any ideas for solutions to this?  I could use a CD-ROM drive from another computer, however I'd rather look at other solutions before going to that, and perhaps having even that fail.

Thanks.

---

### Post by az on 2005-12-01
Well, if the drive is deffective, there is not much the OS can do.

You can try changing the DMA settings in BIOS (UDMA, DMA, PIO-mode) to the lowest setting (PIO) or none or auto (if that is not what is selected)

---

### Post by BotBuilder on 2005-12-01
I've verified that it's not actually the cd-rom drives.  I used a drive from another computer that was booting the ubuntu install just fine. Same error.  I've got it on the IDE master, and the Jumpers are set to cable select, so it shouldn't matter.  The BIOS recognizes the drive fine - everything, in fact you know its reading something as it starts up "ISOLINUX" but then i get the same error as above.

Any ideas?

I've disconnected all drives except the good one and the hard drive.

I could start yanking out cards but I doubt it would make a difference.

BIOS has no DMA settings, its pretty primitive.  Basically just some password settings, boot preference settings, time settings, power saving, and that's about it.

Note, this isn't an upgrade.  It's a install on a comp that has win98 on the hard drive.

---

### Post by BotBuilder on 2005-12-02
Ok, i've solved it by connecting the hard drive to my good computer and installing on to it.  So now I'm having problems booting up linux off the hard drive.  Probably closely related to the problems here.

i've uploaded two screenshots, the first is the one that matters, the second one is an interesting error i got on first install attempt (the second install worked fine).

I've disconnected all the cd drives, and the zip drive.  All that is connected is the empty floppy drive and the 4gb hard drive.  Oh, and I'm booting in recovery mode with the additional arguments "ro noacpi quiet"

alt-f2 does nothing, and apt-get doesn't work.

Thanks for any help.

---

### Post by bwog on 2005-12-02
Can you install over (local) network from your new computer? (with the hard disk in the old computer). See the Wiki eg [https://wiki.ubuntu.com/Installation/WindowsServerNetboot?highlight=%28PXE%29%7C%28Netboot%29](https://wiki.ubuntu.com/Installation/WindowsServerNetboot?highlight=%28PXE%29%7C%28Netboot%29)

---

### Post by teaker1s on 2005-12-02
before condeming a drive many people don't realise there are firmware updates-take my dvd writer it has regular updates as and when the company find a media the drive dislikes or should the dvd standards change.

Same with cd rom and cdrw If it causes problems clean the laser with a cotton wool bud or photograpic lense cleaner and look for firmware before you bin it- very old cd drives before cdr's were popular suffer this majorly if the cdr is much off silver in colour

---

### Post by KermitJr on 2005-12-02
I'm a bit confused, but you mean you are using a 3500+ system and this error is on an older machine? (not the 3500+).  What are some of the specs with the old machine?

I had this error a few times on older machines and a bios upgrade fixed about 80% of them.

---

### Post by BotBuilder on 2005-12-02
> I'm a bit confused, but you mean you are using a 3500+ system and this error is on an older machine? (not the 3500+). What are some of the specs with the old machine?Yeah, my good computer is the 3500+ The old computer is an old dell XPS 200mhz pentium 1, 64mb ram comp.  The hard drive is 4gb.

> before condeming a drive many people don't realise there are firmware updates-take my dvd writer it has regular updates as and when the company find a media the drive dislikes or should the dvd standards change.Thanks, I'll keep that in mind in case I manage to fix this problem/ get new mobo/cpu/ram.

> Can you install over (local) network from your new computer? (with the hard disk in the old computer). See the Wiki eg [https://wiki.ubuntu.com/Installation...28Netb](https://wiki.ubuntu.com/Installation...28Netb) oot%29Should I try? I've got ubuntu on there now.  It just doesn't want to run.

---

### Post by mpsii on 2005-12-02
Some of the older dell (and compaq) systems hated the Cable Select feature for hard drives and/or CDROM drives. I would suggest that you set the jumper on the drive to match where it is in the chain. 

Also, if you have two connectors on your IDE cable, make sure that the position on the cable matches the jumper setting on the drive. For example, jumper set to master, plug the drive into the middle connector on the cable. Also, remember that the cable has an end intended to go into the motherboard (the plug all by itself).

---

### Post by bwog on 2005-12-02
[QUOTE=mpsii]Also, if you have two connectors on your IDE cable, make sure that the position on the cable matches the jumper setting on the drive. For example, jumper set to master, plug the drive into the middle connector on the cable. Also, remember that the cable has an end intended to go into the motherboard (the plug all by itself).[/QUOTE]

Are you sure about that. I am reading from the installation sheet from (Maxtor Diamondmax UDMA66), which says that the master should go to the end of an 80 cable.

---

### Post by BotBuilder on 2005-12-02
Yeah, the end of the cable is master, middle is slave.  Thanks for the advice though.

I got it working!

I realized there are 3 useless cards sitting in the PCI slots - modem, some SCSI card for a scanner, and a sound card.  After taking them out it finally worked.  No idea what the problem was - clearly something it couldn't just ignore.

Now I've just got to get putty on my windows PCs and setup ssh to start up on boot or something.

Admins - mark this topic SOLVED!

---

### Post by bwog on 2005-12-03
Great that you found a solution, good detective work.

I think that you can edit the title when you select the first post.

---

### Post by vampire_janus on 2005-12-03
guys, is it possible to install from iso image (if the cdrom is defective)? if so, please let me know how?

---

### Post by bwog on 2005-12-03
@vampirejanus; Some users install from hard disk. Someone recommended buying a CDplayer, and that is good advice too.

---

### Post by az on 2005-12-03
[QUOTE=BotBuilder]Y
Now I've just got to get putty on my windows PCs and setup ssh to start up on boot or something.
[/QUOTE]

sudo apt-get install ssh

or install ssh using synaptic.

---

### Post by vampire_janus on 2005-12-04
if you need to install from iso, maybe this thread can help
[http://ubuntuforums.org/showthread.php?t=98451](http://ubuntuforums.org/showthread.php?t=98451)

---

