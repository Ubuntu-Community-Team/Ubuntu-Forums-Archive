---
title: "Kernel panic during installation (Caps and Scroll Lock lights flash)"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by GryphElyse on 2008-07-13
Hello, 

I'm brand-new to Linux and it seems as if the computer gods are determined to keep me from ever using it. Here is my sad story.

I have a friend who convinced me to try it out. The first burn try of the Live CD was a failure - "I/O Error: cannot read from boot disk." I assumed it was just a burning problem and there had been an error somewhere. I burned the second LiveCD attempt in InfraRecorder and managed to get the Live environment started up, played with it, decided to install. And trying to burn a live disk for Kubuntu.... Twenty disks in my trash bin, all with either "I/O Error: cannot read from boot disk" when click "install", "try", or "integrity check"; or, if it managed to load ANYTHING past that splash screen, a sudden cascade of error lines all reading "buffer I/O error on device sr0, logical block [insert large number]".

The same happens with a Ubuntu 6.04 and 7.10; and now even my regular 8.04 disk that worked before is now malfunctioning in the same way. Either it is on the slider bar loading screen and suddenly freezes with the Caps and Scroll Lock lights flashing, or - once, ONCE, oh such blooming hope I had till it was shattered - I managed to get into "Install" and it froze right after Date&Time, not a kernel panic but rather another buffer I/O error. I know this because I was able to click "cancel" and right before everything went black, I saw that familiar cascading screen of errors.

I have Googled my problems repeatedly. 
Some say that the boot disk read error is because of confusion with a DVDRW drive and they "set the mode in BIOS to UDMA2 and it worked perfectly"; I managed to find it in Bios and tried that, but it didn't really seem to work. There seemed to be TWO of each drive, one in PIO and one in UDMA, and the only options for UDMA were "enable" or "disable"; it was PIO that had mode options. Obviously fiddling around with this didn't work. 

As for the kernel panic, that could be the same problem or related or something entirely different...
I know it's not a CD problem; I downloaded 3 different versions from 4 different mirrors, burned it with Alcohol, InfraRecorder, ISOrecorder... Gah. I have a stack of CDs in my trash bin 2 inches high. It's depressing.

If anyone knows how to fix this - the buffer I/O error OR the kernel panic - please, please help.

System information:
MSI K7N2 Delta-L mainboard, BIOS v5.9 (The most current BIOS; I just flashed it - that's how I managed to get as far as the beginning of the installation, but then it froze... and haven't gotten that far since, kernel panic every time)
AMD Athlon XP 1800+, about 1.5GHz
512MB RAM
40GB HDD, I think it's a Maxtor but not entirely sure what make; Secondary Master
Lite-On DVDRW, CDRW in Primary Master (should I switch it with the HD as far as primary/secondary goes? Not entirely sure what's optimal there)
NVidia GeForce FX5700LE, 128MB RAM
As you can see, it's a veritable FrankenPC patched together of cheap, now-outdated parts. It's years old. It was built mostly by my dad when I was younger, and I can't afford to buy any different parts.
It probably doesn't make any difference, but my current OS is WinXP SP2.

Thanks in advance!

---

### Post by GryphElyse on 2008-07-13
One more thing forgot to mention - I did manage to install Ubuntu *within windows*. I noticed that during installation, it downloaded a fully new copy of Ubuntu instead of installing from the CD. (I noticed, because it took a freaking hour and a half.) I have a theory that, since it was obviously not running from CD, it may be mostly my DVDRW drive that is the problem.....?

---

### Post by PmDematagoda on 2008-07-13
At what speed did you burn the CD?

---

### Post by GryphElyse on 2008-07-13
The problem is NOT the CD. I tried two different burners, both at the lowest possible speed allowed (I selected 1x, but it decided on 8x); and again, both Alchohol and InfraReforder, three different versions of the file from three different mirrors... *stares sadly at stack of wasted CDs in trash bin*

---

### Post by PmDematagoda on 2008-07-13
Then perhaps the errors concern your DVD/CD ROM. Did you try mounting the ISO image and installing Ubuntu as a Wubi image within Windows?

---

### Post by GryphElyse on 2008-07-13
> **GryphElyse said:**
> One more thing forgot to mention - I did manage to install Ubuntu *within windows*. I noticed that during installation, it downloaded a fully new copy of Ubuntu instead of installing from the CD. (I noticed, because it took a freaking hour and a half.) I have a theory that, since it was obviously not running from CD, it may be mostly my DVDRW drive that is the problem.....?

As you can see from above, yes in fact I did. I guess that post hadn't shown up by the time you were posting. I don't know what you mean by WUBI but... yeahz. It works without the CD.

Do you have any suggestions as to what to do about the drive? I googled the problem and someone mentioned changing the drive mode in the BIOS to UDMA2, because it's a DVD writer and the writing is messing up the reading; but I plunked around the BIOS for a little while and couldn't figure out how to do so. There isn't really an option for doing that, as far as I could tell. I don't have any spare drives lying around, so if you have any other fixer suggestions, let me know.

---

### Post by fencer on 2008-08-23
Same problem down here, plz we need an expert's answer ASAP because I've googled and found the same issue over and over again, without a consistent answer, plz help us, ¿¿Is this a bug??, who knows, 
I'm a ubuntu newwie and havent found the way to install it yet :-( 
> **GryphElyse said:**
> As you can see from above, yes in fact I did. I guess that post hadn't shown up by the time you were posting. I don't know what you mean by WUBI but... yeahz. It works without the CD.

Do you have any suggestions as to what to do about the drive? I googled the problem and someone mentioned changing the drive mode in the BIOS to UDMA2, because it's a DVD writer and the writing is messing up the reading; but I plunked around the BIOS for a little while and couldn't figure out how to do so. There isn't really an option for doing that, as far as I could tell. I don't have any spare drives lying around, so if you have any other fixer suggestions, let me know.

---

### Post by gatenby_jp on 2008-08-24
most common cause of kernel panic will be apic issues ... try turning off apic in the bios. However if you are getting I/O errors try changing the IDE cable to cd rom. You get a lot of similar type problems in installing Windows if the IDE cable is bad or the dvd/cd Rom drive is faulty. In Windows it is a BSOD and you never know why or the install just hangs. You could perhaps try the alternate cd install rather than the Live cd ... it does give you command line options ... and you might be able to set the install "no apic"

---

### Post by marseille on 2009-02-10
recently, i had a similar kernel panic prob that started out w/an OOPS (soft panic), running ubuntustudio.  i read this exact thread when it all started but my prob progressed (i had about 3-4 month left from when it actually started -- during my last 2mo. i could only boot up DSL w/noapic vga=normal). 

initially i thought `oh, i just need a new HD` but both my internal/external HD were fine, my CD/DVD hardware all good too.  so then i thought i had a video issue cuz my screen went black but eventually my computer would just reboot repeatedly (a cpu prob i guess -- based on what i read) and i could only turn it off if i hit my main *hardware* power button (not good).

my gut feeling told me toss my mobo/cpu but instead i dropped in a new video card ... wrong choice!  installing a new motherboard + cpu completely solved my kernel panic.  so i just thought i would jot down this note 4 future ref,  in this thread, since i hit it up first... and it aint ubuntu that had a problem :)

----

---

