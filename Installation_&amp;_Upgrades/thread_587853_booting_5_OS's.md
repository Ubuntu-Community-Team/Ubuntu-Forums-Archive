---
title: "booting 5 OS's"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by uknowho008 on 2007-10-23
whats up guys? i just ordered some parts to put together a new computer for myself. heres whats on its way.

MB ASUS A8V-VM SE K8M890 939
CPU AMD|A64 X2 4200+ 2.2G 939 90N
A64 COOLER |ARCTIC FREEZER 64 PRO R
DDR 2GB 3200 DUAL KINGST (2X1GB) SPEED 400MHz
CASE APEVIA(ASP)|X-QPACK-NW-BK/420
HD 160G|WD 7K 8M SATA2 WD1600AAJS

well anyway when it gets here i would like to set it up to boot 2 xp, 1 vista, 1 OS X, and ubuntu. i have seen plenty how-to's on booting xp, vista, os x, and linux. but im a little worried about the whole "primary" partition thing. lixux is supposed to run just fine on an extended partion if i read correcty, but im not so sure about the others and at least one other OS is going to need to be put on an extended partition. so can anybody give me some input on the possibility of this as well as a few pointers if you could. also if anybody has any recommendations on what they think is the best way or "how-to" to follow.

by the way the reason i want to copies of xp is because ill be doing recording in protools which doesnt work well with antivirus and such installed. so i like to set up a seperate xp to run all of my music and video editing software on. plus it just makes it a lot nicer to have it seperate for me.

i will also have a 500gb SATA hard drive to store all of my data on.

thanks for all the help and reading through by long post (if you did).

---

### Post by Shazaam on 2007-10-23
Linux runs fine in an extended partition. At one time I had XP on a Primary partition; dsl (damnsmalllinux), PuppyLinux, Mepis, Mandriva and Ubuntu (inside an extended partition) installed on one 80gig drive. I have since put XP on one drive and my linux flavors on another drive because I was tired of Windows problems that required a reinstall.

Partition sizes (80gig drive)
XP= 30gig

Extended= 50gig

Linux logicals (inside extended)
Shared swap= 1gig
dsl= 1gig
Puppy= 5gig
Mepis= 10gig
Mandriva= 10gig
Ubuntu= the rest of the extended partition.

---

### Post by uknowho008 on 2007-10-23
i understand that linux runs fine from an extended partition but my problem is  either one of my xp's, vista or OS X is going to need to be on an extended partition because i can only have 3 primaries and some extended otherwise im limited to only 4 primaries and no extened right? so i need to know if i can install one of the other os's on an extended partion as well as linux.

---

### Post by uknowho008 on 2007-10-23
anybody?

---

### Post by psusi on 2007-10-23
Doesn't OSX only run on macs?  You're going to have to return all that nice hardware and go hit the apple store I think for that one.  As for the others, I'm fairly sure that windows must be installed to a primary partition.

---

### Post by DagonSphere on 2007-10-23
I was able to get XP installed on the Primary partition, with Ubuntu installed somewhere else (can't remember if it was a primary or extended partiton)

*nix variants are very flexible in terms of installation, so no problems there.  Windows likes to be installed on the first partition of the first hard drive.  I don't know if Vista 'plays nice' with other OS's.

Here's the approach I've used in the past.

Each copy of Windows would reside on its own hard disk.  When installing Windows, remove all disks except the one being installed to.  When installation completes, swap drives and repeat.

When installing your first Linux, load up all drives and proceed to install.  After installation, check out your Grub menu.lst file.  Because Windows likes to be first, you may have to modify the Windows entries 

```

root (hd1,0)
chainloader +1
map (hd0) (hd1)
map (hd1) (hd0)
```

The above code will trick your computer into thinking the second hard drive is really the first.  More info here:  [http://www.gnu.org/software/grub/grub-faq.en.html](http://www.gnu.org/software/grub/grub-faq.en.html)

I've never tried to install several Windows variants on a single drive, but I have a feeling it's not possible, or very difficult to do.

As an option, perhaps you could install Windows inside of a VMware server running on Linux.  That is, if you're not looking to run advanced games :)

HTH

---

### Post by uknowho008 on 2007-10-23
right now (on my old machine) im running 2 copies of xp and one ubuntu off the same hard drive and its actually very easy. and you can run OS X on a pc now since apple now uses intel chips. so im farely certain that all of these OS's will run on my new system, i guess im just going to hope OS X doesnt mind running on an extended partition.

also: lots of people have successfully quad booted xp, vista, OS X and linux. so the only worry i have is having 2 XP's because i cant have anymore primary partitions.

---

### Post by DagonSphere on 2007-10-25
Well, my dual booting experience is definitely outdated.  It's been well over a year since I did it last.

I have no clue as to whether Windows will install on an extended partition.  I can't be of help there, but my first instinct tells me that it can't.  All you can do is try.

I'm also guessing that OS X will run in an extended partition, considering that it's now Unix based.

Good luck!!

---

### Post by snickers295 on 2007-10-25
Well if OS X is Unix based it should run on a extended partition.
That sounds like a gamble to me to boot 5 OSes but hey, I used format my hard drive weekly from playing around on one system:).
Oh and they do have OS X for Intel computers now.

---

### Post by DagonSphere on 2007-10-25
The only gamble is having more than 3 installs of Windows on a single hdd.  Perhaps the way to go is to try to install Windows into an extended partition first, before installing anything anywhere else.

And now for my 2 cents worth:

I'm not sure how the windows installer will create the partitions, so would it be worth creating a partition table from a Linux Live CD?

When I dual || tri booted, I always had Windows on its own disk, with its own boot loader in the MBR of that disk.  I looked at it as a safety.  If any other OS install got hosed, I could remove all other disks and reinstall just that OS.  This pertains more to Windows, as the flexibility GRUB/LILO gives you far surpasses NTLDR - IMO.

And lastly, if this is your only computer, perhaps testing the 5 boot scheme inside of a virtual machine would be worthwhile.  Not to mention, if you want to do something in the future, you can experiment on the virtual machine and establish your methods.  VMware Server has a nice snapshot feature that allows you to 'roll back' to a snapshot, which would save you hours of reinstalling everything to get back to a working system.  This has saved me a lot of headaches!!

---

### Post by ejket on 2007-10-25
> **snickers295 said:**
> That sounds like a gamble to me to boot 5 OSes

Not really.  I was booting 6 until I replaced debian sid with gutsy yesterday -- now I'm only booting 5 ...

For some reason GRUB fails silently trying to load the kernel.

---

### Post by mrfelker on 2007-10-25
Hard disks can only use 4 partitions but the 4th can be an extended partition which can consist of as main "volumes" as you wish.  As I said in a post I just made to an earlier subject install windows xp to a primary first.  You can install Vista either to a primary or a volume - but only on the first disk.  Linux can install on either hard disks and doesn't care if its primary or an extended volume.  As to Mac OS I have never used it so I don't know its partition requirements.  I do know that Apple has a program called BootCamp which allows for dual booting OSX and Windows.  I'm particularly in the dark because OSX is now essentially UNIX.  

If you really want to install 5 OS's I highly recommend  BootITNG from TerraByteUnlimited.
You can get a trial (and uninstall it if you don't like it) then you have to buy a S/N.  Works absolutely great for me as a multiboot loader, partition editor, and image creator.  Also there is an active forum, mailing lists, and the staff is highly responsive to questions.

---

### Post by uknowho008 on 2007-10-27
thanks for the feedback guys. i got all my new stuff set up so im gonna try and get it going. i figured os x might be able to run on an extended partition as well because it is unix based. so well see if it all works out. ill let you know about my success.

---

### Post by uknowho008 on 2007-10-27
well im having problems running os x just by itself so i dont know if im going to even get a chance to try booting all of the os's. im getting and error after the install is finished "unable to find driver for this platform: 'acpi'"

that was with os x 10.4.8 so im gonna try 10.5 and see what happens.

---

