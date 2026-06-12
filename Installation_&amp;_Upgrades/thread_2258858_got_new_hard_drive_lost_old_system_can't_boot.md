---
title: "got new hard drive lost old system can't boot"
date: 2014-12-31
forum: Installation &amp; Upgrades
---

### Post by bryan37 on 2014-12-31
I was running ubuntu 14.04 lts and my hard drive died. I got a new hard drive but when I go to boot up with the ubuntu-14.04.1-desktop-amd64.iso dvd nothing happens. How do I get the new ubuntu to load on to my machine and start working?

---

### Post by Bucky Ball on 2014-12-31
*Thread moved to **Installation & Upgrades**.*

Welcome. How did you burn the disk image to the DVD? Are you sure you are booting from the DVD? You need to set that in the BIOS.

---

### Post by bryan37 on 2015-01-02
Thanks for the help. I don't understand what you mean by how did I burn the disk image to DVD. Is there more than one way? Which way should I use?

---

### Post by lisati on 2015-01-03
> **bryan37 said:**
> Thanks for the help. I don't understand what you mean by how did I burn the disk image to DVD. Is there more than one way? Which way should I use?

What did you do with the ISO file you downloaded when it had finished downloading? There *are* different ways of preparing it for use.

---

### Post by Bucky Ball on 2015-01-03
You burnt a disk image to DVD and didn't simply drag and drop the ISO file or you've installed 14.04 from this disk previously?

---

### Post by bryan37 on 2015-01-03
It is a completely blank hard drive without anything on it. I have never installed a system from this DVD before.

And thank you again for the help!  :-)

---

### Post by Bucky Ball on 2015-01-03
Then back to the first question: How did you burn the ISO image to the DVD? What software did you use to do it? UNetbootin? Universal USB Creator? Something else?

---

### Post by bryan37 on 2015-01-03
If my memory is correct, I used k3b to burn it.

---

### Post by lisati on 2015-01-03
I'm looking at an [old turorial]("http://www.ghacks.net/2009/01/11/burn-cd-and-dvd-iso-images-with-k3b/") for burning imgaes with K3B at the moment. Do you remember using an option similar to the one "Burn DVD ISO image"?

---

### Post by bryan37 on 2015-01-03
No, I don 't recall the details of how I burnt the file. Maybe I should start over again? What should I use to burn a new disk and how should I burn it?

---

### Post by oldos2er on 2015-01-04
> **bryan37 said:**
> I was running ubuntu 14.04 lts and my hard drive died. I got a new hard drive but when I go to boot up with the ubuntu-14.04.1-desktop-amd64.iso dvd nothing happens. How do I get the new ubuntu to load on to my machine and start working?

How old is your computer, and what are your hardware specs? Computers beyond a certain may need you to make a change in the BIOS before it will boot from DVD (assuming it was burnt correctly).

---

### Post by oldos2er on 2015-01-04
> **bryan37 said:**
> I was running ubuntu 14.04 lts and my hard drive died. I got a new hard drive but when I go to boot up with the ubuntu-14.04.1-desktop-amd64.iso dvd nothing happens. How do I get the new ubuntu to load on to my machine and start working?

How old is your computer, and what are your hardware specs? Computers beyond a certain age may need you to make a change in the BIOS before it will boot from DVD (assuming it was burnt correctly).

---

### Post by MAFoElffen on 2015-01-04
What members are saying is that an ISO image is an archive file of a disk image. If you copied that file to an optical disk (in your case DVD), then it would not create an optical disk bootable disk image. There is software, that specifically takes an ISO image and creates a bootable optical disk (makes that optical disk bootable.)

Once that is accomplished, then you ensure that your BIOS is set to boot from the optical drive before your HDD (in the boot order). Also, while in BIOS Settings, ensure that the controller sees that HDD correctly.

Boot from the  DVD into the  Try LiveCD, to ensure that the LIVECD Live image works on your PC and has no challenges to sort out.

Once working, choose Install... once you get to the partitioner, choose an option... It should see your disk and recognise that it doesn't have a partition table and add one. If not, then you go back and add one manually...

---

### Post by bryan37 on 2015-01-05
I burnt a new dvd from the same old iso file and this time it worked first try. Thanks everyone for all the help!

---

### Post by Bucky Ball on 2015-01-05
Excellent news! Please mark thread as 'solved' to help future travelers by following the second link in my signature. Don't hesitate to post a new thread with any further questions. 

Good luck and enjoy. ;)

---

