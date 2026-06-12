---
title: "Possibly corrupted MBR?"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by kubstix on 2007-01-25
Ok so I installed XP Pro and installed a countless number of applications for a programming class, then installed Unbuntu (configured GRUB, installed GRUB on Windows Partition, ect)  Everything was working fine until I patched SQL Server 2000 to SP4.  Rebooted the computer, and now it just reboots after the bios screen continously.  Could this be a corrupted MBR?  I cannot hit the GRUB menu or anything.  The question is, if i reboot in XP recovery console and FIXMBR will I lose all the GRUB information and probably corrupt the entire system?

---

### Post by bernied on 2007-01-25
If you run FIXMBR you will only be able to boot Windows, not ubuntu. That is until you fix your grub install. It should not 'corrupt the entire system', as it will only overwrite the MBR.

You'll need a linux live-cd (like the ubuntu install cd) or a grub disk like [this one](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html) to fix your grub install.

---

### Post by bernied on 2007-01-25
But are you sure that this is a problem with the MBR? - it sounds very unlikely that installing any software (unless it was malicious) would overwrite your MBR.

Have you checked your bios settings? Do you have a cd in the drive?

---

### Post by kubstix on 2007-01-25
Well when I ran the super Grub Disk and did a Fix Boot (Overwrite MBR ect) it would boot perfectly fine.  Soon as I wanted to reinstall Grub, it would work perfect on the first bootup.  If i restart windows or ubuntu, the rebooting begins again.  So it seems like as soon as I install GRUB the problems are happening.  Why all of a sudden would this start doing what its doing?

---

### Post by chipmonk010 on 2007-01-25
sounds like hardware failure to me

if it does not make it to the grub screen then reboots automatically then it never has a chance to even look at the MBR so even if it was non-existant it would not cause the problem you are having.

is the system overclocked at all?

is it a purchased system aka dell compaq or is it from scratch or a combo?

can you enter the bios?

whats the last thing you see before reboot?


EDIT: must have posted at the same time didnt see the above post

sounds like your HD might be on its last legs

do you have one of those manufacture bootable cds for partitioning etc?

usually you can run some integrity checks with one of them

but given the fact that it happened all of a sudden makes me think the HD is shot

---

### Post by kubstix on 2007-01-25
Its an HP DC5700.  System is just as how it came with HP.  Hits the HP Splash screen for entering bios, ect then goes black and reboots.  But the part about it is, when I Fixboot and uninstall GRUB....it boots to windows fine.  I can reboot numerous times and not have a problem either.  Soon as i fire the disk in and reinstall grub, it works after the initial first reboot.  No matter if i boot into Ubuntu or Windows (Which both work) then reboot again.....it starts the same rebooting crap.

---

### Post by AlanRogers on 2007-01-25
> **chipmonk010 said:**
> sounds like hardware failure to me...makes me think the HD is shotUnrelated to Ubuntu, I had this with a customer's laptop last night. Each time I ran chkdsk /r it just took longer and longer, returning less and less. A new hard drive was the only answer.

---

### Post by kubstix on 2007-01-25
It has nothing to do with hardware failure.  Scandisk, WD Hard drive testing, and defragging all turned out 100% fine.  Not to mention like I said, when using FIX BOOT and Uninstalling GRUB, Windows is working perfectly fine.  No issues, nothing.  Soon as GRUB gets reinstalled and 1 reboot happens, thats when everything gets corrupted.  I just dont understand when I reinstall GRUB and reboot, it works without any problems.  But as soon as I reboot a 2nd time, its crapped out.

---

### Post by chipmonk010 on 2007-01-25
computer hardware is very complex so when a piece of hardware starts to fail its does so a little at a time and may only show itself under certain circumstances.

for example in this case perhaps the MBR is, lets say 5mb(i dono the real amount), the first 2 mb are fine and the other 3Mb are corrupt. When XP installs it only takes up 1.5mb of the MBR when you install grub on the other hand it takes up say 3MB and this part is corrupt/bad sectors whatever and causes massive failure.

thats just a theory but i wouldnt be surprised if something along those lines is what is happening.

---

### Post by kubstix on 2007-01-25
What if i Ghost the drive to another drive?  Will Symantec Ghost ghost all my partitions including linux partitions?  I was thinking maybe ghosting the drive to another, then possibly taking the new drive and reinstalling GRUB on the MBR?  Do you think this is a possible solution when ruling out bad hard drive?  Thanks.

---

### Post by chipmonk010 on 2007-01-25
I havent used norton ghost but i believe it can handle linux partitions. This sounds like a good thing to try if the other drive works problem solved. if it doesnt it could the data from the malfuctioning device was corrupted by the malfunction there for the new drive may still not work. if that happens ur best bet it to start fresh with a new drive and new installs. the ghost method is a little less invasive so id try that first if u got the software.

---

### Post by kwilliam on 2007-01-26
Time to throw in my two cents.

I got a very similar problem when I installed tried installing Ubuntu 6.06 on an eight year old computer.  It would just reboot continuously.  I installed Ubuntu 5.10 and it worked fine.  I blamed it on old hardware and a lack of QA maybe.  In my case it didn't matter, since I was just turning it into one of the slowest Wordpress servers on the planet, and wasn't dual booting.

I can't remeber if GRUB would load sucessfully before it would reboot, however.

---

