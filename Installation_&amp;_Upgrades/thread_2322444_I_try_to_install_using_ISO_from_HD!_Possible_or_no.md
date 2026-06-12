---
title: "I try to install using ISO from HD! Possible or not?"
date: 2016-04-28
forum: Installation &amp; Upgrades
---

### Post by oui on 2016-04-28
Hi

I did download the new Kubuntu ISO and start it with grub from HD with following grub.cfg text:

```

menuentry "Ubuntu64 frugal 16.04" {
insmod loopback
insmod iso9660
set isofile="/kubuntu-16.04-desktop-amd64.iso"
search -sf $isofile
loopback loop $isofile
linux (loop)/casper/vmlinuz.efi locale=fr_FR bootkbd=us console-setup/layoutcode=us_intl iso-scan/filename=$isofile boot=casper file=/cdrom/preseed/ubuntu.seed quiet splash --
initrd (loop)/casper/initrd.lz
}

```

Kubuntu starts willing, operates willing

excepted

intalling!

Different other Linuxe are able to start so (start using grub from iso on the harddisk, and install Linux in graphic mode after the start...).

Is somewhat in my grub.cfg text wrong?

Kind regards

---

### Post by ajgreeny on 2016-04-28
Are you trying to install Kubuntu on the same partition or disk that contains the iso file?

I don't believe that is possible, but I have to admit that I have never booted as iso file from a hard disk, only from a USB multiboot disk, and then installed to a separate HDD; that works the same as any other live system installation..

---

### Post by sudodus on 2016-04-28
I think it is like ajgreeny describes. *Maybe* it works if you read the content of the iso file to RAM, and unmount it afterwards. Use the boot option **toram**

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by grahammechanical on 2016-04-28
If I understand your post correctly you are able to launch the Kubuntu 16.04 live session of an ISO image stored on the hard disk. If the Kubuntu 16.04 live session loads correctly and works correctly, then there can be nothing wrong with the Grub menu entry that you are using.

So, what is the problem? Is the installer failing to install Kubuntu 16.04? Is Kubuntu failing to load after it is installed? What install options are you choosing? Erase disk and install Ubuntu or Something Else? Please explain where you want to install Kubuntu to.

Regards

---

### Post by oldfred on 2016-04-28
Is it complaining about a mounted partition?

I install Ubuntu from ISO on my sdb drive, but boot from sda. And then for some reason it mounts /isodevice to a partition on sda and then will not install. It does offer to unmount partitions, but does not work.

       # Required as /isodevice usually mounts to a partition and installer does not correctly unmount. Boot into live version and in terminal unmount the isodevice.
sudo umount -lrf /isodevice

This says we should be adding the toram parameter:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/684280](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/684280)

---

### Post by oui on 2016-04-29
Hi

I am a step more now as I did make a netinstall from Lubuntu minimal (as it is relatively not slow -I will avoid to say "fast", ah ah ah! in CLI nothing is fast as you can't do other thing excepted turn your thumbs...).

So I will in the future renounce to use KDE: The Lubuntu minimal installation works pretty and is about completely ready to use with all the exigent that I have...

I thank you very much for above answer!

For better comprehension of my initial question:

- I use a DELL Laptop 8 32bit core 8 Gb / 750 GB (initially UEFI converted into DOS file system). I have only 6 partitions sda1 (reactOS as it prefers sda1), sda2 freeDOS32, sda3 extended and in it sda5 little chroot as well as sda6 named "big", it contains all (sda1, sda2, sda5 are experimental) in 700 GB, and sda4. In sda6 are main dirs, 0deb64, a live Jessie Debian 64 bit started and used frugal without to use some "save file" or equivalent and offering about all that, what I did install yesterday in Lubuntu64 minimal excepted pulseaudio, skype, flashplugin and TTF for Asian languages (It is the real reason why I reinstall ;) , no other! But the full installation from 16.04 will give me a great advantage as I can use a bit more modern software and actualize a bit more simply, as I don't need to remaster at all, as that Jessie Debian 64 bit can also be actualized with the same apt-get or synaptic but, as it runs entirely in RAM, it forget the actualization if you don't write it in a new file dotsquashfs. But the size of installation is considerably different! And, as I did say, Jessie is 3/4 y. older and new packages come really slow from Debian (I know: It would be better to use Strech... I have an old installation live Strech Debian 64 bit, but the maintainer will actually abandon the publication as it is a lot of hard job to maintain an unstable version, I can easily admit it.,, Pin on a live and unstable? Hm, perhaps not the best idea to be quite... The third live I have ist my 0LazYUnicorn32, It is a fork from the Ubuntu Utopic Unicorn made by Barry Kauler as Quirky 6.0 (the only one Quirky higher than 5 adapted to the old usage "live frugal start". LazY is a creation of 2 men, a college teatcher and a talented coder to install this (indirect) Utopic Unicorn fork on a park of over 100 all PC's in a school for adult young pupils (technical school), also an exigent people. LazY comes from Lararus as this big programming language has to be available and run as well as over 300 app's about all more or less interesting in education. See Puppy forum, especially the German division where the over 1000 messages long initial discussion to elaborate LazY Puppy, the initial version, is to find completely open to read for interesting men having to do such a great development! My next main dir is 0puppy. I put in it the vmlinuz and initrd.somewhat won opening the divers Puppy ISOs that I will test as discover the ideas of those hobby coders is a part of my hobbies! The last is 0slitaz for the same reason: It start live frugal the base and, as SliTaz is started, I can install SliTaz full on sda5, my chroot, as a full install is really better: SliTaz is a great system maintained by a little staff from idealist, especially, now a great hobby coder answering with best patience all questions on the SliTaz forum. SliTaz is the best Swiss Knife on the Linux world...

Next Dir is 1brother, yes I need a fast and direct access to complete cups... And 1hidden: templates collection for stuff like grub.cfg, .jwmrc, .twmrc, etc. Other entries in the root dir under 1... concern only links to my main dir name /ym ("my" writen from right to left).

This organisation is important:

In the middle are all dir's /bin .. /var of the only one full installation I have on the hard disk! I can so clean the hard disk from that installation without risk for my data and have never to change the partition ;-) (excepted i I really use a real chroot (it is of course possible to chroot into a simple dir or subdir also using "mount": See instructions to build NuTyx, an automatized compilation system for the base of LinuxFromScratch. But, as NuTyx recommends implicatly, I prefer to compile outside my big partition...)

Why all that gymnastic?

Because I did loose to much data in the past using external memory and distributing the data on all the surface of my hard disk(s, at the time where more disk were better)... I did loose data impossible to recover as all data from PC from my dead father. And producers of external memory do extremely rarely somewhat useful to avoid such ruination of data: See micro memory cards! Did you find some pencil able to write with fine writing on the black surface of those things? I not. The (it names itself so) most important European of office material had nothing to propose me (only a pencil Paint marker edding 750 "white" that is about nonsens on USB sticks or cards for USB adapters: The writing is absolutely not fine enough!). Next question: Why are a lot of stick without some surface dedicated to write on it (like the underwriting field on Credit cards)? Why not. Next question: Are we not a really terribly poor civilization to wast the environment with a terrible quantity of absolutely superfluous hardware like sticks? I have perhaps 100 sticks and cards in my house (where 4 persons did live, we have two children living today outside but her old usb sticks stay here). excepted 5..10 pieces of them actually stick in the phone devices, the most have a poor size and speed: We will never use them any more although they are without doubt completely ok - they are detritus.

GNU, with the bad conception of grub (yes: gnu is the owner ;-) ) causes one of the major source of pollution and wastage of material (such memory cards contains precious material not being able to be produced a long time for an exploding world population!)...

And each one using software solution requiring the unconsiderate use of the middle.

Over the anxiety for data security the environmental problem is giant...

---

### Post by oldfred on 2016-04-29
Bit hard to read your long rant. 

> Why are a lot of stick without some surface dedicated to write on it (like the underwriting field on Credit cards)? Why not.
+1 I was just thinking the same thing. And I only have 5 or 6 flash drives.

I also was housecleaning and found a sheet of floppy drive labels. But they are a bit large.
I put a small label with a code and then made a list of the codes & what was on flash drive.

---

