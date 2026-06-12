---
title: "RAID 0 question"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by fin on 2006-07-05
I have a Sony Vaio [VGC RC210G]("http://www.pcmag.com/article2/0,1759,1943744,00.asp") that runs a pair of SATA hard drives in a RAID 0 array. What that means... I have no idea.

How can I instruct my computer to use one HD for Windows and the other for Ubuntu... dual-boot type thing?

I have tested the Ubuntu live cd on this machine and everything works great (loads rather slowly, however... on my last computer it loaded much faster, tho the machine itself was much slower than this machine!), but I am still not as comfortable with linux as I should be to totally wipe Windows from my drive(s).

While I am very happy with this computer, Windows Media Center has several bugs, and crashes often (every other day or so. Once, three times in one day), even with the latest updates.

Thanks in advance.

---

### Post by scxtt on 2006-07-05
RAID0 (striping) basically copies 1/2 the data to 1 drive and the other 1/2 to the other drive - writing faster overall ... so your 2 disks will appear as one ... i can't get Ubuntu to recognize my 2 SATA drives in a RAID0 config (mb has hardware RAID0 and RAID1) -- so i don't know how you'd stop it, if it's not from your bios or an intentional software RAID ...

---

### Post by fin on 2006-07-06
[QUOTE=scxtt]RAID0 (striping) basically copies 1/2 the data to 1 drive and the other 1/2 to the other drive - writing faster overall ... so your 2 disks will appear as one ... [/QUOTE]

Oh. Thanks for the info! 

[QUOTE=scxtt]i can't get Ubuntu to recognize my 2 SATA drives in a RAID0 config (mb has hardware RAID0 and RAID1) -- so i don't know how you'd stop it, if it's not from your bios or an intentional software RAID ...[/QUOTE]

I don't want Ubuntu to recognize both drives... just one. I want the other to run Windows, until such a time that I can confidently raze Windows and run Ubuntu primarily.

Sorry if I'm not making sense... I barely understand my keyboard #-o

---

### Post by scxtt on 2006-07-06
well if you have a hardware RAID (supplied by your motherboard or maybe an add-on card), you should be able to set it up during boot (mine was set to NOT use RAID by default, i'd be surprised if any do) by pressing a "function" key (mine's F6 i think) ... i can't think of any reason why you'd be 'stuck' in a RAID0 config if you have 2 separate disks ...

EDIT: i looked at the specs in the links you provided, and it is intentionally set to RAID0 - but i can't imagine you're stuck like that ... too bad i can't mess w/ your computer to get a better idea ...[quote=from the article]A door that's easy to open without tools exposes a pair of SATA hard drives in a RAID 0 array and two more empty drive bays.[/quote]

---

### Post by fin on 2006-07-06
[QUOTE=scxtt]well if you have a hardware RAID (supplied by your motherboard or maybe an add-on card), you should be able to set it up during boot (mine was set to NOT use RAID by default, i'd be surprised if any do) by pressing a "function" key (mine's F6 i think) ... i can't think of any reason why you'd be 'stuck' in a RAID0 config if you have 2 separate disks ...[/QUOTE]

Well, that's the thing... I understand that, currently, my data is spread across these two HDs... I'm looking for a way to seperate the two (firstly transferring all data from both to one, if possible), and make drive A Windows and drive B Ubuntu, with the option to choose one or the other at boot.

I'm willing to reinstall WMC if need be. I can always back up important data.

---

### Post by scxtt on 2006-07-06
right, that's what i'm saying -- seems like you have a hardware RAID0, which you'll need to "dismantle" when you boot the box, for me it's something i can edit when i boot my box - maybe you need to look @ the manual for your motherboard ...

and i'm almost certain you'll need to get ALL files you want to keep off your box before you break the raid since the data is split between them, meaning a 3rd storage device will be needed ...

that box almost seems setup to use RAID0 'no matter what' -- it might be easier for you to just stick another drive in there ...

---

### Post by fin on 2006-07-06
[QUOTE=scxtt]i'm almost certain you'll need to get ALL files you want to keep off your box before you break the raid since the data is split between them, meaning a 3rd storage device will be needed ...[/QUOTE]

Okay, I may give it a go. Thanks for your help.

Also - I have an 80 gig HD not being used, and considered sliding it into one of the bays, but according to links I read, if you add a 3rd HD to a RAID0 array, the system will report all drives as being the smaller size... this make sense?

If it is not true, the I'll just do that. Much easier.

---

### Post by scxtt on 2006-07-06
not sure - but i doubt you'd *have to* add the 3rd drive to the raid - and all that'd do is compound your problem ...

---

### Post by fin on 2006-07-06
[QUOTE=scxtt]not sure - but i doubt you'd *have to* add the 3rd drive to the raid - and all that'd do is compound your problem ...[/QUOTE]

So, just slide the 3rd drive in, boot to bios and make the changes there? Kinda makes sense.

I'll wait until tomorrow before attempting anything... in case anyone else has more info I can use.

Thanks, scxtt ;-)

---

### Post by scxtt on 2006-07-06
all you'll really need to do, IMO, is put the 3rd drive in (make sure the bios recognizes it) and install ubuntu there -- leave the raid alone, then you don't have to worry about messing it up / losing data ...

---

### Post by fin on 2006-07-06
[QUOTE=scxtt]all you'll really need to do, IMO, is put the 3rd drive in (make sure the bios recognizes it) and install ubuntu there -- leave the raid alone, then you don't have to worry about messing it up / losing data ...[/QUOTE]

Cool... will do. Thank you for your help! I'll let you know how it went ;)

---

### Post by scxtt on 2006-07-06
best of luck -- keep us posted, next time i reinstall i want to get RAID0 working (preferrably hardware, but i don't think my chipset is supported) so i'll probably go w/ software [it's quasi-working now, but not being utilized] ...

---

### Post by fin on 2006-07-06
I'm dumb.

Turns out the 80 gig drive I had sitting around is IDE, not ATA. So it is useless. At least I learned the difference.

I'll pick up a cheap drive this weekend and give it a go.

---

### Post by scxtt on 2006-07-06
i've never seen a motherboard that has SATA connections and doesn't have IDE connections ... i can't think of any reason why you can't stick an IDE drive in there ... IDE/ATA = same difference ...

---

### Post by AndyM3 on 2008-04-10
Well, I've got the same computer, and the HDD bay has only SATA connections.

---

