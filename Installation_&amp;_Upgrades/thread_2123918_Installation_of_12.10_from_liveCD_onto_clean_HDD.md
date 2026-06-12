---
title: "Installation of 12.10 from liveCD onto clean HDD"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by Ionedric on 2013-03-09
Hello to all-  This is my first post, and in hopes of avoiding public humiliation, have spent two days researching similar problems with no success.

I am attempting to install 12.10 from a livecd download.  The computer is an HP a320n which had been running Win XP until a HDD crash. I pulled and re-formatted an old drive which had Win 95 installed. When the 12.10 CD is installed, the drive activity light goes on, the drive does a track search, and after about 30 sec of searching, gives an error message saying that the CD is not bootable and that I should install a bootable source and try again.

The 12.10 CD is a good download since I can install it on another computer running Win XP with no problem. Everything works as expected.
The target computer is good since it will recognise a bootable (old Win ) CD, and would proceed with installation if allowed.

Computer - HP a320n
Proc - Pentium 4 2.8 Ghz single core.
Mem - 1.5 Gb

The main chunk of information I'm looking for is whether this should work. Is the download expected to work on a non-Win machine or does it look for a previous installation?

Hoping for a stupidly simple answer....

---

### Post by grahammechanical on 2013-03-09
We call it a live session. When the machine boots it will look for an operating system. The machine does not care what the operating system is. What the machine needs is direction on where to look first for an OS and then second and then third. You seem to have set this up correctly. Have you considered the possibility that the CD drive is faulty? Or that the lens in it needs cleaning?

You have tested the Ubuntu image on the CD. It works in another computer but not on this computer. Why? Because the image on the CD is faulty? No. Because the boot priority is set incorrectly? No. What about the CD drive itself? I have installed Ubuntu on a blank hard disk. The live session/installer is designed to detect other operating system on the target hard disk but it can still install Ubuntu even if the hard disk is blank and unformatted. Take my word for it. I have done it. 

Regards.

---

### Post by omid2s on 2013-03-09
[FONT=arial black]hello dear [**[COLOR=#000000]Ionedric[/COLOR]**]("http://ubuntuforums.org/member.php?u=1797286")
you have check some problem.
first: your HDD  havent  problem.with a program / such as HDD life.
you had make free space one of your drive for install ubuntu12.10.
live cd havent problem if you download it from ubuntu site.
if your speed of internet is low //the iso file maybe have problem[/FONT]

---

### Post by ibjsb4 on 2013-03-09
You do seem to have an odd problem.

One thing I notice is you tested your drive with a CD and it worked fine.  But 12.10 comes on a DVD.  So me wonders if this is a DVD problem with your drive.

A workaround to this would be to install 12.04, it will fit on a CD.  12.04 is an LTS (long term support) and good till 2017.

Also I notice that your processor (AMD Athlon XP 2800+) is a 32bit processor.  You did download the 32bit version and not the 64, right?

---

### Post by Ionedric on 2013-03-09
Firstly, thanks to all for the quick response!  I do have a DVD with 12.10 rather than a CD, sorry. I believe I downloaded the 32bit version, I may download it again just to check for any problems.

There seems to be nothing wrong with the CD drive as it works fine to read a Win disk.  I don't have anything bootable on DVD so can't swear that the drive would boot, but it was working fine earlier.

As a further test, I downloaded lubuntu and created a CD which also fails to boot in this machine. I can change the order of device selection in the BIOS and still get the same results with all devices showing activity before the "boot failure" message appears.

Any more ideas would be welcomed, I'll go back over the download process just to be sure.   Regards,

---

### Post by ibjsb4 on 2013-03-09
Yep, think I found it.  Or should I say not found it :)  I have not been able to confirm anywhere that your processor can run a PAE kernel.  All ubuntu distros these days run the PAE kernel.  So I am thinking that the other computer used for testing your DVD/CD **is** PAE capable.  If you want to confirm this you could try to install "Ubuntu Lucid 10.04".  That version uses a non-pae kernel.

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

If that works, you should be able to upgrade to 12.04.  But I have not tried that so really not sure if it will work.  Need someone else to confirm that.

---

### Post by fiodev on 2013-03-09
use ubuntu minimal and you can choose a non-pae kernel and lots of other cool things

---

### Post by ibjsb4 on 2013-03-09
@fiodev

How do you get the non-pae install on the mini iso?

---

### Post by Ionedric on 2013-03-09
OK, lots of stuff to try!  Have found a stack of old Win XP recovery CDs and have tested the machine by restoring XP (both the CD & DVD drives work fine.  When that's done I'll see if 12.10 will install.  Meanwhile I'll look into the PAE related aspect.  Tried to download 12.04 but never get beyond 128Mb before the download terminates with no explanation.  Appreciate all the help......

---

### Post by Ionedric on 2013-03-09
It seems that all Pentium processors after II should support PAE so that seems to be a non-issue.  After spending 3 hours inserting CDs to do a system restore, the final result is that the machine will not boot from the HDD. Something really strange here. May try to find another HDD to try although the fact that the machine sees the liveCD as a non-bootable source is the real mystery. May have to give up for now,can only stand so much fun.......

---

### Post by ibjsb4 on 2013-03-09
Pentium?  I thought its AMD Athlon XP 2800+ :confused:

---

### Post by Ionedric on 2013-03-10
> **ibjsb4 said:**
> Pentium? I thought its AMD Athlon XP 2800+ :confused:

Processor is a Pentium 4 at 2.8 Ghz, my newer a1600n has an Athlon 64x2 but these older HPs were not all AMD.

Final status of the problem: Seems it can't be solved easily.  Tried another HDD to see if the system would recognise it and it does. Both the CD and DVD drives are working fine since they each attempt to read the source disk when it is inserted.  With either Ubuntu 12.10 on DVD or Lubuntu on CD, the error message is "invalid system disk" followed by "insert bootable disk and hit any key".  This shows me that the BIOS boot order config is set properly.

Seems a shame that this perfectly fine older computer cannot be set up as a Ubuntu workstation.  I will try either Red Hat or opensuse or something else to see if there is any difference.  Guess I can always look for an older version of Win and go back to that....

Thanks to all who offered help!  If I find a solution I'll post it.  Best Regards,

---

### Post by darkod on 2013-03-10
If I understand it right, you can't even get the 12.10 DVD to boot so that you can try to install. If you have installed it, but you get message about invalid system disk, it might be that you have no boot flag on any og the partitions. Ubuntu (Linux) doesn't use the boot flag so when you have ubuntu only system it often doesn't get set. But many boards expect to see a boot flag on the hdd since they are designed with windows in mind. You can easily sort this from live mode by opening Gparted and setting a boot flag on any primary partition, for example if your root partition is primary.

As for not booting from any ubuntu cd/dvd, first of all try downloading ISO files with torrent, it checks for corruption during download.
Second, burn them at very low speed. For cd at max 8x or 10x. For dvd 2x or 4x. Never burn an OS install cd at the max speed of 56x etc. It can produce burn errors that won't be reported but prevent it to install the OS correctly.

If none of that works you can consider trying to boot with usb stick, if the machine supports it.

---

### Post by Ionedric on 2013-03-10
Darko-  That's what is so frustrating, the DVD appears to have been downloaded just fine since I can run the demo on my other machine. I cannot get the older one to see the downloaded disk as a bootable source, in fact nothing I have downloaded will boot. Is it possible that the older DVD drive cannot read the source disk?  This BIOS does not give the option of selecting a usb port as a boot option. I went back and created another DVD at the slowest speeds, etc., but can't really see the point since the first one seems fine. I'd like to upgrade the BIOS but can't seem to think of a way to do it without an operating system running.  I guess this one may finally push me over the edge.....

---

### Post by darkod on 2013-03-10
If it has a floppy drive, you should be able to update the BIOS with a floppy. The download section of the manufacturer might even include floppy images. Earlier I would always update a BIOS from a system floppy, never from inside windows. But even that might not help you.

I don't know if the machine can recognize external usb dvd drive. If you don't have one maybe you can borrow from a friend and give that a shot.

---

### Post by deadflowr on 2013-03-10
If the disk runs fine on a separate machine, then I venture to guess the issue is with the DVD drive itself.
It's an unfortunate part of computers that mechanical parts fail.
You could try switching in a newer or different DVD drive, if possible.

---

### Post by Ionedric on 2013-03-13
Just to tie the ribbons on this one, I still have not found the magic solution as to why the liveCD(DVD) is not seen as a bootable disk.  I performed a perfectly normal installation on a Compaq Presario V5000 laptop using the same liveCD source, so it's not a corrupted disk.  I'll eventually swap out some of the hardware and possibly the BIOS later.

Many thanks to those who gave this their attention.  Bests Regards.

---

### Post by Ionedric on 2013-03-18
Thought I'd post a final time on this issue since I've found an answer, although not the one I was looking for.

As reported previously, my live DVD was used to do a normal install on a laptop. This satisfied me that the disk was good.  I found an old WIN 98 disk and did a Windows installation on the target desktop machine, which satisfied me that the DVD drive worked fine (although there were the normal memory and processor issues with this newer machine).  Tried both Ubuntu and Lubuntu again with no success.  I downloaded a copy of Puppy Linux and did a normal installation. Everything looks good and the DVD drive is working fine. I'll continue to play with the system and will try to do a 12.10 installation again later.


Still have not run into anything that would explain the problem, and have not seen a similar complaint from anyone.  I see no place to mark this as "solved", but may report other happenings if they are interesting enough!  Regards,

---

### Post by mörgæs on 2013-03-19
The 'solved' switch is broken, but I shall set it manually. Thanks for reporting back.

---

### Post by Ionedric on 2013-03-24
Hello again. Even though this has been marked "solved" due to running out of options and getting PuppyLinux to do a normal installation and run fine, I thought I'd post the latest situation just for archival purposes.

Tried different HDD, no change.
Downloaded 12.04 and tried installing from both USB drive and DVD, both fail in the same way.
Downloaded Gparted and tried to launch, no results.
Put Win 98 in same DVD drive, did normal installation.
Can snoop around on the Ubuntu DVD and see all the files using DOS commands but nothing will run.
Took the DVD of 12.10 and installed on a Compaq V5000 notebook with no problems.

I have seen this (or very similarly described) problems mentioned in many other places, and every solution seems to be both different and not understood using any normal logic. I would partition the drive and install from the console if I could get Gparted to run.

Trying to think of a logical next step but running out of ideas......

---

### Post by Ionedric on 2013-03-24
OK, I promise that this is the LAST post on this subject.

As mentioned, I created a PuppyLinux installation and found that although the DVD drive showed up in the bios hardware list and was listed in the Linux systems info, when I installed a DVD and tried to access the drive, it would not function. The activity light would flash briefly but nothing more. Remember, this is the _same drive that just created the new installation_! I then downloaded 12.04 and burned a CD (rather than DVD as I had done earlier) which, when installed in the CD drive, worked as it should and allowed a normal installation. I'm happy to have found a solution but still not sure of the drive failure mode. This is like watching close-up magic, don't believe what you see happening!

---

