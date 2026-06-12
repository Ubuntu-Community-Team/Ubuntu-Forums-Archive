---
title: "Linux Partitions"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by DamienFox on 2008-08-02
Does anyone know how i can remove all partitions of linux? I need to re-install vista due to other members of the family be to used to windows. Thanks.

---

### Post by sstvinc2 on 2008-08-02
I'd say boot the live cd and run gparted off of it.  Alternatively, there's a gparted live cd out there on the interwebs, although I haven't tried it and can't attest to its quality.

I'd think the Vista installer would have partition management too, but then MS has surprised me before.

---

### Post by DamienFox on 2008-08-02
I was told to remove all partitions so that windows its own in.

---

### Post by Sef on 2008-08-02
Just tell Vista to use the whole disk.  That will cause Vista to write over everything.

> I'd say boot the live cd and run gparted off of it. Alternatively, there's a gparted live cd out there on the interwebs, although I haven't tried it and can't attest to its quality.


GParted is an excellent partitioner.

---

### Post by DamienFox on 2008-08-02
Sorry, i hate to be a bother. But could somebody just explain briefly how gparted works and how i can use to help?

---

### Post by SunnyRabbiera on 2008-08-02
well Vista does have its own partitioner, you can use that if you are unsure.
But do yourself a big favor, buy a computer for yourself so you dont have to suffer, its what I did :D

---

### Post by sstvinc2 on 2008-08-02
Sure.  Just run ```
sudo gparted
``` and then you can right-click on partitions and delete them.  Once you've deleted all of them, you can reformat them into NTFS for Vista.

But I'd also recomment using the Vista partitioner if you're more comfortable with it.

---

### Post by DamienFox on 2008-08-02
My friend installed ubuntu for me. But i have the Windows Vista home Premium disc. I just want to install that :(

---

### Post by sstvinc2 on 2008-08-02
Then just instert your Vista disk, boot your PC from that disk, and let Vista take care of the rest.  Windows' partition editors tend to be very straightforward.

---

### Post by DamienFox on 2008-08-02
It's asking for the password and i don't know it :confused:

---

### Post by DamienFox on 2008-08-02
> **sstvinc2 said:**
> Then just instert your Vista disk, boot your PC from that disk, and let Vista take care of the rest.  Windows' partition editors tend to be very straightforward.

When i do that, it says 'To use the pass key you have entered, please install from your current version of windows'.

---

### Post by sstvinc2 on 2008-08-02
gparted is you mean?  Are you running off the live CD?  If so, I think gparted is also in the System menu at the top of the screen.  You might not need to say "sudo" on the command line, which would keep from asking for a password.

---

### Post by sstvinc2 on 2008-08-02
> **DamienFox said:**
> When i do that, it says 'To use the pass key you have entered, please install from your current version of windows'.

Wow, I have no idea what that's about.  Vista is the first Windows installer that I *haven't* used since Win95... Anyone else know what this Vista business is about?  If it were me, I'd stick with gparted, but I understand that you're not all that familiar with Ubuntu, so I can see why you wouldn't want to.

---

### Post by DamienFox on 2008-08-02
Is there anyway somebody could remote screen my computer? Im really bad at this kind of stuff

---

### Post by cbr_king on 2008-08-02
> **DamienFox said:**
> When i do that, it says 'To use the pass key you have entered, please install from your current version of windows'.

It looks like that you use an upgrade key or an windows Vista upgrade version media that needs a previous windows version to install Vista. If you have not a previous Windows, take a look at this page:

[http://www.winsupersite.com/showcase/winvista_upgrade_clean.asp](http://www.winsupersite.com/showcase/winvista_upgrade_clean.asp)

---

