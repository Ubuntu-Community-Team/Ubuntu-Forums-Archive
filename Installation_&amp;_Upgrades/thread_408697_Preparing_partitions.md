---
title: "Preparing partitions"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by alfreddo on 2007-04-13
I am trying to install Dapper Drake on my desktop, to dual boot with Windows 98. All goes well until I reach the screen headed 'Prepare Partitions' which looks like this:

Long box at the top contains ;  /dev/hda1
                                              37.27GB

Below there is a small green square followed by FAT 32

Below that a box with these headings - (horizontal, not vertical as here:)

Partition
/dev/hda1 (then an orange triangle with a ! in it)

File system
(green square) FAT 32

Size 
37.27 GB

Flags
boot lba

Clicking on 'forward' brings me to the next screen:

Top right, two choices:     /dev/hda  (37.27GB)
                                     /dev/hdb  (14.30 GB)

Then a long narrow box with slider arrows at both ends that don't slide.
 Under it says: minimum size: 38162 MB. Maximum size : 38162 MB

Free space preceding (MB)  0   (up and down arrows greyed out)
New Size  (MB)  38162     (I can manually type in a new figure, but it then reverts)
Free space following  (MB)  0

Resize/Move button greyed out

All I can do then is return to the previous screen.

Any thoughts?

---

### Post by Tsen on 2007-04-13
A screen shot would be nice.
Just press the "Print Screen" button on your keyboard, save it and upload it.

Although, out of curiosity, why are you running '98?  That was before MS switched to using NTFS, which is why your disk is in FAT32.
Anyway, a tip to try first of all would be to defragment the disk a few times in Windows.  One of FAT32's biggest problems is that it fragments like no other, which can make it so that there's no usable empty space at the end of the disk, even if there's open space still on it.  Defragmenting should take care of that problem.

---

### Post by ffxr on 2007-04-13
so you have 2 hard disks in there..? one formatted with FAT32 & an empty one? is that correct?

---

### Post by alfreddo on 2007-04-13
This is an old machine with an AMD Athlon 850 Mhz processor, Elsa Gladiac MX graphics card (Nvidia chipset), and 250 Mb RAM. I used the second hard drive for backups and archives. 

It's been lying around unused for a while so I thought I'd use it as a testbed to try out Ubundu. 

Would it be simpler if I just forgot about the dual boot and did a clean installation of Ubundu without having to worry about partitions? 

I only wanted to retain Windows 98 because of a couple of old games that prefer it to XP  (eg Starship Titanic). So no big deal if it goes.

If I do install Ubundu as the only OS on the main hard drive, can I do anything with the secondary drive to make it still useful?

---

### Post by Tsen on 2007-04-15
Yeah, you'll still be able to use the second hard drive for just about anything you want.
A clean install would be easier, I think, and would probably be a concrete improvement over '98.  And if you really wanted, you could probably tweak WINE or VMWare to run those old games...
(Though VMWare might have trouble running on an older machine)

---

### Post by alfreddo on 2007-04-16
Thanks, Tsen.

I've done a clean install and everything looks good. I now have to study the literature to work out how to get the new setup to recognise the second hard drive (FAT 32) and the zip drive - both shown as existing but inaccessible. I know it has to do with installing mount points. Also it won't talk to the printer on my Windows network. 

I think RTFM is the answer...

---

