---
title: "Edgy live cd wont boot up! urgent help needed"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by gnarula on 2006-10-30
This is the third time i am posting some errors about edgy and in the previous topics no one replied...

Bak to the main point.. I am trying to install edgy on my system... i have downloaded the image and burned it on a cd. Now when i boot using it i get all the options. I select the first one.. it shows a bar which just moves on and after like 10-15mins i get the following error:

"ata4: command 0x25 timeout, stat 0x50 host_stat 0x64"

I have verified the iso image and its okay. Even i have tested the cd by running it with VMWare Player ad it boots successfully.. 

what is the problem with it?? i have even tried the alternate cd. It installs and then after that it just sits on with the bar and then shows the same error as above.

P.S.: I have a Pentium D processor thus i have downloaded the desktop iso. Also i have a Seagate SATA 160GB HDD.

Thanks in advance,

Gaurav

---

### Post by Rhubarb on 2006-10-30
If the CD burn is ok (you might want to burn another, at the lowest speed), then there's a chance it could be a hardware issue.
Try running the memtest program and let it run for 30 min or so.
It could be your RAM, or your RAM / FSB timings - in the BIOS if you can set them all back to "Stable" or just a safe slow setting.

In my last PC Warty and Dapper wouldn't install, even though windows would.
- It was my FSB frequency that was set too high.

Other than that, I don't have much of a clue what else it could be.
That's probably why no one has responded to your pleas of help here.

---

### Post by gnarula on 2006-10-30
k, i'll run the memory test and tell you. Also will edit the BIOS settings according to ur instructions.. just hope it works...

---

### Post by Kateikyoushi on 2006-10-30
Which mobo do you use, does it have a silicon controller ? Is it a seagate SATA drive ?
You could try to install from the alternate install.

---

### Post by Rhubarb on 2006-10-30
Finger's crossed :cool:

---

### Post by Rhubarb on 2006-10-30
> **Kateikyoushi said:**
> Which mobo do you use, does it have a silicon controller ? Is it a seagate SATA drive ?
Yeah, gnarula's got a 160Gb seagate SATA drive installed.
Haven't had heaps of experience with SATA drives + controllers myself, I just know that I personally haven't had any probs with SATA yet.

---

### Post by Kateikyoushi on 2006-10-30
Yes, I noticed and I bet he has a Silicon controller on the mobo those had issues with the Seagete drives, and maybe still not yet sorted out.

---

### Post by gnarula on 2006-10-30
@Kateikyoushi
Yes, I got a SATA Seagate drive but, duno ant the sillicon controller...

I have also tried the memory test and have passed it successfully. Still no success. Any idea when will this be fixed?

---

### Post by Kateikyoushi on 2006-10-30
I read it works with the 2.6.12.2 kernel, I have no idea when is it going to be fixed, kernel problem not ubuntu.

---

### Post by gnarula on 2006-10-30
> **Kateikyoushi said:**
> I read it works with the 2.6.12.2 kernel, I have no idea when is it going to be fixed, kernel problem not ubuntu.

hmm.. is there any way with which i can replace the present kernel with the one mentioned above:-k ?? Sorry if its a noob talk :-?

---

### Post by Kateikyoushi on 2006-10-30
You could try to boot with these options or try the alternate install cd.

Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux nolapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by gnarula on 2006-10-30
still not working dude.. it just sits on there and relaxes. Will post screenshot of it as soon as i find my usb cable for camera.

btw i have tried the alternate cd. It installs it but then i cannot boot it from hdd..

---

### Post by tep200377 on 2006-10-30
The trick is to Press F6 "other options" when grup starts on the cd.

Press E to edit the startupline and add noapic   and if that doesnt do the trick, try noapic nolapic

---

### Post by gnarula on 2006-10-30
Thanks!! noapic nolapic worked out and just finished installing edgy!! Although edgy seems to be a bit slow than dapper but its okay... just need to install the ati driver now whih will be done in a few mins ;).

Earlier i deleted the whole line while i was trying Kateikyoushi's method. i think that may have caused it not to boot that time...

anyways thumbs up to both of u

---

### Post by Kateikyoushi on 2006-10-30
Thanks for letting us know how did you solve it, can recommend it to others and will come up in the search as well.

---

### Post by san antonio fj on 2006-11-14
Thanks so much noapic nolapic worked you guy F'n rock I burned like 5 different copies and was about to give up thinking my mobo was a piece

---

