---
title: "Incorrect Parttition Table!?!?"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by telmo on 2005-04-19
Hi.
I'm trying to customize a version of ubuntu/knoppix and i need to create a partition using QTPARTED. But it tells me that probably another partitioning tool created an [COLOR=Red]incorrect partition table[/COLOR],... bla, bla, bla... and fdisk tells me the allocated sectors are higher than the maximum allowed... :( And i can't use qtparted. I can simply ignore this error using parted, but the instalation requires qtparted...

Is there any quick solution to this? How can i correct this problem??

thx

---

### Post by heimo on 2005-04-19
I recall having similar symptoms. Could it be LBA problem? Try changing the access mode setting in BIOS.

---

### Post by telmo on 2005-04-19
I tried that. But i don't have that option in my BIOS.  :-? 
Isn't there any kind of software i can use to fix it?
I cannot just format my HD! I simply cannot!

---

### Post by telmo on 2005-04-20
I tried that. But i don't have that option in my BIOS.  
Isn't there any kind of software i can use to fix it?

My partition table is NOT healthy! PLEASE help!!!

---

### Post by heimo on 2005-04-20
Hmm.. I don't know if this could help, but you can pass CHS (cylinder, head, sector) information to kernel, I believe it was something as simple as ```
hda=C,H,S
``` where hda is the device and CHS the numbers for your drive geometry (probably available from you HDD manufacturer / manual).

---

### Post by telmo on 2005-04-20
[QUOTE=heimo]Hmm.. I don't know if this could help, but you can pass CHS (cylinder, head, sector) information to kernel, I believe it was something as simple as ```
hda=C,H,S
``` where hda is the device and CHS the numbers for your drive geometry (probably available from you HDD manufacturer / manual).[/QUOTE]

Thank you! I'll try that!
I've searched google all night long and haven't found a solution that fits me. So... in the meantime, if anyone else has another solution, please advise ;)

---

### Post by telmo on 2005-04-20
Anyone??? PLEASE!?

---

### Post by skoal on 2005-04-20
Well, I hesitate to post this, but if I could borrow a line from a great movie [Krull](http://www.imdb.com/title/tt0085811/), "here's the knowledge you seek...":  You can rebuild your partition table using fdisk.  If you've seen that movie and remember that line, you'll understand the relevance of it.  It can be dangerous...

I used [this](http://linux-universe.com/HOWTO/Partition/recovering.html) techique to rebuild my partition table succesfully a few months ago.  If you feel uncomfortable doing it this way, you might want to {look at|try} the other 2 tools mentioned on the first line.

---

### Post by telmo on 2005-04-20
[QUOTE=skoal]Well, I hesitate to post this, but if I could borrow a line from a great movie [Krull](http://www.imdb.com/title/tt0085811/), "here's the knowledge you seek...":  You can rebuild your partition table using fdisk.  If you've seen that movie and remember that line, you'll understand the relevance of it.  It can be dangerous...

I used [this](http://linux-universe.com/HOWTO/Partition/recovering.html) techique to rebuild my partition table succesfully a few months ago.  If you feel uncomfortable doing it this way, you might want to {look at|try} the other 2 tools mentioned on the first line.[/QUOTE]

Thank you!
Just a question... what are the other 2 tools you mencioned in the first line?? :)



EDIT: Sorry... found it|  O:)

---

### Post by skoal on 2005-04-21
oops!  I made 1 assumption when I gave you that information Telmo.  I used that technique (from the link provided) to rebuild my partition table while using an ext3 filesystem.  It will work for ext2 as well (of course).  

I use reiserfs now and that 'trick' won't work (since it relies on superblock info gleaned from dumpe2fs).  If you were using a reiserfs filesystem you're probabably stuck with using one of those 2 other tools.

---

