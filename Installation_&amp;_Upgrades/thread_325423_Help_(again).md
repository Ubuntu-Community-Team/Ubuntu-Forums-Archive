---
title: "Help (again?)"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by janaia on 2006-12-25
I can't seem to find my previous post, so here goes again.

I am trying to install ubuntu (edgy eft) as a second OS to try it out.  I'm running Windows XP on a Dell PC.  The main menu will appear when I boot up from the CD, but when I choose Start/Install Ubuntu, I get a "Loading" message and then nothing.  I tried to partition my hard drive using GParted Live CD.  I partitioned my primary boot drive (C:), since the previous time I tried it, I used a different partition.  I formatted two additional partitions after shrinking the NTFS partition:  a 4-gig partition using ext3 and a 1.5-gig partition, linux-swap.  I checked the download with MD5sum and I *think* it is error-free.  When I booted up with the ubuntu cd, I got the same "loading" message, followed by nothing.  I can't imagine what I'm doing wrong, except perhaps the ext3 partition needs to be bootable?  (makes no sense.)  If anyone is able to help me this, I'd greatly appreciate it.  

I'm planning on reformatting my entire hard drive/zapping my current Windows installation to "clean house" anyway.  If I proceed with that, is it necessary to load Windows first before installing Ubuntu if I want a dual-boot capability?

Thanks in advance for any and all help!

---

### Post by DaveBorealis on 2006-12-25
> **janaia said:**
> The main menu will appear when I boot up from the CD, but when I choose Start/Install Ubuntu, I get a "Loading" message and then nothing.

This could be a memory problem.  How much does the machine have?  If it's 256 MB RAM or less, then you might have to go with Xubuntu or even something a little more customized.  (I just loaded Xubuntu on a PII 450 MHz with 128 MB RAM and it went well  Works fine, also.)

HTH,
Dave

---

### Post by RRS on 2006-12-25
If the MD5sum checked  ok then perhaps a problem occured when you wrote the disc. What speed did you use? The slower the better, I use 4x though many people seem to do ok with 8x.

Backing up your data and doing a clean reinstallation of windows before before partitioning and installing Ubuntu is a good idea.

As for your hardware I wouldn't expect many problems though if you have less then 512 ram the desktop (live) cd won't be very happy but the alternate cd will still install ok.

4g is just barely enough for installation, 6 to 8 would be better if you have the space, and swap only needs to be 1 to 1.5 times your ram. The more ram, the lower the ratio.

You might want to check out [Aysiu's site]("http://www.psychocats.net/ubuntu/index.php"), it has an excellent installation guide and a lot of good tuorials for post installation help too.

Hope this helps get you started :)

---

### Post by janaia on 2006-12-25
I've got 512K RAM and I used 4x to write the CD.  I'm really at a loss here.  If I wipe out Windows, I'm assuming I need to reinstall it first, then?  Thanks for the help!

---

### Post by bulldog on 2006-12-25
Don't wipe windows yet,if the cd won't boot it has nothing to do with you hard disk.

---

### Post by janaia on 2006-12-25
If I'm not to zap Windoze, whatever can I do?

---

### Post by bulldog on 2006-12-25
Install Ubuntu?
If your windows is a mess you can reinstall of course,what I meant was,don't throw away a working windows,while you haven't a working live cd.

Check the cd  again on errors or burn a new one on low speed.
Something is wrong if you can't boot from the cd.

---

### Post by j.miller565 on 2006-12-25
Try the alternate CD. The default CD never worked for me even though I have 512MB RAM. On the alternate one, it should ask you whether you want to wipe the whole disk or keep the part you have used. It should split the hardrive into two equal partitions. I have a 80GB hard drive, it spilt 40 Gigs with Windows and another 40 Gigs with Ubuntu. So I suggest to try installing Ubuntu with the alternate CD

---

### Post by bulldog on 2006-12-25
Maybe this can help you out,just saw it in another post,

[http://instlux.sourceforge.net/](http://instlux.sourceforge.net/)

---

### Post by janaia on 2006-12-25
Thanks, Bulldog!  I've just downloaded it and will let you all know how well it works!  On another note, it appears it will install Ubuntu 5. something so an upgrade will have to follow.  Uh ohhhhh :)

---

### Post by janaia on 2006-12-25
Guess it's just not my day.  Downloaded the executable, supposedly installed it and nada.  So much for Ubuntu this year, I guess.  If I order the actual CDs, is it possible to load ubuntu first and then install windows (anything's *possible*, I guess...).

Thanks all for your thoughtful help.  Seems you're a terrific community I someday hope to join.

---

### Post by bulldog on 2006-12-26
> **janaia said:**
> Thanks, Bulldog!  I've just downloaded it and will let you all know how well it works!  On another note, it appears it will install Ubuntu 5. something so an upgrade will have to follow.  Uh ohhhhh :)

If you scroll down the page you'll see version5 with the Dapper Drake version!!

---

