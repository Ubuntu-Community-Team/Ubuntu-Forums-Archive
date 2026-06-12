---
title: "Progress with installation on laptop, but new problem encountered"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by renzokuken on 2006-11-20
OK, so after a few weeks of frustration not being able to get any distribution to even boot let alone install on my new laptop (see here [http://www.ubuntuforums.org/showthread.php?t=288090](http://www.ubuntuforums.org/showthread.php?t=288090) ), I stumbled across a mailing list post that suggested passing the following options on boot

acpi=ht acpi=conf2

Well i passed those at boot and managed to boot straight into the Edgy liveCD, SUCCESS i thought.

However, neither my touchpad nor my USB mouse worked so i had to do everything with the keyboard. 

The major problem though is, when i tried to install it to the hard disk, it could not detect my hard drive and so i had no were to install it. Although ive made a huge leap forward, im stuck again because of this.

**Q1.**  Is the harddrive not being detected because of the two boot options i used???

**Q2.**  What exactly do acpi=ht and pci=conf2 mean??

Thanks


EDIT: apologies, i just realised how vague the topic title is, and i cant change it

---

### Post by renzokuken on 2006-11-21
UPDATE

OK, so I tried booting with just the acpi=ht option and obviously i wasnt able to boot to the LiveCD, however, a black screen came up with messages about error with the PnPbios.

It mentioned passing the PnPbios=off option at boot. I havent tried this yet.

I think my harddrive is SATA. Is SATA controlled by plug'n'play? so another question

**Q3.**  Is there any common options in the BIOS that may help me resolve this? (I have tried to find a flash update for my bios but havent found one yet)

---

### Post by the Jaan on 2006-11-21
I'm not sure, but I think most hard drives are SATA2. Another option would be to install ubuntu on an external hard drive. Speed would be alot slower - granted, but it might work. Also, does the ubuntu live thingy load? Like boot off the disk?

EDIT: OHH yeah... and what program did you burn with, and what CD burner + CD stuff did you use? Cause it might just be the CD. I tried with Nero 7 Pro, but it didn't work. I got an excellent freeware app (windows) called Burnatonce ([http://www.burnatonce.com/)](http://www.burnatonce.com/)). I wrote at 8x, or the minimum speed of my drive. Try using that to burn...
Cheers.

---

### Post by renzokuken on 2006-11-21
yeah the live CD loads fine as long as i use the acpi=ht and pci=conf2 option.

i used gnomebaker to burn the cd images but i know they are all fine, i checked the md5sums and booted them all on my desktop ok

my problem is definately a hardware incompatibility issue

---

### Post by renzokuken on 2006-11-22
*bump*

so any advice or possible workarounds?

 an external harddrive wont work since for whatever reason PnP is disabled and so no USB

---

