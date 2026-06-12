---
title: "I think i need a new HDD"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by push_harder on 2008-01-23
Hi all.

I reformatted the ubuntu partition in Vista's disk management.
Then i rebooted and got error 17 from GRUB
I messed around with TestDisk and fixed a few things
Then i re-booted and got error 15.

So i inserted my XP (yes XP not Vista) and entered Recovery Console
I did fixboot and FIXMBR

And then CHKDSK.
I got something back saying that there is errors that  CHKDSK cannot recover.

So i rebooted and then got: 'The volume appears to contain one or more unrecoverable problems'

And i've also tried to run Super Grub but it just hangs at the loading stage.

I'm beginning to think my HDD is completly rooted and i can't reformat because XP installation now says that it can't find a HDD to install on.

And ubuntu installation gives me an error at 69% explaining that my HDD or CD must be faulty, but i've used another CD and still the same thing.

Anyone?
Cheers, Matt.

---

### Post by tgalati4 on 2008-01-23
How old is the drive?  It's possible to have a problem as new drives don't go through a lot of quality control.  Try running  Ubuntu Live CD and see if you can run cfdisk from a terminal.  You might need to perform a low-level format using a manufacturer's tool that can be found on the Ultimate Boot CD.

Don't for get to check your power and ribbon cables.  They sometimes get loose.

---

### Post by Pandemic187 on 2008-01-23
Yeah, that doesn't sound too good. Might be f&#^ed.

---

### Post by push_harder on 2008-01-23
It's an ACER Extensa 5220.
80Gig HDD, pretty much brand new lappy.
It's an hitachi HDD.

I really don't know what to do here =[

Thanks, Matt.

---

### Post by push_harder on 2008-01-23
Oh and now it just reboots continuously just after the Acer BIOS load.
I can still boot from ubuntu live cd and see that theres a C: drive called VISTA, but i can't mount it.

Any idea's?

Cheers guys =]

---

### Post by push_harder on 2008-01-23
Anyone?
x

---

### Post by tgalati4 on 2008-01-23
Hitachi Travelstars are similar to IBM/Lenovo OEM drives, so are perhaps better than others, but overall quality control of most pc components has declined over the past few years.

Go to Hitachi's website and look for a low-level format utility.  I assume you don't need to recover any data off of the drive.  After formating you should be able to reparition and load an operating system.

I did fix to a similar desktop drive by using cfdisk and simply rewriting the partition table as best as I remembered it.  Try making the entire drive an NTFS partition and enable the boot flag, then write it.  Then see if boots.

But before you do that, Boot the Ubuntu Live CD and report what you see in /media or /mnt.

ls /media

ls /mnt

---

### Post by push_harder on 2008-01-23
There was some crack software and movies aswell as my resume, school assignments and various other important financial doco's.

I've just used testdisk to copy them to the flash drive from the live cd

Ha, go TESTDISK!

And i've just found my copy of vista, so i'll try and recover the drive through that.

And i did what you said before but it made no differance, i went into the partition manager on the live cd, and there was a very disturbing Exclamation mark next to the NTFS VISTA partition, i had a look in and it said alot of **** about missing clusters.

ah well, aslong as i have my important files, i suppose i'm happy =]

Cheers for the help mate, and i'll definetly be trying ubuntu again soon.

---

### Post by push_harder on 2008-01-23
Well, after 2 days of ******* around.
I have the solution.

INSERT THE VISTA DISK AND REPAIR THE C:/ DRIVE!

It did take 6 attempts and but now Vista's running just the way used to, perfectly, and i plan to re-install ubuntu tomorrow arvo.

Thanks to everyone for helping me. it ment alot!

---

### Post by splot on 2008-01-23
If the HD is sata, you may continue having problems with it.
I've been having problems for 6 months plus, and have had my HD checked out, there's nothing wrong with it.
Just came on to post and ask if there's a fix yet, and saw your post.

Good luck

---

### Post by push_harder on 2008-01-23
Cheers mate, Nah it's an SCSI Drive.
Although it may still cause problems.

But after going through so many damn tutorials and various programs and boot loaders, it's damn'd good to have Vista back.

And i'm reinstalling ubuntu on a much smaller partition.

Once again, if anyone else has this problem, i might be able to help.
I love learning about this ****.

Cheers, Matt

---

### Post by push_harder on 2008-01-23
Could mods mark as SOLVED please.
and thank you to the ubuntu community and Herman =]:)

---

### Post by Battie on 2008-01-23
Hello again.

I'm glad to hear everything is working, but the problems you had with your HDD are worrisome.  Just in case, I would run some diagnostics.

Hitachi should have some available on their website, or you can download the Ultimate Boot Disk and try one of the tools that are loaded on it.

You won't hurt anything by testing it, and if they drive is indeed fault, and the laptop is under warranty, you can get a replacement before something else goes wrong.

Good luck!

---

