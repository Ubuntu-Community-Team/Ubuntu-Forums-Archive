---
title: "Looking for an mbr utility"
date: 2006-03-26
forum: Installation &amp; Upgrades
---

### Post by kcy29581 on 2006-03-26
Hi all,

I want to install Windows (Xp, 2000 etc) after installing Ubuntu and other Linuxes on my machines. I realise (after experience! :rolleyes:) that Windows always writes to the MBR, which obviously removes GRUB.

I know how to reinstall GRUB, using livecd's etc, but I would rather have a good utility that simply copies and restores the MBR, and I personally find this easier and less tricky for some friends (and me!). Ideally the utility would be a graphical one in Windows/Linux or a livecd.

Anyone know of such a utility? Preferably a recent one, as I tried the Partition Magic command line based mbr utilty and managed to mess up too many pc's...

(Mods, I hope I put this topic in the right place)

---

### Post by kcy29581 on 2006-03-26
Hmmm..

I just had a quick look at the Wiki, and noticed the entry about the GRUB boot disk. Is this recommended?

I might have answered my own question, but I'm still wondering if there is a gui based utility.

---

### Post by lullebakman on 2006-03-26
Partition Table Doctor 3
You can Backup and Restore your MBR and you Partition Table.
[http://www.ptdd.com/ptdmoreinfo.htm]("http://www.ptdd.com/ptdmoreinfo.htm")

EDIT: I just read it's only able to backup & restore the Partition Table. But it can rebuild the MBR.

---

### Post by Mustard on 2006-03-26
Something like Super Grub Disk might be a temporary workaround.

Freshmeat link..
[http://freshmeat.net/projects/supergrub/](http://freshmeat.net/projects/supergrub/)
Super Grub Disk home page
[http://adrian15.raulete.net/grub/tiki-index.php?page=En](http://adrian15.raulete.net/grub/tiki-index.php?page=En)

It's not going to restore your MBR, but you may be able to boot to windows with either a floppy or CD.

-edit-

After reading your first post again, I think it might be the sort of thing you are after actually.  I was thinking for some reason you needed to restore your windows MBR, but you just need to install grub on the MBR.

-edit2-

Oh one more thing.  For just copying and restoring the MBR, its a pretty easy process really.  If you have a look at the **bottom of this documentation page** at the partimage website, you will see just how easy it is (via command line)...
[http://www.partimage.org/doc/index-3.html#ss3.7](http://www.partimage.org/doc/index-3.html#ss3.7)

To quote from the page in question...
[quote=partimage documentation page]

**Backing up the MBR**
First, we will save the MBR with DD (GNU convert and copy)

    * cd /root
    * mkdir partition-backup
    * cd partition-backup
    * **dd if=/dev/hda of=backup-hda.mbr count=1 bs=512**

.....

**Restoring the MBR**
Be careful, restoring is a dangerous action - it can destroy data! First, we will restore the Master Boot Record:

    * **dd if=backup-hda.mbr of=/dev/hda**

[/quote]

---

### Post by kcy29581 on 2006-03-26
Thanks for the replies. I think the copy/restore using dd doesn't look too bad! It's not gui but it seems fairly simple.

Which would be safer though, the dd method, or reinstalling grub?

Thanks again

---

### Post by Mustard on 2006-03-26
[QUOTE=kcy29581]Thanks for the replies. I think the copy/restore using dd doesn't look too bad! It's not gui but it seems fairly simple.

Which would be safer though, the dd method, or reinstalling grub?

Thanks again[/QUOTE]

I couldn't really say which is safer.  Both of them are going to write over the MBR.  Doing it via Grub is pretty conventional.  I assume when they say the use of dd to copy/restore the MBR is a dangerous operation they mean, 'watch out you are doing this process correctly' ie don't make a typo, don't put the wrong backup on MBR etc.  I have used the dd method twice now to restore the MBR for my win98 install on my second hard drive and I have survived the process both times. :)

I was feeling a bit ignorant about troubleshooting partitioning problems, since I had never really done a lot of partitioning, so I set myself a project  of installing windows on a second drive, then making an image with partimage (as well as backing up the partition tables and mbr), then completely changing the partitioning of the drive, creating three linux installs (mepis, dapper flight 4, puppy linux), playing with the linux installs and then recreating the original windows partition (which wasn't too hard as I had just used a single partition for the whole drive), then restoring the hard drive image of windows using partimage, restoring the partition tables and mbr and booting back up into windows.  After doing this, and then going on to fiddle around some more, I feel pretty confident that it works and I can do it safely.

After I did the first 'restoration' of windows, I actually shrunk the windows partition, installed all the latest updates/drivers/favourite games, defragged the windows partition and then made a new image of the partition with partimage.  So now if I want to reinstall windows for whatever reason, I can just restore the image I have stored away, and I have a fully installed and defragged windows install without all the hassle of installing drivers/software and updating everything again.

---

