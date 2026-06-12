---
title: "Multiboot grub entry for XP"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by reiki on 2007-01-31
Not sure I'm posting this in the correct place but here goes...

My machine has both SATA and IDE drives. Actually just one IDE drive. It's in a removeable drive carrier.
1 IDE drive 
Grub sees this as hd0

2 SATA drives

sda I refer to as SATA1 has my Dapper install for stability
Grub sees this as hd1

sdb I refer to as SATA2 has my Edgy install

In BIOS, SATA1 is my first hard drive in boot order, so the grub menu.lst on there is the important one to me in terms of showing me all of my boot possibilities.

Here's what I'd like to try...

I want to put an IDE hard drive in the removable carrier and install WindowsXP to it.
To do this I would set that IDE drive as the first hard drive and set the system to boot from CDROM.

I am hoping that this won't touch either of my SATA drives.

After installing XP I would like to then set my system back like it is now. Booting from SATA1 (sda) with a Grub entry to boot the IDE drive. I believe that entry would look like this:

```

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

```

Am I thinking correctly? Darn near all of the dual boot or multiboot instructions I see are for installing both operating systems on the same physical drive. I absolutely will not do that.

Is there an easier way to add a drive with XP on it into this mix? My main criteria is that I do NOT want to mess up either of the 2 SATA drives. I don't want XP touching it with its greasy, filthy paws. :)

---

### Post by dcstar on 2007-02-01
> **reiki said:**
> Not sure I'm posting this in the correct place but here goes...

My machine has both SATA and IDE drives. Actually just one IDE drive. It's in a removeable drive carrier.
1 IDE drive 
Grub sees this as hd0

2 SATA drives

sda I refer to as SATA1 has my Dapper install for stability
Grub sees this as hd1

sdb I refer to as SATA2 has my Edgy install

In BIOS, SATA1 is my first hard drive in boot order, so the grub menu.lst on there is the important one to me in terms of showing me all of my boot possibilities.

Here's what I'd like to try...

I want to put an IDE hard drive in the removable carrier and install WindowsXP to it.
To do this I would set that IDE drive as the first hard drive and set the system to boot from CDROM.

I am hoping that this won't touch either of my SATA drives.

After installing XP I would like to then set my system back like it is now. Booting from SATA1 (sda) with a Grub entry to boot the IDE drive. I believe that entry would look like this:

```

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

```

Am I thinking correctly? Darn near all of the dual boot or multiboot instructions I see are for installing both operating systems on the same physical drive. I absolutely will not do that.

Is there an easier way to add a drive with XP on it into this mix? My main criteria is that I do NOT want to mess up either of the 2 SATA drives. I don't want XP touching it with its greasy, filthy paws. :)

Grub loads off the drive you have set as the boot drive in your BIOS, XP can't "touch anything in your BIOS - just set your IDE drive as the boot drive when you install XP on it so it doesn't mess up the existing Grub setup. Then change things back after the install.

XP *should* boot ok with your Grub settings, but there may be issues within Windows that may need tweaking.

You should experiment, see how the various things work!     :)

---

### Post by reiki on 2007-02-01
Thanks. I'll give it a try. I set my machine to boot from the IDE drive and installed XP. By the time it finished updating and rebooting several times, ...well I finished that part up this morning. Then I had to go to work. Tonight when I get home I'll reset back to boot from SATA1 and then edit grub and see if it works. :)

I'll be a little surprised if it works as it would almost be too easy... heheh. I did see someplace that someone used :

```

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1
boot

```

Can't remember where I saw that or what "boot" was in there for, but.... it's GRUB. Hard to hurt it. Easy to fix it. hehehe... this is nothing compared to what I've seen some folks do. It will be convenient for me if this works.

Thanks for the input.

---

### Post by reiki on 2007-02-01
Got it.
My grub entry looks like this:
```

title		Windows XP
root		(hd1,0)
map                          (hd1) (hd0)
map                          (hd0) (hd1)
makeactive
chainloader	+1
boot

```

Why? Because I had swapped out which drive was first boot when I installed WindowsXP so that it would leave my linux drives alone. In doing that I changed drive orders. So now, in grub, I basically have to map them back to how they were when I installed WindowsXP. No big deal I guess. Grub can handle it and it works. My understanding is that it DOESN'T work without the map entries in there because WINDOWS is too stupid to know where it is.

That's ok. Like I said... it works and it's simple.

---

