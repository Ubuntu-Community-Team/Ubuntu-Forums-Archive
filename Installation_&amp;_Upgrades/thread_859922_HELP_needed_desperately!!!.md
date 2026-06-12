---
title: "HELP needed desperately!!!"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by sp23 on 2008-07-15
Im installing Ubuntu 8.04.1 on my other laptop.

It started up, I chose Install Ubuntu. A error came up but then started installing (Black page with Orange bar going back and forth)

It finished and then came up with a missing file after it was finished.

But now it shows a orange background with a crane looking object made of curly lines.

My CD drive is still reading constantly, but my screen isnt doing anything.

---

### Post by cyclobs on 2008-07-15
so what is the problem?

i don't quite understand what you are saying

---

### Post by Drizzel on 2008-07-15
Hi, I just experienced similar problems when installing Ubuntu. It locked up on me a few times. Turn off your laptop and Just install Ubuntu in text mode. After I did that it was a very smooth install. Good luck :)

---

### Post by OutOfReach on 2008-07-15
You might have burned the disc wrong. Boot back into the LiveCD and select the option "Check CD for Defects". And see what it outputs after its done testing the CD.

Also did you do [this]("https://help.ubuntu.com/community/HowToMD5SUM") before burning the disc?

Not sure if this is the problem or not.

---

### Post by sp23 on 2008-07-15
> **cyclobs said:**
> so what is the problem?

i don't quite understand what you are saying


Well, is it doing anything? I mean, Is it installing becuase it has been this way for like 10 minutes. I have no idea if its installing...

---

### Post by cariboo on 2008-07-15
If you've got less than 348MB ram you may have to wait a while until it's done. I installed Hardy on an old Apple G3 with only 256MB ram annd it took about half an hour before the desktop was fully loaded. What are you computer specifications?

Jim

---

### Post by lisati on 2008-07-15
> **sp23 said:**
> Well, is it doing anything? I mean, Is it installing becuase it has been this way for like 10 minutes. I have no idea if its installing...
Checking your CD for defects has already been suggested. Another possibility is that you don't have enough memory on your computer (or some such problem).

---

### Post by sp23 on 2008-07-15
> **cariboo907 said:**
> If you've got less than 348MB ram you may have to wait a while until it's done. I installed Hardy on an old Apple G3 with only 256MB ram annd it took about half an hour before the desktop was fully loaded. What are you computer specifications?

Jim

Oh really? Mine has 256 (subtract 32MB for Graphics)

SO I guess it was installing :|

Is it bad that I restarted it?

EDIT: Right before it goes to the background, it shows a error for incorrect firmware.
And the integrity is fine.

---

### Post by sp23 on 2008-07-15
Ok, Ive posted this twice before but no one is responding.

First of all I have 256MB of RAM (subract 32MB for graphics).

Its finished installing and is now at a orange screen with a formation of some kind of bird made of lines.

Its been this way for about 40 minutes. My optical drive isnt spinning and my hard drive isnt doing anything, and the cursor doesnt move.

I had 2 errors, one was right after the Linux loader started up (right after I picked "Install Ubuntu".

The second was after it finished the black screenwith the orange bar moving across with the Ubuntu logo.

Right after that, the screen went fully black and displayed an error saying something about incorrect firmware and gave me a URL to a drivers place in the Ubuntu website.

---

### Post by lisati on 2008-07-15
Please be patient! Your previous request for help has been seen. It's not that we don't want to help or anything like that!

Please check back at [http://ubuntuforums.org/showthread.php?t=859922](http://ubuntuforums.org/showthread.php?t=859922) in a few minutes.

---

### Post by lisati on 2008-07-15
> **Drizzel said:**
> Hi, I just experienced similar problems when installing Ubuntu. It locked up on me a few times. Turn off your laptop and Just install Ubuntu in text mode. After I did that it was a very smooth install. Good luck :)

> **sp23 said:**
> Oh really? Mine has 256 (subtract 32MB for Graphics)

SO I guess it was installing :|

Is it bad that I restarted it?

EDIT: Right before it goes to the background, it shows a error for incorrect firmware.
And the integrity is fine.

I'm not sure about the "incorrect firmware" message, but 256Mb might be pushing it for installation using a "Live" CD. My laptop has 256Mb, and I experienced similar difficulties with nothing much happening for a VERY long time.

As Drizzel suggeted you might have to install in text mode. You can do that by downloading an "alternate" installation disk. (This is what I ended up doing the first time I successfully installed  Ubuntu)

---

### Post by sp23 on 2008-07-15
> **lisati said:**
> Please be patient! Your previous request for help has been seen. It's not that we don't want to help or anything like that!

Please check back at [http://ubuntuforums.org/showthread.php?t=859922](http://ubuntuforums.org/showthread.php?t=859922) in a few minutes.

Well that one hasnt been replied to in 50 minutes...

I know that the CD is fine, but whats the problem with this firmware thing?

And I partitioned my hard drive so there 2 partitions. But does it autmatically notice that? The other partition has windows XP. I dont know if it still works.

---

### Post by sp23 on 2008-07-15
> **lisati said:**
> I'm not sure about the "incorrect firmware" message, but 256Mb might be pushing it for installation using a "Live" CD. My laptop has 256Mb, and I experienced similar difficulties with nothing much happening for a VERY long time.

As Drizzel suggeted you might have to install in text mode. You can do that by downloading an "alternate" installation disk. (This is what I ended up doing the first time I successfully installed  Ubuntu)

Where can I get a alternate download at?

---

### Post by nickdbliss on 2008-07-15
> **sp23 said:**
> Where can I get a alternate download at?

[http://astromirror.uchicago.edu/ubuntu-releases/8.04/](http://astromirror.uchicago.edu/ubuntu-releases/8.04/)

You will see ubuntu-8.04.1-alternate-i386.iso
or u can download a torrent file.

---

### Post by housam on 2008-07-15
Or you can download/install xubuntu. it is more suitable for your ram size. 
Also after downloading the iso file ,burn it at slow speed as 2x or 4x . this will eleminate the possibility of any disc defects.

---

### Post by Partyboi2 on 2008-07-15
> **sp23 said:**
> Well that one hasnt been replied to in 50 minutes...

I know that the CD is fine, but whats the problem with this firmware thing?

And I partitioned my hard drive so there 2 partitions. But does it autmatically notice that? The other partition has windows XP. I dont know if it still works.
It should notice your partitions including your windows partition(s)

---

### Post by Sef on 2008-07-15
> Or you can download/install xubuntu. it is more suitable for your ram size.
Also after downloading the iso file ,burn it at slow speed as 2x or 4x . this will eleminate the possibility of any disc defects.


Agreed. [Xubuntu]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/8.04/release/") download site, (includes live and alternate cds) and specs:

> Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.

---

### Post by lisati on 2008-07-15
Sorry for the delay responding. I think (and this is just my opinion) that Xubuntu might suit your computer's specs better than Ubuntu. For more information, have a look here: [http://www.ubuntu.com/products/whatisubuntu/xubuntu](http://www.ubuntu.com/products/whatisubuntu/xubuntu)

Edit: Just spotted Sef's comments about Xubuntu

---

