---
title: "Need help restoring 95GB backup.tar.gz file"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by BoredOutOfMyMind on 2011-01-20
I did a backup of /photos /documents /downloads and /music with mintbackup creating backup on /dev/sdb1

I cannot get mintbackup to restore the file, and I was able finally to get /music file restored. Below is error from cli 

```
BoredOOMM@ursa-major ~/temp $ sudo tar xzvf 2011-01-16-1424-backup.tar.gz
[sudo] password for BoredOOMM:
.mintbackup
Music/TheWhistler1947.zip
Music/SUSPENSE6.zip
Music/TheWhistler1946.zip
Music/WSBAM750.pls
Music/listen.pls
Music/SUSPENSE8_64kb_mp3.zip
Music/AM1710.pls
Music/KHGY.m3u
Music/SUSPENSE7.zip
tar: Skipping to next header
tar: Exiting with failure status due to previous errors
```

Please help with how to access /folders within the backup as I need the /documents files? 

Thank you!

---

### Post by psusi on 2011-01-20
Your backup is corrupted/truncated.  Are you sure it is 95g?  How big are those files that it did extract?

---

### Post by BoredOutOfMyMind on 2011-01-20
> **psusi said:**
> Your backup is corrupted/truncated.  Are you sure it is 95g?  How big are those files that it did extract?

/Download is 8GB and what /Music was saved is about 6 Gig. 
/Pictures is 8 GB and the rest would have been /Documents with subfolders with jpg photos. 
 I did get all the /Music that was in it's own archive (should have placed each folder in seperate archive I guess)

The .virtualbox folder is 20GB and other than that, I did not keep any system files except .conkyrc

I have read there is a way to read the headers and folders in the file, but I did not understand all of it. If I can skip part of what is there, I would like to try to recover some more. :D

---

### Post by psusi on 2011-01-21
I mean how big are the files you extracted, not how big were they when you backed them up.  It tried to skip past the bad part and still didn't find any more, which is why I asked what is the size of the backup file, because it seems like you only have part of it.

ls -lh 2011-01-16-1424-backup.tar.gz
du -sh Music

---

### Post by BoredOutOfMyMind on 2011-01-21
> **psusi said:**
> I mean how big are the files you extracted, not how big were they when you backed them up.  It tried to skip past the bad part and still didn't find any more, which is why I asked what is the size of the backup file, because it seems like you only have part of it.

ls -lh 2011-01-16-1424-backup.tar.gz
du -sh Music

Some of the files were small scanned .jpg pages and some were the 20GB .virtualbox.  

```
bkberger@ursa-major:/media/42adc5c9-f8ab-4fa0-81c8-66d20cbf3ecb$ sudo ls -lh 2011-01-16-1424-backup.tar.gz du -sh Music
ls: cannot access du: No such file or directory
ls: cannot access Music: No such file or directory
96G -rwxrwxrwx 1 bkberger boredoomm 96G 2011-01-16 20:50 2011-01-16-1424-backup.tar.gz
```

---

### Post by psusi on 2011-01-21
You plastered both lines into one.

At any rate, your backup is corrupt so you're pretty much out of luck.  Without compression tar can try to skip past the bad part and pick back up after, but this isn't possible when it is compressed.  At least, not the way tar does compression.

---

### Post by BoredOutOfMyMind on 2011-01-21
> **psusi said:**
> You plastered both lines into one.

**At any rate, your backup is corrupt so you're pretty much out of luck.**  Without compression tar can try to skip past the bad part and pick back up after, but this isn't possible when it is compressed.  At least, not the way tar does compression.

 The wise guy would say "I find your lack of faith disturbing.":o

I did get a copy of some of the files from 08/2010 so not all is entirely lost.  Next time I will create smaller files and verify. 

Thanks for trying to help. ;)

---

### Post by psusi on 2011-01-22
Also don't use compression, especially when most of what you are backing up is already compressed ( mp3s, etc ).

---

