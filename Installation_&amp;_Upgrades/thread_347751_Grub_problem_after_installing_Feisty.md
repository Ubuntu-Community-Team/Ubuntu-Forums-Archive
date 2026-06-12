---
title: "Grub problem after installing Feisty"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by gjones on 2007-01-27
I think I've done something stupid...

I have Edgy installed on my hard-drive as the only OS, / is on one partition, /home is on another and I have another partition for my music and such things.

I downloaded the Feisty Herd 2 Live-CD, and (after upgrading debconf and ubiquity after it crashing and me finding a bug-report with a fix) successfully installed Feisty.

When I reboot, I get 'Error 18' from Grub. I (now!) know this means that it can't find the things it needs to boot at the beginning of the drive, what can I do to fix it?

I think that I need to make a /boot partition that both of my OSs can use, at the start of the drive, but how would I go about doing this? (if it is infact what I should be doing?)

(The Feisty Live-CD stopped working after I'd installed, giving me CRC errors, despite installing properly, so I'm using a Dapper Live-CD at the moment, if that should make any difference).

I was sensible, and I do have things backed up should it become necessary, but I quite enjoy learning through messing up, so if anyone can help, that would be wonderful. I know just about enough with Linux to be dangerous, but don't have a great deal of experience in fixing things when they go wrong...

---

### Post by gjones on 2007-01-27
OK, I seem to have saved myself.
I had tried running grub-install from the live-cd, but it didn't work. Running it with --root-directory=/media/disk-1 (where I'd mounted /dev/hda1 - my edgy / partition) works.)

So, I have a working machine again...is there any way for me to get the Feisty partition bootable?

---

### Post by andrian.ivanov on 2007-02-10
:)

---

### Post by geek_Man on 2007-02-10
> **gjones said:**
> <snip />is there any way for me to get the Feisty partition bootable?

Yeah, just add an entry for it in your menu.lst file. I can tell you how if you want.

---

