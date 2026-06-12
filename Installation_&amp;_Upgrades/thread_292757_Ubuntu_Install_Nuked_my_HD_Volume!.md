---
title: "Ubuntu Install Nuked my HD Volume!"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by randallsell on 2006-11-04
Man, I couldn't have asked for a worse result... Here's the skinny on what happened...

I purchased a 320G drive. I created 4 partitions. 3GB (for root) 1GB for swap, and then what remained (316) I divided into two equal size partitions. The large 158GB partitions were formatted with NTFS.

Here's the part were I really messed up. I assumed that the two unformatted partitions (3gb and 1gb) would happily be "seen" by the Ubuntu installer (6.0.6?) and not touch my other partitions.

Well, it didn't. And to make matters much worse - I copied about 60GB of backups to the first 158gb partition.

After getting cold feet on the Ubuntu install (i run a multi boot with Win98, 2k, XP, and XP-Media Center) I went back to Windows to find that my large 320g drive was now empty! I have spent the last 10 hours searching for tools on the web to recover it.

So, my question is not so much - how to install Ubuntu. It is a given that that is not my top priority right now.

My question is - what exactly does the Install process do - when I pick my partitions to install to? I need to know this, in order to know what tools might help me recover.

The point I got up to - is what I beleive is the last screen. I did a "manual edit" of the partition tables. and selected my 3gb and 1gb drives for root and swap respectively. And then blanked everything else as I beleive I read from some instructions somewhere else. I also opted to format these two. At that point when I clicked "forward" it told me it could not format, for whatever reason, and that's when I backed out and went back to Windows to find an unpleasant surprise.

If anyone knows exactly what the install did at that time, or any tools they recommend to restore the partition, that info would be much appreciated.

I shoudl also mention that in Windows, the Drive was created as a Dynamic drive. but I am not sure what that means relative to a "Basic" drive but Windows seemed to choose that for me - so I went with the flow.

cheers
-randall

---

### Post by Neky on 2006-11-04
Insert the live CD, boot Ubuntu as live distro and open Terminal.

then type *sudo gparted* and edit your partitions there, format them the correct way ( the root and the swap one ) and then try to reinstall Ubuntu the way you did it the last time ( Manually edit partition tables and that ). That`s what i`ve done and worked for me but that`s only 1/2 answers. I`m affraid i can`t help you with your data backup.

Cheers!

---

### Post by Thomas,Bakker on 2006-11-04
you could trie [Restorer 2000 professional]("http://www.restorer2000.com/") to try recover your files.
be prepared for a long wait though 60 GB is a lot to recover and it needs to scan your entire drive (all 320 GB of it)

only i dont know if there is an trial version of this software i would say google it up i hope its usefull.

---

### Post by randallsell on 2006-11-04
Well, for all those people that are reading this thread becuase they made the same mistake I did - here's the answer...

[http://www.windowsitpro.com/Articles/Index.cfm?ArticleID=25375&DisplayTab=Article](http://www.windowsitpro.com/Articles/Index.cfm?ArticleID=25375&DisplayTab=Article)
and
[http://support.microsoft.com/default.aspx?scid=kb;en-us;q153973&id=kb;en-us;q153973](http://support.microsoft.com/default.aspx?scid=kb;en-us;q153973&id=kb;en-us;q153973)

In short, I was able to recover the boot sectors of my partitions (which seem to be called Volumes on a dynamic disk). It was confusing because the first link above talks about "restoring a dynamic volume" whereas the second link talks about partitions. I had to jump thru many MS hoops on the MSDN site to get WindowsXP-KB838079-SupportTools-ENU.exe which is the XP Support Tools - it has the dmDiag.exe and dskprobe.exe tools needed to find and re-write the boot sectors respectively. And it only worked because I knew the exact sizes of the various volumes/partitions. 

Anyway, after a lot of checking to ensure I had it all right, all my data magically re-appeared again. Order in the universe is once again restored :)

while on the topic - not all the recovery tools out there are as good as they claim - the largest, and most expensive (Easy Recovery Pro 6.1) did an average job of recovering files. Whereas simpler tools like Handy Recovery 3.0 recovered files that Easy Recovery could not. In this case, you don't get what you pay for. (I was using trial versions on both).

Now - back to getting a multi-boot happening. It would appear the general stategy by everyone is to install Ubuntu last, then use a Rescue/boot CD for XP to restore the MBR/NTLDR? If anyone has a step by step guide, I'm all ears.

thanx for those who responded.

cheers
-randall

---

