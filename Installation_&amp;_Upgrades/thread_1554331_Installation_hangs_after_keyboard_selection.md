---
title: "Installation hangs after keyboard selection"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by n0c0d3 on 2010-08-16
I have an AMD Athlon 3200+ 64  K8 and I want to install a dual boot Win7/Xubuntu system. When I try to install Xubuntu 64 bit, but the also the 32 bit version and both Kubuntu versions, the installation stops after the keyboard layout screen. The install completely hangs (no cd or other noticeable activity on the computer) and I have to do a hard reboot to get out of it. I've been looking for a solution and found that the options noapic and/or nolapic in the installer F6 menu might solve this problem, but unfortunately they didn't work for me. I've done the CD integrety and memory checks, but no errors were found. I'm pretty lost from here.

I also read installing from the alternative CD might work, but I'm not sure what to expect from this textual installation. If it's only a command-line installer I don't think I will be able to do much with it as I haven't yet been able to find a tutorial on how to use it. Does anyone konw where I can find instructions?

Any advice on how to get (X)ubuntu installed on this computer?

Bart

---

### Post by mörgæs on 2010-08-17
The alternative installer is a good option to try. It is only the installation itself, which is text-based; the installed system is the full Ubuntu.

Remember to have wired web access while installing.

---

### Post by n0c0d3 on 2010-08-17
Thanks for your reply. But what does "text-based" mean? Is this no more than a command line or do I still get options to choose from like in the graphical installer, but then in plain text? And how is the partitioning? I want to install a dual boot and need my Win-partition to be resized and do not want to loose it.

Bart

---

### Post by mörgæs on 2010-08-17
It has the functionality like the graphical installer, but it looks like DOS 5. You can see a video here:

[http://www.youtube.com/watch?v=hAy-BD6KyHM](http://www.youtube.com/watch?v=hAy-BD6KyHM)

The video is a little old, but you get an impression of how it works.

---

### Post by n0c0d3 on 2010-08-17
Thanks Morgæs. When I just finished my last post I thought to have better called it an early eighties graphical interface :) And then I found a thread on another forum where someone made it clear already what it looks like. But this helps me a lot because I now know what to expect in detail. I already burnt the CD because I was going for the deep dive anyway.
I hope this will help me overcome the hangman problem, but as my memory isn't the problem (1024 MB) I doubt it. But I'll see what happens, never loose hope... I'll post the results when I'm finished trying.


Edit:

I did the alternate Xubuntu 64 bit install and that when without problems. But I couldn't update or open files or run whatever program because then the system hung again. I booted in recovery mode with low resolution and then the update went fine and updated to 2.6.23-24 etc. and did an upgrade of my video card from the hardware menu. Things seem to run fine now, but the system hung once when running Firefox after the updates. I hope this won't happen too often...
One little strange thing is that the Gparted boot disk recognized 10G unallocated space before making any changes to my HD or Windows partition while the Ubuntu partitioner didn't see it. But that's pretty off topic and I still have to install Gparted to see what it detects now... Tomorrow's another day (tomorrow is actually is today ;) )

Thanks for your help,
Bart

---

