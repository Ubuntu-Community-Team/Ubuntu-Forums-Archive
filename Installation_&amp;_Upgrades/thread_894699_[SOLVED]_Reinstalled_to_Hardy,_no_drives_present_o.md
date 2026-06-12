---
title: "[SOLVED] Reinstalled to Hardy, no drives present or accessable."
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by robelliott2125 on 2008-08-19
Well,

Last night, after having some problems of using Vbox, I finally gave in, and started to update to Hardy.

Hardy Froze on something, which I can't remember now, however being the lazy and irresponsible ex-windows user I am, I simply switched the computer off regardless, more to deal with it in the morning.

I came down this morning to find no FSTAB, to which I ended up giving up and mearly reinstalling, luckily my /home is on a seperate partition.

So, reinstall done, I can't change my Refresh Rate, Resolution or even select my Video Card / Monitor.
So with that, bored and fed up, I rebooted to my XP install, to then find everything on my Music, Storage and Backup drive has disappeared!

Windows can only see .trash, to which its got some files which I deleted last night, but nothing else.

No backed up files, no music, nothing...  Gone.

<Enter sinking feeling here>

All my website work gone, all my photos, gone.

Needless to say, I'm not happy, I'm not amused, and I'm extremely upset now, because what was a seperate drive for Backups, has become pointless.

My storage drive, which is an overflow drive, gone.

Trying to access GPart is proving useless, since its mearly stating "theres a prob" (see image).

I really hope someone can help, as thats three drives i've lost else, and no way of recovering the data.

---

### Post by robelliott2125 on 2008-08-19
Anyone?

---

### Post by wpshooter on 2008-08-19
I am really sorry that this has happened and I hope you can manage to recover your information SOMEHOW.

But what I wanted to point out is that things like this is the very reason that I have always said and continue to this day to say that a single computer should NOT have multiple operating systems installed on it !!!  And I know that there are lots of users out there that will rage about how they are using SEVERAL different O/S on the same computer and I say good luck to them but IMO, eventually they may really need it.

My only advice would be that if you want to continue to use M/S windows, is to see if you can come up with the funds to buy yourself another puter.

---

### Post by robelliott2125 on 2008-08-19
> **wpshooter said:**
> I am really sorry that this has happened and I hope you can manage to recover your information SOMEHOW.

But what I wanted to point out is that things like this is the very reason that I have always said and continue to this day to say that a single computer should NOT have multiple operating systems installed on it !!!  And I know that there are lots of users out there that will rage about how they are using SEVERAL different O/S on the same computer and I say good luck to them but IMO, eventually they may really need it.

My only advice would be that if you want to continue to use M/S windows, is to see if you can come up with the funds to buy yourself another puter.

Thanks wpshooter.

Tbh bud, I was slowly coming onto Ubuntu, and the only reason why I was keeping Windows, was mearly for SAM Broadcaster (till I could install into WINE).

So yes, I had multi-OS's, however the XP installation wasn't the cause of this issue.

The drives were still in NTFS format, which was something I had planned to change once the final move to Ubuntu was done, however I had to reinstall Ubuntu this morning, which is when all my files have gone.

I would have to say, this would make me just do the typical move, and go back to Windows, however I'm someone who tries to persevere, and ask, why this happened.

The photos, as much as I am annoyed and upset my files have gone, I can try and build them up again, none of them were for work / college / school etc, so its rebuildable (especially since my book which I am working on was in my <luckily> /home partition).

My main problem is, at the minute, is my backup drive (which was for Linux only), my Music, and my Storage drives have no data, and I want to know why, and if i can get them back, plus, why aren't they showing up in my Computer?

---

### Post by robelliott2125 on 2008-08-20
Anyone else???  Still needing my drives back, with/out the data.

---

### Post by elect82 on 2008-08-20
Hi 
I couldn't exactly understand your problem, but i guess u r trying to   install hardy and lost your data. it might be the case that when u install it, it has formatted that drive and hence u might be lost data. if u had lost data then u can recover that data. better not to write any thing on the disk otherwise it makes difficult to recover the data. i have done same mistake dual boot vista with ubuntu and it format my whole drive. i have restarted my computer and boot from live CD (cd in which ubuntu installed to the computer) and then i have download testdisk package from website. and then using test disk i have recovered all my data which was lost due to formatting.  u can get better help from ubuntu help and in that go to community and search for title "data recovery"i m sorry if this answer is not what u r looking for.

---

### Post by robelliott2125 on 2008-08-20
> **elect82 said:**
> Hi 
I couldn't exactly understand your problem, but i guess u r trying to   install hardy and lost your data. it might be the case that when u install it, it has formatted that drive and hence u might be lost data. if u had lost data then u can recover that data. better not to write any thing on the disk otherwise it makes difficult to recover the data. i have done same mistake dual boot vista with ubuntu and it format my whole drive. i have restarted my computer and boot from live CD (cd in which ubuntu installed to the computer) and then i have download testdisk package from website. and then using test disk i have recovered all my data which was lost due to formatting.  u can get better help from ubuntu help and in that go to community and search for title "data recovery"i m sorry if this answer is not what u r looking for.

Thanks for your reply Elect.

Basically, I have my Ubuntu / Windows drive, 3 partitions for Ubuntu (Swap, /, and /home) then I have one for Windows (10Gb), then within the PC, I have 2 more physical drives, one split in two (Backed up Data from Ubuntu and Music), the final drive is a Storage drive.

The data on my Backup Partition, Music and my Storage Drive has all gone.

During installing Hardy, I left the other partitions alone, as I did when I originally installed Gutsy.

Due to a problem while upgrading from Gutsy to Hardy, I lost my /home partition, booted into the Live CD, and mainly from suggestions from people on IRC, I fully Reinstalled Hardy on a fresh Install, but ensuring my /home was untouched.

The only drive which I commanded the install to format, was my / (root?) partition.

So I'm annoyed that the drive I used to backup my data, has proved worthless, my storage drive is gone, and my music (no biggy on that).

Plus, I can not see the drives in Places > Computer, only my Filesystem.

Under mnt, theres no Storage drive, No Music and no Backup.

So if I can just get the drives working, i'd be happy.

If I could get the drives working, and also have my data, I'd be extremely chuffed.

Hope this helps.

---

### Post by robelliott2125 on 2008-08-20
I've just booted back onto a Live CD, and mounted all the drives.

Backup - has data on there, but not see-able.
Music - Same as above
Storage - Again, same as above.

With View Hidden folders enabled, I can see the .trash-robert folder, but theres nothing else.
Properties on each drive shows there is used space, and unused, which off the top of my head, I'd say is about right for the data on each drive.

Any ideas if I can salvage them somehow?

---

### Post by spitfireVII on 2008-08-20
from experience, you should attempt to get a hold of a disk recovery program that will read the "raw sectors on your hard drive"
but this can prove useless, still worth a try.
there is a good chance you will recover what you needed if you didn't write over the section, sections sector, sectors.
P.S if you can get one for Linux your probably set, but if you try to install windows... lets just say I wouldn't risk random sectors being written over.
I think so because I simply cannot fathom how the 2(Linux,windows) interact with each other on the hard disk platters.
editing to add idea!.
how bout, pul your drive, take it to your friends house, stick it in his computer and get some  recovery program to scan your* hard drive?
just a thought

---

### Post by J$oney on 2008-08-20
Download the Helix Live CD, its a Knoppix based distro, there are utilities directly related to data recovery on there including autopsy. I'm not sure how much it will do for you, but I would surely give it a chance. You should be able to recover all data to an image, and then just recover that image back to your drive. GOOD LUCK:popcorn: Hopefully that helps you.

---

### Post by robelliott2125 on 2008-08-21
> **J$oney said:**
> Download the Helix Live CD, its a Knoppix based distro, there are utilities directly related to data recovery on there including autopsy. I'm not sure how much it will do for you, but I would surely give it a chance. You should be able to recover all data to an image, and then just recover that image back to your drive. GOOD LUCK:popcorn: Hopefully that helps you.

Thanks guys,

I've formatted the drives since this now, and was meant to have solved this last night.

I swallowed my pride, and did it, there wasn't anything really important, luckily thats all on my /home drive.

Thanks anyway guys.  Problem solved.

---

