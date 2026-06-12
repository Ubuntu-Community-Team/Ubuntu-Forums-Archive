---
title: "Wiping Ubuntu"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by Flamemonkey on 2008-08-05
Alright, I tried Ubuntu, hate it. I don't see what all of you like about it, and I don't care to find out, either. All I want, is to remove the blasted thing from my computer.

My main obstacle is Grub. See, Ubuntu is on it's own seperate HDD, which unfortunately is rather loud and squeals like a rusty fan. I tried simply removing the HDD from my computer, but of course Grub doesn't like that, and won't let me do anything until I plug the thing back in.

I'm hearing about oh, say, 26513213 different ways to change Grub, but all of which are about editing it from *within Linux with the purpose of deleting XP.* Which is the complete opposite of what I want.

I want to, from within XP, delete Grub/Remove Ubuntu from it, so that I can pull out this HDD and remove all trace of Ubuntu from my computer. Is there anyway to do this?

NOTE: Don't give me any crap about why I should keep Ubuntu, either. And sorry for sounding so angry, but I'm pretty annoyed with this right now.

---

### Post by cdtech on 2008-08-05
Just boot from your windows XP install CD and "fixmbr". This will let you boot back into windows (removing the grub bootloader).

**P.S.**
You are pretty annoying with your thread. We didn't make you try Ubuntu, just here to help. I'm certainly glad you didn't have to pay for it, I would have never answered this post. Sorry for your problems.......

---

### Post by Flamemonkey on 2008-08-05
Unfortunately, I do not have an XP install disk. I have a Compaq, and I never thought I'd need the restore disk (Rather, my parents, who it originally belonged to, felt it was unneccessary), so I do not have one of those. However, my friend has a Windows XP Pro boot disk, would that work? I'm using OEM Windows XP Home.

EDIT: Like I said, I am annoyed. Not with you, but with Ubuntu users in general. In every thread I've seen trying to find a solution, they're always, "Oh, why are you doing that? Ubuntu >>>> XP, loser!"

---

### Post by redraiderbum on 2008-08-05
I'm guessing you are currently dual booting?  If that is true Grub was probably installed to the Master Boot Record and the Windows boot loader was probably obliterated in the process.  So you can run the fixmbr from a windows install disk.  Then you can boot to windows and reformat the partition that is holding ubuntu.

Yes your friends disk will probably work.

Edit: The reason I like Ubuntu is it's free.  You can get the same functionality out of this free alternative that you get from Microsoft's server software that costs many thousands of dollars.  Have you ever considered that you can build a relatively fast computer for $500 and if you put windows vista ultimate on it you are increasing the price of the system by 50%?  And it can't even do a software RAID 5 out of the box, or have a volume bigger than 2 TB.  Both of which are a large problem for me.

---

### Post by maybeway36 on 2008-08-05
Find some way to boot DOS (MS-DOS or FreeDOS will work.) If you don' have a floppy drive get [fdbasecd.iso]("http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso") and burn it to a CD. Choose the "Live CD" option when you start up.
At the DOS command prompt, type:
```
FDISK /MBR
```
That gets rid of GRUB.

---

