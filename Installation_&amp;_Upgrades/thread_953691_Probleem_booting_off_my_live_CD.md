---
title: "Probleem booting off my live CD"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by Darael on 2008-10-20
Been trying to install 64-bit Ubuntu Hardy on my computer, and I've run into a problem.  Even though I've set "CD-ROM" as the boot first device in my BIOS, when I turn on my computer with a Live CD in the drive, it just boots into windows.  I've run an MD5 on my ISO and compared the file to the CD, no problems.  I've tried the disk in another machine - works fine.  I've tried the other CD drive in the one I'm having a problem with - still doesn't work.  If I go into the boot menu to select a boot device by hitting f4, it says there's no valid boot media in either CD drive.  I even redownloaded the ISO and burned another CD, but I have the same problem.  My computer's less than a year old, so I don't think that's the problem.  I tried using Wubi, but after installing it nothing happened on boot, and even when I used a utility to add it to the boot menu manually, all I got was GRUB.  I've tried just about everything.  Any ideas?

Darael

---

### Post by 22flames on 2008-10-20
What did you use to burn the iso .... windows media burner will not work.... :) try and download an iso burning tool there are many out there and ubuntu even tells you .... that is probobly your problem tell me how it goes :)

22FLAMES

---

### Post by Darael on 2008-10-20
Thanks, but I used a decent burning tool to burn the disc, Virtual CD V9.  It has a function to compare the CD to the ISO, and I got no difference whatsoever.  Anyway, It worked on another machine.

---

### Post by 22flames on 2008-10-20
Oh sorry lol im not sure than:confused:

22FLAMES

---

### Post by Darael on 2008-10-20
Yeah, It's an odd one

---

### Post by robert shearer on 2008-10-20
What are the system specs/graphics card etc and what 'windows' is installed?

Saw something on the forums last night about a laptop that was 'Vista optimized' and could not boot a 'buntu cd.  

Will look again and post back if I find it.

Edit.. this is it, [http://ubuntuforums.org/showthread.php?t=952457](http://ubuntuforums.org/showthread.php?t=952457)

---

### Post by Darael on 2008-10-20
That could be it, I guess...
Vista Home Premium 64-bit.

The following is pretty much quoted from DxDiag.
4GiB RAM
Various HDDs - 160GB (Windows root) and 500GB internal, 320GB USB
AMD Athlon 64 (dual core) 5600+, ~2.8Ghz
NVidia Geforce 8400 GS graphics card.

If you need any more details, just say so.
Oh, and I got it from Evesham Technology, which is now bust.  Typical.

Edit: Had a look at that post, they seem to have a problem after actually booting from the CD.  My machine won't let me get that far.

---

### Post by robert shearer on 2008-10-20
> **Darael said:**
> That could be it, I guess...
Vista Home Premium 64-bit.

The following is pretty much quoted from DxDiag.
4GiB RAM
Various HDDs - 160GB (Windows root) and 500GB internal, 320GB USB
AMD Athlon 64 (dual core) 5600+, ~2.8Ghz
NVidia Geforce 8400 GS graphics card.

If you need any more details, just say so.
Oh, and I got it from Evesham Technology, which is now bust.  Typical.

Edit: Had a look at that post, they seem to have a problem after actually booting from the CD.  My machine won't let me get that far.

Nothing looks out of place there. I agree about the other thread,does not sound like your problem.

Have you tried downloading the 'Alternate install" cd image  and using that to install from. ?

It works with more hardware than the live cd option but runs in text mode.
Still easy to understand and use but you do not have the option of trying it on your hardware first.

I would also try 32-bit Hardy to see if that loads.(live or alternate)

You say the cd you burnt is good. When you are in Windows and put it in the cd drive,navigate to it using Explorer, does it show as one big file with a .iso tag or a number of files and folders?

What is the cd drive brand/model?

When you got GRUB what were the options displayed.?

What is the motherboard?

---

### Post by Darael on 2008-10-22
> **robert shearer said:**
> Nothing looks out of place there. I agree about the other thread,does not sound like your problem.

Have you tried downloading the 'Alternate install" cd image  and using that to install from. ?

It works with more hardware than the live cd option but runs in text mode.
Still easy to understand and use but you do not have the option of trying it on your hardware first.

I would also try 32-bit Hardy to see if that loads.(live or alternate)

You say the cd you burnt is good. When you are in Windows and put it in the cd drive,navigate to it using Explorer, does it show as one big file with a .iso tag or a number of files and folders?

What is the cd drive brand/model?

When you got GRUB what were the options displayed.?

What is the motherboard?

Thanks for the advice.  The CD's good, it has various folders on it rather than an ISO, and I can get the autorun within Vista.

I might try using the alternate CD or the 32-bit version, I'll try another bootable CD I have and see if it boots before I download it, though.

The CD drives are (from device manager):

DVDRW IDE H16X ATA Device
TSSTcorp CDDVDWSG-S203D SCSI CdRom Device

The former came with the system, I added the latter.

When I got GRUB, I just got something that looked like this:

GRUB>_

As for the motherboard, is the phrase "Nforce 590 SLI AMD" any use?

Darael

---

### Post by robert shearer on 2008-10-22
I wonder if the two disc drives are causing some confusion?

Are they both on the same cable? and how are they jumpered?

I would disconnect one temporarily and see if the live cd gets recognised.
If not then try with the other drive.

---

### Post by Darael on 2008-10-22
The drive I added is on an IDE cable, jumpered to let the cable decide master/slave, the other drive is connected with ATA and I haven't seen any jumpers on it.

Should I still try disconnecting one?

---

### Post by robert shearer on 2008-10-22
> **Darael said:**
> The drive I added is on an IDE cable, jumpered to let the cable decide master/slave, the other drive is connected with ATA and I haven't seen any jumpers on it.

Should I still try disconnecting one?

Now we're getting somewhere.
We know that the cd is good.We know that the bios is set to boot from cd.
Therefore it must be something between  these that is the problem and a process of substitution should resolve it.

Now I think that we may be talking about different drives.

I feel you need to disconnect one of the cd/dvd drives and try booting the live cd on the remaining one.
DVDRW IDE H16X ATA Device
TSSTcorp CDDVDWSG-S203D SCSI CdRom Device
Disconnect the TSSTcorp drive.

You post above seems to refer to Hard drives??
Correct me if otherwise.

 But if it refers to cd/dvd drives then disconnect one.Leave the other plugged in to the Master slot on it's cable and jumper it as master.

Reboot and check the bios settings to see that it is recognised as a cd drive on its own cable and as master on that cable.

If not post with details.
If it is then reboot and see if the live cd loads.

---

### Post by Darael on 2008-10-23
> **robert shearer said:**
> Now we're getting somewhere.
You post above seems to refer to Hard drives??
Correct me if otherwise.

 But if it refers to cd/dvd drives then disconnect one.Leave the other plugged in to the Master slot on it's cable and jumper it as master.


I did mean CD/DVD drives, sorry for the ambiguity.

I must also apologise for forgetting something - the CD drive that came with the machine is **S**ATA

  I'll try unplugging the TSSTCorp drive and see if it works with only the SATA drive plugged in.  The only thing is, there are no jumpers on it, but that's likely because you can only have a single device on a SATA cable.

---

### Post by Darael on 2009-09-03
OK, this is horriffic necromancy, but I ought to note that I solved the problem by flashing my BIOS.

---

