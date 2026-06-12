---
title: "Computer Reboots after pressing enter at &quot;Install Ubuntu&quot;"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by Burny on 2007-11-09
So, I decided to play with ubuntu and it dislikes me.

I have downloaded both the normal and alternate .ISO and burned them several times, they all come to the same conclusions.
I have even tried to use the earlier 7.04 realease to see if it was just this [7.10] release that wasn't working with me.

I have even tried Unetbootin to try and do it without the LiveCD disk but even that went in the same direction.

So this is what happens:

The CD Boots and it comes up with the main menu, all is well until i press enter on the start or install ubuntu button, it says something along the lines of "Launching Linux Kernel" and loads to 100%, after this there are a few flashes of the underscore bar at the top left and my PC then reboots, even on the safety mode option aswel as the alternate version. 

I have really tried all the things that I read about, sorry for asking but this is really my last resort.

PC Specs:

Intel Pentium D 3.2 GHz
2 GB Ram
512mb GeForce 7600 GS graphics card
3 HDDs, 
C: running Windows
D: for storage
E: hopefully got ubuntu
running Windows XP Pro 32bit with SP 2 [fresh install today]

I'm not too sure about this but my friend told me that maybe I should take one stick of RAM out and leave it with just 1GB? I'm not sure if this would make much of a difference, so i'd like to hear from you before I go and open up my pc.

Thanks.

-Burny

---

### Post by sloggerkhan on 2007-11-09
I've had friends with similar problems. In one case, turned out the RAM was fried and couldn't pass memtest. In the other, we had to unplug some peripheral. So it's the kind of glitch that could be from anything, maybe even a bad CD. So far as the peripheral thing goes, some USB stuff seems to have random weird effects. I have  a USB hub, for example, that I have to unplug to boot my computer. If I plug it in before the progress bar screen starts, my boot will pause until I unplug it again.

---

### Post by Burny on 2007-11-09
I've tried 4-5 CDs at different burn speeds to be safe, they were even bought today.

---

### Post by Pumalite on 2007-11-09
Follow this:

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum of iso, burn at 4x, check CD for integrity before install.
If not, try the CD's in different computer, clean the lens of your burner or change it if necessary.

---

### Post by Burny on 2007-11-09
Tried using that burner at 4x burn speed, checked the hashes for both of the files [normal/alternate] and they're fine, the verification should be fine because I tell it to verify the disk.

It shouldn't have anything to do with the DVD drives, I tried it on both and the outcome was the same, i'm only saying i'm sure of this because I tried Unetbootin and it was the same, you don't even need a cd/dvd drive to install it that way.

As for trying the CDs on a different computer, i'll have to try the next time around one of my friend's houses.

I've also tried removing one of the DDR Rams from it's slot and trying each one independently, that also failed.

Any other ideas? =/

---

### Post by Laserbeast on 2007-11-09
Sounds like bad RAM to me. Does your computer currently have an OS installed? Boot into one and run a full memtest. 

Just for the sake of argument, what CD-Rs are you using and on what CD/DVD-ROM(s)?

---

### Post by DarkDancer on 2007-11-09
I would boot the computer with the live cd up to the point where the menu comes up and choose memtest. Let it run over night. I have recently found two computers that were acting flaky and memtest found the problem (bad ram). If nothing else it will set your mind at ease.

---

### Post by Burny on 2007-11-09
Freshly bought Imation CD-R 700MB 52x
Burning with:  DVD-RW 16X HL-DT-ST DVDRRW GSA-H20L. [HP burner]
other DVD drive I use is called IDE-DVD DROM6216 which is also made by HP.

---

### Post by Laserbeast on 2007-11-09
> **Burny said:**
> Freshly bought Imation CD-R 700MB 52x
Burning with:  DVD-RW 16X HL-DT-ST DVDRRW GSA-H20L. [HP burner]
other DVD drive I use is called IDE-DVD DROM6216 which is also made by HP.

Do you have any other CD-Rs you could try besides Imation? I had some terrible problems with those on my Memorex Dual-Layer DVD-RW. That's probably your problem if it's not the RAM.

---

### Post by Burny on 2007-11-09
No, I don't have any other CDs that I can use, I only bought these today for this purpose >_<.

---

### Post by Laserbeast on 2007-11-09
> **Burny said:**
> No, I don't have any other CDs that I can use, I only bought these today for this purpose >_<.

Well that bites. Run the memtest first, make sure that isn't your problem. If it's not, return the disks where you got them and try another brand?

---

### Post by Burny on 2007-11-09
Yeah, I'll run the memory test now while I sleep, I'll tell you the results in the morning.

Thanks for your help.

-Burny [Goodnight]

---

### Post by Burny on 2007-11-10
Alright, I ran the memory test all night, it did it 10 times and there were 0 errors.

Any other ideas or should I just give up? =/

---

### Post by Burny on 2007-11-10
So, I tried to see if it was just ubuntu that was playing up so I downloaded Fedora and burnt it to a DVD and booted from it, SAME problem with that linux too.

I also took out all unnecessary PCI things I could and it still didn't make a difference.

Could it be that my computer just isn't compatible with any type of linux?
or that Windows has somehow made it so that I can't install linux?

I'm really really out of ideas now.

---

### Post by Pumalite on 2007-11-10
If you have Vista; it's probably Vista. If not, it's your computer.

---

### Post by Burny on 2007-11-10
Friend finally found a fix for it.
All it needed was 

acpi=off and it worked fine, now my only problem is that my USB mouse doesn't work on the desktop :P I'll try and figure it out now.

Thanks for all your help.

---

### Post by Pumalite on 2007-11-10
You are welcome. Good luck.

---

