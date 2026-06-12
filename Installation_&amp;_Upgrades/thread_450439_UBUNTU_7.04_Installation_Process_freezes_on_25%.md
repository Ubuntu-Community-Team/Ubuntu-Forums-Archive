---
title: "UBUNTU 7.04 Installation Process freezes on 25%"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by marcelocero on 2007-05-21
HELP!! I NEED SOMEBODY, HELP!!:(
I really don't know what I'm doing...
I have a Samsung HDD of 12.1 Gb, it has a NTFS partition.
I downloaded the UBUNTU 7.04 from its page to the CD and boot it
I went to the Start or Install UBUNTU menu
Once all the Ubuntu began, I clicked on the Install icon.
From there... can anybody help me? because it doesn't matter what I do, it keeps freezing on the 22~25% when it says "Copying Files..."
Can anybody give me a Step-by-Step guide of how to install UBUNTU 7.04??

---

### Post by Ub1476 on 2007-05-21
Probably the CD that isn't working. Try to download a new .iso file, maybe with a download program so you prevent that you miss a few files when downloading from the source. Next, burn the cd with a good, appreciated program at lowest speed possible. 

Hope it works:)

Ub

---

### Post by Death_Sargent on 2007-05-21
course if that is your only computer i recomend buying a CD as they tend to be 100% good and you don't have to have a working comp to burn them

---

### Post by fivepointe on 2007-05-21
There could be several things causing this. 

If you still have the iso check it against the md5sum. If it passes, burn a new disc. Also once you have booted from the CD there is an option to check the disc for errors. It passes and the install still fails you could have a hardware issue.

Most likely if it is a hardware issue I would guess it is either a ram or hard drive issue. Start by running memtest and see if it drops any errors. If that passes move on to the hard drive. An easy test for it would be to use a windows 2000 or xp disk a do a full format, not a quick format. If everything turns out good then try using a different CD-Rom drive. I've seen many CD-Rom drives crap out on an install half way through.

---

### Post by southernman on 2007-05-21
What are the specs of your computer?

How long are you waiting when it hits this 22 - 25% in the installer?

Older hardware can take a rather long time to do certain functions of the installation process... It did on an ole p2 350 - 128mb - 10gb dell that I dug out of the closet last night. Took over 2 hours to install fiesty.

---

### Post by marcelocero on 2007-05-21
> **southernman said:**
> What are the specs of your computer?

How long are you waiting when it hits this 22 - 25% in the installer?

Older hardware can take a rather long time to do certain functions of the installation process... It did on an ole p2 350 - 128mb - 10gb dell that I dug out of the closet last night. Took over 2 hours to install fiesty.

well... It's a P4 2.4 Ghz, 512Mb RAM and the HDD is just a experimental one since I want to try UBUNTU. I have like 9 HDD for backups and stuff, using one of them instead of the principal one is good idea just in case that... U know, something goes wrong... I think it's the CD... I tried UBUNTU using the same CD on a different machine, and it did exactly the same thing, ABSOLUTE Freeze at 25%, and the other computer was slightly bigger than mine.
and... about the freezing, at one point I thought "ok... maybe is doing something" but... not even the NumBlock led turn on/off when I pushed the key. but, still, I waited 2 hours just to see if it was doing something... but... Nothing...

---

### Post by southernman on 2007-05-21
Ok. Sounds as if you got a bad burn on the cd - or possibly file corruption during downloading.

Did you check the md5 of the iso?
You could try burning a new cd at the slowest speed possible, Perhaps?

Installing from the live cd seems to be causing a lot of problems, judging by all the post on the forums about that. Might want to grab the alternate cd, if all else fails.

---

### Post by marcelocero on 2007-05-21
> **southernman said:**
> Ok. Sounds as if you got a bad burn on the cd - or possibly file corruption during downloading.

Did you check the md5 of the iso?
You could try burning a new cd at the slowest speed possible, Perhaps?

Installing from the live cd seems to be causing a lot of problems, judging by all the post on the forums about that. Might want to grab the alternate cd, if all else fails.

I'd like to know more about that "md5", what is it?

---

### Post by marcelocero on 2007-05-21
Could be the problem that I recorded the ISO image on a CD-RW using Nero at 4x (that's the max speed for my CD RW)?

---

### Post by southernman on 2007-05-21
> **marcelocero said:**
> I'd like to know more about that "md5", what is it?

[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

You'll see a section dealing with md5sums also.
> Could be the problem that I recorded the ISO image on a CD-RW using Nero at 4x (that's the max speed for my CD RW)?

Not sure if you can burn slower than that...

---

### Post by southernman on 2007-05-21
If you'd like to try using infrarecoder mentioned in the burning section, [go here]("http://sourceforge.net/project/showfiles.php?group_id=175271&package_id=201144&release_id=508375") for the proper working .exe file. It's as close as you'll get to nero, for free. :)

I tried it myself in winders and it did a great job...

---

### Post by marcelocero on 2007-06-19
Last Week, I got the Original UBUNTU 6.04 CD, I still have the same problem; however at this time, the progress of the installation freezes at the 26~28%... well.... that's a progress...

---

