---
title: "XP can IDE but Linux can't recognize the IDE HD?"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by CaptBry on 2010-07-26
I had a motherboard 'POP' and die. 
I replaced it, the CPU, and ram along with a new PS.
Then the IDE CDROM always read 'zero' for any media placed in it, so I bought a new USB DVD/CD do-all drive (LG G08)
The system was desktop Dual (sic) Boot with WinXP.

The XP would boot from the GRUB, but no Ubuntu.
I used >find /vmlinuz and got H0,6, right where it always was.

But I could not get it to boot - Thanks for Forums that taught me all about GRUB, its great to know. But no grub commands could find Ubuntu. I guessed MBR corruption.

So I reformatted the IDE with Winxp (all my good stuff is on a SATA drive that I left out of all this ;-))) unplugged.

The Live CD wouldn't find the IDE hard Drive XP had just installed on- same as BEFORE I reformatted it. 

I tried all the distros I have (Puppy through Slackware, Suse, Sabayon, etc) .

Nothing could find the IDE drive.
I flashed BIOS on the new MB-no help.
I put Linux on a Flash drive and booted from there- no help
No Partitioner can SEE the IDE...but XP runs on the IDE C:/ just fine (ntfs for C:, with 70GB unpartitioned, waiting for Linux)

I am at a loss. 

As far as I know, if the BIOS sees the IDE, and XP can run on it, the IDE HD is THERE and working.
Yet no Linux can see the IDE HD, XP partition, blank partition, NOTHING.
even dmesg shows no IDE
The boot text shows no IDE in linux, right after the BIOS lists it correctly while booting.

The IDE controller is built into the MB, its new too.

What is going ON???

thanks!

---

### Post by jerrykenny on 2010-07-26
Since none of the linux distros can find it, it would seem to be a BIOS problem.

You could try resetting all the BIOS settings to safe-default ?

The HD is jumpered correctly i take it ?  try booting with no hard-drive jumper as well.

---

