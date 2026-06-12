---
title: "How to format?"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2006-07-18
System - Administration - Disks. Right?
I just went there and format is grayed out. I'm not too sure what to do. Long story short, I have 64 bit Ubuntu installed and I want 32 bit. I have the 32 bit Ubuntu on an ISO on this CD here, but I'm having some issues booting from it since GRUB just takes over and does it's thing even though I'm mashing the key to boot from CD (yes my boot sequence is in order). 

How can I just crash this hard drive? It's separate from my Windows drive, so how can I ditch it and start fresh with 32 bit Ubuntu?

---

### Post by scxtt on 2006-07-18
you can install right on top of a current install - no need to "pre format" - that will be taken care of on the new install ... and it's greyed out cause you can't format a mounted disk, especially a disk that you're running the format program on ...

---

### Post by Roasted on 2006-07-18
Okay. How do I overwrite it then? That was my first intention but I wasn't sure how I could do that after I couldn't boot from the CD. :confused:

---

### Post by scxtt on 2006-07-18
it's not possible for grub to boot before the CD drive if you have your BIOS set to boot from CD before HDD ... it's possible your CD isn't bootable, for some reason (a bad burn, 'to fast', ???) ...

---

### Post by Roasted on 2006-07-18
Linux 32 bit is an ISO. I burned it in data format with Nero in Windows XP Home.

My boot sequence has CD ROM before hard drive.

I've booted without touching anything, as well as booted with hitting the space bar over and over. 

I cannot simply boot from the CD. This is the SAME thing I did when I originally got Linux in my system the other day. So I doubt that the CD isn't bootable, because the one I burned 2 days ago was just fine. 

Even if I have to format first, then reinstall Linux, how can I just format this drive? Linux is on it's own drive... how can I format it?

---

### Post by scxtt on 2006-07-18
it's part of the install process to format a partition (or the entire disk) - so you have a / "root" partition and some swap space ... it almost has to be a disk issue (or the wrong iso) if it won't boot from your CD - doesn't have anything to do w/ PRE-formatting your HDD ...

---

### Post by Roasted on 2006-07-18
I know. I formatted my 80 gig drive in Windows, then installed Linux on it with no problems. So if I can get this drive formatted, I know I can install Linux which is my goal. BUT I can't figure out how to format it. So, what can I do? How can I get this rolling? I know the CD is fine - how can I get this hard disk formatted?

---

### Post by scxtt on 2006-07-18
even if you format it, the CD still isn't gonna boot - that is your problem - not a need to format your HDD ...

what iso did you download/burn - the LiveCD or the Alternate? (not that it matters, since both should be bootable) ...

also, if you've got a working XP install, you can format a disk / partition ... hell, i think you can format a drive w/ a bootable W98 floppy, but again - formatting the disk is NOT the issue ...

---

### Post by Roasted on 2006-07-18
I understand that the hard drive won't boot. But back before I had linux on that drive and the drive was just empty and I put the CD in, it would run off of the CD and ask me where I wanted to install linux. I chose the 2nd drive, and the installation went flawless.

Now I've got a new problem, and I'm about to go on a killing spree. I went in windows to the disk management and deleted the partition on the 2nd hard drive where linux was present. Now, I can't get into anything. Even with the 2nd drive completely unplugged from my system, I can't get into anything. Grub gives me an error. First it gave me error 17 until I unclipped the drive, now it gives me error 21. I just want to get into windows and get this shit done. ](*,)

---

### Post by scxtt on 2006-07-18
i'm not talking about your HDD (the one w/ linux, or that had linux til a few minutes ago) - i'm trying to get the point across that your problem lies in your burned CD (the one from the ubuntu ISO) -- if you can't boot from it, it's a problem w/ your BIOS settings or the ubuntu CD -- it has NOTHING to do w/ your HDD being formatted ...

and your new problem is because grub is still on your master boot record ... you can either fix grub w/ an Ubuntu (or knoppix) Live CD and a grub-install ... or you should be able to boot to a DOS prompt and run a **A:> format /mbr** to get windows visible again ...

but your windows install isn't gone, just "lost" ...

---

### Post by Roasted on 2006-07-19
OKAY.

PHEW. I got Linux back in. But it's the 64 bit AMD linux. I used my live cd and installed linux from there and it was the 64 bit version.

IM NOT TOUCHING A DAMN THING this time. What do you folks suggest I do first? The first thing I should do is get to the 32 bit version. My fricken CD with the 32 bit ubuntu ISO is being stupid. I don't know what to do. I extracted all of the files to the desktop but only the folders transfer. I then tried opening the start.exe but I get an error. Maybe it's the ISO? Now that I'm back online with Linux I'm downloading it directly from the web now, so hopefully this will work.

But when I get it up and running (the 32 bit version), what should be my first step?

---

### Post by Roasted on 2006-07-19
:(

---

### Post by scxtt on 2006-07-19
look, i'm not trying to give you a hard time - but you seem intent on not actually listening ...

[QUOTE=Roasted]My fricken CD with the 32 bit ubuntu ISO is being stupid.
I extracted all of the files to the desktop but only the folders transfer.[/quote]so are you finally seeing my point about there being a problem w/ the disk?

[quote=Roasted]I then tried opening the start.exe but I get an error.[/quote]of course you can't open the "start.exe", that's a windows 32-bit executable, the ubuntu LiveCDs can 'preview' ubuntu from windows ...

[quote=Random]Maybe it's the ISO?[/quote]doubtful, most likely the disk you burned it to - not that i do it often (don't have burning problems), but if you think it's the iso, you can run a checksum on the iso after download [of course i'm sure you don't have it anymore, but for future reference] ... i've also heard that burning on 2x-4x will give you a 'better' burn, you might want to try that ...

---

