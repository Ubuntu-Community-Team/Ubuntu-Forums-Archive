---
title: "Ubuntu Studio/Vista Dual Boot Raid0 issues Please help"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by Tumbledown on 2008-01-25
Hi there,

I'm hoping there is someone out there that can help me!

I have been working on getting Ubuntu studio 7.10 installed on my new system for the last few days.

I have tried various methods but i'm still having issues.

Below is my spec and what I want to accomplish

CPU - Q6600 2.4
Mobo - Asus P5k Premium
Ram - 8GB OCZ PC2-6400 (800Mhz)
HDD - 3 x Western Digital Caviar SE16 500GB SATA-II 16MB Cache
GFX - Nvidia 8800GT (512mb)

Plan:-
[LIST]
[*]Have 1.5TB Raid0
[*]Have 150GB assigned for Vista (Gaminig etc)
[*]150GB Base install for Ubuntu Studio
[*]Remainder to be used for Ubuntu File Storage (Blender Renderings and Video)
[/LIST]

Issue:
My Mobo seems to use FakeRaid - Have followed the How-to on this but when I 
chroot to the /Target drive and apt-get install grub etc I get errors that i cannot 
recover from and apt screws up and gives me a command line to fix the issues, but doesn't.

I have tried various methods to get this system installed:-
[LIST]
[*]Software Raid (With BIOS raid disabled) 3 Drives
[*]Software Raid with 2 drives
[*]LVS
[*]7.10 liveCD with the view to migrate to Studio
[/LIST]

TBH I'm about ready to throw the system out the window, but that won't work either:lolflag:

I'm thinking the only way i'm gonna get this to work is with a hardware sataII raid 
card. but they are pricey.

Any help or suggestion would be much appreciated
PS Vista doesn' have to be on the raid, All I want is it to work :(

TIA
Tumbledown

---

### Post by Pumalite on 2008-01-25
In general, Vista demands that you allocate space for Ubuntu from WITHIN vista. If you are installing to a different drive, you are still going to have trouble getting Grub to install to sda (the Raid)

---

### Post by Tumbledown on 2008-01-25
Ok - I have had the same experiance setting up with just Ubuntu on the
drives.

I cannot seem to get past the partitioning screens.

I have followed the screen casts for gutsy regarding alternat install
and my experiance differs from what is being shown.

for example: -

my drives show up as 500.1GB so I create a 499GB partition an make it
a volume for RAD.

I complete the same task on the reamining 2 drives.
When i come to configure the software raid, i cannot create a RAID0
as it is already populated.

I then delete the raid partition and the partitons on the drives and repeat
the process. I can now create the RAID0 and the respective mount points (only configured for / ).

I then use the remining space on drive 1 for swap.
When the system tries to partion and format the dirives, i get an error
either the swap cannot be mounted, or / cannot be mounted

this is where i bomb out! :(

Any thought?

---

### Post by bwtranch on 2008-01-25
Re: #2 This is true. Please look at what this post is saying.

---

