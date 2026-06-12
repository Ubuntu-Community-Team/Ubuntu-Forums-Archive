---
title: "can't mount installation CD-ROM - i386"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by UphillSkier on 2005-11-25
I am trying to install 5.10 from a freshly burned cdrom.  We progress through language selection and keyboard layout, but fail on "Detect and mount CD-ROM" step with a message "Your installation CD-ROM" could not be mounted" .  This is strange because the machine already found the cd-rom to start the installation.

If I exit to a shell and do
mount /dev/cdroms/cdrom0 /cdrom 
I get the message
mount: /dev/cdroms/cdrom0 is write-protected, mounting read-only.
(repeated three times)
mount: Mounting on /dev/cdroms/cdrom0 on /cdrom failed: Invalid argument

If I do
mount -t cd9600 /dev/cdroms/cdrom0 /cdrom 
I get
mount: Mounting on /dev/cdroms/cdrom0 on /cdrom failed: No such device

Searching this forum on "mount cdrom"  yields one thread with a similar problem on a ppc instead of a 386.   That thread doesn't seemed to have reached a resolution.

I hope someone can help with this because I am desperately trying to install Breezy on my machine at work, and I need to get it done soon.

---

### Post by UphillSkier on 2005-11-25
Curioser and curioser...

I went home, got the preview disc I had used to install my home system, brought it back to the office and lo and behold ... it mounted the cd-rom with no problem.  This is really a puzzle to me, but at least I can keep on trucking...:smile:

---

### Post by famwennink on 2005-11-26
Hello,
I have the same problem, 
The same problem i did have with Knoppix 4.0 
There was the solution to start with the option "dma"
But i can't find a treath about dma for Ubuntu

---

### Post by dsjas297 on 2005-11-26
I couldn't directly boot from the cd drive either, but since I have a floppy drive in my computer I was able to use the RIP floppy to boot the Ubuntu installation from the cd drive.

[http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)

scroll down to the section of the floppy rescue system.

---

### Post by tebibyte on 2005-12-17
I have the same problem on a dell 2350 (I believe. I don't have the computer with me) when installing edubuntu from a cd rom i burned at home. The install manager starts, and asks me for language, keyboard , and exctera. Then it comes up with the message " unable to mount cdrom" (or something very similar). 
	I select "try again". no luck. I tried rebooting multiple times. No luck. I have to abort the installation. No matter what I do I can't get the installation past that point. Can someone please help me. Thank you very much in advance.

---

### Post by Darkhack on 2005-12-17
I too have this problem.  Here is my situation.  I have two drives.  A CD/DVD-RW  combo and a CDROM.  I get the "Failed to mount" message when I use the CDROM however I am able to mount the CD when I use the combo drive.  However, it freezes when scanning it.  It only gets to 22% and freezes.  This isnt the install, just the scanning part that is directly after the mounting.  I've tried tinkering my BIOS and everything.  Are there any boot parameters that can fix this?  I am running a Athlon64 3200+ and this occurs with both the i386 and AMD64 install CDs.  Also I have to use "linux irqpoll" at the boot prompt to even get to the installation screen if that makes any difference at all.  Like maybe its an IRQ issue that causes the CD problems???

---

### Post by UphillSkier on 2005-12-19
Althought I never tried it (because my preview disk worked), I think it's worthwhile trying to burn another installation disk at lower speed.  

good luck

---

### Post by tebibyte on 2005-12-19
[QUOTE=UphillSkier]Althought I never tried it (because my preview disk worked), I think it's worthwhile trying to burn another installation disk at lower speed.  

good luck[/QUOTE]

OK thank you, I'll give it a try. :smile: 
---
Just for refrence, My CD rom drive was:

_NEC CD-RW NR-9300A

---

### Post by tebibyte on 2005-12-20
Still no luck. I burned a new CD as carefully as I could. I did it at 2X. It is not the CD thats the problem. Is there any extra steps I need to take because its a dell? Thank you in advance.

P.S. 
I might try to install a diffrent CD-Rom drive, to see if that helps.

---

### Post by tebibyte on 2005-12-29
It's been a week, and there still is no solution mentioned. When school starts up again I'm going to try to installing edubuntu from windoze.

---

### Post by LittleGiant on 2006-01-07
I'm having the same problem, does anyone have a solution for this!?

---

### Post by skinnysweaty on 2006-01-08
I just resolved this issue for my situation; I can't guarantee it'll work for you, but here's my situation:

I was working with a CD burned generic Office Depot CD-R at "high" speed (I think for the PC it was burned at 32x, which isn't a super-screaming speed).  I successfully used that CD to install on a five-year old Dell, so I figured, "Hey, this is ok."  I tried to now load that CD on another "frankenstein" project box which has a seven year-old CD-R/W and was getting sporadic mounting problems.  I took the advice earlier mentioned and burned at the slowest speed possible in my Win box (4x) on DIFFERENT CD-R media (this time a cheap TDK) and it's a world of difference; no mounting issues, everything loads faster (bizarre, I know) and things seem to be fine so far.

My advice: burn at the slowest speed and try different media, especially if you're working with an older CD-Rom drive.

---

### Post by HorrorStory on 2006-01-11
[QUOTE=dsjas297]I couldn't directly boot from the cd drive either, but since I have a floppy drive in my computer I was able to use the RIP floppy to boot the Ubuntu installation from the cd drive.

[http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)

scroll down to the section of the floppy rescue system.[/QUOTE]



I created the boot floppy disk and booted it with the command line of:

linux root=/dev/hdc

Returns error: Warning Unable to open an intial console
Kernel Panic - not syncing: No init found
Try passing init= option

I've tried a few suggested "options" but I'm not sure if they are even correct.

Suggestions?

I'm trying to boot the uBuntu LIVE CD

---

### Post by tebibyte on 2006-01-12
It turn out the problem was with my disk. It  may have been the DVD burner. MY dad burned a copy at work (with windoze) and it worked fine. My dvd burner was a HP DVD 300e, I used a Fuji film cd-r that came in a stack of slim cases. I burnt multible failed install disks with that drive, so it wasn't just chance.

---

