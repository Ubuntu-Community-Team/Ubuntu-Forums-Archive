---
title: "Dual Boot damages Windows partition. Dad will kill me."
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Directive on 2010-05-02
Hello, I have just installed Lucid Lynx on my dad's computer, with a Windows partition. Now, I wanted to access Windows but the following problem happened:

1) Open Computer
2) Grub Menu appears, with Ubuntu First, Memtest second, and Windows XP third
3) Select Windows
4) Windows is launching system recovery
5) Gateway loading (never seen that before)
6) The following message appeared on a blue screen (not the blue screen of death):

Stop c000021a {Fatal System Error}
The session manager Initialization system process terminated unexpectedly
Status Oxc0000013 (0x00000000).
The system has been shutdown.

7) Nothing happens, must hard-reboot computer.

I need help on this or my Dad will Strangulate me with a Pickaxe.[-o<

](*,)

---

### Post by mk1w86 on 2010-05-02
There is a possibility that the Windows boot entry in grub is booting some sort of recovery partition. :-s

Could you please post the output of:

```
sudo fdisk -l
```

to list your partitions and post the contents of your /boot/grub/grub.cfg file.

---

### Post by Directive on 2010-05-02
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27030   217114113+  44  Unknown
/dev/sda2           27030       30402    27083777    5  Extended
/dev/sda5           27030       30257    25918464   83  Linux
/dev/sda6           30257       30402     1164288   82  Linux swap / Solaris


Thanks for the help.

This was written on a live cd by the way.

Thanks!

---

### Post by mk1w86 on 2010-05-02
> **Directive said:**
> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x14cb14cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27030   217114113+  44  Unknown
/dev/sda2           27030       30402    27083777    5  Extended
/dev/sda5           27030       30257    25918464   83  Linux
/dev/sda6           30257       30402     1164288   82  Linux swap / Solaris


Thanks for the help.

This was written on a live cd by the way.

Thanks!

It looks like your Windows partition (/dev/sda1) is not being recognised so the filesystem could be corrupt.  Did you resize the Windows partition during Ubuntu installation?

Also before going any further, is there any important data on the Windows partition that has not been backed up?

---

### Post by Directive on 2010-05-02
> **mk1w86 said:**
> It looks like your Windows partition (/dev/sda1) is not being recognised so the filesystem could be corrupt.  Did you resize the Windows partition during Ubuntu installation?

Also before going any further, is there any important data on the Windows partition that has not been backed up?

yes
yes

thanks again

---

### Post by mk1w86 on 2010-05-02
The corruption was probably caused when you resized the partition, did you defragment it first?  Before making any further changes to or using the disk you should take an image of it to minimise the risk of you loosing your data. 

You can use a tool such as Clonezilla to take an image of your disk, you will need some form of external storage such as an external hard drive or a network share.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Directive on 2010-05-02
DAAAMN IT. That's what I forgot to do, defragment the drive. How does clonezila work?

---

### Post by Jose Catre-Vandis on 2010-05-02
Hope you can recover, but a trip to the timber merchants might be in order (coffin materials :) )

Can you access the Windows partition from Ubuntu. If so, you should be able to rescue any created files. You may need to mount the partition, after xcreating a mount point in /media:
```
sudo mkdir /media/Windows
sudo mount /dev/sda1 /media/Windows
```

It's always best to resize Windows 7 / Vista using its own disk management software, and also to leave it where it is.

---

### Post by Directive on 2010-05-02
> **Jose Catre-Vandis said:**
> Hope you can recover, but a trip to the timber merchants might be in order (coffin materials :) )

Can you access the Windows partition from Ubuntu. If so, you should be able to rescue any created files. You may need to mount the partition, after xcreating a mount point in /media:
```
sudo mkdir /media/Windows
sudo mount /dev/sda1 /media/Windows
```It's always best to resize Windows 7 / Vista using its own disk management software, and also to leave it where it is.

Yes. Using your technique I mounted the windows partition, but it's only like 2GB out of 200GB, instead of like 170 out of 200...

It's Windows XP by the way

I should probably run away while I still can right?8-[

---

### Post by mk1w86 on 2010-05-02
> **Directive said:**
> DAAAMN IT. That's what I forgot to do, defragment the drive. How does clonezila work?

Clonezilla boots in a similar way to a Ubuntu LiveCD, you can boot it from a variety of mediums such as USB flash drives, hard drives or over a network, however the easiest way is to boot it from a CD.  First download and burn the iso like you did for Ubuntu.

Once you have booted from the CD and started Clonezilla you can choose where to save your hard drive image, once you have chosen and given the image a name Clonezilla will copy your entire drive and save it as an image.  You can then restore the image later in case you make a change to your disk trying to recover the data that actually makes it worst. ;)

---

### Post by Directive on 2010-05-02
> **mk1w86 said:**
> Clonezilla boots in a similar way to a Ubuntu LiveCD, you can boot it from a variety of mediums such as USB flash drives, hard drives or over a network, however the easiest way is to boot it from a CD.  First download and burn the iso like you did for Ubuntu.

Once you have booted from the CD and started Clonezilla you can choose where to save your hard drive image, once you have chosen and given the image a name Clonezilla will copy your entire drive and save it as an image.  You can then restore the image later in case you make a change to your disk trying to recover the data that actually makes it worst. ;)

It's bad if the Windows file is just a hundredth of the original file, right?

---

### Post by Directive on 2010-05-02
How do I uninstall Ubuntu?

---

### Post by mk1w86 on 2010-05-02
> **Directive said:**
> It's bad if the Windows file is just a hundredth of the original file, right?

I can't say for sure but like I said earlier, take an image of the drive first.  You will then probably have to look at using a tool such as TestDisk to try to recover your data.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Another thing, remember to keep regular backups of important data in future. ;)

---

### Post by mk1w86 on 2010-05-02
> **Directive said:**
> How do I uninstall Ubuntu?

I wouldn't do this until you've recovered your data.

You're not trying to hide the evidence are you? [-X

---

### Post by allstar123 on 2010-05-02
I am having the same problem only reversed..

---

### Post by Directive on 2010-05-02
> **mk1w86 said:**
> Another thing, remember to keep regular backups of important data in future. ;)

Damn good idea.

How do I use testdisk exactly, I don't get it.

---

### Post by Directive on 2010-05-02
How can I uninstall Ubuntu?

---

### Post by mk1w86 on 2010-05-02
> **allstar123 said:**
> I am having the same problem only reversed..

So your Ubuntu partition is corrupt?  Could you please post the output of:

```
sudo fdisk -l
```

---

### Post by mk1w86 on 2010-05-02
> **Directive said:**
> Damn good idea.

How do I use testdisk exactly, I don't get it.

Unfortunately I can't help you there, hopefully someone else can. :(

I've never actually had to use TestDisk myself.

---

### Post by djchandler on 2010-05-02
Have you tried sudo update-grub from the Ubuntu installation?

People losing the other OS on a hard drive may want to read these:

[http://www.phoronix.com/scan.php?pag...item&px=ODE5Ng]("http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng")

[https://wiki.ubuntu.com/IncidentRepo...for-bug-570765]("https://wiki.ubuntu.com/IncidentReports/2010-04-29-Late-respin-for-bug-570765")

---

### Post by MCVenom on 2010-05-02
> **djchandler said:**
> Have you tried sudo update-grub from the Ubuntu installation?

People losing the other OS on a hard drive may want to read these:

[http://www.phoronix.com/scan.php?pag...item&px=ODE5Ng]("http://www.phoronix.com/scan.php?page=news_item&px=ODE5Ng")

[https://wiki.ubuntu.com/IncidentRepo...for-bug-570765]("https://wiki.ubuntu.com/IncidentReports/2010-04-29-Late-respin-for-bug-570765")
That's a different, entirely unrelated problem :p

---

### Post by djchandler on 2010-05-03
> **BlackOtaku said:**
> That's a different, entirely unrelated problem :p
Yeah, *now* it is an entirely unrelated problem.:P

---

### Post by Doug11 on 2010-05-03
I wonder if you boot with your windows cd and go into the repair console and try a "fixmbr" or something like that. There is also a tool out there that I used to recover a windows from a bad install. It's a general windows recovery disc. It worked well. If I can find it, I will post or pm a link, depending.

---

### Post by Doug11 on 2010-05-03
Directive,,,check your PM.

---

