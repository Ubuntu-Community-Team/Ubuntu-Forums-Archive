---
title: "Installing Ubuntu needs partition; GPart not working; living with Vista"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by _Paladin on 2007-04-21
Already, thanks for any help.  

I have been searching for days for a solution to this problem, so any help is greatly appreciated.  

I would like to dual boot Vista and Ubuntu, but I have having some problems.  I need to make a large partition for Ubuntu, but I cannot make one.

I have a HP Pavilion dv6000z.  I do not have a Vista Disc, rather, I only have HP restore cd's that I made myself.  

I have tried in Vista the whole "Disk Management" deal, both the GUI and the command line method and I cannot shrink it.  An example of that can be found [here]("http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/").  The GParted Live CD would also not do the trick. 

I have tried the Acronis Disk Director Suite 10.0, and the trial seems to work.  Alas, the trial will only shrink about 7 mb at a time, and I do not have $50 to spend on a one time partition.  

This is the message I got from Fiesty when I tried resizing the partition during an attempted installation:   

GParted 0.2.5

Resize /dev/sda1 from 105.58 GiB to 28.84 GiB    ( ERROR )
    	
check filesystem on /dev/sda1 for errors and (if possible) fix them    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 113364627968 bytes (113365 MB)
Current device size: 113364632576 bytes (113365 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 3147732 (0x3007d4): extra cluster in $Bitmap
Filesystem check failed! Totally 1 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

How would I accomplish that inside of Vista?  I tried the "Error-checking" under properties, but that does not seem to work either.  I do not have any OS cd other than Ubuntu.  

Thanks

---

### Post by spin2cool on 2007-04-21
The problem isn't with the tools, but with your filesystem.  Have you run a check disk from windows?  I've never used vista, but on XP, it would be accomplished by going into the drive's properties and choosing scan disk.   You'll need to fix the filesystem errors before any tool will let you resize.

---

### Post by _Paladin on 2007-04-21
That is one of my problems.  I have tried the "Error-checking" tool under my hard drive properties, and that didn't do anything.  I have also been scanning the internet for something, but everything is XP related.

---

### Post by pepsi_max2k on 2007-04-21
probably won't have any affect but, you could try some of this...
[http://ubuntuforums.org/showthread.php?t=413745&page=2](http://ubuntuforums.org/showthread.php?t=413745&page=2)

---

### Post by _Paladin on 2007-04-21
I don't think that will work either.  I tried running the utility, nothing has seemed to work with that. Also, on the wiki page, Vista is not listed as a supported OS.  Thanks though...

---

