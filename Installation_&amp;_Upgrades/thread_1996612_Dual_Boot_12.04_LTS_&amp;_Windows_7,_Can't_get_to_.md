---
title: "Dual Boot: 12.04 LTS &amp; Windows 7, Can't get to Win7 now"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by ooboontwo on 2012-06-04
[B]My Problem Has Been Solved, see below for details all ye Googlers!

--

[/B]**Problem Solved** (give me a minute to mark the thread as such)

Unbelievable. The answer was pretty simple.

I unhooked the power cables to my two PATA (IDE) drives (sdb and sdc)  and started up Windows Repair CD again. This time it found my Windows 7  OS. I ran startup repair twice.

Next, I hooked the IDE drives back up, booted into Ubuntu, ran boot-repair and restarted.

Grub now appears with Linux, Memtest, and Windows options. I am typing this on Windows as we speak.

Weird, huh? It seems Windows repair was freaking out because of those  two other HDDs / my Ubuntu install. Once I took those out of the  equation it fixed everything.

Hope this helps someone else in the same position I was in! This was frustrating!

Cheers,
Cody

--
[B]
Original Post:

Please note: I have no idea whether or not this matters but both Ubuntu and Windows 7 are 64 bit versions![/B]

Hello everyone,

I have done a lot of googling and research, not to mention my own troubleshooting in an attempt to fix this problem. However, I have been unsuccessful in every attempt and need your help!

I have three physical hard disks in my computer:

sda: SATA: Solid State Drive (120gb)
sdb: PATA (IDE): 200 GB HDD
sdc: PATA (IDE): 250 GB HDD

Here is how I have them set up:

sda: Windows 7 64 bit (Installed first, before Ubuntu)
sdb: Ubuntu 12.04 LTS 64 bit (Installed after Windows)
sdc: NTFS Storage drive, no OS

**You may want to skip to the bottom for a quick summary of this info.**

The 12.04 Ubuntu install ran just fine. No errors. I verified the md5 checksum of the ISO and checked the disc for errors. Everything looked good, and Ubuntu runs great.

The first problem: When I restarted my machine, it simply booted into Ubuntu. Grub did not appear at all.

I ran boot-repair, recommended repair.

Second problem: Grub then appeared, but it only listed Ubuntu and Memtest86+. Grub did not list Windows 7.

I booted up my windows repair CD. The Windows repair CD did NOT list my Windows 7 installation when I was asked to select an operating system to repair.

I booted back into Ubuntu. I loaded up Gparted. sda (my Windows 7 installation disk - SSD) was not flagged with "boot". I flagged it as boot and reloaded Windows 7 repair CD.

I ran: CHKDSK [my win7 drive] /r

Check disk ran, did not find errors, and therefore corrected no errors.

I then ran: bootrec.exe /fixmbr

Successful.

Next, I checked: bootrec.exe /scanos

Windows 7 DID appear (i.e. was recognized) after I ran bootrec.exe /scanos

Next, I ran bootrec.exe /rebuildbcd

This is where I don't know what is happening.

It found Windows 7 and asked me if I wanted to add it to the boot list / record (whatever). I said, "yes." After I hit yes it says something about an unknown or unrecognized filesystem, and the entry could not be added to the boot list / record.

Adding to my frustration: my BIOS do NOT see sda (SSD Win7 disk) as a bootable device. Yet, somehow, when I boot up I don't see grub anymore (grub is installed on SDB, my secondary boot device after floppy) I get the "missing operating system" screen.

Ubuntu works fine when I select the drive (sdb) from the boot menu (I am typing this on Ubuntu 12.04 right now).

I'm sorry this is such a long post, but I am really trying to give you all the info I have. **Here's a quick summary:**

Drive configuration:
sda: SATA: Solid State Drive (120gb) (Windows 7 installed here BEFORE Ubuntu)
sdb: PATA (IDE): 200 GB HDD (Ubuntu installed here AFTER Windows 7)
sdc: PATA (IDE): 250 GB HDD

Ubuntu 12.04 Installation Notes:
MD5 checksum of ISO file verified before burning. Good.
Disc checked for errors after burnning. Good.
Ubuntu Install worked perfectly, runs good.

BIOS:
Does not recognize sda (see above) as a bootable device

Grub:
Originally, did not load at all, ran boot-repair, now lists only Linux and Memtest

WIndows 7 Repair:
Windows 7 installation does not appear when asked to select OS (nothing appears)
Ran "CHKDSK /r" on sda, no errors
Ran "bootrec.exe /fixmbr"
"bootrec.exe /scanos" Sees my Win 7 installation
"bootrec.exe /rebuildbcd" will NOT let me add Win 7, though it sees it

Gparted:
sda was not flagged as boot. Flagged as boot. Doesn't seem to have helped anything.

**Please note: I have no idea whether or not this matters but both Ubuntu and Windows 7 are 64 bit versions!**

Please help! I am an experienced computer user, but this is killing me.

- Cody

---

### Post by wilee-nilee on 2012-06-04
Hello Cody, post the http address of the bootinfo summary from the boot-repair.

Make sure it is a version that shows your set up as it is right now, you can just run it by itself.

---

### Post by strask on 2012-06-04
Clarification question: Have you ever booted into Windows 7 after the initial install, but before you installed ubuntu? Or did you just install windows 7 then immediately install ubuntu?

---

### Post by wilee-nilee on 2012-06-04
> **strask said:**
> Clarification question: Have you ever booted into Windows 7 after the initial install, but before you installed ubuntu? Or did you just install windows 7 then immediately install ubuntu?

On different HD's it appears so far.

sda: Windows 7 64 bit (Installed first, before Ubuntu)
sdb: Ubuntu 12.04 LTS 64 bit (Installed after Windows)
sdc: NTFS Storage drive, no OS

---

### Post by strask on 2012-06-04
I read the original post and saw WHERE the operating systems were installed. What I'm asking is more WHEN they were installed, and more specifically IF windows ever booted properly after install time.

---

### Post by ooboontwo on 2012-06-04
**Problem Solved** (give me a minute to mark the thread as such)

Unbelievable. The answer was pretty simple.

I unhooked the power cables to my two PATA (IDE) drives (sdb and sdc) and started up Windows Repair CD again. This time it found my Windows 7 OS. I ran startup repair twice.

Next, I hooked the IDE drives back up, booted into Ubuntu, ran boot-repair and restarted.

Grub now appears with Linux, Memtest, and Windows options. I am typing this on Windows as we speak.

Weird, huh? It seems Windows repair was freaking out because of those two other HDDs / my Ubuntu install. Once I took those out of the equation it fixed everything.

Hope this helps someone else in the same position I was in! This was frustrating!

Cheers,
Cody

---

### Post by strask on 2012-06-04
Awesome, congratulations. :)

---

### Post by wilee-nilee on 2012-06-04
> **ooboontwo said:**
> **Problem Solved** (give me a minute to mark the thread as such)

Unbelievable. The answer was pretty simple.

I unhooked the power cables to my two PATA (IDE) drives (sdb and sdc) and started up Windows Repair CD again. This time it found my Windows 7 OS. I ran startup repair twice.

Next, I hooked the IDE drives back up, booted into Ubuntu, ran boot-repair and restarted.

Grub now appears with Linux, Memtest, and Windows options. I am typing this on Windows as we speak.

Weird, huh? It seems Windows repair was freaking out because of those two other HDDs / my Ubuntu install. Once I took those out of the equation it fixed everything.

Hope this helps someone else in the same position I was in! This was frustrating!

Cheers,
Cody

Cool, enjoy. ;)

---

### Post by oldfred on 2012-06-04
Post link to Boot_info from Boot-Repair.

We have seen where Windows installs to one drive and installs its (hidden) 100MB boot/repair partition to another drive. If BIOS showed sdb as boot drive, then Windows boot partition may have been on sdb. Then your install of Ubuntu overwrote the boot partition. You can repair the install in sda as you have done, but BIOS has to correctly see the SSD drive so it is bootable.

---

