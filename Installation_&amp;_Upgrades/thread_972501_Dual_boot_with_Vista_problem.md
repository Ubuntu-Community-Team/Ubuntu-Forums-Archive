---
title: "Dual boot with Vista problem"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by gufcfan on 2008-11-05
Hi guys, I'm a new convert to Linux and have hit a small problem while attempting to set up a dual boot with vista and ubuntu.

I'm using this tutorial **[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)**

On that page of the tutorial it has 30690 Mb highlighted in red.

When I go to shrink my own c drive, it shows up as only 1082 Mb by default(see below).

[IMG]http://i190.photobucket.com/albums/z246/gufcfan/Misc/shrinkspace-1.jpg[/IMG]

What I would like to know is, will it cause problems if I continue with this shrink? 1082 mb doesn't seem like much.

Thanks in advance :)

---

### Post by cariboo on 2008-11-05
It may be wise to defrag your hard drive at least twice before shrinking your Vista partition.

Jim

---

### Post by gufcfan on 2008-11-05
OK, will do, thanks.

One question though, and the answer is probably obvious but, how does the second defrag make a difference?

---

### Post by gufcfan on 2008-11-05
My question about whether or not doing the shrink is wise? What size would be acceptable, if the 1082 Mb isn't sufficient?

---

### Post by gufcfan on 2008-11-06
> **cariboo907 said:**
> It may be wise to defrag your hard drive at least twice before shrinking your Vista partition.

Jim

I left my PC to defrag a couple of times overnight and now I have hit another problem... When I try to shrink C:/, this is what appears...

[IMG]http://i190.photobucket.com/albums/z246/gufcfan/Misc/shrinkspace0.jpg[/IMG]

As you can see, the "total size after shrink in MB" has changed to zero. All I have done is a couple of defrags. Haven't messed with anything else...

This is what the computer management tab looks like, if it's of any help.

[IMG]http://i190.photobucket.com/albums/z246/gufcfan/Misc/computermanagement.jpg[/IMG]

Would manually adjusting the paging file help? or even be advisable?

---

### Post by kfrancart on 2008-11-06
I had a similar problem in upgrading to ubuntu/kubuntu. The issue isn't if your system is defragged, in windoz the files may be left in the place vista is trying to shrink. The shinking part is looking for a contiguous area to shrink. 

There is a great utility for defragging for free at pc mag utilities:
[http://www.pcmag.com/article2/0,2817,2235831,00.asp](http://www.pcmag.com/article2/0,2817,2235831,00.asp)

Do a defrag of the drive you want to use and then defrag the free space. This will move all of the files into the smallest area available on the drive to the left side as you look at the partition manager. Now when you shrink it you should take care to leave enough free area for any expansion.  

BTW, I'm using a 4th partition on my 2nd hard drive for my Kubuntu - I've also only been doing linux for 2 weeks and I'm not looking back! I had quite a few problems, had to learn about super grub and a lot of terminal commands and found all of the answers here in these forums.

---

### Post by gufcfan on 2008-11-06
> **kfrancart said:**
> The shinking part is looking for a contiguous area to shrink.
I figured that had something to do with it, but wasn't really sure.

> **kfrancart said:**
> ...had to learn about super grub and a lot of terminal commands and found all of the answers here in these forums.
Sorry dude, I don't speak Linux! Yet... :)

---

### Post by caljohnsmith on 2008-11-06
Using Vista's Disk Management is definitely the most ideal way of resizing Vista *if* it works. But if Vista won't let you resize its partition, you could use Ubuntu's partition editor gparted from the Live CD (System > Admin > Partition Editor) to resize the Vista partition; the one small problem with this is Vista maintains its own partition table outside of the MBR (Master Boot Record), so using any software other than Vista's Disk Management to resize Vista can temporarily break Vista and make it unbootable. But in nearly all cases that I've seen in the forums (and there have been many), it is easy to fix Vista's partition table so it will recognize the partition changes, and therefore be able to boot again. Just boot up your Vista Install CD and use the "Vista Repair" option, or if you go to the command line, simply do:
```
bootrec /rebuildbcd
```
And you should be able to boot Vista again. If you don't have a Vista Install CD, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Good luck and let us know how it goes. :)

---

### Post by gufcfan on 2008-11-06
I think I'll go by that route... Ubuntu install disk and break Vista. I like the sound of that. I hate Vista so much, more than Windoze ME even!

---

### Post by gufcfan on 2008-11-06
> **caljohnsmith said:**
> you could use Ubuntu's partition editor gparted from the Live CD (System > Admin > Partition Editor) to resize the Vista partition; 

I'm going ahead with that but, I don't really know how I should resize the partition... this is where I'm at...

[IMG]http://i190.photobucket.com/albums/z246/gufcfan/Misc/gparted.jpg[/IMG]

---

### Post by caljohnsmith on 2008-11-06
Looks good, just type in the new size you want for Vista in that "New Size" field, or use the down arrow key to decrease the size. With the newly created space, I would recommend creating an "extended" partition, rather than a primary partition, so that you can create as many logical partitions as you want with that extended partition. That's because you'll want to create two partitions for Ubuntu, one for the main Ubuntu install, and one for swap.

---

### Post by gufcfan on 2008-11-06
> **caljohnsmith said:**
> Looks good, just type in the new size you want for Vista in that "New Size" field, or use the down arrow key to decrease the size.
I've decreased it by 10000, and it is currently shrinking it.

> **caljohnsmith said:**
> With the newly created space, I would recommend creating an "extended" partition, rather than a primary partition, so that you can create as many logical partitions as you want with that extended partition.
How do I create an extended partition? That's because you'll want to create two partitions for Ubuntu, one for the main Ubuntu install, and one for swap.[/QUOTE]
Ok, so how will I do that?

I have so many questions, I fell like an idiot.

---

### Post by caljohnsmith on 2008-11-06
I think in gparted, if you just click on the unallocated space that you created by shrinking Vista, then go to Partition > New, it should give you the option of what type of partition to create.

---

### Post by gufcfan on 2008-11-06
Oh, OK thanks.

It's still working away but I'll see about that when it's done.

---

