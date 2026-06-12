---
title: "NTFS PArtition not accessible after grub install"
date: 2005-07-01
forum: Installation &amp; Upgrades
---

### Post by WotC on 2005-07-01
Hi!

I've a question - during my ubuntu setup i thought i wanted to install the bootloader grub to the partition (hd0,5) - unfortunatley, i meant (hd0,4) - now i cannot access (hd0,5) - its a ntfs partition - from windows any longer... can i undo this (according to the grub website i cannot uninstall it!?!?!?)? please don't tell me NO because i have a LOT of data on that partition....

thanks in advance

---

### Post by akcanadianeh on 2005-07-01
I don't know if this will work, but it might be worth a try. There are linux drivers you can search for that allow Linux to read NTFS partitions (writing is unstable, I've heard). With these drivers though, you should be able to copy the files out of the NTFS partition, possibly only a FAT partition or burn onto something windows can read. Once you've recovered all the data, you could reformat the patition and copy all the files back onto it.

Once again, this is a guess, and probably how I'd go about it, but I've never done it before.

---

### Post by SQFreak on 2005-07-01
Try this:

Boot off your Windows XP/2000 CD. Wait for the setup to load, and at the first opportunity, press "R" to start the Recovery Console. You'll be prompted what installation of Windows you want. Select the correct one, type the Administrator password (if you don't have one, don't know it, or use XP Home Edition, press Enter). You'll be presented with a prompt. Be sure you have an Ubuntu CD handy because we're about to remove GRUB entirely, making it impossible to boot Ubuntu. You'll have to reinstall GRUB to the MBR.
Type fixmbr and press Enter. You'll be told you have a non-standard MBR, this could render all your partitions inaccessible, blah, blah. Say yes.
Type fixboot c: and press Enter. Then, substitute whatever your other drive letter (hd0,5) is for c and do another fixboot.
Type exit and press Enter. Your system should boot into Windows.

There are a few other things to try in Linux (forcibly changing the partition type identifier in the partition table to read that it's an NTFS partition), but this is the easiest and most likely to work from my experience.

---

### Post by mingus on 2005-07-01
After looking at SQFreak's post, I edited off my suggestions.  

Do you mean that you cannot *boot* into XP?  Or than you cannot *access* that drive while you are in Windows, that is, that (hd0,5) is not the main NTFS partition?

In either case, the MBR should not be the problem, if you did not install grub to it.  

My guess is that the problem is with the partition table.

---

### Post by WotC on 2005-07-01
Hi!

Thanks for the fast replies!
Ok, running some disk management tools under XP its say that its an NTFS partition, 168GB, all occupied (thats in fact not true). Running diskprobe from the XP support tools is what i did next - whenever i read the partition (its 4, in an extended partition) i can see that the MBR was changed by grub - i cannot do much with this tool up to now because i have to get used to it - however, it syay that a starting sector if this partition is somewhat -xxxxxx (the MINUS sucks)!

@cannot access it: i SEE that it still has a driveletter (e:\), but whenever i try to access it i get the "not formatted, wanna do it now" message :-(.

i found a tool at the inet called "Partition Table Doctor 3.0" - i just installed the demo and when i try to manipulate the disk there is a message saying something like "if u cannot access this disk using windows, try to use the bootfix option" (it doesnt say this checking the other two ntfs partitions). however, the demo cant fix, so i have to ask around to give the full version a try...

@SQFreak: thanks, ill try this (copying is painful as i have only a 20GB ext3 partition)...
Re-installing grub isnt that i problem i suppose - i wanted to switch to acronis os selector anyways (it natively detects freebsd, but not ubuntu - damn :-)))

@mingus: i can boot intu ubuntu (or at least install it again...)

i keep u informed about that tool (im more used to windows, so i feel more secure trying it that way)
thanks

---

### Post by mingus on 2005-07-01
Here is PartitionMagic's DOS partition table editor:
[www.computerworkscentral.com/PTEDIT.EXE](www.computerworkscentral.com/PTEDIT.EXE)
Good info on using it at:
[http://www.goodells.net/multiboot/ptedit.htm](http://www.goodells.net/multiboot/ptedit.htm)
you'll need to find what the hex value is for NTFS.  Since your partition is a logical, you'll need to get into the Extended Partition table.  There is a "boot record" screen which you can pop-up that will interpret what the type is.  Obviously, if it is not NTFS that's a problem.  I think Linux will be 0x8C. 

[I]EDIT:  From M$ support site:
"usually 0x06 for FAT, 0x0B for FAT32 or 0x07 for NTFS"
also see:
[http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_kyrr.asp](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_kyrr.asp)
[http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_kljx.asp](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_kljx.asp)
Looking at this info, it appears that possibly in addition - or instead of - the change having been made to the partition table, it is the boot sector on the partition that is the problem.  If that is the case, the fixboot command may be your fix.[/I]

[I]EDIT:  This also may be useful:
"If you want to replace the boot sector on an NTFS volume, you have another alternative. When you create or reformat an existing volume as an NTFS volume, NTFS writes a duplicate of the boot sector at the end of the volume on volumes formatted with XP & W2K. You can use DiskProbe to locate and copy a duplicate boot sector to the beginning of the volume."[/I]

Good luck.

---

