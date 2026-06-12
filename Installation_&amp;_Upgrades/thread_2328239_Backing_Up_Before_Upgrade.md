---
title: "Backing Up Before Upgrade"
date: 2016-06-19
forum: Installation &amp; Upgrades
---

### Post by willy9 on 2016-06-19
So this problem that I have has not been resolved by any of the possible solutions that I have searched for (my system freezes on when the graphical environment launches, presumably a package problem with my graphics driver but a purge and reinstall did not work among many other solutions). I have given up at this point and have decided to just do a clean install preferably of 16 but I am on 14.04.

My main concern is not maintaining the installed packages through the update (as this does not seem possible with the advent of snap) as it is to preserve my file data (i.e pictures, scripts, documents, etc.). I have a flash drive large enough to hold said files but no means to easily transport between filesystems.

What I need guidance on is how should I go about backing up these files to the flash drive (through command line or live disk) and then doing a clean install of 16 over 14? (I also have an empty partition that I would like to expand the install onto. The partition is on the same drive)

P.S. I have Windows 7, Ubuntu 14.04, and Kali Rolling all on this drive (it's a laptop)

---

### Post by sudodus on 2016-06-19
There are basically two strategies:

1 - backup everything for example with ***Clonezilla***: Make a cloned copy or a compressed image (actually a directory with some files) of the whole drive or of selected partitions.

2 - backup only your personal files and maybe your settings and tweaks: You can do this with a ***dedicated backup program*** or 'manually' with ***rsync*** by copying the directory tree(s) with the files you want to keep.

It seems to me that you would prefer the second strategy. Would you prefer a dedicated backup program, or would you like to learn how to use rsync via the command line?

-o-

By the way, if you mean a USB pendrive, when you write 'flash drive', I should warn, that such drives are not as reliable as hard disk drives, and therefore not the best to store valuable data. You can use it temporarily, if that is your only option right now, but I suggest that you plan to get an external hard disk drive or even better, a high quality 'naked' internal hard disk drive and a box to connect it externally (best via USB 3 or eSATA; USB 2 works too but much slower).

---

### Post by willy9 on 2016-06-21
Thank you for the quick response! And sorry for this late one! Lol

I do mean a pendrive and it is my only option. But I'm only planning on saving stuff that I have made or downloaded. So we're only talking about a few GB's.

On that note; I think that we should do rsync because I don't need the whole partition (only pictures, scripts, etc. on the desktop) and I can't get the graphical enviornment running (I can drop to root command line through recovery since the whole envirnment freezes on full boot). And can we also cover how I would go about doing a clean install of 16 over 14 after the backup?

Thanks again for all the info and the quick help!

---

### Post by sudodus on 2016-06-21
***rsync*** is a good tool :-)

Wait until the backup problem is solved, and then I suggest that you click on **Thread Tools** at the top of the page and mark this thread as SOLVED

-o-

You will probably get better help (from more people) in a ***new thread*** with a good descriptive title and a good description of your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

- what you want (a clean install of 16.04 LTS)

- how you want to use the computer.

This information will help us suggest a suitable flavour of Ubuntu (depending on the hardware and usage, different flavours will be the best).

-o-

Make a link to the new thread from here, to help me and other people find it.

---

