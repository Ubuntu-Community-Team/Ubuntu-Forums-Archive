---
title: "LiveCD Install Issues"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by nicknrs on 2007-09-21
Hello,

I am trying to install using the livecd and text based iso's, I have these burned to discs already.  I can get to the menu where i choose what to do, once i select anything install, safe graphics mode, check cd i get the following error message.

[39.142205] invalid compressed format (err=1)     
[39.142853] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown=block(104,1)
[39.142908]

The format error on the live disk is err=1 and the textbased its err=2, otherwise everything is the same.

This box is a AMD Sempron 3300+
Asus K8V-VM mobo

Receiving same message from both these SATA drive:
Western Digital WD800JD-19MSA1  
Seagate Barracuda 7200.9 160gb ST3160812AS

Any help would be appreciated.

THank You.

---

### Post by Pumalite on 2007-09-21
Graphics?Memory? Do md5sum on isos, burn at 4x, check for CD corruption after burn and before install.Clean the lens in your burner if necessary.

---

### Post by nicknrs on 2007-09-21
Graphics are the onboard video - 
memory - 512mb

md5sum checks out ok
lowest speed im able to use is 8x, burned another copy and still recieving the same errors. 

Put the cd and one of the disks in a intel based board and it is currently installing no issues.

unsure why it wont work in this other machine.

---

### Post by Pumalite on 2007-09-21
First you need Alternate CD iso because of your graphics. Second: I think you have a dirty or bad burner.

---

### Post by SonicSteve on 2007-09-29
I can almost verify that you burner is not the issue. Not entirely but...
I have an old IBM thinkpad 600E 
It gives me the exact same error, it used to be OK, it won't even load up XP anymore. I know that my ubuntu CD is OK and same for the XP CD. I've used them both before and since and they are fine. XP kicks out as soon as it comes time to write to the disk. I get stop errors pointing to NTFS.sys and mup.sys. 

It has to be some kind of hardware issue, I can't figure out what though. Is it the CD drives ability to read? I don't think so.
I lean towards a problem with the Mainboards drive controller. Though I can't confirm this in anyway. I would be very curious to know if you can load up XP. As soon as formatting is about to finish the stop error hits. 
As for ubuntu it won't matter if you try the alternate or the live CD. Depending on what kind of video card you're using you might have better success with the alternate but I have that exact same mainboard in my desktop pc. I'm running the sempron 3000 and it works quite well with very few issues. My graphics are Nvidia geforce fx5200 AGP.  Ubuntu installs like a champ every time. 
You likely have a failing piece of hardware in your mix, it could even be something stupid like a bad IDE or Sata cable. Really who knows, I know for me and my IBM600e it seems to be disk related except that I know the disk is good. Yours probably are too. Hence I point to the controller, maybe even a flakey CPU, hey who knows.

******EDIT*****
I just pulled out an old live CD of 6.06 and it's working. This doesn't explain why XP won't install anymore but at least I have some success. Maybe 6.10 would work too.
I should add that even if you do get 6.06 to install you find that no matter what you try that sound will not work. Last time I ran ubuntu on this I tried many things but the sound would not work.

---

