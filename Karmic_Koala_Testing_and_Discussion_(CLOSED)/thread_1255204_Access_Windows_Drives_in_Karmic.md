---
title: "Access Windows Drives in Karmic"
date: 2009-09-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by A.R.R on 2009-09-01
This is my second problem of the day! :
When I had jaunty I could mount my windows partitions (dual-boot) by entering my password when asked for and could therefore access windows files. 
When I upgraded to Karmic aplha 4, It denied me access (it did not ask for password or anything). I went to authentications and enabled administrative privileges to mount drives and yet it did not work. 
What should I do?

---

### Post by dearingj on 2009-09-01
I'm having a similar problem with Karmic. Mine asks me for my password, despite the fact that in 'authorizations' I set it to always allow that without admin authentication.

---

### Post by muteXe on 2009-09-01
So you're both having problems with software that hasn't officially been released yet?
Funny that.....

---

### Post by dearingj on 2009-09-01
> **muteXe said:**
> So you're both having problems with software that hasn't officially been released yet?
Funny that.....

That's why we're running it, so we can find these problems and try to get them fixed :)

---

### Post by muteXe on 2009-09-01
Yea I guess, but... well I dont know. I just think stuff like that is more bug reporting than asking for forum help.

(sorry i'm in a bit of a bad mood :()

---

### Post by dearingj on 2009-09-01
> **muteXe said:**
> Yea I guess, but... well I dont know. I just think stuff like that is more bug reporting than asking for forum help.

(sorry i'm in a bit of a bad mood :()

It is. That's why the bug I'm experiencing has been reported :)
[https://bugs.launchpad.net/bugs/409216](https://bugs.launchpad.net/bugs/409216)

---

### Post by muteXe on 2009-09-01
Excellent :)

---

### Post by ranch hand on 2009-09-01
I don't have any MS on my box so I do not have this problem.  I hope you can get it squared away soon though.

I do depend on this function when dealing with the Dreaded Mother in Laws computer and, to me, it is one of the greatest things about Ubuntu.  The ease of access to MS files is great.  I would be worried about people with Cds or thumb drives if I were running a business that used MS though.

---

### Post by gwenn on 2009-09-01
Was windows shut down properly?
Try sudo nautilus or if not luck you must make a mount point.Take a look and see what is the name of your winblows partition, then 
mkdir win
sudo mount /dev/sda"your hd" win
See man mount for that.Hope that help you.
I have vista inside my machine just for testing (I'm using it as a storage partition) and I do have ext4 and x86_64

---

### Post by jwssr on 2009-09-01
I think your problem is that ntfs will not work ext4...it did work with ext3.  lots in info about this out there....google is your friend....

---

### Post by jwssr on 2009-09-01
I think your problem is that ntfs will not work with ext4...it did work with ext3. lots in info about this out there....google is your friend....

---

### Post by VMC on 2009-09-01
I have Windows installed and another NTFS partition, yet I don't have any problem with accessing NTFS partitions. My karmic is on ext4.

As someone mentioned, not shutting down Windows properly may be the culprit.

From Windows , then reboot:
```
chkdsk c:/f
```

---

### Post by bacardiandwatermelon on 2009-09-01
I initially got around the Karmic automounting drive issue by using pysdm. Using the assistant I set it so any user could mount and unmount the drive. Haven't had any issues since, maybe it is worth a shot?

---

### Post by A.R.R on 2009-09-02
I just wanted to know whether this is actually a bug (because I could do it with 9.04 pretty easily) or is it because karmic is yet under development or is it because of some wrong setting.

---

### Post by chrismine on 2009-09-02
> **VMC said:**
> I have Windows inatlled and another NTFS partition, yet I don't have any problem with accessing NTFS partitions. My karmic is on ext4.

As someone mentioned, not shutting down Windows properly may be the culprit.

From Windows , then reboot:
```
chkdsk c:/f
```

I have found when Windows was improperly dismounted this can happen but it is fixed by running a checkdisk as mentioned above.
Another thing I have found is that when the Windows NTFS drive is "unclean" is that your Vista entry will not show up in the grub2 menu - also fixed by checkdisk and then os-prober to make it appear again.

Hope it help.

---

### Post by trulan on 2009-09-02
I think it's connected with the 'authenticate drives' bug that has been hanging around for a while.  If I authenticate that first window that pops up, all my drives get mounted, including my windows drive, and I can use it just fine.  If I deny that first authentication, it will never ask again, and there is no way I have found to access it.

And since giving alpha software free reign of my Windows drive is a bit scary, I don't do that more often than necessary.

---

### Post by trulan on 2009-09-02
...and since the last update, this issue is gone.  It now works as it should.

---

### Post by jwssr on 2009-09-02
I was incomplete in my above post....we can mount and see ntfs files from linux....but can you also read write linux files from win....using  ext2fs?

I cant.  

this ubuntu thread talks about it.

[http://ubuntuforums.org/showthread.php?t=1138245](http://ubuntuforums.org/showthread.php?t=1138245)

---

### Post by trulan on 2009-09-03
The OP mentioned being unable to mount an NTFS partition in Karmic (booting in Karmic and accessing you Windows drive from there), which was an issue for some, including myself, but this issue has been solved.  I never had any success mounting an ext3 file system in Windows, let alone an ext4 file system like Karmic uses.

---

