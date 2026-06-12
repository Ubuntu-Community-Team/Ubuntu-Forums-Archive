---
title: "Alpha5 alternate installer no good"
date: 2008-09-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by hajk on 2008-09-15
I tried to install the Alpha5 from the intrepid-alternate-amd64.iso on my computer with Asus M3A32-MVP DeLuxe mobo and AMD Phenom 9850 Black Edition quad processor, but this failed miserably. Yes, I did check the quality of the CD burn, and I'm not talking about the additional "acpi=off" boot option (without which my USB keyboard would be unresponsive). 

The problem occurred much later during installation of the base system, where the installer asks for insertion of the disc labelled "Ubuntu 8.10 _Intrepid Ibex_-Alpha amd64 (20080903.2)' in the drive /cdrom/ and to press Enter. Mmm..., isn't that disc already in that drive? Whatever else is the installer installing from? But no change after hitting Enter, and no change after hitting Back either... so no way to proceed beyond the above message.

I did manage to install Intrepid, but only after first installing Hardy from the alternate-amd64.iso (went without a hitch, no additional boot options needed, recognized all my hardware), then used the "update-manager -d" command to install the latest Intrepid packages, all of which went without a hitch as well.

I'm not sure whether this should be further reported somewhere...

---

### Post by ronacc on 2008-09-15
sounds like it is "losing" your cd drive , I would say file a bug . I went through a period like that  couple of versions ago on a box where I had 2 dvd drives one sata and one ide , I could install from the sata ok but if I tried to install from the ide exactly what you describe would happen.

---

### Post by hajk on 2008-09-15
OK, good to know that it's probably not a malfunction in the IDE dvd/cd-drive. I had reused that drive from an earlier computer, since I had seen reports of recent SATA drives not being recognized... There were no bug reports filed on this problem, so I've now filed my own.

---

### Post by hajk on 2008-09-15
I've exchanged the IDE dvd/cd-drive for a SATA one, and now the installation of Alpha-5 with the alternate installer went OK. So, it was indeed related to the IDE interface of the drive.

---

### Post by ronacc on 2008-09-15
if this is the same sort of thing I mentioned above you may find that it is only that particuar make and model of ide drive that causes the problem, I did quite a bit of troubleshooting at the time and found that a different ide drive would work ok for install and that the one in question would work ok for earlier versions of ubuntu it was just that particular drive on that particular version of Ubuntu .

---

### Post by Gina on 2008-09-15
Computers are black magic!!  Of this I'm convinced.  I found the same CD drive problem on an old AMD K6-2 machine.  I had installed Xubuntu Dapper a couple years ago and after a reshuffle of my hardware decided to try again as recent versions seemed not to like the graphics card.  Both desktop and alternate CDs just refused to boot - the GRUB menu appeared but then nothing worked.  Other versions and other distros at least boot as far as starting the X server.  I'm having another swap around as I now have a CD/DVD ROM drive free - this has had little use.

---

### Post by hajk on 2008-09-15
> **Gina said:**
> Computers are black magic!! 
Black magic indeed! I used that very same IDE drive to install Debian Lenny and Ubuntu Hardy (to different partitions) without any problem, in both cases also using the text-based d-i. This must have been the same d-i, as I can't imagine that Canonical would waste resources on tweaking it (even Debian have spent their effort on a graphical installer lately). 

Is that what you get when resurrecting Harry Potter, I wonder? :)

---

### Post by Nullack on 2008-09-16
Please provide the bug number

---

### Post by hajk on 2008-09-16
> **Nullack said:**
> Please provide the bug number
	[Bug 270461] Re: Alpha-5 alternate installer fails

---

### Post by ronacc on 2008-09-16
computers are not black magic , heck they can only count to 1 , they just do it real fast .

---

