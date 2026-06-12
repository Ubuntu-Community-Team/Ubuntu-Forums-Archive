---
title: "Hardy runs extremely slow..help!"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by Em-Buntu on 2008-05-04
I've run Feisty Fawn on the same system and it ran very well.
My system is an ASUS K8N-DL with dual core Opteron, 4 GB SDRAM, 400GB SATA (Windows XP-64), 20 GB PATA (Ubuntu), ATI graphics.

When Hardy was released I performed the online update. Once the update was complete I noticed an ususally large amout of disk trashing, and applications (Firefox, Evolution, and tools) seemed to take excessively long time to start.
Finally, the system crashed wiping out the system.

I decided to download the Hardy AMD64 ISO and burn to CD to do a clean install.
After wiping and formating the disk (20GB ATA100 MATXTOR) I reinstalled Hardy onto the clean disk using the CD ISO. The CD was good, I checked with the Hardy image verify tool.

During the install, I encountered Blackbox error, and used F6, all_generic_ide floppy=off irqpoll command. This worked and the system install completed.

Now when I start boot the system, it takes approx. 10 minutes from grub to completing the install.
Once running, if I start Firefox it takes approx. 5 minutes before Firefox appears.
If I start Evolution, it takes approx. 5 minutes before it starts.
During this time, there is a tremendous amount of disk activity and trashing.

Feisty ran well on the exact same system.
Hardy runs like crap and is virtually unusable.
Does anyone here have an idea of what could be causing this?

---

### Post by Pumalite on 2008-05-04
I suggest you take off 'quiet splash' from your menu.lst and take a look at dmesg to see what going on. I have Hardy 32 bit and 64 bit on an Intel D975XBX Core 2 Duo with 2 GB of RAM and they are both a flash.

---

### Post by Em-Buntu on 2008-05-04
> **Pumalite said:**
> I suggest you take off 'quiet splash' from your menu.lst and take a look at dmesg to see what going on. I have Hardy 32 bit and 64 bit on an Intel D975XBX Core 2 Duo with 2 GB of RAM and they are both a flash.


Thanks for your reply.

There is no quiet splash in Menu.lst. It seems it installed without loading quiet splash, so I can see all the load commands.
This is terrible!
After booting, it stays at the Grub screen for about 45 secs.
Than it goes to the GUI screen with rectangle for 1 min.
Than it gets to the, "Reading files needed to boot" screen and stays there for about 11 minutes.
Than it starts loading processes for about 6 minutes before getting to the login screen.
After logging on, the GUI loads and the disk spins for about 4-5 minutes.
When it is up, it has some KDE errors and asks if I want to delete them. I answer ignore and it boots the rest of the way.
In all, it takes about 20 minutes before I have a usuable system, and still, it takes forever to run any app.

At this point I think I'm giving up on Hardy. It seems with each release, Ubuntu is getting more complex and less user friendly (consistent).
Many it's the new kernel, maybe it's the new KDE. Since Feisty was running just fine, chances are this terrible performance is related to teh Hardy release.
After the initial Gutsy->hardy upgrade, I lost a lot of data when it crashed and wiped the disk.

At this point, as much as I hate WIndows, I think I'll just stay with my Windows Xp-64. It only takes 2 minutes to load and use. :guitar:

---

### Post by revoltism on 2008-05-05
I had this problem with Feisty and now with Hardy. It is not as bad for me as for you but it take 5-10 min before i get to login screen. I did a alternate install to bypass the problem.
 
I overcome the problem with Feisty after i ordered a free CD from shipit. When i burnt the iso Festy boot was very slow but a clean install with the shipit cd no problem occurred.
 
I would really like why my home made CD get this problem and not the shipit CD. It would be swell. I think it has with either my hdd or dvd-rom. As i get the ata error in busybox.

---

### Post by Pumalite on 2008-05-05
> **Em-Buntu said:**
> Thanks for your reply.

There is no quiet splash in Menu.lst. It seems it installed without loading quiet splash, so I can see all the load commands.
This is terrible!
After booting, it stays at the Grub screen for about 45 secs.
Than it goes to the GUI screen with rectangle for 1 min.
Than it gets to the, "Reading files needed to boot" screen and stays there for about 11 minutes.
Than it starts loading processes for about 6 minutes before getting to the login screen.
After logging on, the GUI loads and the disk spins for about 4-5 minutes.
When it is up, it has some KDE errors and asks if I want to delete them. I answer ignore and it boots the rest of the way.
In all, it takes about 20 minutes before I have a usuable system, and still, it takes forever to run any app.

At this point I think I'm giving up on Hardy. It seems with each release, Ubuntu is getting more complex and less user friendly (consistent).
Many it's the new kernel, maybe it's the new KDE. Since Feisty was running just fine, chances are this terrible performance is related to teh Hardy release.
After the initial Feisty->hardy upgrade, I lost a lot of data when it crashed and wiped the disk.

At this point, as much as I hate WIndows, I think I'll just stay with my Windows Xp-64. It only takes 2 minutes to load and use. :guitar:

You are not giving Hardy a chance. Do a clean install at least.

---

### Post by Em-Buntu on 2008-05-05
> **Pumalite said:**
> You are not giving Hardy a chance. Do a clean install at least.

I've been attempting to use since it was in beta. I performed the online update from Gutsy to Hardy. It ran slow, then finally crashed wiping the system.

I downloaded the ISO and burnt to CD (twice) reformatted the hard drive and reinstalled. I performed this reformat/install twice. Once using the AMD 64 standard format, and once using the alternative CD. 
So far, I have A LOT of time and effort invested in attempting to get it to run reasonably and stable. So far, it's a no-go and unusable.
I may decide to switch out the 20GB hard drive I've been using and replace it with another.

Thanks for all the responses I've received so far. IMM, this is the best feature of Ubuntu, the community. :guitar:

---

### Post by Pumalite on 2008-05-05
I can assure you it's your hardware. I have 4. 2 32 bit and 2 64 bit and they are all doing fine. Sorry to hear you have the problem. I think Hardy is one of the best OS around. I just took Mandriva and Fedora for a spin. No match. Good luck.

---

### Post by Em-Buntu on 2008-05-05
> **Pumalite said:**
> I can assure you it's your hardware. I have 4. 2 32 bit and 2 64 bit and they are all doing fine. Sorry to hear you have the problem. I think Hardy is one of the best OS around. I just took Mandriva and Fedora for a spin. No match. Good luck.

I'm thinking the 20GB hard drive must be faulty or Hardy has issues with both IDE and SATA in the same system.

I'll replace the 20GB IDE drive with a newer 120GB SATA and see if this cures the problem.

After using Feisty->Gutsy->Hardy, so far on my machine, Feisty has offered the best speed/performance/stability. Seems I have more issues with each release. I wonder if these are Compiz related?

---

### Post by HeruLuingul on 2008-05-05
I've been having similar problems, figured I'd post in an existing thread instead of polluting the place.
I did the online upgrade to Hardy the day after it was officially released, and somewhere along the install something got FUBAR'd (possibly my unreliable router cutting out) and I ended up with this half-feisty-half-hardy monstrosity that changed in appearance every time I rebooted. I said "F THIS" and burned a Hardy ISO to do a complete reformat. Post-install, it takes my PC at least 5 minutes to get past the boot splash screen (where it displays the manufacturer name of the PC, before even the BIOS option screen). Any way to solve this? It works fine if I just keep it turned on constantly, but rebooting is a pain in my ***.

---

### Post by lemming465 on 2008-05-05
The last time I had a system booting this slowly, it turned out to be read errors from a failing disk drive.  I'd check for hardware problems.  The *smartctl* tool from the *smartmontools* package may be able to tell you what the disk is actually doing.

---

### Post by Em-Buntu on 2008-05-05
> **lemming465 said:**
> The last time I had a system booting this slowly, it turned out to be read errors from a failing disk drive.  I'd check for hardware problems.  The *smartctl* tool from the *smartmontools* package may be able to tell you what the disk is actually doing.

Thanks for the reply lemming.
This is what I thought also.
Although it's an old ATA100 drive, it still supports smartdrive which sort of usually predicts when a drive is experiencing a problem(s) and about fails. 
I have several old drives in my junk box I don't use because they give smartdrive failure predcitions. When smartdrive says a drive is about to fail, it usually does.

Still, I'm going to replace it with a newer drive later and see if that corrects the problem.
I really like Ubuntu but I haven't had a good stable installation since Feisty. Maybe the new HD will change this.
Thx everybody.

---

### Post by HeruLuingul on 2008-05-05
> **lemming465 said:**
> The last time I had a system booting this slowly, it turned out to be read errors from a failing disk drive.  I'd check for hardware problems.  The *smartctl* tool from the *smartmontools* package may be able to tell you what the disk is actually doing.

I'll try that smartctl thing when I get home, posting from work. Thanks for the tip, I *have* had the drive for about 5 years now, and it's seen plenty a hard-reboot. (I'm hard on computers like city driving on gas-guzzlers)

---

### Post by jsandeo on 2008-06-06
After updating my amd64 system to Hardy, everything started being slow as hell... my box was constantly doing swap.

I added the following boot options to my boot image at /boot/grub/menu.lst :
fb=false noapic nolapic

Now everything seems to be fine again.

---

