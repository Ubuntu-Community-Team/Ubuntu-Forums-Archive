---
title: "grub questions"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by klaasvanschelven on 2008-05-02
Hi

What I'm trying to do is have a bunch of partitions for different linux distros which share one home and swap partition. The main reason is that my experience with Ubuntu upgrades is that they may not work well. I then want to be able to go back. In the future I may want to try some different distros side by side as well.

My problem is that Ubuntu (and possably other distros) eat up my menu.list every time, and that the way they influence grub is not clearly defined (at least to me). For every upgrade or kernel upgrade I fear for both my MBR and my menu.lst files, and I generally don't understand well what the behavior is or is supposed to be.
Edit: specifically, I don't understand for a kernel upgrade or full upgrade to which partition's boot directory will be referenced by the MBR or grub.

My most recent attempt to work around this was by creating a seperate boot partition, so that at least I don't have to guess which menu.lst is the real one. However, the second ubuntu just reformatted the first one's boot partition (yes I could have figured that out) so not much was solved.

What is the proper way to attack this problem?

---

### Post by Pumalite on 2008-05-02
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
In general, you can have one /home for different distros using different usernames. Ubuntu lets you choose where to install Grub. Suse doesn't. Install everything else first and Ubuntu last. It will pick up the others and you'll have multiboot. To prevent damage in upgrades, #kopt is important.

---

### Post by klaasvanschelven on 2008-05-02
* You say Ubuntu gives you the option, but I don't remember being asked in any installation procedure or kernel upgrade... what have I missed?

* Having overwritten my Hardy boot partition, is there any way I can restore this without having to do a full reinstall?

* With my new knowledge I will probably want to have the boot directories in the same partition as the distro that goes with it. I assume I have to start with copying the files, I have to tell Grub where to look (this I'll look up)  and I'll have to somehow adapt fstab (just remove the boot line?) Anything I've missed?

---

### Post by Pumalite on 2008-05-02
I can answer your 2 first questions:
1.-Yes. Step 8>Advanced TAB>You can change (hd0) for whatever device you want.
2.-No. If it's overwritten, they are lost.

---

### Post by unutbu on 2008-05-02
I don't think it is necessary to have a separate boot partition (or directory) for each operating system.

Before installing a new OS, you can save a copy of the entire boot partition:

```

cd /
tar cf boot.tar /boot
```

After the OS overwrites /boot, you can 

```

cd /
sudo mkdir oldboot
sudo mv boot.tar oldboot
cd oldboot
tar xvf boot.tar
cd oldboot/boot
cp -iR * /boot

```

Say no to any questions so you don't overwrite any files. Then you'll have to manually edit the menu.lst. Just copy the stanzas from /oldboo/boot/grub/menu.lst (that correspond to the OS you want) near the bottom that start with the word "title".

---

### Post by klaasvanschelven on 2008-05-02
edit: I didn't read unutbu's reply when writing all this, I'll talk about that in the next post...

Thanks, your help so far is much appreciated!

Ok, learned something new (the hard way). I'm trying to understand how it's done right for the future, so let me explain what I'd like to do:

I'll install ubuntu twice (say Gutsy and Hardy) on two seperate partitions, sharing swap and home but each having its boot directory on its own partition. If I do this twice without touching special options, the secondly installed ubuntu's partitions /boot directory should be referenced by the MBR, and this should have magically figured out that there is also another partition, and have a menu.lst accordingly. ubuntu #1 has a dangling menu.lst which contains only 1 option (but is not referenced, so no trouble).

Kernel updates on ubuntu#2 should automagically adapt the right menu.lst, while kernel updates on ubuntu#1 will adapt a dangling menu.lst, which must then be copied to the other partition.... or is there some command that I could run from ubuntu#2 that will pull in updates over all partitions?

Right? ... Right? I hope to finally get this grub thing cause the price for getting it wrong is getting a little too high... again, help so far is much appreciated

---

### Post by klaasvanschelven on 2008-05-02
Hi Unutbu,

Thanks, that's a nice approach... I feel something for a seperate boot partition because I don't feel any particular distro/version should "own" the process and your solution seems to address that.

However, what if the two different distros or versions use the same kernel nr? Would that not automatically lead to a conflict of some kind?

---

### Post by Oldsoldier2003 on 2008-05-02
You can run separate /boot if you please, however sharing the /boot is a disaster and will cause issues. it is especially problematic when you share /boot between distros that are largely different, like Fedora and Ubuntu or RHel And Debian.

If your machine has the brawn you might want to consider running one OS as a VM server and running the other oses as virtual machines. This saves a lot of hassles and means you dont need to rebbot when you want to change Oses.

---

### Post by unutbu on 2008-05-02
If you have the time and inclination, you might want to take a look at 
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

There, Herman shows how you can edit a menu.lst (for the SuperGrub/GParted-Clonezilla/PuppyLinux rescue CD)
so you can boot 3 different operating systems residing on one CD. 

To give you an idea, here are the relevant lines:

```
title Super Grub Disk
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
configfile $(grub_device)/boot/sgd/sgd.lst

title GParted-Clonezilla-2.0
configfile $(grub_device)/boot/grub/menu.lsta

title Puppy-2.16-Seamonkey-Fulldrivers
kernel $(grub_device)/vmlinuz  root=/dev/ram0 pmedia=cd
initrd $(grub_device)/initrd.gz
```

The configfile lines tells GRUB to read another file which is written in the same format as menu.lst! This way you can build a menu system of grub boot options. In your case, this means you could save all the different menu.lst that each OS creates, and link them together with "one menu.lst to rule them all".

---

### Post by klaasvanschelven on 2008-05-02
Thanks... I was also thinking in the lines of
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

a separate grub partition but not boot dir....
I'll read more, try more and will report back at some point :-)

---

### Post by unutbu on 2008-05-02
If Oldsoldier2003 says combining /boot's is a bad idea, I'm inclined to believe him. Please scratch that idea.

Herman's 3 OS's on one CD actually do mix all the files in one /boot directory, so I guess it is possible, but like Oldsoldier2003 warns, it could lead to disaster if there is, for example, an unanticipated name conflict.

I don't have actual experience mixing more than 2 OSs on one hard drive, so it's very possible there are problems I'm not foreseeing.

---

### Post by Pumalite on 2008-05-02
I have 6 OS in 3 SATAII HDD. Separate homes. All have their Grub which I can interchange. All Grubs have all the rest of the OS's in then. Hardy owns the boot loader at the moment

---

### Post by klaasvanschelven on 2008-05-02
A separate grub partition (not boot partition) works like a breeze... menu.lst of the various distros are simply referenced.

Thanks everyone for the kind help

---

### Post by unutbu on 2008-05-02
Thanks for the notice. Would you please provide more details of how you did it?
```

sudo fdisk -l

```

and a listing of menu.lst perhaps? Thanks!

---

### Post by klaasvanschelven on 2008-05-02
No problem:

DISCLAIMER:
think before you type. This is a non checked rant.

I used GParted (available in the live CD as "partition editor" in the admin menu). Created one big virtual partition containing others like so:

```

[sda6][           sda5             ]  ...(empty space). [ sda9 ][ sda8 ][ sda7 ]
```


sda6: 100 MB (though 1 or 10 is probably enough) ext2 (though ext3 is no problem)

sda5 is big home partition (nrs 5 & 6 are a bit weird for historic reasons, on a truly clean system I would simply work left to right and mayby not put everything in a virtual partition)

starting at the right/end:
sda7 = 10G swap
from there on I put my distros right to left, giving each 10G which should be easily enough for"ever"


Install nr 1:
choose your distro > insert CD > walk through the steps;
in terms of partitioning, choose manual, choose the correct mounting for /home (sda5) and swap (sda7) and choose (sda8 ) for /
Note that there's no mention of boot (sda6 ) here.

triple check that the /home partition is not about to be formatted :-)

Get coffee, restart, switching disks, set timezone etc. and:

do install#2 as install #1, but make sure to select the next partition (sda9) for / and reverify all format checks are off.

Now for the interesting part:

after this, mount sda8 and sda6. I then just copied the whole grub directory (from /boot/grub) to sda6. (sudo cp -R /mnt/sda8/boot/grub /mnt/sda6 )

I then replaced the menu section in the menu.lst (on sda6!) by this:
(sda8 menu.lst is unchanged, except for hiddenmenu and timeout settings)

```

title        Ubuntu Gusty Gibbon
configfile   (hd0,7)/boot/grub/menu.lst

title        Ubuntu Hardy Heron
configfile   (hd0,8)/boot/grub/menu.lst
```

hiddenmenu and timeout have been set according to taste.

Finish up with grub:

```

$ sudo grub

```

in the terminal:

```

root (hd0,5)

setup (hd0)

quit

```

note the number 5 which is sda6 in grubspeak

.... that should do the trick, at least, as far as I remember....

---

