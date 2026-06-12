---
title: "Dual Boot Install XP Pro &amp; Ubuntu 10.04 on SSD &amp; HDD"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by DonkeyShark on 2010-08-09
Hello Ubuntu amigos.  I'm new here and new to Linux (less than a week's experience on Linux).  I just purchased a 128GB Kingston V Series SSD and found out that my laptop has 2 HDD bays when I went to swap it in.  This got me somewhat excited as I now have a place for my 160GB HDD as well.  I previously installed Windows XP Pro & Ubuntu 10.04 last week with no problems (on the 160GB HDD), however I feel like I'm getting in a bit over my head with where to go now that I have two hard drives to work with, one SSD and one HDD.  I currently have a fresh install of XP Pro on the 128GB SSD and nothing else.  The old 160GB HDD has the dual boot of XP Pro & Ubuntu 10.04, but I'm considering swiping it and starting off fresh.  I've read about people dual booting drives and repartitioning to have shared storage (Dual booting the SSD and using the HDD for storage).  I've also read about people booting XP on one and Linux on the other (though they were using two HDDs).  However, since I have a SSD, I think it may be more efficient to run both OS's on it and use the HDD for shared storage.  Is that possible and or efficient?  I assume it is, but I'm not sure how to go about it.  I don't have a lot of experience with drive partitioning, but I do follow directions somewhat well.  I'm not opposed to running XP on the SSD and Linux on the HDD, but I don't know how to set up a dual boot option if I do it that way.  Also, I don't want to hurt Ubuntu's feelings by putting him/her on the "lesser" drive.

I'm very much open to suggestions.  I have an Intel Core 2 Duo processor, which if I understand things correctly, that qualifies me for the 64-bit version of Ubuntu, though I'm not really convinced that I need it, however I can be coerced if it won't cause too many problems and if there aren't many compatibility issues.  I value compatibility above performance.  FWIW I run the 32-bit XP.  I'm not a gamer, but I do make and edit weekly videos for a poker site, so I'm somewhat of a cpu heavy user.

Please advise regarding my options, my do's and don'ts as well as a how to.

Thank you in advance,

Donkey

---

### Post by ajgreeny on 2010-08-09
Put both OSs on the SSD for speed, and format the HDD to ntfs and share it between both OSs as the data storage.

There is plenty of information on dual booting XP and ubuntu, but don't use wubi would be my main comment, as that is just for trying it, rather than really using it properly.  At this stage I personally would suggest you stick with 32 bit system, just to make a few things a little easier, but I'm sure others will disagree.

You already have XP installed on the SSD, which makes things easier, so run the live CD, install as normal and then at the partitioning stage you will get the option to choose manual partitioning, which I think will be the best choice.  Choose the 128GB SSD and shrink the XP partition to what you want; as you will be sharing all data on the HDD it will not need to be huge, maybe 20GB, but I don't run windows so am not quite sure about that.  Similarly ubuntu will not need huge space for the OS / partition as again all data will be on the HDD, so you will have some spare space on the SSD to use as storage as well.

---

### Post by DonkeyShark on 2010-08-09
Thanks for the quick reply.  That's sort of what I was leaning toward was using the SSD for both and storing everything else on the HDD.  I read that Ubuntu can read NTFS but that XP can't read EXT2/3.  Also read there are some programs that allow XP to read them, but that there are issues.  I think NTFS storage drive sounds like a great idea.  Also, dual booting Ubuntu onto the same drive as the XP was easy before, should be again I hope.  

Thanks again,

Donkey

---

### Post by DonkeyShark on 2010-08-09
Also, are there any issues with installing Ubuntu 10.04 on the SSD?  Any special provisions I need to make?

---

### Post by ajgreeny on 2010-08-09
Not that I'm aware of, but I've never done it, so I am the wrong person to answer that question.

---

### Post by oldfred on 2010-08-09
Some more info:

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

This was karmic but should be almost identical for lucid:
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by DonkeyShark on 2010-08-14
I'm having issues installing Ubuntu on the SSD. I can't get the Ubuntu installation disc to make it past the "Ubuntu Logo" screen.  I hear the disk firing up, then the screen says "Ubuntu" in the center, but never does anything else, it just hangs for over an hour.  I can install it just fine on my SATA drive, but not on the SSD.  I tried enabling AHCI in BIOS and that didn't change anything.  Any ideas?

---

### Post by oldfred on 2010-08-14
Do you have a newer motherboard with the 6GB/sec setting, change to 3GB/sec.

If it gets to the logo I would suspect a video issue but you say it works ok with your SATA drive.

Try f6  and choose nomodeset or f4 safe mode.

---

