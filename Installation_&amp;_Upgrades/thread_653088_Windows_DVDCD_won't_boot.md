---
title: "Windows DVD/CD won't boot"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by jvtyu2007 on 2007-12-29
Hi,

I've just installed Ubuntu on my PC (with a ASUS Motherboard), and now I want to have it dual-booting with Windows Vista.
I've read a lot about how to do this, but I have a "simple" problem, my PC wont boot from the Vista DVD (or any other Windows Boot DVD or CD), but it boots fine from the Ubuntu Live CD.
Since I have a ASUS Motherboard I don't have the option to choose which device the PC should boot from, I'm only able to define the boot order. I did this, saying that DVD/CD drive is the first, but GRUB overtakes this option and runs before the Windows Boot DVD.

Can some one help me?
Is it possible to create an option in the Grub Menu, so that I'm able to chose "Boot from DVD or something like that.

Thanks.

---

### Post by Pumalite on 2007-12-29
If CD-DVD is really first in boot order and you cannot boot, you should check your disk. It's probably not bootable.

---

### Post by jvtyu2007 on 2007-12-29
Thanks, but it's not that, because I tested the DVD on a Windows Only machine and I works just fine.

---

### Post by Pumalite on 2007-12-29
Are you able to get into BIOS?

---

### Post by ARhere on 2007-12-29
So... let me make sure I go this right...
PC#1 will boot from an Ubuntu Live CD, even if an OS is loaded on the main HDD; but will not boot from a Windows CD/DVD.  You have tested this Windows CD/DVD on PC#2 and it works.

1.  First, reboot from the Ubuntu CD on PC#1 that has Grub already loaded, just to verify that you did not try it before installing the OS.  If the BIOS goes to the HDD and sees no OS, it will then goto the CD and you may not notice that.  This will verify that you BIOS is actually checking the CD-ROM first.
2.  My first thought, is the Windows disk a DVD or a CD?  if it is a DVD,then verify the optical drive on PC#1 actually a DVD-ROM.
3.  If it is a CD, then inspect it to see if it is dirty or scratched.  Some drives have a better laser diode then others and can read through scratches.
4.  IF that does not help, then take the optical drive out of PC#2 and put it into PC#1 and try again with both disks.
5.  Last check the data cable.  If it is horribly pinched, replace it.  The IDE controller might be getting a lot of errors that barely work with one disk, but not another.

Try these steps and post results for each so I can continue to help.

-AR

---

### Post by Craigus on 2007-12-29
> I did this, saying that DVD/CD drive is the first, but GRUB overtakes this option and runs before the Windows Boot DVD.

That cannot be what is actually happening, because it is impossible. Grub cannot over-ride the BIOS boot order settings.

The real possibilities are either that you haven't actually got the boot order set in BIOS the way you think you have, or the optical drive is not functioning properly (or there is something wrong with the optical boot media). Is the optical drive actually showing up as present in the basic BIOS screen ?

---

### Post by jvtyu2007 on 2007-12-29
I thank you all for your suggestions, but theres nothing wrong with the hardware.
Everything is OK with the BIOS, I even tried to just disable all options except the one for CD-ROM, so I only have the first boot, and it's set for CD-ROM, and doesn't work.
The drive is a DVD-writer, I cant exchange the drives, because one is a desktop and the other is a Laptop.

I simply don't know what to do. The "funny" thing is that the only CD/DVDs that boot are the ones with Linux (Ubuntu Live CDs).

---

### Post by Craigus on 2007-12-29
Does the drive LED come on, as if it is trying to boot from the optical drive, even though it eventually doesn't ?

Does the system have a floppy drive ?

---

### Post by Pumalite on 2007-12-29
Post your specs. Maybe that will help us help you.

---

### Post by meierfra on 2007-12-29
I don't believe that it is Grub's fault. But it is east to check:
FixMBR is my signatures  has instructions how to remove Grub from the MBR.
FixGrub has instructions how to reinstall Grub.

---

### Post by TornMorals on 2008-01-01
Thanks for that FixMBR link.  I just got this problem on my new laptop being that I needed to re-install Windowz and my OEM disc would not boot.  I have had this with other computers and always was able to fix it by doing a massive format of the disk, though that didn't work this time. And usually the second option of just installing LILO and having it overwrite the MBR with itself.  There seams to be something in the Windows installer that when it see's GRUB it panic's or something and dies.  I was able to get a Vista Ultimate =/ upgrade disc to boot and re-write the MBR.  I have called Microsoft over this ishue also and the person I talked to agnoliged this problem, though this was back when Vista wasn't out.  I guess they like having the error to make linux look bad...
It seems like a ploy to make money to me.  OEM disk that comes at low cost to end user hates grub.  Full store copy of XP/Vista dose not mind grub on MBR and will boot anyways.:mad:
<Writes MBR fix command on XP and Vista cases...>
Damn school makes me have Windows...

---

