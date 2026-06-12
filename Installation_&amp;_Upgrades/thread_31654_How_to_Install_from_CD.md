---
title: "How to Install from CD?"
date: 2005-05-04
forum: Installation &amp; Upgrades
---

### Post by im4u2nv on 2005-05-04
Hi there...i've downloaded hoary install cd for PC...

when i put the cd and boot it up...it detected my usb land card BUT it directly go to DR-DOS...

what is the next step? i have no idea what so ever...tried to find from internet but the CD should actually start the installer and go to the installation process.

in my case...it goes to A PROMPT from dr.dos...any idea why?  ](*,) 

i've checked MD5 of my CD and everything are fine...

please help me...

thx in advance

---

### Post by jameswilhelm on 2005-05-04
It sounds like you are still booting from the hard drive (or the floppy, perhaps?). On my  PC I have to change bios settings to get it to boot from the CD.

---

### Post by im4u2nv on 2005-05-04
nope..i've boot from CD directly...my other hard drive got XP installed...i'm trying to install in my separate HD...

when i boot from CD then it detected my usb lan card and then enter the dos mode...

---

### Post by jameswilhelm on 2005-05-04
Do you mean Linux command line mode or, litterally DOS mode? You cannot enter DOS mode from the install.

I've had problems in the past where an install would not configure X as it could not find a driver for my graphics card. In that case (Mandrake) I ended up in command line mode. It still did the install, and all non-graphics things workd, but I would have had to then set up the graphics manually.

---

### Post by im4u2nv on 2005-05-04
apprarently i burn the cd as bootable..that's why it came out w/ DOS winblows...sorry about the mistake...anyhow i burn the cd again and now i can boot to the installer..

but the new problem is after i choose my keyboard lay out, the installer said that it can't load installation from the cd eventhough it had detect my hardware and cd rom drive (it has checked over pool, etc, i know because i saw the bar went to 100%) ...i checked the integrity and it said no valid ubuntu cd is detected...

my md5sum only give me this 1 error:

.\pool\main\m\mozilla-firefox-locale-all\mozilla-firefox-locale-en-gb_1.0.1lang20050309ubuntu1-0ubuntu3_all.deb ERROR: C:\Documents and Settings\Alfred\Local Settings\Temp\WinISO\.\pool\main\m\mozilla-firefox-locale-all\mozilla-firefox-locale-en-gb_1.0.1lang20050309ubuntu1-0ubuntu3_all.deb does not exists.

it's because when i burn the cd, it make that file

pool\main\m\mozilla-firefox-locale-all\mozilla-firefox-locale-en-gb_1.01

instead of the long name..

any idea how to fix it? does it matter if the firefox can NOT be installed?

---

### Post by im4u2nv on 2005-05-04
forgot to add...

i can go to the linux line mode...but i just dunno how to continue the installer...(i'm a newbie here :) )

oh..and i can take out the cd in the cd-rom..i have to reset my computer then i can take out the cd...i think the ubuntu installer locked the cd or something?  ](*,)

---

### Post by Dr Gonzo on 2005-05-05
It sounds like you have a bad cd.  Try burning it from a different program.

---

### Post by jameswilhelm on 2005-05-05
Yes, it sounds like a bad CD. Another program, perhaps, or just try another disk and burn it at low speed. The quality of the media is not always that good.

---

### Post by im4u2nv on 2005-05-06
i tested md5sum of my CD and it's all normal...browsing using windows explorer is also ok...

installation start normally but only until step detecting cd-rom...i've used 4 CD-ROM w/ not much luck...same problem...

is it possible taht the media (cd) is corrupted and somehow unreadable in linux eventhough md5 and windows explorer worked normal?

is it my image? or the cd media?

---

### Post by jameswilhelm on 2005-05-07
Almost sounds like a hardware problem, but then why does it work in Windows and for a while with the Hoary install? Linux should read any filesystem as well as Windows. In my experience it is often more reliable in reading filesystems than Windows. But you never know.

Have you tried to install Warty or another distribution or to read the CD from another distribution? What happens if you boot a Live  CD - Knoppix or Hoary Live CD?

---

### Post by kosmic on 2005-05-07
Does your Drives are SATA ? insted of ATA, there is a small problem with SATA drives you need to go to BIOS to change a parameter so the Ubuntu CD can find the CD after enter the install process

---

### Post by im4u2nv on 2005-05-07
unfortunately i don't have others distro available yet...i need to download that in my office...

anyway i tried to re-download the ubuntu again and it has the same problem..  ](*,) 

is it because i have 2 different HD? or my wireless LAN? i'm gonna try to take those and see what's happening...

---

### Post by im4u2nv on 2005-05-07
noope...mine is regular ata100 drive...it is hooked to the RAID port though...but i want to install to my HD that is hooked to the regular ata controller...

and the CD does work for the 1st 3 step..it even detected my hardware and try to read the cd...it stuck afterward...

---

### Post by im4u2nv on 2005-05-09
hi there...just downloaded the LIVE cd and it works fine...

now i'm trying to download install cd from different location...i picked US before..and now i try UK...the download should be done tomorrow...hopefully i have no problem :)

thx

---

### Post by jameswilhelm on 2005-05-09
I doubt that another image will give different results. I know very little about the ins and outs of the hardware, but I suspect there is something to do with your CD drive that Hoary doesn't like - as kosmic suggested. Try to install a different distribution or try different CD drive if you have one lying around. I can't comment on bios settings as I normally just fiddle around with them until something works.

CD drives multiply around here at roughly the same rate as coat hangers - there always seem to be more in the cupboard than what I put there! Perhaps you're not that lucky?   :)

---

### Post by im4u2nv on 2005-05-10
hi there...guess what? my download is finished and i burn again using nero burning rom (was burning using nero oem at home) i burn using nero full in my office and wooohhhooooo the installation runs through the part that was stucked before...(yeap it stucked both in my office and my home)

i'll try to install in my machine at home tonight...still crossing my finger here..

---

### Post by jameswilhelm on 2005-05-11
Hi, im4u2nv,

How did it go? I'm curious.

---

### Post by im4u2nv on 2005-05-12
hi..sorry for the delay...after i downloaded it..and it worked wonderful...i can install ubuntu...but the problem is when i install GRUB...it said it will installed on MBR and HD0....and it totally blew everything..i can't login to windows nor to ubuntu...it just keep restarting...there's an error message saying something about grub but i can't read it because it was too fast then it restarted my comp..

anyway i reinstall everything and choose lilo...it work fine now...

any idea how to install grub? or fix the mbr? right now i'm still trying to search in the forum about grub...

---

### Post by jameswilhelm on 2005-05-14
In Win98 of DOS you can fix the MBR by booting from a floppy and running:

A:\fdisk /MBR

This will probably work in XP, but I've never tried it - sorry - I switched to Linux before XP.

I'm not an expert, so it is difficult to figure it out away from the PC. I've always used lilo, so grub is new to me.

Good to hear you've got things going in the end.

I see in the grub documentation they don't guarrantee that it will install correctly.

I found this link that gives a lot of info:

[http://geodsoft.com/howto/dualboot/grub.htm](http://geodsoft.com/howto/dualboot/grub.htm)

Let me know how it goes. Sorry I can't be more help. Perhaps you should start a new thread for your grub problem.

---

