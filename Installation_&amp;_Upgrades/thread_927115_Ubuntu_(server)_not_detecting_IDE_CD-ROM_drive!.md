---
title: "Ubuntu (server) not detecting IDE CD-ROM drive!"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by stweston on 2008-09-22
Hello, all. I am trying to install Ubuntu Server Hardy on my old-ish PC. It has a SATA 4.3GB HDD and an IDE CD-R Drive. (I'm also using the Alternate install)

Things I have done to make my system as up-to-date as possible:
[LIST=1]
[*]I downloaded & burned the ISO file (new wireless N router made it much faster than before on a wireless B, by the way)
[*]I updated my Award BIOS version from 1009.A to 1013.A, making it be able to boot into Ubuntu (the cutoff date is 2000 but the BIOS version was from 98).
[*]Changed the boot sequence in BIOS from A,C to A,CDROM,C.
[/LIST]
Things I have done to configure my system in different (experimental) ways:
[LIST]
[*]Various BIOS settings changed based on ideas in other threads on this forum.
[*]Changed the HDD-CDROM hardware config from HDD as Master0 & CDROM as Slave0 -> HDD as Master0 & CDROM as Master1.
[INDENT][*]Changed BIOS in subsequent config (I think)[/INDENT]
[/LIST]
(NOTE: that I had this error message before changing any of the hardware/BIOS config.)
And that's about it... I guess I'm thinking that I have problems with Hardware, but it still could be software.

Anyway... My error I'm getting comes up after the boot-up into Ubuntu Server's install process comes after (turns on computer to find out what exactly happens):
turn-on, wait for boot-up scripts->English language->Install Ubuntu Server, wait for start-up scripts->English->US->detect keyboard layout? no->origin of keyboard=USA->layout=USA->wait to detect CDROM drive...

Nothing happens! Specifically, I get an error message saying that "no common CD-ROM drive was found. You may need additional drivers from a driver floppy..."
So, since I don't have a driver floppy, I'm going to select "no"... which I did.

It now says that it may be an old Mitsumi or other non-IDE, non-SCSI CD-ROM drive. That's a little inaccurate, because my drive IS IDE.

It asks me to "manually select a CD-ROM module and device?" I select "yes", followed by "cdrom" OR "none" (either gives me the same options), and it gives me a directory prompt thing...:
"Device file for accessing CD-ROM:"
"/dev/cdrom_______..."

That's my problem... If I go and continue, I get a red error message that the install failed. What can I do now?

My dad even tried this (even though he's a whiz at Windows, not Linux), and helped me with the hardware configs and BIOS upgrade and such, but nothing's working! I need help, O nice people of the Internet!

I'm going to shut the system down, since it always gives the same trouble after the process... If anyone has any ideas, PLEASE respond ASAP. I don't care if it works or not, because we have more HDDs of the same size, but I really want to be able to run a web server.

Thanks again!

---

