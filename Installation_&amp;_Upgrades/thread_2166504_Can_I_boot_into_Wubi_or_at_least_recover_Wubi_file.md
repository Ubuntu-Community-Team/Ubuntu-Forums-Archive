---
title: "Can I boot into Wubi or at least recover Wubi files when root.disk is 0kb in size?"
date: 2013-08-09
forum: Installation &amp; Upgrades
---

### Post by XKRh8WA on 2013-08-09
I installed Wubi two months ago for an internship.  It worked great all summer, but roughly a week ago I could no longer boot into Ubuntu.  I get the GRUB screen.

I've followed countless instructions on the web.  I've run dskchk, I've tried using "ext2read" type software, I've tried running GRUB commands, etc.  Nothing so far has worked (if you want specifics about how none of them worked, just ask).  Today though I noticed something...

My root.disk file is 0kb in size!  

It never occurred to me to check the size until I kept reading the same story about it over and over again.  However, to my horror, no one seems to have explained how to fix it.

So, is there a way to boot into Wubi again if root.disk is 0kb?  If not, how could I go about recovering my files?  The files I want to recover are nearly all ".cpp" or ".txt" files.

---

### Post by Mark Phelps on 2013-08-09
IF the root.disk file is indeed empty, there is (1) nothing to boot into and (2) nothing to recover.  Sorry ...

---

### Post by XKRh8WA on 2013-08-10
> **Mark Phelps said:**
> IF the root.disk file is indeed empty, there is (1) nothing to boot into and (2) nothing to recover.  Sorry ...

I can't accept this as an answer.  My entire Ubuntu hard drive couldn't have simply been wiped!

Two questions (for anyone and everyone):
Is root.disk the entire Ubuntu partition?

Might the missing files show up in a hard drive recovery tool like photorec?

---

### Post by XKRh8WA on 2013-08-11
Is it really DEAD dead?  Are all my Ubuntu Wubi files that I spent a summer working on completely wiped from hard drive?  Is there no recovery that will find them?

If so, say so!

---

### Post by oldos2er on 2013-08-11
root.disk isn't a partition, it's a file within your Windows partition.

---

### Post by Mark Phelps on 2013-08-12
> **XKRh8WA said:**
> I can't accept this as an answer.  My entire Ubuntu hard drive couldn't have simply been wiped!

Two questions (for anyone and everyone):
Is root.disk the entire Ubuntu partition? YES --  it's a file that acts like a Linux filesystem.

> Might the missing files show up in a hard drive recovery tool like photorec?
Don't know for sure -- but probably not, as it is not a native Linux filesystem.

---

### Post by SlugSlug on 2013-08-12
Where was your root.disk stored? If your win7 and kept it in your Documents you might be able to use shadow copies

---

### Post by Frogs Hair on 2013-08-12
The root disk is installed on the c drive by default . To most Windows (defrag) disk tools the root disk is seen as series of clusters. There may be some third party applications that _could_ affect, harm, or remove the root disk.

I know a few Wubi users (Win7) and have never heard of the disk volume being reduced or removed without Wubi being removed  and in that case there would be no Ubuntu option in the windows boot loader. Windows 7 system tools can identify Ubuntu as an unknown operating system. 

> My root.disk file is 0kb in size!    How did you verify this ? If this is the case I would be inclined to agree with Marks first response to the thread. If the root disk is 0kb it is not ok so knowing how that was determined may be important .

---

### Post by XKRh8WA on 2013-08-13
When I open My Computer in Windows 7 and navigate to C:\ubuntu\disks, it lists root.disk as being 0kb in size.  Also, if I open root.disk in a text editor, it's basically a blank file.

Could this information be inaccurate though?

---

### Post by Frogs Hair on 2013-08-13
After checking with a Wubi user I found that you should see a volume thousands of Kb  under[COLOR=#000000] C:\ubuntu\disks and in his system there is a swap volume as well. The root disk is definitely gone. I don't know if a recovery tool is an option with a Wubi installation or not.    [/COLOR]

---

### Post by XKRh8WA on 2013-08-18
The only files I absolutely must recover are a handful of C++ files and headers.  Photorec seems like a good option because it ignores the file system, but the website doesn't say it supports .cpp files (it supports .c and .h files though).  Are there any other tools?

---

### Post by XKRh8WA on 2013-08-18
I've read that its extremely difficult to remove all the information from a hard disk.  Theoretically, a disk could be buried in the ocean for a hundred years and still be recoverable.

If the FBI wanted to search my poor old disk for .cpp files, what would *their *options be?

---

### Post by Frogs Hair on 2013-08-18
I don't know of a Win based recovery tool that can locate and read files from a deleted Linux file system inside Windows and  would have search . The first recommendation from most tutorials I have seen  state to stop using the computer immediately because the data  degrades the more the system is used.

Any recovery tool would require the ability to read deleted ext files and run in Windows. [http://www.differencebetween.com/difference-between-linux-file-system-and-vs-windows-file-system/](http://www.differencebetween.com/difference-between-linux-file-system-and-vs-windows-file-system/)

---

### Post by Mark Phelps on 2013-08-19
There is the possibility that this is a "new"  version of root.disk that is zero-length and an older version still exists on the drive.  Since this file existing inside a Windows filesystem, you would do best using Windows data recovery utilities to try to get it back.

Since your data was on a Windows partition, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by XKRh8WA on 2013-08-26
I've run RecoverMyFiles over drive C.  In the results of recovered files, I've sorted through a list of things called "root.disk".  

The root.disk's from 8/3/13 (when I started having my problems) are 0kb, but the rest of them don't even mention a size.  The size fields are just blank.  Are these files trashed or recoverable?

EDIT: In the viewer at the bottom of the screen, I've selected "TEXT", but absolutely nothing is showing.  Could my root.disk be renamed/reformated/misplaced or is this the end of the line?

---

### Post by Frogs Hair on 2013-08-26
I think Marks suggestion is the end of the line. Renaming a 0 byte root disk won't change its volume.

---

