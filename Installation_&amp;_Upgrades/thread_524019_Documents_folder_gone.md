---
title: "Documents folder gone"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by revtds on 2007-08-12
Last night, I edited and saved a file into a folder in "Documents", located on my Desktop.

This morning, when I went to retrieve by document, I noticed the icon for my "Documents" folder was missing.  Gone.  I opened Nautilus, it said it didn't exist.

I restarted the PC, and I still do not have a "Documents" folder, nor any record of one that I can find.

Where to start and how do I recover this folder.

I recently upgraded to 7.04, running on a AMD Athlon with 1G RAM, a new 80G hdd.

---

### Post by forestpixie on 2007-08-12
Firstly I assume you checked trash 

open terminal and you can use it to search, first do

```
sudo updatedb
```

it'll take a while to update. then you can search in the terminal
```

locate <name>
```

so if you where looking for your document put that name in - be careful with upper and lower case

Edit - if you find the file I assume you'll have found the folder

---

### Post by revtds on 2007-08-12
I ran updatedb, which only took 2-3 seconds, then I searched for "Documents" looking for the folder, and it returned:
tom@tom-desktop:~$ locate Documents
/home/tom/.nautilus/metafiles/file:%2F%2F%2Fhome%2Ftom%2FDesktop%2FDocuments.xml
/home/tom/.nautilus/metafiles/file:%2F%2F%2Fhome%2Ftom%2FDesktop%2FDocuments%2FGraphics.xml
/home/tom/.nautilus/metafiles/file:%2F%2F%2Fhome%2Ftom%2FDesktop%2FDocuments%2FLPMentors.xml
/home/tom/.nautilus/metafiles/file:%2F%2F%2Fhome%2Ftom%2FDesktop%2FDocuments%2FPDF's.xml
/home/tom/.nautilus/metafiles/file:%2F%2F%2Fhome%2Ftom%2FDesktop%2FDocuments%2F2007Worship.xml
/home/tom/.nautilus/metafiles/file:%2F%2F%2Fhome%2Ftom%2FDesktop%2FDocuments%2FChurch.xml
/home/tom/.nautilus/metafiles/file:%2F%2F%2Fhome%2Ftom%2FDesktop%2FDocuments%2FChurch%2FWebsites%2FNorwich.xml
/home/tom/.evolution/cache/http/2b/http:%2f%2fPatriotShop.US%2fimages%2fFoundingDocuments.jpg
/home/tom/.evolution/cache/http/2b/http:%2f%2fpatriotshop.us%2fimages%2fFoundingDocuments.jpg

Not seeing what I was looking for, the "Documents" folder, I searched for the specific file I needed and got this:
tom@tom-desktop:~$ sudo updatedb
tom@tom-desktop:~$ locate 081207ser.ods
tom@tom-desktop:~$ 

Telling me, I assume, that it doesn't exist.  The PC was not turned off last night, so when I came to it this morning, it was still, running.  The power was not off, and it is on a UPS anyway.

---

### Post by forestpixie on 2007-08-12
Is your system linux only or do you dual boot? 

Is your document folder on the same drive?

---

### Post by revtds on 2007-08-12
This is a Ubuntu only system, no dual booting, and the hdd is partitioned with a swap partition of 2G, a 10G home partition and the balance of the 80G is for the OS.  "Documents" resides (or did) in my Desktop folder, /home/tom/Desktop/Documents.

---

### Post by forestpixie on 2007-08-12
I really have no idea then - the only thing i could think of trying would be looking through nautilus again - show hidden files - View - Show Hidden Files. 

Try locate *.ods to look for any of them 

Sorry I can't be of more help :( 

If I think of anything else I'll post it here

---

### Post by revtds on 2007-08-12
Thanks for your efforts.  I tried locating *.ods, and one file shows up, in an examples folder.

Anyone else out there have any ideas?

---

### Post by ryoko345 on 2008-07-23
I had a similar problem that I am still working to resolve.  My documents folder has not dissappeared, but everything in it has.  Although I can still access it if I run a "sudo nautilus" command and browse it that way.  Does your's exist under root?  Might this be the same bug?  I don't know.  You are the only one I have seen that has remotely the same problem.

---

