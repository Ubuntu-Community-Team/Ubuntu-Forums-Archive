---
title: "Hardy - Partitions, Emails and Bookmarks"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by Weta on 2008-05-02
Hi   
I would like to do a fresh install of Ubuntu from Dapper to Hardy, on a fairly basic desktop where Ubuntu is the only OS, using an live/install CD (because we are on dial-up). I haven't been able to find guidance about:
1.  the sizes that I should make the root, home and swap partitions;
2.  how to import current emails into Nautilus once Hardy is installed;  
3.  how to import existing bookmarks into Firefox once Hardy is installed.
Any advice would be appreciated. Thank you!

---

### Post by Dale61 on 2008-05-02
I can understand why you don't want to upgrade via the update manager when on dial-up.  I did that in early April, and it took 100 hours.

However, I have not had a problem whatsoever, sans a few minor things that were covered in these forums, after upgrading from 6.06 to 8.04.

As I said, I'm on dial-up, and my pc was connecting (successfully) during the first boot up of 8.04, and I was straight into 1440 x 900 resolution (widescreen) from the get-go.

I didn't have to resize any partitions, or import bookmarks, etc, as for me, it was all done automatically.

I could be wrong, but I remember reading that there is an upgrade option on the CD, so that could be your best bet.

---

### Post by Pumalite on 2008-05-02
Tell me your specs. How large is your HDD? and are you planning to keep Dapper while you install 8.04 in a separate partition?. Once you wipe that HDD for 8.04, the is nowhere to import emails. Save them and restore them.
A good scheme is:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops for hibernatition)
The rest for /home.
Are you dual booting?
(You can go straight from 6.06 to 8.04 LTS)

---

### Post by Weta on 2008-05-02
Thank You.  The HDD is 40GB, and I wasn't planning on keeping Dapper (or any other OS) while I install Hardy. I have a few more specific related questions: 
1. Would it be sensible to create a small "/boot" partition (c.50MB), and to leave much of the hard drive unpartitioned (to enable the partitions to be easily adjusted)?
2. I was planning to copy my existing "home" folder into the new "/home" partition.  Assuming this is sensible, then will doing this automatically restore the Evolution emails/contacts?  
3.  What is the file name that I should use to import/restore my Bookmarks into Firefox?
Thanks again.

---

### Post by Pumalite on 2008-05-02
Don't use a /boot partition. Work with '/', /home and /swap. I'm not sure your 6.06 settings will be any good in Hardy. I usually copy bookmarks.html to a CD and later copy them back.

---

### Post by Weta on 2008-05-03
Thanks Pumalite.  
Ok - I'll stick to three partitions. And, yes, of course I only need to copy my personal files into Hardy.  
I think that I have found the Firefox bookmarks (and cookies) files, and the Evolution contacts and mail directories, and have made a backup CD of them (and personal files).  
So, time now to install Hardy.  Should be OK, especially as I did a fresh install of 6.06 when it was released (I just couldn't recall exactly how I did it).  Thanks for your help.

---

### Post by Pumalite on 2008-05-03
You are welcome. Good luck.

---

### Post by Weta on 2008-05-04
Hi Pumalite!  Just in case you are wondering, the fresh install eventually went OK.  I managed to restore my documents, photos, bookmarks, contacts and emails.  Nice to be working with Hardy now.

---

### Post by Pumalite on 2008-05-04
Congrats!

---

