---
title: "transfer installation to same size hard drive"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by cain071546 on 2010-03-25
my 40gig drive is failing and im worried it just wont work one day instead of trying to fix all the bad sectors i would like to transfer my installation to my other 40gig drive
but all the damn tutorials online assume the new drive is always bigger so i can not find instructions on how to do this with identical size drives would someone help before this drive decides to die on me

---

### Post by 2hot6ft2 on 2010-03-25
Many recommend clonezilla.
Personally I use the dd command and haven't had any issues with it yet, while others say they have had issues using the dd command for cloning a drive. For that matter GParted can copy an entire partition to another drive (I haven't tried that either).
So there are ways to do it and cloning to a larger drive is what people do most often but as long as the destination drive is NOT smaller than the source it amounts to the same thing just without expanding the partitions after the cloning is done.

If you want the instructions for using dd to clone it let me know and I can post it.

---

### Post by srs5694 on 2010-03-25
One issue with dd is that the new drive might not be *exactly* the same size as the old one. If the original drive is (making up a number) 40.02GB and the new drive is 40.00GB, then the partitions on the old drive might not exactly fit on the new drive. Depending on what's in that final 0.02GB of space, you could end up omitting some critical file. OTOH, it might work OK; that 0.02GB of space might be unpartitioned and therefore unimportant, or if the new disk is slightly bigger than the old one, it'll also work fine (assuming you're using MBR partitions; with GPT an easy post-copy adjustment will be necessary if the drives differ by even just 1 sector in size).

A dd copy will also take longer than will many other methods, particularly if your partitions have a lot of free space on them. That might or might not be important, of course.

Since the original drive is said to be failing, it should be noted that a dd copy may take longer or fail if it encounters bad sectors on the source, even if those bad sectors are currently unused.

Overall, I'd recommend using a utility with enough smarts to handle partition resizing while cloning the installation and to copy only those sectors that are in use. I've never used Clonezilla, but as 2hot6ft2 says, it seems to be quite popular, and its feature list looks pretty good for this sort of thing.

---

### Post by Slim Odds on 2010-03-25
I totally agree with srs5694.

If you have two identical drives, dd might be just fine. But even if the drives are the same size, they may have different geometry (platters, cylinder, etc.) which dd will not account for.

clonezilla is very good.

---

### Post by 2hot6ft2 on 2010-03-25
srs5694 makes some good points. Clonezilla's not in the repos but here's the website for it.
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

