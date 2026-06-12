---
title: "Trying to reinstall Ubuntu"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by bill40 on 2011-04-05
I'm trying to help my dad, who's recently got a computer that had Ubuntu 10.10 preinstalled. After some problems while I wasn't in a position to help out, I think a reinstallation is necessary. But when I make a USB drive to install it from, it only has .exe files, and nothing Ubuntu can use, so it doesn't boot on startup (even though it's set to boot from USB first) and it can't be run later either. This happens when I download the ISO from the main download page on the Ubuntu website, so is there a link to download one without Windows files?

---

### Post by mörgæs on 2011-04-05
Have you tried to create the USB stick using Unetbootin? 

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by KegHead on 2011-04-05
Hi!

You could try this also:

1. Download 10.10 iso from Ubuntu.

2. Format your stick.

3. Goto: System..admin..start up disk creator.

4. Your source is the iso you downloaded.

5. Disk to use is your USB stick.

This has always worked for me.

KegHead

---

### Post by bill40 on 2011-04-07
KegHead- That's the way I tried doing it the first time around.

mörgæs- I've tried that, and once again ended up with a USB stick that only works with Windows. It doesn't even try to boot it on startup, and the same thing happens when I try using it on my laptop, which I installed Ubuntu on using that method before.

I also tried using Unetbootin on the computer itself, as it's started working a bit better for some reason, and had it directed at the hard disk instead of a USB, but that just puts the same unusable .exe files in there instead.

I'm a bit confused, because whatever I try just gives us files that Ubuntu won't use and won't load on startup either.

---

### Post by KegHead on 2011-04-07
Hi!

Have you tried formating your stick in Ubunutu?

KegHead

---

### Post by bill40 on 2011-04-07
What I've been doing is erasing the data using the option in Startup Disk Creator. I don't know whether this is enough though. Should I format it using a separate program?

---

### Post by KegHead on 2011-04-07
Hi!

It should.

Are you reserving any extra space?

Also does you stick hold any other data...music, docs?

Maybe try a new stick?

KegHead

---

### Post by bill40 on 2011-04-07
No, nothing else on it, and it's the same one I used before successfully, so the space on it shouldn't be an issue, but I might try a different one anyway, in case what I've done so far wasn't doing the job properly for whatever reason.

---

### Post by KegHead on 2011-04-07
Good luck and let us know.

KegHead

---

### Post by bill40 on 2011-04-08
I'm now using a new USB, and when looking at it I saw its file system type is msdos. I'd like to change it to FAT32, which is mentioned in gparted tutorials, but Ubuntu on my computer will no longer connect to the internet, and my dad's seems to have an aversion to running any programs at all - nothing appears under Applications or System, and when I try sudo apt-get install gparted, nothing happens. I'm very confused.

---

### Post by Dutch70 on 2011-04-08
Can you install gparted from software center?

---

### Post by KegHead on 2011-04-08
Hi!

When you format in Ubuntu you can select fat 32.

KegHead

---

### Post by bill40 on 2011-04-09
Dutch70- I can't get into Software Centre on my dad's computer. The Applications and System menus are empty, and Run Application can't find it either. I haven't tried on mine yet, but I expect it won't work with the internet connection misbehaving.

KegHead- Where/how can I do this without installing gparted? Is there already a way of formatting as FAT32 among the standard programs?

---

### Post by Dutch70 on 2011-04-09
Have you checked the md5sum of your downloaded .iso? 
[[COLOR="Red"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")
Did you check the cd/usb for defects? 
[[COLOR="Red"]CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")

---

### Post by bill40 on 2011-04-09
I haven't tried those yet, but a thing I noticed when looking at the pages was that the [BootFromCD help page]("https://help.ubuntu.com/community/BootFromCD") shows an image of what the contents of the CD/USB should be. Several of the files there haven't appeared on any of my attempts, most importantly **ubuntu.ko**. Does this sound like an MD5 issue?

---

### Post by Dutch70 on 2011-04-09
Possibly, it's very easy to check. In fact I think all you have to do is double click the .iso to get the md5sum.

Here is the number you should match up to.
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/UbuntuHashes[/COLOR]]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by bill40 on 2011-04-09
Thanks, but the md5sum wasn't necessary after all. I finally managed to reformat the USB, and that seems to have done the trick! We're reinstalling now.

---

### Post by Dutch70 on 2011-04-09
Nice!!! Hope it all goes well.

---

### Post by KegHead on 2011-04-09
Congrats!

Keep us updated.

Please close out this thread if all is well.

KegHead

---

