---
title: "Unable to install Ubuntu"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by tehDeuce on 2007-02-10
I am trying to install Ubuntu on a new computer of mine, but I am running into a major problem.  Here is a link to the exact computer that I am using: [http://pc.ncix.com/ncixpc/ncixpc.cfm?uuid=E6E4DFD9-1018-119B-8BB760567E61A7CD-1277810](http://pc.ncix.com/ncixpc/ncixpc.cfm?uuid=E6E4DFD9-1018-119B-8BB760567E61A7CD-1277810)
As the live cd starts to boot, it suddenly takes to to a black screen which says:
```
BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)
```

I am positive that it is nothing to do with the cd I am trying to install with, as I have tried it with several different cds (Ubuntu and Kubuntu), some of which have installed on different computers. 
I have tried installing more errors.  Here they are (in case they might help diagnose the problem):
```
>> No bootable medium found.  Waiting for new devices...
>> Attempting to mount media:- /dev/sda
>> Attempting to mount media:- /dev/sda1
umount: Couldn't umount /newroot: Invalid argument
!! Could not find CD to boot, something else needed!
>> Determining root device...
!! The root block device is unspecified or not detected.
>> Please specify a device to boot, or "shell" for a shell...
boot() ::

```
At first I thought it was a problem with my dvd+rw drive, but I tried swapping it with a cd drive from an older computer and I got the same errors.

If I try to use the alternate install cd, it fails to detect my dvd+rw drive, and asks me to choose a module to use.

Thank you for any help.

---

### Post by laidback on 2007-02-10
I don't now the answer but I would check (not in order):-

CD/DVD in another machine to check it works (think you've done that)
BIOS settings to allow booting from DVD
Cables to DVD are correctly installed/attached and aren't damaged
Any jumpers on back of DVD are sensibly set (I've never had to change mine so I don't know       what they actually do, but DVDs seem to have them in a similar way to hdd's)
That you can boot from some other bootable CD
That the DVD you're using to boot from is in the correct position on the IDE cable (I believe it should be on the end of the cable, secondary one uses the middle attachment plug)
If possible use the DVD drive from the PC, can you play music, read files?, i.e. does it actually work when installed.

I just work through the issue eliminating all sources of error, one by one.

Not much help I'm sure but it may clear the mind.

---

### Post by tehDeuce on 2007-02-10
> **laidback said:**
> I don't now the answer but I would check (not in order):-

CD/DVD in another machine to check it works (think you've done that)
BIOS settings to allow booting from DVD
Cables to DVD are correctly installed/attached and aren't damaged
Any jumpers on back of DVD are sensibly set (I've never had to change mine so I don't know       what they actually do, but DVDs seem to have them in a similar way to hdd's)
That you can boot from some other bootable CD
That the DVD you're using to boot from is in the correct position on the IDE cable (I believe it should be on the end of the cable, secondary one uses the middle attachment plug)
If possible use the DVD drive from the PC, can you play music, read files?, i.e. does it actually work when installed.

I just work through the issue eliminating all sources of error, one by one.

Not much help I'm sure but it may clear the mind.

I have tried switching the dvd+rw drive with a cd drive, and that did not fix it, so I do not think the problem is anything to do with the drive itself.  I was able to install Windows from a cd with the drive, and it has no problems reading and writing inside Windows.

I was told by a friend that it may be related to "motherboard drivers".  I am not aware of what he is referring to, but it might jog someone's memory.

---

### Post by pay on 2007-02-10
Try burning the disc at a lower speed. Your friend was probably refering to the bios.

---

### Post by jcbkr on 2007-02-10
I'm have the same type of issue with a system that I built from scratch. Have to believe the issue is with the serial ATA ( sata) hard drives. These do not connect the same as an IDE drive which your DVD and CD drives would be if they are older. Windows installed without a problem but when I was out of options with Ubuntu. I even tried SUSE and Gentoo before resorting to Windows. If I can find a solution I will let you know. Or if someone who reads this thread can assist with installing to a single SATA hard drive we can create documentation for it as these hard drives are quickly becoming the new standard for booting pc's.

---

### Post by laidback on 2007-02-11
Funny you should mention SATA. In this thread a correspondent named reiki seems to be getting on well with Sata:-
[http://www.ubuntuforums.org/showthread.php?t=358274](http://www.ubuntuforums.org/showthread.php?t=358274)

worth a look.

Could you insert an IDE drive and install onto that in the first instance, then move over to the Sata? reiki may have some ideas.

---

### Post by trustno12003 on 2007-02-12
Hello

I have the same problem with kubuntu 6.10 live cd. I've been looking for a solution in several  forums and I haven't found anything. I've also got a SATA hard drive, in which I want to install the distro. I suppose the problem is related with this, but I can't see why the Live CD does not boot, because it should boot from the CD-Rom. I hope someone will be able to give us a clue or I will have to use 6.06.

Best Regards

---

### Post by serlex on 2007-02-14
anyone got solution to this? trying to install feisty, goes as far as
```
 (initramfs)
```
 seen people edit grub, but where the hell is it in the download

---

### Post by tehDeuce on 2007-02-18
Sorry for bumping this topic, but can anyone offer any help?  I am unable to hook up an IDE drive at the time, and I really want ubuntu (or any linux distro really) on this computer.

---

