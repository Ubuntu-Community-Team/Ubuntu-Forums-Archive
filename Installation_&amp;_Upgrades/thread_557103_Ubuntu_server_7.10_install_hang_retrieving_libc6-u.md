---
title: "Ubuntu server 7.10 install hang retrieving libc6-udeb"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by jarthurs on 2007-09-22
I'm trying to install Ubuntu Server 7.10 on a Compaq ML350 (G1) but have come unstuck as it always freezes on 'retrieving libc6-udeb'.

I've tried multiple discs, different media, different drives (to write and install the disc from) checksums are OK but no joy...

I've read various solutions regarding adding cdrom-detect/cdrom_hdparm=-d1 but this doesn't work for my system. There seem to have been quite a few people with this problem but no working solutions posted anywhere.

Anyone shed some light on this one?

Regards,
Jason.

---

### Post by Pumalite on 2007-09-22
[http://lists.debian.org/debian-glibc/2004/05/msg00080.html](http://lists.debian.org/debian-glibc/2004/05/msg00080.html)

[http://lists.debian.org/debian-glibc/2004/05/msg00095.html](http://lists.debian.org/debian-glibc/2004/05/msg00095.html)

---

### Post by jarthurs on 2007-09-22
> **Pumalite said:**
> [http://lists.debian.org/debian-glibc/2004/05/msg00080.html](http://lists.debian.org/debian-glibc/2004/05/msg00080.html)

[http://lists.debian.org/debian-glibc/2004/05/msg00095.html](http://lists.debian.org/debian-glibc/2004/05/msg00095.html)

Interesting posts, no idea what relevance they have to the question though?

Regards,
Jason.

---

### Post by Pumalite on 2007-09-22
Sorry I couldn't help then.

---

### Post by gsmiller on 2007-09-26
I'm also trying to load 7.04 server on my ML350 and am having the same problem.  Has anyone come up with a solution to this problem?  I'm a noobie to Ubuntu but have dabbled with solaris, windows server and xenix in the past.  Any help would be appriciaed.

---

### Post by Pumalite on 2007-09-26
[https://bugs.launchpad.net/ubuntu/+source/kbd-chooser/+bug/96733](https://bugs.launchpad.net/ubuntu/+source/kbd-chooser/+bug/96733)

---

### Post by gsmiller on 2007-09-27
I came up with a solution that worked for me.  I downloaded Debian 40r1 i386 netinstall iso image.  It booted right up and loaded the server software along with the desktop without a hitch.  It did load PostgreSQL instaead of mySQL but that is a minor issue.  I've been messing with it most of the day today and seems to be pretty stable.  Hope it helps out.

---

### Post by nathan42100 on 2007-12-02
I also seem to be having this problem but on the server version. I have yet to try the boot parameters, but I have heard that you can install 6.061 and then possibly later upgrade to 7.10

---

### Post by KimTas on 2008-01-23
I am getting the same problem - have done the following:

1) Checked the MD5's match
2) Tried adding -d1 to the hdparm options doing an expert install
3) Tried the CD-ROM as Primary Master (rather than Slave)
4) Tried a different CD-ROM (a new Pioneer DVD combo drive)

Nothing seems to work! This seems like a common problem :(

---

### Post by KimTas on 2008-01-25
Got it working finally! 

This is what I did (sorry my description is probably not that accurate - I didn't take note of the exact things, but this should give you a basic idea). I'm not sure which of the following fixed it:

1) Change the CD-ROM to a different model (had already done this, but tried a third one)

2) Did an Expert Install and added _acpi=off apm=off_ to the end of the Expert Install string - I read this in another thread about Proliant servers.

3) During the Expert Install, in the spot that detects CD-ROM hardware, I disabled all the drivers except for the Linux IDE driver.

4) In the spot that asks for alternative drivers to load - I selected the option to download components from another source (http?). This seemed to add a few extra steps to the install process - such as detecting network hardware.

Then I proceeded through the rest of the steps - and am now up and running with Ubuntu 7.10! 

Cheers,
Kim :)

---

### Post by davidpodhola on 2008-01-29
I must say that I have fallen into the same problem. After trying almost everything I have found here or elsewhere on the Internet, I decided that the best would be to simply run the installation from the disk or through the network.
There have been an old Windows XP installation so I have simply followed the instructions [**here**]("http://ubuntuforums.org/showthread.php?t=28948") with changing the locations of the files for the latest version and voila - I am up and running. I am not sure if network installation from the custom CD would work.

---

### Post by escentrix on 2008-02-12
I had this problem with my server install and it almost made me want to give up. However, it appears to be (at least in my case) just a CDROM issue. I went through 3 drives before I got the system to install without freezing up on libc6 and giving me a validation error. It seems that Ubuntu Server is sorta flaky when it comes to dealing with some packages under certain CDROMs.

[What eventually fixed mine was digging out an old 12X drive and putting it on Master by itself on the IDE channel. Why some drives don't work is beyond me, but if you're having trouble I suggest testing any drives at your disposal.]

---

### Post by brunobelo on 2008-04-10
I was having the very same problem here, trying to install Ubuntu Server on a ML370. I tried 3 CD-ROM drives and burned 2 CDRs with no success. Then I found an old 4x Creative CD-ROM drive and I installed it on the machine. The installation worked flawlessly, amazingly flawlessly. If you're having problems with CD-ROM reading, try changing your drive, you won't regret.

---

