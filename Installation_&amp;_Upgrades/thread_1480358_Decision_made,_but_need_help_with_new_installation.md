---
title: "Decision made, but need help with new installation"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by Cathhsmom on 2010-05-11
I have decided to reinstall Ubuntu 10.4 with no dual boot.   I hardly ever use Windows anymore, not enough to keep it on my computer.  Besides, I have other computers in the house with Windows.   

I am buying an external portable hard drive to remove all my data files on laptop.  Later the portable hard drive will be used as a back up drive.  Is there a particular hard drive that works best with Linux?   And using GParted, how should I format the external hard drive for this use?

When I install Lucid, do I let the installation CD do the formatting on my laptop internal hard drive?  Or do I reformat beforehand? If beforehand, how should I format it?

Any of you do a fresh install each time a new release of Ubuntu comes out?  If so, how do you do it without making it a big chore?   

Well, that is enough questions for now.  I will probably have more when I have help with these questions.  Thanks in advance for your generous help.

---

### Post by davidmohammed on 2010-05-11
my view on some of your questions...
  given that you said you have other windows computers - I would format it as ntfs - it will give you flexability allowing you to move between lucid and windows.

Let Lucid erase the whole hard-drive when prompted during partitioning.

---

### Post by darkod on 2010-05-11
Just to add, this is a perfect situation for you to create separate /home partition. That way in future you can do clean installs with keeping all data and settings in the Home folders for all users.
But the automated methods never offer to create separate /home.

You would need to sit down and decide how to split your int hdd between /, /home and swap partitions. That's minimum 3 unless you want to create more.

Then in the ubuntu installer use the Manual Partitioning method. Just delete all partitions one by one, and create the 3 new partitions with the sizes you decided. That's it.

Of course, you will backup all the data before that, as you said.

---

### Post by Cathhsmom on 2010-05-11
> **davidmohammed said:**
> my view on some of your questions...
  given that you said you have other windows computers - I would format it as ntfs - it will give you flexability allowing you to move between lucid and windows.

Let Lucid erase the whole hard-drive when prompted during partitioning.

I am confused a little.  I thought Ubuntu works in a Fat32 or Ext3.  Does Ubuntu work in a ntfs?  If my file system is a Ext3 and I put a Open Office document or a pdf document on a usb drive, will Windows be able to see it?

---

### Post by darkod on 2010-05-11
> **Cathhsmom said:**
> I am confused a little.  I thought Ubuntu works in a Fat32 or Ext3.  Does Ubuntu work in a ntfs?  If my file system is a Ext3 and I put a Open Office document or a pdf document on a usb drive, will Windows be able to see it?

The filesystem of the ubuntu root, /home, etc partition would usually be ext4 (newer version of ext3). There are other options too, but not fat32 or ntfs. The root partition can't be fat32 or ntfs.

But of course ubuntu can read and write to fat32 and ntfs. The suggestion was for your external hdd, to make it ntfs. That way ubuntu can read/write, but also if you plug the disk in windows computer, you can read/write from windows.

If you make the external ext4, you can only read/write on linux (there are some options to make windows read/write to ext4 but don't count on them too much).

When you copy the office document on your external hdd, it doesn't matter that the ubuntu partition is ext4. The document is saved on ntfs on the ext hdd, and windows will be able to read it and use it. Same goes for photos, movies, etc.

---

### Post by Cathhsmom on 2010-05-11
Thank you so much Darko for clearing that up.  I have a better understanding than when I originally asked my questions. 

I want to spend my money wisely on a new portable hard drive. Is there a brand and model hard drive that sticks out to be better? I am thinking that I will stay away from hard drives that have preloaded back up software that only pertains to window or mac systems.

---

### Post by darkod on 2010-05-11
Well, it depends. When you say portable, myself also when mentioning external drives I think of 2.5" and the newer 1.8" drives.

There are 3.5" drives meant to sit on your desk which are slightly cheaper for the same capacity, but there are some very elegant and portable 2.5" drives (if that matters to you).

I have a WD Passport (or was it called MyPassport) since 2007. But these days Samsung have a very elegant S2 line for 2.5", and S1 for 1.8". And I trust Samsung for electronics a lot.

See how you like them. The performance of most drives will be similar, I can't really point out a particular model. Maybe someone else can.

---

### Post by Cathhsmom on 2010-05-11
Thank you.  I do not necessarily need it to be elegant, but maybe take a beating.   I was leaning towards a WD Passport, but then I saw some portables (2.5 and less) that have an enclosure that can take an accidental fall.  I have two toddler grand-babies that touch everything and I can see them dropping it.   Iomega and LaCie have hard drives that can take some abuse, but I do not know if they are good.   Then again, I may just get a cushion case and WD passport.  I would solicit an opinion.

---

