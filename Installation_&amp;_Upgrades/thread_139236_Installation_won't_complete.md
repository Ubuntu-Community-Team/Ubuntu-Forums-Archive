---
title: "Installation won't complete"
date: 2006-03-03
forum: Installation &amp; Upgrades
---

### Post by Zunino on 2006-03-03
Hello.

Two days ago, I downloaded and burned a CD image of Ubuntu 5.10 and successfully installed it on my machine at work (the one from which I am typing). However, I have been struggling to get it installed on my home computer. The installation process will not complete, no matter what I try.

At first, it would always fail during the "Detect and mount CD-ROM" step. After a lot of research, I found a suggestion about using "install irqpoll" at the installation prompt. I was so relieved when I saw the progress bar reach the end of the screen and move on to the next phase of the installation. It then asked me for hostname, etc. but, unfortunately, it all halted sometime later, during the package installation.

I did try many times, with different combinations of acpi=off, noacpi, nolacpi, etc. I do wish to get Ubuntu installed on my machine. I know I am not alone, for I have found plenty of other messages reporting similar problems. Is there some sort of guide to help people whose installation won't complete?

FWIW, here's a brief description of my equipment:
    CPU: Pentium 4 2.53GHz
    RAM: 1GB DDR
    MB: ASUS P4P800-E Deluxe
    VGA: nVidia 6600GT
    CD-RW/DVD-R: LG

I really hope I will be able to install Ubuntu soon.

Thank you for any assistance.

Regards,

-- 
Ney André de Mello Zunino

---

### Post by Sherlock Holmboy on 2006-03-04
try running "memtest86" at the install boot prompt to ensure that you don't have a buggy stick of memory

---

### Post by Zunino on 2006-03-04
[QUOTE=Sherlock Holmboy]try running "memtest86" at the install boot prompt to ensure that you don't have a buggy stick of memory[/QUOTE]
Thanks for the suggestion. I ran the memory test and it found 6 errors during test #4. I would assume that's pretty normal for generic RAM modules. I then tried installing with only one memory module in place, swapping them later on. To no avail. The installation still fails.

So far, I have already realized that I must use "irqpoll" in order to get through the CD-ROM detection part. However, I don't know what to do with the hanging that follows.

I wonder: is this installation really so demanding and "picky" that it fails in a lot of configurations? I mean, my system has no trouble installing the-OS-that-must-not-be-named as well as its games and applications, some of which being quite demanding. What's so special about the Ubuntu installation that it won't be able to do the same? Is it a consequence of the fact that Linux is meant to run on a whole lot of different architectures?

By no means did I intend to be provocative with my previous paragraph. Those were sincere questions from someone who is mostly ignorant of the details behind the creation and maintenance of a complex project such as a Linux distribution. Let me also say that I have been impressed by Ubuntu from the first time I tried it. I often tell people that Ubuntu has provided me with the best Linux experience so far. And I do wish it stays this way.

At the moment, I am downloading a test version of Dapper to see if it can get installed on my system. I've got my fingers crossed.

Regards,

-- 
Ney André de Mello Zunino

---

### Post by Zunino on 2006-03-07
Hello.

I have **finally found a solution** to my problem. And, because I've struggled so much, I would like to share my findings in the hope that I can save someone from the same trouble.

The successful strategy involved tweaking a BIOS setting related to the IDE interface. The BIOS of my ASUS P4P800-E Deluxe motherboard has an option for *IDE mode*, which can be either *Enhanced* or *Compatible*. I had it set to *Enhanced* before, which was fine for Windows XP; setting it to ***Compatible*** solved the Ubuntu installation problems I described earlier on this thread. I even no longer needed to use the *irqpoll* option on the boot command line.

I will be pleased if anybody can benefit from this. I reckon at least those with a similar motherboard are likely to. If you are having trouble with your IDE CD-ROM device during install, look for this option in your BIOS, or an equivalent ont.

As a final note, I observed that the BIOS setting change must not be reverted after the installation is complete. Doing so caused problems upon loading of the kernel.

Cheers,

-- 
Ney André de Mello Zunino

---

### Post by Ocxic on 2006-03-07
i have the enhanced detting on in my bios workin fine, check for the IDE PCI busmater being enable, it should be

---

### Post by Zunino on 2006-03-07
[QUOTE=Ocxic]i have the enhanced detting on in my bios workin fine, check for the IDE PCI busmater being enable, it should be[/QUOTE]
PCI busmastering is also enabled in my BIOS, so there must be something else. What I can tell is that, in my case, switching the *IDE mode* from *Compatible* to *Enhanced* will cause the installation to fail, always. Switching back will make it all work fine.

But anyway, thank you very much for the remark.

Regards,

-- 
Ney André de Mello Zunino

---

