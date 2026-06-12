---
title: "Ubuntu10.10 dual boot with Vista Problems"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by Jwood725 on 2010-10-30
Ok guys another noob here. I recently install Ubuntu next to Vista, everything seemed to be going great. I love Ubuntu, however I had some important files on Vista. When I went to restart and choose Vista to boot in I received an error message. 

"Cannot find file: Z:\D2D\Images\*.WSI When trying to determine UI language"

Then I moved on to erecovery for this laptop and received

"Restore failed - reason 0xa0000001"

Is there any way I can recover Vista with out screwing up Ubuntu, or totally wiping my drive with a clean install of vista. And please when giving advise remember your speaking with a Ubuntu illiterate lol. :confused:

---

### Post by Mark Phelps on 2010-10-30
Did you do a side-by-side install, allowing the Ubuntu installer to shrink your Vista OS and make room for Ubuntu? If so, you fell victim to the common problem of that installer corrupting the Vista OS partition during the process.

Any time you have "important" files, you should come here BEFORE you mess around with something that's going to mess with your partitions -- or, at least, back up your important data so it can be recovered.

How did you try the recovery? Was it pressing a function key? Or was it by booting from a recovery CD?

If your dual-boot install wiped out your Recovery partition, then you have nothing to recover FROM.

If you don't have a Vista install DVD, then go to the link below, download and burn the appropriate Vista Repair CD:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

Boot from that CD, and run Startup Repair three times -- that's right, three times.  That should get you back into being able to boot Vista.

---

### Post by Jwood725 on 2010-10-30
> **Mark Phelps said:**
> Did you do a side-by-side install, allowing the Ubuntu installer to shrink your Vista OS and make room for Ubuntu? If so, you fell victim to the common problem of that installer corrupting the Vista OS partition during the process.

Any time you have "important" files, you should come here BEFORE you mess around with something that's going to mess with your partitions -- or, at least, back up your important data so it can be recovered.

How did you try the recovery? Was it pressing a function key? Or was it by booting from a recovery CD?

If your dual-boot install wiped out your Recovery partition, then you have nothing to recover FROM.

If you don't have a Vista install DVD, then go to the link below, download and burn the appropriate Vista Repair CD:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Boot from that CD, and run Startup Repair three times -- that's right, three times.  That should get you back into being able to boot Vista.

Yes I did do the side by side install, according to the instructions when downloading and installing from USB. That little button that says "Show Me" I did exactly as it said.

As for the recovery after it fails to boot, Acer gives you 3 choices.
1. Recover from CD
2. Recover using eRecovery
3. cant remember I wasn't able to choose this one.

I tried the eRecovery, however Ubuntu didn't wipe my recovery partition, I can open the file from Ubuntu and see all contents. My only guess is that it corrupted something vital.

I would download that repair tool for vista however my cd burner doesn't burn, its be broken for a while. I will have to wait till I get my original recovery cd back I suppose. 

Anyway thanks for suggestions, I was hoping for something more along the lines as a desk repairer or partition recovery tool I guess.:(

---

