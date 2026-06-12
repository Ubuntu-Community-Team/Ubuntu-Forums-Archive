---
title: "Unbuntu CD won't boot"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by mskristinahall on 2007-12-24
Hello.

This is my absolute first attempt at installing any version of linux ever, so expect to see me on this forum a lot asking questions. :)

Anyway, I have an old clunker of a machine that I want to setup as a linux test server with sql, php etc...

I downloaded, and burned ubuntu to CD. 

Now, popped CD in, and tried to boot off the CD... No dice. Skips right to an old unfinished win XP install that was never completed because the computer does not have enough RAM.

I'm not sure what other information is needed to diagnose and resolve the problem... Just let me know and I will do my best to provide any info you ask for.

---

### Post by oldsoundguy on 2007-12-24
if you just burned the file as is, you will get that result.  You have to take the ISO file and burn it as a disk image.  Both Ashampoo and Nero offer those options.  Not sure what that POS Roxio that comes with WinBLOWS does.

---

### Post by Tristicus on 2007-12-24
Can your BIOS boot from CD? (It should, but make sure it is set to boot from CD first).

---

### Post by mskristinahall on 2007-12-24
Hi.

Don't worry. :) I did "extract" the ISO... It's not the.iso file burned on the cd but the whole set of files. I may be clueless but not that clueless. 

I have set it to boot from the cd first. It says it's looking for the cds boot record and the skips to the windows install.

And, normally when I install windows xp for example it boots from the cd just fine so this really confuses me.

---

### Post by mskristinahall on 2007-12-28
OK.

Found out why the disk was not working. I had extracted the ISO which apparently wipes the boot information.

Ok install went fine.

I got to the point where it wanted me to reboot my system which I did. CD is out of the drive and all that.

It asked for my login and pass. I typed them in same as I did during the install and now it has:

kristina@Puck: "$

I'm not sure what I'm supposed to do, and the install manual on the website doesn't explain this behavior. Is this normal?

---

