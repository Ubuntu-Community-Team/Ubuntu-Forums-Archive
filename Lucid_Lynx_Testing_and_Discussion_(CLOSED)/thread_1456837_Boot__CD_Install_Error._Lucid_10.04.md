---
title: "Boot  CD Install Error. Lucid 10.04"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cK` on 2010-04-17
Hello everyone,

I am trying to install lucid 10.04 on my computer but when i put in the bootable cd it starts to load the install and then i get this error.

" Unrecoverable error. WIll now open a desktop session so you can diagnose the problem or try running the install again".

Things i have done:

1. Set it to SlOW burning speed.
2. tried booting on on multiple machines, Same error on each one.
3. Tried re burning cd from different computers. i have tried cds and dvds (Same error).

 

Is there something wrong with the iso images on the official ubuntu download page, i have burned the image on several different cds and several different downloads?

Note: i have been able to upgrade from 9.10 to 10.04 but i do not want an upgrade i want a clean install of only 10.04 (IMO its cleaner).

i like the look of lucid and would love to use it!

Any help would be awesome. It seems to me that its the iso image from the website that is corrupt but i am probably wrong.

---

### Post by howefield on 2010-04-17
> **cK` said:**
> It seems to me that its the iso image from the website that is corrupt but i am probably wrong.

I'll put money on you being wrong on that score.

Have you checked the md5sum against your downloaded iso and also the burned CD ?

---

### Post by cK` on 2010-04-17
No i have not, i do not know how to either.

I found the checksum files but its just a bunch of gibberish to me.

What is this going to do? Tell me if the cd burned correctly?

I will attempt to do this and get back to you.


Thanks for responding.

---

### Post by cheetaux on 2010-04-17
The link below contains instructions on how to verify your download with md5sum:

[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by cK` on 2010-04-17
I checked the md5sum and they are both the same.

I then continued to install it on a third machine and it worked!

The computer it worked on was dedicated entirely to windows.

The computer it did not work on had Hard drive space reserved for another OS (unallocated space). Could this be the reason it is not working?

This has got me confused because i know 10.04 will run on the machine i am trying to install it onto. IT just wont boot up the disk!

---

### Post by overdrank on 2010-04-17
Moved to Lucid Lynx Testing and Discussion :)

---

### Post by ronparent on 2010-04-17
I haven't yet seen that particular problem. If you can, try burning to a dvd. Hypothesis is that the drive, if it is a cd/dvd drive, can't read the cd right.

Also try using <F6> at the live cd menu screen to turn off some of the kernel boot parameters. Based on the symptoms this doesn't seem the most likely cause. But just maybe nomodeset would allow the x-server to start.
That's all I can thik of right now.

---

### Post by jkxx on 2010-04-17
I may have seen it and agree with the above post. Certain CD drives will fail to install Ubuntu (and usually BSD or other free OS) although they install windows OK.

Maybe hook up a second CD just to do the install from? Unfortunately I can't get the manufacturer info for a drive I've seen do the above to compare.

---

### Post by cK` on 2010-04-18
I have tryed a DVD and same problem. 
 
 Ihave got it to succsessfully boot up on two computers but not the one i want it to work on.
 
I think it may have somthing to do with the CDROM drive.
 
But i can install 9.10 no problem.
 
Is there an alternative to booting from a CD? (not wubi)

---

### Post by cariboo on 2010-04-18
Try the alternate install iso from [here]("http://releases.ubuntu.com/lucid/"), it's text based, but it should work for you.

---

### Post by cK` on 2010-04-18
> **cariboo907 said:**
> Try the alternate install iso from [here]("http://releases.ubuntu.com/lucid/"), it's text based, but it should work for you.


Worked perfectly.

Thanks!!

Love the new look.

---

### Post by Orographic on 2010-04-26
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1461157](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1461157)

Look at post 2, it solved it for me and saved a lot of time.

---

### Post by Ericwt on 2010-04-26
I have this problem on a toshiba satallite A45, Will not install just a blank screen. The dvd runs long enough to show ubuntu screen. The dvd drive stops running something to do with 10.04. All other versions load ok. I burned a dvd and it loads fine on my dell desktop ck some is ok.

---

