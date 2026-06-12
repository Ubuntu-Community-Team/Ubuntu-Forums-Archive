---
title: "GRUB menu items showing twice"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by 8_Bit on 2011-05-26
I reinstalled Natty yesterday and then installed Fedora on a separate partition.

I now have**double** the menu items in GRUB2 for both of these.


I ran the update grub command in the terminal and it goes smoothly, but the extra menu items still don't go away.

Puzzingly the menu items  point to the same partition on the drive as their clone. Both of the Fedora menu items point to sda8  for example.

[SIZE=4]**tl;dr: How can I remove menu entries in GRUB?**[SIZE=2] I searched but could not find a reliable answer other than re-running update-grub which does not help.[/SIZE][/SIZE]
P.s. How could I remove GRUB and replace it with Plymouth? Ubuntu Software Centre actually shows Plymouth as "Installed" even though it does not run on startup.

---

### Post by ajgreeny on 2011-05-26
Are you sure this is not just updated kernels that are showing, or just the "recovery mode" for each?

Look at the number at the end of the line, which may be slightly different to each other, or for the words "recovery mode".

Can we also see the output of the command ```
sudo fdisk -l
```please, as this will tell more about your partition setup.

---

### Post by 8_Bit on 2011-05-26
Thank you for your reply! 

Yes I'm sure they are not recovery partitions. The recovery partitions show up separately. (Basically I see 2 regular Ubuntu entries along with the recovery-mode entry.

The Fedora entry does not say "Recovery mode", it is just Fedora 15 doubled. I had Fedora 15 installed before this all happened, and there was no double showing up back then. 

Here is the output from sudo fdisk -l.


> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xacc8b171

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1048782847   524288000    7  HPFS/NTFS/exFAT
/dev/sda3      1048782848  1677928447   314572800    7  HPFS/NTFS/exFAT
/dev/sda4      1677930494  1952663551   137366529    5  Extended
/dev/sda5      1940080640  1952663551     6291456   83  Linux
/dev/sda6      1677930496  1739681791    30875648   83  Linux
/dev/sda7      1931692032  1940078591     4193280   82  Linux swap / Solaris
/dev/sda8      1739683840  1931689983    96003072   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006b442

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62    15650907     7825423    c  W95 FAT32 (LBA)Here is what my partitions look like in Gparted. See attachment:

---

### Post by oldfred on 2011-05-26
Are the last two digits different. Then it is just different kernel versions.

Some have had issues with Natty, not sure if all resolved now. We normally suggest that you keep two kernels in case one gets corrupted you may be able to boot the other.

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by 8_Bit on 2011-05-26
No, here is what they look like, exactly.

[LIST]
[*]*Ubuntu, with Linux 2.6.38-8-generic*
[*]*Ubuntu, with Linux 2.6.38-8-generic*
[*]*[recovery mode options show here]*
[*][I]Fedora release 15 (Lovelock) (on /dev/sda8 )
[/I]
[*][I]Fedora release 15 (Lovelock) (on /dev/sda8 )
[/I]
[/LIST]

I just used the Grub Customizer you linked me to, to hide the doubles. They no longer appear. I suppose this will do.
It would have been nice to figure out why this was occurring in the first place, but as long as I don't see them anymore I don't really care. :P

Thank you for your help, I appreciate it!

---

### Post by oldfred on 2011-05-26
Doubles may occur if you created a custom version of one or more of the grub update scripts and then grub added back the standard script. 

Did you create a second copy of this with a different name before?
/etc/grub.d/30_os-prober

---

### Post by henryp on 2013-01-06
had this same problem, all OS's doubled. 
Following  advice given here found two similar entries  40-custom**  and 41-custom** 
also a uefi entry which I've also chmod -x'd as I've old kit

---

### Post by jlh68 on 2013-02-07
OK, I updated my netbook two days ago after a long time of not updating. When I restarted I have the duplicate grub menu items. This is the same situation I had with my laptop, which I posted to this thread earlier.

This makes me believe that the Grub Customizer application introduces this problem. The OS-prober is not doing this because it would not lhappen to two of my computers with in two months.

This may be an old problem but is is still NOT FIXED since I had it appear on 2013.02.05 and that is only two day ago.

So how about a fix instead of just pushing this problem around.

---

