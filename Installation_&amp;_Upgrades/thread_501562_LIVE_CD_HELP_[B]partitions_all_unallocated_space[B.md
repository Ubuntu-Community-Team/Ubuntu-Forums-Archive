---
title: "LIVE CD HELP [B]partitions all unallocated space[/B]"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by bdelin88 on 2007-07-15
Hello,
I'm pretty new to ubuntu, but I'm pretty experienced with computer lingo, and I've learned how to use the basics of the terminal.  I'm trying to make ubuntu work, I had a problem with wireless so I decided the best thing would be to reinstall, so from Vista I reformatted ubuntu's ext3 and swap drives into unallocated space...and not thinking first... it messed up the Grub bootloader bad.  Tried Vista repair startup, didn't detect errors so I reinstalled Vista.  Booted into Vista just fine.  

So now Vista is back up and I want to start ubuntu from live cd, so every time i get to the screen where i can select install/start ubuntu live cd it tries to load up but then I get this huge list of failures of how it can't mount drives and the numbers just keep adding up like [100.223.23] and they keep increasing... that's feisty.  And another error that says: "ata1: translated ATA stat/err 0x51/40"  and it just keeps scrolling down the screen.

NOW with ubuntu Dapper cd it does the same however it will finally boot in.  Which I was thinking yes! GREAT!  I can just partition some extra space...but sadly when I go to the partition manager or choose the install option... it shows my entire drive as unallocated space all 110 GB, which is BS because I have a Vista partition (~50GB) a Media partition (~20GB) a Software partition (~30GB) and 8 GB I reformatted and left unallocated from Vista.  

So what's the deal here, can anyone help me out?  I love linux but I need to be able to dual boot and I absolutely don't want to reformat everything if I don't have to...... there's got to be a way.  Thanks, need any more info just let me know!

---

### Post by merlinus on 2007-07-15
Use vista's disk manager to create the partitions.  First, get rid of temp files and other no-longer-used stuff and defrag several times.

Then try the live cd.

-merlin

---

### Post by bdelin88 on 2007-07-15
**I did all of that already** (checked all partitions for junk and ran Disk Cleanup as well, emptied recycle bins, made space for ubuntu reformatted it, formatted to ntfs, then reformatted again to unallocated), defraged once, I'll try that again...  it's got to be some left over file or something from the old Feisty installation.......

**Where else would it store files like that?  Is there an old version of grub somewhere still on here that is corrupted?  I mean the livecd should be independent of other files right?  It shouldn't even be receiving those error messages.**

I have a feeling that it might have somehow stored something on that little sliver of unallocated space that alludes all the partitions that little 8mb bits of space or something but I don't know how it would or how you would format that

---

### Post by merlinus on 2007-07-15
Another option might be to use the gparted live cd to set up and format your partitions before installing ubuntu.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by bdelin88 on 2007-07-15
Hey thanks merlin, I'll try that!!

---

