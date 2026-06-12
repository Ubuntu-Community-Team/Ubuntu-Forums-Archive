---
title: "Installation modifies partition structure"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by jakenn-linux on 2011-07-31
I've been dual booting Windows and Ubuntu for a number of years.  I usually have two primary partitions (one for Windows and one for Ubuntu) and an extended partition for everything else (Swap, and shared partition for data).  With the last version, 11.04, I have experienced a strange happening.  On both my desktop and laptop I did a clean install.  After running into some other related problems, I used gparted to examine the hard drive.  I discovered that during the upgrade, Ubuntu's primary partition was "moved" within the extended partition.  So now I have just one primary partition and one extended partition (which included Ubuntu, 2 swap, and the shared data partition).  Both Windows and Ubuntu seem to run just fine, but I did not tell it to change the partitions (I said to use the current partition I had for Ubuntu).  I just checked the laptop and it's the same: one primary partition and one extended, when I know that I had it set up with 2 primary and one extended.  Anyone with explanation as to what happened so I know what to do when I wipe the hard drives and start all over?

---

### Post by oldfred on 2011-07-31
Did you choose one of the auto install options, not the manual install (Something Else in Natty)?

---

### Post by jakenn-linux on 2011-08-02
Since I already had two partitions created (one for Windows and the other for Ubuntu - 10.10), I used the manual option so that I could tell the installer to use the already created partition.  I did tell it to format the partition so it would clear out the old version and install 11.04.

---

### Post by oldfred on 2011-08-02
I run this script as part of my rsync backup just to document my configuration. Run it and we can see exactly how you are set up now.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by jakenn-linux on 2011-08-03
My original hard drive configuration was:  sda1=windows (primary, boot); sda2=Ubuntu (primary); sda3=extended, with; sda4=sway; sda5=downloads; sda6=shared.

Now the configuration is: sda1=windows (primary); sda2=extended, with; sda3=Ubuntu (inside the extended); sda4=swap; sda5-swap (another one, but different size); sda6=downloads, sda7=shared.

The questions is how did my Ubuntu partition during the upgrade (clean install) go from a primary partition to inside the extended partition.  This happened on both my desktop and laptop.

---

### Post by oldfred on 2011-08-03
Partition sda3 cannot be inside the extended partition by definition. All partitions in the extended start at sda5 and go up from sda5. Sda1 thru sda4 are primary partitions with one primary often the extended.

If sda3 is showing as inside the extended you have partition problems.

Often if that is the only issue this may work. But boot script would help us be sure.

Backup current partition table first and save to some other device:
sudo sfdisk -d /dev/sda > parts.txt

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

