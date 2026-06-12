---
title: "Triple boot with GRUB?"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by julio_cortez on 2010-09-24
So, this is what I'm planning to do sooner or later:

I'd like to add an XP SP3 install (I already have the disc and all I need) to my current dual-boot scheme, and I wonder whether there's the chance to have it available in GRUB (without having to have a cascade of loaders e.g. **select W7 in GRUB** *then* **select XP in W7 loader**).

So, the GRUB menu itself should look something like this itself:```
Ubuntu Linux 2.6.32-24-generic
Ubuntu Linux 2.6.32-24-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
**Windows XP (loader) (on /dev/*whatever*****)**
```The last line, in bold, is what I'd like to see added.

So I was wondering, if I added a second HD just for Windows XP (I'm planning to remove the one I currently have for W7 and Ubuntu, while installing) and then re-attach the HD I'm currently using, would I be able to make GRUB recognize it and let me have also XP in its menu?
I think I should load Ubuntu in recovery mode and launch a *sudo update-grub*, would it be enough?

Would it be wise to do so, or there's another way I'm not aware of that maybe I should know?
[I]
Then I plan to do something like hide 7's drive from XP and hide XP's drive from 7, but it clearly doesn't belong here so it's something I'll figure out on my own..[/I]

---

### Post by Herman on 2010-09-24
:) I think your plan should work, it looks like you know what you are talking about and your ideas make sense.
I don't think partition 'hiding' works anymore with modern versions of Windows, or at least I read that somewhere. I haven't tested it myself. I think as long as you unplug your other hard disk during the installation probably everything will be okay. Once the Windows systems are installed I don't think they'll donate their boot loaders. Maybe get a second opinion on that though.  :)

---

### Post by fysiker on 2010-09-24
For me the easiest way would be:

1. install from cd/usb windows XP
2. boot from ubuntu cd
3. chroot into the system
4. grub-install

have a look at grub/Ubuntu :D

---

### Post by julio_cortez on 2010-09-26
> **Herman said:**
> :) I think your plan should work, it looks like you know what you are talking about and your ideas make sense.I'm going to try in the next days, I have a "spare" 160GB drive from my old stripe (the other one is, well, dead *after I accidentally made it fall*) to do the experiment, so I'll keep you updated when I have more info.. **Thanks in advance** for the moment!!

> **Herman said:**
> Maybe get  a second opinion on that though.  :)Mmmmmh.. Yes, I will definitely get a second opinion: it will be my one after I try it :P

The setup is mine, I've moved all the data on an external hard drive just in case, so even if I fail I'll just have to spend a night reinstalling W7 and Ubuntu, which won't be a very big deal :)

---

### Post by presence1960 on 2010-09-26
> **julio_cortez said:**
> I'm going to try in the next days, I have a "spare" 160GB drive from my old stripe (the other one is, well, dead *after I accidentally made it fall*) to do the experiment, so I'll keep you updated when I have more info.. **Thanks in advance** for the moment!!

Mmmmmh.. Yes, I will definitely get a second opinion: it will be my one after I try it :P

The setup is mine, I've moved all the data on an external hard drive just in case, so even if I fail I'll just have to spend a night reinstalling W7 and Ubuntu, which won't be a very big deal :)

If you are going to install a "second" version of windows and want GRUB to boot both windows installations you need to partition your disk for the new windows install prior to installation. Then place the boot flag on the partition which will get the new install. make sure windows 7 boot flag is turned off.

if you do this then the bootloaders of both windows versions will not be combined. If you fail to do this then they will be combined and you will experience what you mentioned above. Another downfall of the combined boot loader scenario is if you remove one version of windows the remainaing version may be unbootable since the files necessary for booting may have been removed with the other version of windows.

P.S. I missed the part where you mentioned removing the disk with your current dual boot set up. That will work. But if you don't remove it in addition to the above directions you also want to make the disk getting the new windows first in the hard disk boot order in BIOS because windows automatically writes it's boot loader to the MBR of the first disk to boot. Once the install is complete and you verify the new windows will boot successfully you can switch the hard disk boot order back, boot into ubuntu, open a terminal and run ```
sudo update-grub
```This will detect  and add the new windows install to the GRUB menu.

---

### Post by julio_cortez on 2010-09-28
Tonight is *the* night: I'll try it out and let you know, but I'm confident it will work fine, from what I've read in your post..
Again, thank you :)

---

### Post by julio_cortez on 2010-09-28
Tried it:

[LIST]
[*]Removed sda (which had 7 and Ubuntu on it)
[*]Attached sdb and installed XP on it
[*]Re-attached sda and loaded Ubuntu in safe mode, updating Grub
[*]At this stage, both Windows installs were recognized correctly
[*]Booted into Windows 7 and removed the letter from the XP partition
[*]Did the same, the other way round, in XP
[/LIST]
[SIZE=5]**..ET VOILÀ!!**[/SIZE]

It worked a treat!! No issues of any kind. All went smooth and as easy as drinking a glass of water :)

The only trouble I encountered: **[SIZE=4]PEBKAC!![/SIZE]**
I've typed my password with an Italian keyboard layout from within my profile and it wouldn't let me login if I typed the password with the US keyboard layout that is loaded at startup :(
I had several minutes of panic before I realized that I could force the Italian keyboard layout even at startup, by editing the regional settings as Administrator.. :guitar:

**[SIZE=4]Thank you everyone!![/SIZE]**

---

### Post by presence1960 on 2010-09-28
> **julio_cortez said:**
> Tried it:

[LIST]
[*]Removed sda (which had 7 and Ubuntu on it)
[*]Attached sdb and installed XP on it
[*]Re-attached sda and loaded Ubuntu in safe mode, updating Grub
[*]At this stage, both Windows installs were recognized correctly
[*]Booted into Windows 7 and removed the letter from the XP partition
[*]Did the same, the other way round, in XP
[/LIST]
[SIZE=5]**..ET VOILÀ!!**[/SIZE]

It worked a treat!! No issues of any kind. All went smooth and as easy as drinking a glass of water :)

The only trouble I encountered: **[SIZE=4]PEBKAC!![/SIZE]**
I've typed my password with an Italian keyboard layout from within my profile and it wouldn't let me login if I typed the password with the US keyboard layout that is loaded at startup :(
I had several minutes of panic before I realized that I could force the Italian keyboard layout even at startup, by editing the regional settings as Administrator.. :guitar:

**[SIZE=4]Thank you everyone!![/SIZE]**

Glad you got it on the first try. Enjoy!

---

### Post by Herman on 2010-09-29
:cool: Cool! Well done and congratulations!

---

### Post by julio_cortez on 2010-09-29
Thanks for the support. *Guess I've earned a new signature then* :P

---

### Post by 1danjack on 2010-10-13
I'm looking to do virutally same set-up as above but on a laptop: Win 7 64 bit, Win XP Pro 32bit and Ubunut 10.xx xxbit (not sure of version just yet).

Is there a known good sequence to do to allow triple boot with only one hard disk?

---

### Post by oldfred on 2010-10-13
You have to have a primary partition available.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by 1danjack on 2010-10-14
sweet thanks for your help

---

