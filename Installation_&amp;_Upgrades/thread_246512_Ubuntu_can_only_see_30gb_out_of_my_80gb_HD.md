---
title: "Ubuntu can only see 30gb out of my 80gb HD"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by paul_b on 2006-08-29
I went through the live install and evething was fine until it was time to prepare the disk. I want to completly remove WinXP and install Ubuntu (take the entire disk). ubuntu gives me 2 options: erase and install ubuntu on 31gb hd or manually partition the disk.
I selected the second option in an effort to give ubuntu the 80gb of space with gparted but gparted can only see 31gb.

I also tried the gparted live cd with the same results

Should I try QTparted?

Should I try to install the alternate ubuntu cd?
thanks paul

my system is basic amd duron 900 256 ram ati video card.....

---

### Post by steven43126 on 2006-08-29
hmm maybe a corrupt partition table? try a livecd with fdisk and delete all the paritions, i think fdisk may give an option to delete the partition table?. Also use fdisk to reset the MBR, then try again and see what you can see.

Maybe also check the BIOS make sure the settings for Cylindars/Heads/Sectors are correct with the drive specification?

steve.

---

### Post by paul_b on 2006-08-29
Something I forgot to mention is that when working off the live cd the hard disk appeard with the correct size of 76.5gb.

Maybe this will help.

thanks
paul

---

### Post by etcpool on 2006-08-29
have you checked that your bios is up to the latest version?

---

### Post by paul_b on 2006-08-29
Thanks guys, I will try these suggestions once I get home tonight.
Paul

---

