---
title: "Ubuntu does not see all drives"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by Mark_Galeck on 2010-05-26
Hello, 

I have two hard drives, 160GB has WinXP installation, the other 200GB has just data. In the 200GB I installed Ubuntu. At boot, I now have a choice: Ubuntu or XP. If I boot to Ubuntu, "Places" show the 160GB drive contents, but from the 200GB drive, only the Ubuntu filesystem, not the whole disk.

What do I do to get the whole disk contents to show??

Thank you,

Mark

---

### Post by darkod on 2010-05-26
Are you sure you have other partitions on the 200GB disk?

Can you post the results of:

sudo fdisk -l

---

### Post by jerenept on 2010-05-26
Are you sure you didn't delete your data?

---

### Post by Mark_Galeck on 2010-05-26
Yes, I did not delete my data :)  and also, I only have one partition (Ubuntu was installed as a file on a Windows filesystem).  

OK, so what I see, is that Places->Computer, does not show my 200GB drive. Like I said before.  

But, I discovered that under /host, there are all the files on that other drive.  OK, I guess that is the way it is?  Hope this helps others with the same problem.  

Thank you,

Mark

---

### Post by darkod on 2010-05-26
> **Mark_Galeck said:**
> and also, I only have one partition (Ubuntu was installed as a file on a Windows filesystem).  


You should have started with that. :)
Also, that's called wubi and it has its own thread type, [wubi], not [ubuntu]. We can't know if you don't tell/show us.

---

### Post by Mark_Galeck on 2010-05-28
> **darkod said:**
> You should have started with that. :)
Also, that's called wubi and it has its own thread type, [wubi], not [ubuntu]. We can't know if you don't tell/show us.

Oh, thanks I did not know that wubi mattered.  Actually, I could not run wubi at all from it's website, it gives me errors, which I posted here, there were many views but no replys.

So, I went to the Ubuntu site, burned a CD with the downloaded Ubuntu latest image, and then, on the CD, there was a wubi.exe, OK this time it worked.

---

### Post by darkod on 2010-05-28
Unfortunately, I don't use wubi at all, and I don't know in details how it works. I have no idea why it shows or doesn't show any disk or partition. Sorry.

---

