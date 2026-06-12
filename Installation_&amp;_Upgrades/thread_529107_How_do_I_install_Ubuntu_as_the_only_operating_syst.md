---
title: "How do I install Ubuntu as the only operating system?"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by Roberto80 on 2007-08-18
My brother has  a computer resurrected from the depths of a dumpster and decided to play with the Windows XP Pro system folder and delete a bunch of "spare" files. You know, those files that have the same name. It seems he decided to clean house and delete half of the operating system. He wondered why it didn't start up the following day. Long story short: He though formating the hard drive would solve everything. No operating system.

Since it is now my task to get this thing going, I decided to try and install Ubuntu. Seems the iso file that's so widely distributed only works on computers that have windows installed. Is this correct?

Is there any way to install Ubuntu on a clean hard drive?

Thanks!

---

### Post by maybeway36 on 2007-08-18
Burn the iso, boot it up, and when it installs, tell it to use the whole hard drive. It works just fine :)

---

### Post by merlinus on 2007-08-18
You might post system specs for advice on which flavor of ubuntu to install.

There are minimum hardware and RAM requirements.

-merlin

---

### Post by mister harbies on 2007-08-18
I am only running Ubuntu on my computer. No Windows.

Just burn the ISO onto a DVD (or was that CD?). Boot up the computer to read from CD drive and it will prompt to install. Its pretty straightforward.

Enjoy

---

### Post by Roberto80 on 2007-08-18
I thought it would have been that straight forward. I remember installing Lindows a few years back just the same. There's another problem with this thing then. I tried just that, burned a boot on a CD-ROM, told the BIOS to boot from the CD drive and bang, I'm at a DR-DOS prompt.

As for specs: AMD Athlon (not sure of the speed. I'll have to boot it up to check tomorrow)with 256M RAM. Original OS looks like it was Windows ME. When he booted it up for me prior to his "house cleaning" I remember seeing Windows XP Pro and was quite surprised that he found it in a dumpster.

I tried booting it from the DOS prompt but it says disk is write protected... That reminds me of the 3.5 floppy days. And I wasn't writing anything to the disk either. Lets see... where the heck is the write protect tab on these new fangled round disks, eh?

Thank you for the replies. They are very helpful. I thought I was doing the wrong thing. I might be still. Any suggestions?

---

### Post by Dark Star on 2007-08-18
> **mister harbies said:**
> I am only running Ubuntu on my computer. No Windows.

Just burn the ISO onto a DVD (or was that CD?). Boot up the computer to read from CD drive and it will prompt to install. Its pretty straightforward.

Enjoy
Same here :D Have used Windows Cd to parttition HDD then installed Ubuntu on 1. btw can any 1 suggest a partitionar like WIndows Cd ?

---

### Post by merlinus on 2007-08-18
With 256MB RAM you will need to install from the Alternate text-based cd.

Also, make sure you burn it as a disk image, not a data disk, at no more than 4x speed.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by merlinus on 2007-08-18
> 
btw can any 1 suggest a partitioner


gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by Dark Star on 2007-08-19
> **merlinus said:**
> gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin
Thanks a ton :)

---

### Post by Roberto80 on 2007-08-19
Oh man, merlinus! Thank you very much! I'm downloading it right now! I'm going to give it a try ASAP!

I have another question: I'm going to install it as its only OS. The HDD is totally wiped clean so it was an easy task of reformatting it from NTFS to FAT32, but do I really need to partition the HDD still?

Thank you very much once again!

---

### Post by merlinus on 2007-08-19
No.  During installation, you will be offered a few choices at the partitioning menu.  Choose use entire disk, and format as ext3.

The partition created will be / (also known as root). 

If you like, depending upon space, you can create a separate partition for /home, which is where your data, preferences and configurations will be stored.

If you choose this, set aside 10-12G for /.

And a /swap partition will be created automatically  It need be no larger than 1.5G.

-merlin

---

### Post by Lord Illidan on 2007-08-19
> **Roberto80 said:**
> Oh man, merlinus! Thank you very much! I'm downloading it right now! I'm going to give it a try ASAP!

I have another question: I'm going to install it as its only OS. The HDD is totally wiped clean so it was an easy task of reformatting it from NTFS to FAT32, but do I really need to partition the HDD still?

Thank you very much once again!
Yep, but it will handle it for you automatically. 256 mb is a bit low, though. Either use Xubuntu or else get some more RAM. 512 mb is good enough. On 1 gig, above it flies.

---

### Post by Roberto80 on 2007-08-19
Thank you very much, everyone! Worked like a charm! I did a quick lookthrough and I think I'll be installing Ubuntu on my laptop! Its a Toshiba Satellite 5105-S501, 1.2 GHZ P4 m with 1Gb RAM, 120Gb HDD. Think I could use the regular DL or should I go text based with this one as well?


Thank you very much, once again!

---

### Post by merlinus on 2007-08-19
Depending upon the video card, you may run into install problems.  The alternate will be easier.

The only advantage of the live cd is "try before you buy," so to speak.

-merlin

---

### Post by ubuntu27 on 2007-08-19
Hello Roberto.


Read this guide on [How to download and burn properly an iso ]("http://www.psychocats.net/ubuntu/iso")(disk image)


[How to install using the Desktop CD]("http://www.psychocats.net/ubuntu/installing")

[How to install using Alternate CD]("http://users.bigpond.net.au/hermanzone/")


Oh, yes! Maybe you will want to read about [How to make partition that suits YOUR NEEDS]("http://www.psychocats.net/ubuntu/partitioning")

---

### Post by Roberto80 on 2007-08-20
Awesome! Thanks!

---

### Post by ubuntu27 on 2007-08-20
Hola Roberto.

Since you want to have Ubuntu as the ONL (1) Operating SYstem in your computer.

I recommend you to use the Alternate CD to install it.

WHen you have the alternate CD (text based installed) after download the iso and burning it.  

Just select default install when it comes to ask about the partition. Let it erase everything on your hard drive.

That is all :)

Links for Ubuntu download:

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

### Post by Mach1US on 2007-08-20
Default Linux system needs at least one root partition and swap space.
Secondly Fat32 is not a good choice for it , you should use Ext3 for it.
The best choice for you is to delete any partitions and let the partitioner set up your system for you.
After you boot into ubuntu cd click on install go through some basic time and such configurations and when you reach partitioner select USE ENTIRE DISC and it will do it all for you.

Partitioner included in default ubuntu cd is similar to Partition Magic.

---

### Post by maybeway36 on 2007-08-20
Its actually not possible to use FAT32 as the root partition, because Linux depends on file permissions.

---

