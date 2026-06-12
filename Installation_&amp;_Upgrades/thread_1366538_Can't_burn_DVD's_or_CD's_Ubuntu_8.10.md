---
title: "Can't burn DVD's or CD's Ubuntu 8.10"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by SVEN1 on 2009-12-28
Can't burn DVD's or CD's Ubuntu 8.10
Have tried every burner for Ubuntu and those in the repository
without success.

Always get a burn error of some sort, occasionally something will burn on the disc but it is unreadable or the disc reads empty. Sure wasted about 25 discs so far...Tried numerous brands also....

I have two burners hooked up correctly, that worked flawlessly when I ran Windows XP 10 months ago. Not in Ubuntu, good thing I didn't have to burn any discs for the most part, just put files on a jump drive instead.

I love Ubuntu 8.10 and it has run perfect for the most part over the past 10 months. Any small problem could always be fixed up in a short time.

All I want for the new year is to be able to burn CD's and DVD's

Any chance having two burners hooked up as Master and Slave is causing the problem?

Here are my burner info:
TOSHIBA DVD-ROM SD-R5112 1031 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R96R, Restricted Overwrite]

SONY DVD RW AW-Q170A 1.73 (/dev/scd1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite, Layer Jump]

=====================================
Today downloaded DEEPBURNER trial for Windows XP and ran it in Wine, it burns CD's and DVD's but some files will not open when burned or certain files with too long of names will not burn. But, it's a start. 
[http://www.deepburner.com/?r=download]("http://www.deepburner.com/?r=download")

---

### Post by peyre on 2009-12-28
I'd been having the same thing.  I downloaded the ISO several times, both in Linux and in Windows.  I tried burning it in either OS on several different machines with different burning software (Brasero & K3B in Linux; CDBurnerXP, ImgBurn, and IIRC Nero and Roxio in Windows) and each time either the burn or the verify failed.

Finally I tried using a CD-R instead of a CD-RW, and the burn succeeded.  I just hate to waste a CD on something temporary like the alternate install CD of a specific version of Xubuntu, but that seems to be the only way to do it this time around.  (I would have used a bootable flash drive, but the old laptop I'm installing on won't boot from USB.)

---

### Post by adam814 on 2009-12-28
I have intermittent burn errors with Brasero.  In the past I solved it by compiling Brasero from source using the real cdrecord instead of wodim which seemed to work better with my drive (albeit it can't be redistributed due to licensing).

Now I use GnomeBaker and I've yet to have a problem with it.

P.S. I had less trouble with Brasero (and Nero in Windows) with burn-proof (buffer under-run protection) off.

---

