---
title: "Restore?"
date: 2006-04-25
forum: Installation &amp; Upgrades
---

### Post by Capheind on 2006-04-25
Is there a way to generate some kind of restore disk? I know Ubuntu has an OEM install now so a restore disk would be quite helpful.

---

### Post by Ocxic on 2006-04-25
your install disk, is your "restore" disk, there is really no way to restore ubuntu and if it would be anything like windows, it would do more harm then good. either fix whatever problem you have, or formate and re-install. if you have your home folder on a seperat partition re-installing is reall easy scince you don't loose any of your data, themes, e-mails, or other stuff in your home folder.

---

### Post by Capheind on 2006-04-25
First I'm not speaking for me, I can usually fix things without any kind of restoration or reinstall. What I am talking about is for other users I may set up with ubuntu systems. Just about every consumer OS on the market that comes pre-loaded on a system has a way, with the OEM disks, to restore their system without having to reinstall or reformat. Admittedly this is very easy with a home partition but there are often reasons you wouldn't want more than one linux partition. But I have kinda answered my own question (just make a modified disk with the option to use a preconfigured install script)

---

### Post by Ocxic on 2006-04-26
well you could make an image of there hard drive or root partiton, after you get everything configured, and all they would have to do is dd the image to the drive or root partiton to restore everything back to installation point but with all of there data, minus anything that happend scince the backup.

---

### Post by Herman on 2006-04-26
[.......... hda1.............][sw][ hda2 ]...........................................................................................|

Here's a trick, say you have an new install of Ubuntu on partition hda2, only about 3 or 4 GB in size. You add all your software, tweaks and customisations first, but not too many files yet.

Now, using GParted LiveCD, you copy hda2 and paste a copy of it up at the end of your hard disk. Like so:
[.......... hda1.............][sw][ hda2 ]................................................................................[ hda3 ]

It gets named hda3. That's okay, just leave it there and ignore it for now...

Resize hda 2 to the size you want (room for your files).
[.......... hda1.............][sw][......................................... hda2........................................... ][ hda3 ]

Now if anything happens to hda2, you have all your files backed up anyway don't you? If not you can rescue them with a Live CD anyway. Then just delete the whole hda2 partition.
[.......... hda1.............][sw]_________________free_space_______________________[ hda3 ]

Then using GParted Livecd again, copy your hda3 and paste it where hda2 used to be and it becomes your hda2 again, complete with tweaks, setting and customisations.
[.......... hda1.............][sw][ hda2 ].................................................. ..............................[ hda3 ]

 Just resize it to the desired size again and replace your files and you're back to normal. Time taken-maybe five minutes.

[.......... hda1.............][sw][....................................... hda2......................................... ][ hda3 ]

Simple! It's also a lot faster and more effective than 'system restore' too! ;) Regards, Herman :D

---

