---
title: "Problem with CDwriter, DVDwriter."
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by OldSeaDog on 2005-11-23
I have updated the info below...

I have a Pacific Digital CDwriter and a LG 4160B DVDwriter.  I was having difficulty with both of them - they would install rw, but they were odd about how to do things - for example, I could do a backup of my system using DVD+RW disks, but not DVD+R.  It was fine in Windoze 2000.  I was trying to find a solution, and someone recommended I try UDFTools (as well, mondo indicated it wanted parts of UDFTools).

I followed his advice and installed UDFTools and went through the full process.  Now I have unmountable CDrwiterand DVDwriter in any mode.  They are lost.  I try and mount them manually and they try to mount, but fail with the following from dmesg | tail for the CDWriter:

end_request: I/O error, dev sr0, sector 64
isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: open failed.
cdrom: sr0: mrw address space DMA selected
cdrom: sr0: mrw address space DMA selected
end_request: I/O error, dev sr0, sector 64
isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

For the DVDwriter:

cdrom: sr0: mrw address space DMA selected
cdrom: sr0: mrw address space DMA selected
end_request: I/O error, dev sr0, sector 64
isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
UDF-fs: No partition found (1)
Unable to identify CD-ROM format.


I did a complete uninstall of UDFTools, but it made no difference.  I know there are probably remnants of it that are causing the problem, but I don't know what they are and I am a newbie and want to avoid losing everything if I can.  Does anyone have a suggestion on what I should do?

UPDATE:
My DVDwriter is now working OK.  However, the CDwriter has completely disappeared.

I just checked out the contents of my /dev directory and was perturbed to find out that I have no devices beginning with the letter "s", except for the links sndstat, stderr, stdin and stdout.  I have a heavily used USB system, with up to 7 items hanging off it (right now there are 5.  It sees my 2 printers and my keyboard/mouse combo fine.   My modem is visible.  My CDwriter is still missing.  However, I can't figure out how to mount it if I can't point to it, and /dev/scd0 is missing.

Any ideas?

---

